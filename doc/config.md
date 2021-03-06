    {
        指牌谱分析使用的语言。目前仅对应中文和基本不能读的英文
        "language": "zh-CN",

        指牌谱来源。目前来源均为雀魂
        "source": "majsoul",
        
        要分析的id。如果id留空，那么会查找data/{source}/*的第一个文件夹作为id
        "id": "",
        
        过滤器参数，用于从所有牌谱中筛选出想要分析的牌谱
        "filter":{
        
            包含过滤器。除了时间外其他均为一个数组。当数组为空，则认为过滤器不存在，所有牌谱都通过判断。若数组不为空，则牌谱必须满足所给出条件中的一个。
            例：room=[1,2] round=[8]则牌谱房间类别必须是1或2，且回合数为8才会被认为满足条件。
            "include": {
            
                ID信息。由于一局对局有多个人，只要任意一人的ID和列表中ID匹配即认为匹配。
                "id": [],
                
                昵称信息。与ID类似，比较昵称。
                "name": [],
                
                牌谱来源。目前牌谱仅为单来源。
                "source": [],
                
                房间级别。对于雀魂牌谱规定如下：0=友人 1=铜 2=银 3=金 4=玉 5=王座
                "room": [],
                
                玩家数，即三麻还是四麻。目前只能解析四麻。
                "player": [],
                
                回合数。1为一局胜负，4为东风场，8为南风场。
                "round": [],
                
                速度。仅通过每次出牌独立用时判断速度，不考虑共享秒数长短。目前规定：fast=3, normal=5, slow=60
                "speed": [],
                
                时间戳。牌谱的对局结束时间需为after之后，before之前。
                "timebefore": "2099-12-31 23:59:59",
                "timeafter": "1970-01-01 08:00:00"
            },
            
            除外过滤器。项目和包含过滤器相同。如果数组为空则不会除外任何牌谱。如果不为空，只要满足其一就会被除外。
            例：room=[1,2] round=[8]则牌谱房间为1或房间为2或回合数为8均会被除外。
            "exclude": {
            
                ID和昵称只要参加玩家其一满足就会除外。
                "id": [],
                "name": [],
                
                "source": [],
                "room": [],
                "player": [],
                "round": [],
                "speed": [],
                
                时间戳需要注意的是，并不是after和before之间的牌谱会被除外，而是只要该牌谱时间早于before或者牌谱时间晚于after就会被除外。如果after时间早于before时间那么所有牌谱都会被除外。
                "timebefore": "1970-01-01 08:00:00",
                "timeafter": "2099-12-31 23:59:59"
            }
        }
    }
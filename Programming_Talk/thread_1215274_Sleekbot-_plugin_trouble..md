---
title: "Sleekbot- plugin trouble."
date: 2009-07-17
forum: Programming Talk
---

### Post by CJ Master on 2009-07-17
This topic was for getting help, but I figured it out by myself. So now I'm going to share with you guys my noobtest plugin!

Pastebin entry here: [http://pastebin.com/f1401c0bb](http://pastebin.com/f1401c0bb)

```
import random
import string

class noobtest(object):
    def __init__(self, bot, config):
        self.bot = bot
        self.config = config
        self.bot.addMUCCommand('noobtest', self.handle_noobtest)
        self.bot.addIMCommand('noobtest', self.handle_noobtest)
        self.bot.addHelp('noobtest','Noob Tester', 'Test the noobiness of a person.', 'noobtest [person]')

    def handle_noobtest(self, command, args, msg):
    
        if args == "":
            return "%s is 0 percent nooby." % (self.getRealNameFromMessage(msg))
        else:
            return "%s is %s percent nooby." % (string.rstrip(args), random.randrange(0,100))
        
        
    def getRealNameFromMessage(self, msg):
        nick = None
        if msg['type'] == 'groupchat':
            if msg['name'] == "":
                            #system message
                nick = None
            else:
                 nick = self.bot.getjidbare(msg.get('name', ''))
        else:
            nick = self.bot.getjidbare(msg.get('name', ''))
        return nick
```

---

### Post by CJ Master on 2009-07-17
<Ignore this post>

---

### Post by CJ Master on 2009-07-17
I fixed it, look at first post for source code! Licensed under GNU GPL v3.

---


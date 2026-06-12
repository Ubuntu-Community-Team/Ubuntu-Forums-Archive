---
title: "How to close a terminal with a python script?"
date: 2009-06-20
forum: Programming Talk
---

### Post by [o_0] Rob on 2009-06-20
I'm using cron to run the command
> python myscript.py args

The script runs OK, but it leaves a terminal open with message
> Press ENTER to continue and close this window.

I would prefer not having an useless terminal stay open.

1. What can I add to the python script to get the terminal to close? The script is probably not relevant but if you're interested it can be seen [here]("http://dev.deluge-torrent.org/ticket/382#comment:4").
2. Alternatively, what can I add to the cron command? I've tried adding "exit" but it doesn't help.
> python myscript.py args | exit

I suspect the solution is trivial, but I'm new to ubuntu and programming. Thanks in advance for any help :)

---

### Post by Cammy on 2009-06-20
killall gnome-terminal ?

---

### Post by [o_0] Rob on 2009-06-20
> **Cammy said:**
> killall gnome-terminal ?

Thanks for the help Cammy :)

I've just tried that. It closes every terminal that may be open though, so it's not ideal. Is there a way to only close one terminal?

---

### Post by kaivalagi on 2009-06-20
Try adding an exit(0) underneath the set_config line in the script as below. It might work...worth a try...

```
#!/usr/bin/python
from sys import argv, exit
import logging

logging.disable(logging.ERROR)

if (len(argv) < 2):
    print "Need value for max_active_limit"
    exit(2)

if (argv[1].isdigit()):
    from deluge.ui.client import sclient as client

    client.set_core_uri()
    client.set_config({'max_active_limit': int(argv[1])})
    **[COLOR="Green"]exit(0)[/COLOR]**

else:
    print "Invalid max_active_limit value"
    exit(3)

```

---

### Post by pokerbirch on 2009-06-20
Surely the script should exit on it's own, without needing to explicitly use the Exit() command? I would check the code in your script. Something is not right.

---

### Post by [o_0] Rob on 2009-06-20
> **kaivalagi said:**
> Try adding an exit(0) underneath the set_config line in the script as below. It might work...worth a try...


Thanks kaivalagi; unfortunately no luck.

After some more searching, I've found someone with the same problem [here]("http://ubuntuforums.org/showthread.php?t=1113168"). No solution though.

---

### Post by [o_0] Rob on 2009-06-20
Thanks for everyone's suggestions. I've found a very trivial solution. Add "&& exit" to the cron command.

---


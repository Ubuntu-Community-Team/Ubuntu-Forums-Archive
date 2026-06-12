---
title: "Xchat and cronjob?"
date: 2015-06-15
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-06-15
Hello guys
Let's that I'm chatting on a random channel from a random  network and I wrote the word "hello" I can send it right now by pressing  the button "Enter" but no this is not my intention. What I want is to  schedule the sending of messages after a specific amount of time, for example 5 minutes after I've written it, or a specific hour, for example, I've written it at 5 p.m. and I want it to be automatically sent by the time of 6 p.m.
I hope that my intention is clear believe me I try my best to simplify the idea.
Thanks for reading

---

### Post by kostkon on 2015-06-15
You can do that by creating and using a script in xchat with [one of the supported languages]("http://xchat.org/docs/") that are supported by its interface, but since I've got some experience with it, I made a simple one for you. I didn't test it so you'll have to run it and see if it works. If you want to have it auto load when xchat starts, save the code as e.g. myscript.py, make it executable and then copy it to your ~/.xchat2 folder.

```
#!/usr/bin/python

import xchat

__module_name__ = "Delayed Message Announcer"
__module_version__ = "0.1"
__module_description__ = "Sends delayed messages"


def _delayed_message_cb(word, word_eol, userdata):
    try:
        msg, dtime = word_eol[1].split("|")
        xchat.hook_timer(int(dtime)*1000, _timer_cb, [msg, xchat.get_context()])
    except Exception:
        xchat.prnt("Try again: /dmesg message|time(in minutes)")
    return xchat.EAT_ALL

def _timer_cb(userdata):
    cmessage = userdata[0]
    ccontext = userdata[1]
    ccontext.command("msg %s %s" % (ccontext.get_info("channel"), cmessage))
    return False

xchat.hook_command("dmesg", _delayed_message_cb, help="/dmesg message|time(in minutes)")
```

Hope it works.

---


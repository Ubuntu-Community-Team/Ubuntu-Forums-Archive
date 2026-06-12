---
title: "broken pipe error"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by steven30 on 2014-04-08
When i restart I see a broken pipe error. It doesn't stay on my screen long enough to read everything else. The restart seems to work successfully. I don't get the error when it boots, only when it shuts down on a restart. **[COLOR=#ff0000]Is this anything to be concerned about?[/COLOR]**

---

### Post by Kirboosy on 2014-04-09
Welcome to the forums!

I don't think this could be anything to worry about. Are you leaving programs running while restarting? This could trigger broken pipe errors

~Caboose

---

### Post by steven30 on 2014-04-09
> **Caboose885 said:**
> Welcome to the forums!

I don't think this could be anything to worry about. Are you leaving programs running while restarting? This could trigger broken pipe errors

~Caboose

Just tried the restart--twice--without launching any programs. Still got the "broken pipe" error. Several other messages follow, but are gone before I can read them. :confused:

---

### Post by slickymaster on 2014-04-09
Do you remember if any of the messages were something like this:```
could not write bytes: Broken pipe

* Stopping save kernel messages...                               [ok]
* Checking battery state...                                          [ok]
* Stopping system V run level compatibility...                  [ok] 
```

---

### Post by steven30 on 2014-04-09
> **slickymaster said:**
> Do you remember if any of the messages were something like this:```
could not write bytes: Broken pipe

* Stopping save kernel messages...                               [ok]
* Checking battery state...                                          [ok]
* Stopping system V run level compatibility...                  [ok] 
```


Saw something about "battery."  These message appear and disappear so quickly, I can't read them. Since reading your reply I have tried rebooting a few times and I simply can't read the messages fast enough to verify whether they match the messages you gave. Is there anyway to freeze them long enough to read them? I'll keep trying, but give me some time, because it's rather cumbersome and frustrating to keep rebooting and then failing to read them...:(

---

### Post by slickymaster on 2014-04-09
> **steven30 said:**
> Saw something about "battery."  These message appear and disappear so quickly, I can't read them. Since reading your reply I have tried rebooting a few times and I simply can't read the messages fast enough to verify whether they match the messages you gave. Is there anyway to freeze them long enough to read them? I'll keep trying, but give me some time, because it's rather cumbersome and frustrating to keep rebooting and then failing to read them...:(

Your boot messages should be in **/var/log/demesg**. There's no need to constantly rebooting your computer.

---

### Post by steven30 on 2014-04-09
> **slickymaster said:**
> Your boot messages should be in **/var/log/demesg**. There's no need to constantly rebooting your computer.


I don't see this "broken pipe" message at all in demesg.  It looks like these are messages from the boot up; but I am getting the "broken pipe" message on the "shut down" phase rather than the "boot up" of a restart.  

Someone elsewhere suggested that the system is unable to save messages issued on the "shut down," and that I should try video recording the messages. Not sure I'm adept enough with my camera to do this. :(

---

### Post by slickymaster on 2014-04-09
> **steven30 said:**
> I don't see this "broken pipe" message at all in demesg.  It looks like these are messages from the boot up; but I am getting the "broken pipe" message on the "shut down" phase rather than the "boot up" of a restart.  

Someone elsewhere suggested that the system is **_[COLOR=#ff0000]unable to save messages issued on the "shut down,[/COLOR]_**" and that I should try video recording the messages. Not sure I'm adept enough with my camera to do this. :(


Try looking in **/var/log/kern.log**

---

### Post by steven30 on 2014-04-09
> **slickymaster said:**
> Try looking in **/var/log/kern.log**


Just checked kern.log, but no luck there either. Can't find "broken pipe" or any of the three messages you quoted earlier. Do I need to get out my camera?

---

### Post by slickymaster on 2014-04-09
> **steven30 said:**
> Just checked kern.log, but no luck there either. Can't find "broken pipe" or any of the three messages you quoted earlier. Do I need to get out my camera?

In this case I would assume that getting your camera would be the faster solution.

---

### Post by steven30 on 2014-04-09
> **slickymaster said:**
> In this case I would assume that getting your camera would be the faster solution.

I actually filmed the reboot! Apparently, I'm no longer getting the "broken pipe" message. However, since starting this thread, I did a GRUB boot selecting **repair packages. **
Not sure if that's what fixed it, though. Anyway, this is what I get now:

* Starting the Winbind daemon winbind
saned disabled; edit /etc/default/saned
* Checking battery state ...

Broadcast message from root@steven-ME051
            (unknown) at 10:45 ...

The system is going down for reboot NOW!
Checking for running unattended-upgrades:
                                                            acpid: exiting
speech-dispatcher disabled; edit /etc/default/speech-dispatcher

---

### Post by steven30 on 2014-04-09
I'm leaving this thread as unsolved. Although I am not getting the error message anymore, I still don't understand why. If I do get it again, I will video record it and transcribe the message onto this thread.

---


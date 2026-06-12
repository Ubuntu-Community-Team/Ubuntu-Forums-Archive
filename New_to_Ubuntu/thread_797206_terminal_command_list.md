---
title: "terminal command list"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by carusoswi on 2008-05-17
Where would I look to find a complete list of all commands, syntax, and proper use for Ubuntu 8.04?  I have tried to search this forum, search the help topics under help on my desktop, etc.

My specific task this morning is to remove some directories (actually, they are left over references to USB drives and a lexar memory card.  These are empty (guess you would call them drives or "places", and I have read about the bug that causes the problem, am advised to reboot with none of these devices connected to my system and then to remove these phantoms.  I just cannot find the correct terminal command to do so.

I am surprised that I cannot just run a search for "terminal commands" or something similar on the forum here and have the answer pop up.

Help would be most appreciated.

Thanks.

Caruso

---

### Post by NightwishFan on 2008-05-17
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://en.wikipedia.org/wiki/Bash](http://en.wikipedia.org/wiki/Bash)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)
[http://ubuntuforums.org/showthread.php?p=990636](http://ubuntuforums.org/showthread.php?p=990636)

---

### Post by sharks on 2008-05-17
To know all commands , press Tab twice in the terminal.

---

### Post by ugm6hr on 2008-05-17
> **carusoswi said:**
> I am surprised that I cannot just run a search for "terminal commands" or something similar on the forum here and have the answer pop up.

Terminal commands in Ubuntu are the same as any Linux (except for use of sudo).

So you could try searching in google (rather than this forum).

This is the list I use: [http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

You can checl for syntax of commands within the Terminal with:
```
man *command*
```

---

### Post by zvacet on 2008-05-17
You can start with [this]("http://linuxcommand.org/") and if you want later you can use [this.]("http://www.oreillynet.com/linux/cmd/")

---

### Post by Xiong Chiamiov on 2008-05-17
As stated, there are quite many options, since there are quite a few commands.  You can buy books on the subject, if you feel like it.  The specific command you are looking for is
```

rm -r [directory name]

```
Technically, running the command "rmdir" is for removing directories, but it will only work on empty directories, so we instead use the normal "rm" (remove) command, with a -r flag to indicate recursive.

---

### Post by carusoswi on 2008-05-17
Thank you all for your prompt replies.  Mission accomplished.  I unplugged all my external storage devices, double checked and triple checked that they were unplugged, used 'Places' to view my list of places to confirm that all the remaining phantom drives showed the 'lock' icon just to make 100% certain I didn't delete a lifetime collection of "digital assets" and other valuable files, then, ran the rm -r xxxxx* to delete the offending items.

Worked like a charm, and now I'm going to reconnect my external devices.

Again, my appreciation to each of you.  Have a great weekend.

Caruso

---

### Post by NightwishFan on 2008-05-17
Thank you very much, sir. You as well, I am glad I could be of service.

---

### Post by vishzilla on 2008-05-17
Found another one quite a lot [http://cb.vu/unixtoolbox.xhtml](http://cb.vu/unixtoolbox.xhtml)

---


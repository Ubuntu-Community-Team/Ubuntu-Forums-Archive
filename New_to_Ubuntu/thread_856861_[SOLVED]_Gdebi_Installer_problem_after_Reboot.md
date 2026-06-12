---
title: "[SOLVED] Gdebi Installer problem after Reboot"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Fighter77 on 2008-07-11
Hi,
I have only been using Ubuntu 8.04 for 2 weeks and am a basic learner to Linux.
Trying to install this Backup Program, called “Areca Backup”
[http://sourceforge.net/project/showfiles.php?group_id=171505](http://sourceforge.net/project/showfiles.php?group_id=171505)
using the Installer “GDebi” to install the “areca_6.0.7_ubuntu-gdk-32.deb” from the
above link the Installer FROZE in the middle of the installation [ was installing Java at the time].
When I say FROZE the installing Bar did not move for about 30 minutes and the CPU was 
running ay 100%
The only option for me was to reboot.

Now when I try to install the above deb file using the Gdebi installer I get the following:
“Only one software management tool is allowed to run at the same time. Please close other
applications eg; “Update Manager”, aptitude” or “Synaptic” first.”
I do not have Synapic open, or Update Manager & cant find aptitude. I do have “Wine” installed.
Question?
How do I get out of this mess without a complete reinstall?

---

### Post by drs305 on 2008-07-11
See if you have a "**lock**" file in /var/lib/dpkg  

If you do, open nautilus and delete the "lock" file:
```
gksu nautilus /var/lib/dpkg
```

---

### Post by Fighter77 on 2008-07-11
Hi,
I ran your code in Terminal and got this:
john@john-laptop:~$ gksu nautilus /var/lib/dpkg
Initializing nautilus-share extension

** (nautilus:17809): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown
john@john-laptop:~$ 

However I could delete the "Lock" OK.
However, this did not fix the problem as on trying to run GDbi installer
I get the same Error message.

---

### Post by drs305 on 2008-07-11
The command should merely have opened nautilus and taken you to the /var/lib/dpkg folder :confused:  I just ran it again and it opened nautilus normally. I certainly didn't mean to scare you!

There are a couple of other 'lock' files you could look at, including /var/lib/apt/lists/lock. You can run a find command:
```
sudo find / -iname lock
```

---

### Post by Fighter77 on 2008-07-11
Hi,
Ran this again & Nautlus ran OK this time, removed Lock OK but still same error.
john@john-laptop:~$ gksu nautilus /var/lib/dpkg
{{if the above Lock file was removed how did it get put back?? don't answer that one please{{

Got this from your help”

john@john-laptop:~$ sudo find / -iname lock

[sudo] password for john: 

/var/lock

/var/cache/apt/archives/lock

/var/lib/dpkg/triggers/Lock

/var/lib/dpkg/lock

/var/lib/apt/lists/lock

/proc/sys/dev/cdrom/lock


Question? Do I cut/remove to bin for each one? Or try each one in turn?

---

### Post by Fighter77 on 2008-07-12
H drs305,
Could you please give me the correct “Kill Command” so I can get my “Gdebi”
installer back.
Thank you.

---

### Post by drs305 on 2008-07-12
There are several ways to kill a command:

System, Administration, System Monitor, Processes > Rt Click

In the following examples, it may be necessary to preceed the kill command with *sudo*.

If you are sure of the appname:
```
killall gdebi
*or*
killall gdebi-gtk
```

Run this to find all running apps, their PID number *and output specific app* Note: the " | grep appname" is optional to limit the results:
ps aux *| grep [I]appname*[/I]

Run this to find *your* running apps:
ps -u *username*

Run this to find *root's* running apps:
ps -u *root*

To find all running apps plus their parents (if parent won't allow termination):
```

ps -ef

```

To kill a process (PID number from previous commands). Add "-s" option to force quit without normal shutdown sequence of app:
```
sudo kill -9 PID.number
```

```
killall appname
```

---

### Post by Fighter77 on 2008-07-12
Hi drs305,
Problem Fixed.
Thank you for all your Expert Help.
I did not have to use Kill afterall.
When I went to open Synapic:

Now I can't open Synaptic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Ran – got this:
john@john-laptop:~$ sudo dpkg --configure -a 
[sudo] password for john: 
Setting up java-common (0.28ubuntu3) ... 

Setting up odbcinst1debian1 (2.2.11-16build1) ... 

Setting up unixodbc (2.2.11-16build1) ... 

Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 
john@john-laptop:~$ 

open synaptic – got this:
You have 1 broken package on your system! 

Use the "Broken" filter to locate it.

I found the Broken [ in red ] uninstalled then reinstalled java 6 bin
All OK now.
Boy, was that some learning curve.
Once again, thank you.

---

### Post by drs305 on 2008-07-12
You are welcome. Please mark this thread solved if you have no other questions about this. "Thread Tools" at upper right of the first post.

See you on the forum. ;-)

---


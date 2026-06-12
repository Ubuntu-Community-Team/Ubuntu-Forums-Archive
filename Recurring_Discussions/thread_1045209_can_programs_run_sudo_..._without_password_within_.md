---
title: "can programs run sudo ... without password within sudo's 15 minutes?"
date: 2009-01-20
forum: Recurring Discussions
---

### Post by q.dinar on 2009-01-20
hello.
one program can run other program.
so can a program like firefox run something like "sudo chmod ..." and get root's permissions within 15 minutes time after i entered password for "sudo something ..." or "gksudo something ..."?
i ask this after [Re: Share your AppArmor Profiles](http://ubuntuforums.org/showpost.php?p=6583949&postcount=34) :
> why firefox has asked for these? :
...
/home/*/.sudo_as_admin_successful
?and what is, by the way, ".sudo_as_admin_successful" file in user's home directory?

21th january 12:01 gmt : and i wrote this after [http://ubuntuforums.org/showthread.php?t=1044495](http://ubuntuforums.org/showthread.php?t=1044495) .

---

### Post by Cracauer on 2009-01-20
You want to check out what a setuid program is about.

And then be very careful when writing it.

---

### Post by damis648 on 2009-01-20
I am not following... what is your exact question?

---

### Post by SeanHodges on 2009-01-20
> **q.dinar said:**
> can a program like firefox run something like "sudo chmod ..." and get root's permissions within 15 minutes time after i entered password for "sudo something ..." or "gksudo something ..."?

Try it for yourself, open 2 bash terminals and type "sudo top" into each one. You'll be asked for your password each time. The sudo session timestamp only applies to the [pts]("http://www.linuxmanpages.com/man4/pts.4.php") session you are running in. 2 programs running in the same pts session can re-use the timestamp, however.

If you are concerned about the security of this behaviour, you can reduce the length of a timestamp in your sudoers file, or manually clear the timestamp after each use using "sudo -k". However, generally the sudo timestamp is not vulnerable in this way.

> **q.dinar said:**
> what is, by the way, ".sudo_as_admin_successful" file in user's home directory?

.sudo_as_admin_successful is a flag that sudo uses to check if you have successfully authenticated in the past. If you delete it, the first-time help will appear when you use sudo next. This applies to each user on the system, hence why it is a hidden file in your /home.

---

### Post by cdenley on 2009-01-20
> **SeanHodges said:**
> Try it for yourself, open 2 bash terminals and type "sudo top" into each one. You'll be asked for your password each time. The sudo session timestamp only applies to the [pts]("http://www.linuxmanpages.com/man4/pts.4.php") session you are running in. 2 programs running in the same pts session can re-use the timestamp, however.

A program can start a new pty which has a valid timestamp, or even kill your shell running on a pty to take it over.

**EDIT:** I posted a proof-of-concept script I wrote, but it was removed by an admin in another thread, so I probably shouldn't post it anymore
> **SeanHodges said:**
> 
If you are concerned about the security of this behaviour, you can reduce the length of a timestamp in your sudoers file, or manually clear the timestamp after each use using "sudo -k". However, generally the sudo timestamp is not vulnerable in this way.

I never heard of timestamps being re-used this way with malicious intent, but I think it is a legitimate privilege escalation concern. I would suggest setting "timestamp_timeout" to "0" in the sudoers file to disable the use of timestamps.

---

### Post by q.dinar on 2009-01-21
in /etc/sudoers file of mine there are only two non-comment lines:
root	ALL=(ALL) ALL
%admin ALL=(ALL) ALL

can i just append "timestamp_timeout=0" line? i have read man sudoers but it is hard for me yet, and i have read man visudo that says visudo make it safer, but i think i can also simply edit it with gedit in my case. there is another command with gedit in [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201) : export EDITOR=gedit && sudo visudo .

also i have written this topic's first post after [http://ubuntuforums.org/showthread.php?t=1044495](http://ubuntuforums.org/showthread.php?t=1044495) that is about a blocked topic about root logon .

---

### Post by cdenley on 2009-01-21
You should have a line like this in sudoers:
```

Defaults env_reset

```
If you don't, add it. Change that line to:
```

Defaults env_reset,timestamp_timeout=0

```

---

### Post by q.dinar on 2009-01-21
> If you don't, add it. Change that line to: ...thanks, i will also read about that in "man sudoers".>14:49 gmt : yes, that line is here, probably i had not noticed/seen it.<
> The sudo session timestamp only applies to the pts session you are running in. 2 programs running in the same pts session can re-use the timestamp, however. does that apply to gksudo? what about graphical session? if i open gksudo nautilus and then firefox (which can be quite untrustable, because is connecting to internet and can have many addons with >22th jan. 06:27 gmt: [s]not verified[/s] not from official mozilla addon site< and closed source among them), can it use that 15 minutes gksudo time?

---

### Post by cdenley on 2009-01-21
> **q.dinar said:**
> does that apply to gksudo? what about graphical session? if i open gksudo nautilus and then firefox (which can be quite untrustable, because is connecting to internet and can have many addons with not verified and closed source among them), can it use that 15 minutes gksudo time?

Launching gksudo from the "System" menu will create a timestamp for the PTS "unknown", which can be used by other gksudo sessions started the same way. If you run gksudo from the terminal, it will use the pts from that terminal.

---

### Post by cdenley on 2009-01-30
[[IMG]http://brainstorm.ubuntu.com/idea/17754/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/17754/)

---

### Post by jerome1232 on 2009-01-30
At first I thought this was kind of a over-reaction, but having the door open to root for 15 minutes, I think I begin to see your point. Although the only things I wouldn't trust on my computer are my firefox plugins, flash and java.

The only problem I see with implementing no timeout in sudo by default is while it seems to make sense from a security stand point, people cry hard enough about sudo as is!

---

### Post by Cracauer on 2009-01-30
The worst part of sudo's timeout is that they are too lazy to check whether there was a logout between the two attempts.

Try it, do a ssh login, `sudo ls`, log out, log back in so that you get the same tty. It'll do without the password if you have a timeout configured. 

Now that's braindead, and I can't believe it would be that hard to fix since you know the login time.

---

### Post by q.dinar on 2009-01-30
there is related ubuntuforums topic field in brainstorm.
now i see -4 votes there and one comment, cite from it: "So, in another shell, I still need to type my password for sudo. Cam you please be more specific about what is the behavior you expect? "

that field's label is "(Optional) Ubuntuforums.org thread URL :" and it is possible to change it when editing.

1st of february: there is also related thread in the forums: [http://ubuntuforums.org/showthread.php?t=1051348](http://ubuntuforums.org/showthread.php?t=1051348) .

---

### Post by q.dinar on 2009-01-30
post #5 in this topic:
[QUOTE=cdenley]A program can start a new pty which has a valid timestamp, or even kill your shell running on a pty to take it over.[/QUOTE]

not allowing of which file/directory and other type resourses with apparmor rules can prevent program from getting that permission? if for example firefox cannot use sudo nor gksudo commands, because they are not allowed in firefox's apparmor profile, is this enough for it cannot get root permission?

---

### Post by q.dinar on 2010-09-16
i reported this to bug tracker and it was set as invalid:
[https://bugs.launchpad.net/ubuntu/+bug/377244](https://bugs.launchpad.net/ubuntu/+bug/377244)

---

### Post by q.dinar on 2010-09-16
new topic about this: [http://ubuntuforums.org/showthread.php?t=1236036](http://ubuntuforums.org/showthread.php?t=1236036) .

---

### Post by q.dinar on 2010-09-16
one more topic about this: [http://ubuntuforums.org/showthread.php?t=1559745](http://ubuntuforums.org/showthread.php?t=1559745) .

i have searched russian pages about this and have found this talk:
[http://www.welinux.ru/post/2314](http://www.welinux.ru/post/2314)
from it i have found this bug report:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429549](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=429549) .

---


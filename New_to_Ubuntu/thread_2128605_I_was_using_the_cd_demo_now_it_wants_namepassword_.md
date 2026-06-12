---
title: "I was using the cd demo now it wants name/password but I don't know it."
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Mat1250 on 2013-03-23
I was using the cd demo now it wants name/password but I don't know it. What happened? How do I get back to cd demo?

---

### Post by grahammechanical on 2013-03-23
You must have tried to do something that requires authorisation. It is not a demo disk. It is the full Ubuntu distribution running as a live session. Have your tried cancelling the dialog box or closing the terminal, if that is what you are using. Press Enter?  How about running Shutdown and choosing Restart?

[http://askubuntu.com/questions/103896/live-cd-asks-for-a-username-and-password](http://askubuntu.com/questions/103896/live-cd-asks-for-a-username-and-password)

You give very little information about what you were doing or about the task that is requiring authorisation. You could try ubuntu as both the name and the password.

Regards.

---

### Post by Mat1250 on 2013-03-23
I was using the livecd, mounted a drive and must have installed ubuntu somehow. Its like installing windows when it first wants a username. Now it is not booting. I still need to salvage a xp drive. How do I recover ubuntu?

---

### Post by Bashing-om on 2013-03-23
Mat1250; Hi !

Before anything is done let's not guess what is on the hard disk, but know.
From the liveCD (try ubuntu) boot to the desk top; key combo ctl+alt+t activates a terminal interface,
Post back to this thread the output of terminal codes:
```
sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

``` Then troubleshooting can begin.
 All that is being done with these commands is looking at the partitions on the hard disk(s) and the related format(s).[INDENT=3]
a tale to be told

[/INDENT]

---

### Post by deadflowr on 2013-03-23
> **Mat1250 said:**
> I was using the livecd, mounted a drive and must have installed ubuntu somehow. Its like installing windows when it first wants a username. Now it is not booting. I still need to salvage a xp drive. How do I recover ubuntu?

You would know if you installed Ubuntu.
It plays a round of twenty questions before you enter the username and password stage.

We'd definitely need more info to go on at this stage.
Follow Bashing-om's advice and possible post the output from the command listed.

---


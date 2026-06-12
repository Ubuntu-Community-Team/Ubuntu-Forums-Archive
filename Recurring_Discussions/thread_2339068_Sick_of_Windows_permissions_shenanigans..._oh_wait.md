---
title: "Sick of Windows permissions shenanigans... oh wait"
date: 2016-10-04
forum: Recurring Discussions
---

### Post by dragomar on 2016-10-04
I am coming from ~18 years of Windows, 98 on up. Was good times until 8 and 10. Disgusted with the bloat, fluff, spyware and most importantly, obnoxious security restrictions on 'Administrator' accounts. The command line does not intimidate me for I have conquered MS-DOS.

However, I was looking around and it appears exactly what I want to do is not allowed by this forum? [https://ubuntuforums.org/showthread.php?t=1486138](https://ubuntuforums.org/showthread.php?t=1486138)

Is linux no better than Windows now a days? Instead of pressing yes to every User Account Crap prompt (or disabling it entirely) Linux just makes it more verbose (seeming like everything it does) by having to type sudo? Seems I found exactly what I was running from.

Is there a Linux distro/Ubuntu fork that is a clone of Windows XP? (No, not you, React OS)

---

### Post by QIII on 2016-10-04
Moved to ***Recurring Discussions***

Hello!

Unfortunately, if you were running from the security benefits of required user privilege elevation, you've run in the wrong direction.  Thus have *nix systems been since before Microsoft existed.  This is not a recent development "now-a-days".  That has been my experience since 1977.  Microsoft was not an OS producer ay the time, but a developer of BASIC interpreter for the Altair 8800.

The thread you referenced speaks of telling people how to log in to a graphical user environment as root -- instructions for which are disallowed on the Ubuntu Forums. Read further in that thread and you will find that we ask all would-be helpers to refer users to the rootsudo link as a consistent resource that will provide enough information for users to decide what they will or will not do on their machines.

Logging in as root is as dangerous as logging in to an administrator account on Windows.  One should not do that, either.  A long-standing best practice in Windows is to have an administrator account that is not used except as necessary and a normal user account to do your normal work-a-day tasks.  Logging in with least privilege is the safest thing to do in both Windows and Linux.  A sudoer in Linux is, in most respects, just a normal user until they elevate their privileges.  This keeps to the practice of least privilege while avoiding the necessity of logging out and back in as an administrator to do things.

In that thread are also some ideas for how to keep from having to use sudo for each and every command.  There are other distros that install with an active root account, such as Fedora.  I use Fedora as well as Ubuntu, but I never log in as root.  At install time I make sure to add another user (a sudoer) that I can use as my normal account.

And no, there is no clone of XP.  XP is Windows.  This is Linux.  It is best to leave Windows preconceptions at the door.

---

### Post by nothingspecial on 2016-10-04
The post you link tells you how to run a shell without using sudo every time.

So go with it. The thing is, unlike windows, linux assumes you know exactly what you're doing.

So if you do it wrong, as so ,so many people do (hello linux, please completely destroy my system), it will do it, without question.

But besides that, disabling root login by default makes your system secure.

'hey, I'm tired of windows so I'm going to use Ubuntu but I can't be bothered with all that sudo rubbish, so I'll enable the root user and give it a password of "myname2002"'

guess how that's going to go.

Anyway, advising people how to log in as root to a graphical interface is non-negotiable here, it is simply not allowed. The information is out there so have fun, Ubuntu is linux, you can do what you want. But there are rules here.

Cheers :)

---

### Post by Geoffrey_Arndt on 2016-10-04
The OP is a good example of why many Windows users don't stand a " . . . . . " chance of keeping their systems from becoming a total  . . . . . .

---


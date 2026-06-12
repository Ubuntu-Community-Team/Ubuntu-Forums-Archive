---
title: "Learning to use Linux"
date: 2011-09-08
forum: New to Ubuntu
---

### Post by unit4216 on 2011-09-08
I've used Linux a little bit in the past, but usually, I just got kind of annoyed at having to configure everything and do all these things just to get things to maybe work.

However, that was a long time ago, when I was basically computer-illiterate.  Now that I've begun using Ubuntu again (even though I know Ubuntu was made to be easy to use), it seems almost more fun to take the long route sometimes.  However, I'm not really sure where I should look besides the manual to learn how to use Linux properly, and how to write code for Linux, etc.  Also, what are the benefits of learning to use Linux and code in whatever language it's written in? (besides being able to use it.)

tl;dr New to linux, need to find out how to use it properly and learn how it works, focusing on commands and using command line.  also, why is learning to use linux and all its bits useful?

---

### Post by haqking on 2011-09-08
> **unit4216 said:**
> I've used Linux a little bit in the past, but usually, I just got kind of annoyed at having to configure everything and do all these things just to get things to maybe work.

However, that was a long time ago, when I was basically computer-illiterate.  Now that I've begun using Ubuntu again (even though I know Ubuntu was made to be easy to use), it seems almost more fun to take the long route sometimes.  However, I'm not really sure where I should look besides the manual to learn how to use Linux properly, and how to write code for Linux, etc.  Also, what are the benefits of learning to use Linux and code in whatever language it's written in? (besides being able to use it.)

tl;dr New to linux, need to find out how to use it properly and learn how it works, focusing on commands and using command line.  also, why is learning to use linux and all its bits useful?




Linux can be daunting due to unfamiliar terrritory but to become a confident user and then onto an expert which only comes only with experience and read, read, read and try, try try then there are at least some basics needed.

First of all i suggest getting to get grips with the security model early on, as there is alot of misunderstanding about Viruses in Linux and malware in general etc so i refer you first to the importance of using sudo here at:

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

here for security in general

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and these stickies (in my signature)

[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

here for virus information

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

You might also want to look at Tor for anonymizing your connection:
[https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

Firewalls are not generally needed on a home desktop machine as that is taken care of by your router however there is a hardcoded firewall in Linux called Netfilter/IPTables and can be configured by reading here:

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Though most people if use anything use UFW/GUFW which is a interface for managing IPTables without the complicated command line. see here:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

Also look at apparmor for profiling your applications and there privelege:

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

and this will give you a good grounding in the security of your system and such like.

After that it is a case of play, setup virtual machines so you can play without trashing your machine, see:

[www.virtualbox.org](www.virtualbox.org)

and this sub-forum [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

that way you can play with partitions and CLI etc without risking anything.

Also see the command line:

[https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

[http://linuxcommand.org/](http://linuxcommand.org/)

Then it comes down to what you want do and achieve, try the following for a starter:

[http://www.makeuseof.com/tag/10-applications-install-ubuntu-lucid-lynx/](http://www.makeuseof.com/tag/10-applications-install-ubuntu-lucid-lynx/)
[http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/](http://blog.sudobits.com/2011/03/19/top-10-ubuntu-apps/)
[http://blog.sudobits.com/2011/03/07/top-10-ubuntu-games/](http://blog.sudobits.com/2011/03/07/top-10-ubuntu-games/)

There is so much, it is a case of where do you start.

These are mainly Desktop related, but you also need a grounding in servers and services so here is a good read:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

This is of course all pertaining to Ubuntu, to become a Linux Guru or Expert you need to have a grounding in all these concepts across Distros so i refer you back to the virtualisation section to play with distros as much as you like.

Set up servers, crack security, network Vm together, do backups, file sharing etc etc

As for programming, it is written in C, but alot of people start with python, head over to the programming sub-forum and take a look at the threads and stickies etc.

The shell scripting using bash i mentioned will give you a good primer

Have fun

Regards

haqking

---

### Post by mastablasta on 2011-09-09
For python: 
[[FONT=Courier New][SIZE=3]http://code.google.com/edu/languages/google-python-class/[/SIZE][/FONT]]("http://code.google.com/edu/languages/google-python-class/")
 
Most servers on internet run on linux, so knowing linux you can set up your own secure server or maintain an accout propperly, do good internet sites and much more. 
also linux evolved as desktop OS lately, so you can simply just use it on your desktop.

---


---
title: "Debian commands on Ubuntu system"
date: 2015-06-14
forum: New to Ubuntu
---

### Post by papakota on 2015-06-14
Hello!
                              I found a nice video tutorial aimed at  Debian 6.x users. I have Ubuntu 14.04  My question is... Can I just  blindly use on modern Ubuntu system what they showed on older Debian  system? Or should I be careful here? What's the risk, if any? Especially  regarding LAMP install and commands (and also Apache configuration).  Apache 2.2 back then (right?) and now it's 2.4... What do you think?

---

### Post by grahammechanical on 2015-06-14
As far as I know Ubuntu is based upon Debian and Debian runs on Linux and the command line is Bash (Borne Again Shell). So, it all comes down to what particular commands you are talking about.

I dare say that there must be some commands that are special to whatever desktop environment you are using with Debian just as there are some commands that are special to Ubuntu and the Unity interface.

---

### Post by Holger_Gehrke on 2015-06-14
While Ubuntu is based on Debian, it's usually based on the "Testing" or even the "Unstable" branch and has quite a few quirks of it's own. Debian 6 (published 2011) would be somewhat comparable to an Ubuntu 10.x or something like that.

A lot of it -- especially the basics of server configuration and command line tools -- is probably still valid, but the effort necessary for checking makes the usefulness of this tutorial dubious.

---

### Post by tgalati4 on 2015-06-14
If you share the link to the tutorial then we can better comment on its usefulness.  In general the commands will work, but there may be differences and that will break things.  But it's all a good learning exercise.  For installing LAMP, I like *tasksel*.

```
sudo apt-get install tasksel
sudo tasksel
```

---

### Post by cooleryawner on 2015-06-14
The basic Debian should be the same, idk about other "more complex" things though.

---

### Post by kerry_s on 2015-06-14
ubuntu is not debian, is based on debian but a whole lot of changes are specific to ubuntu.

find ubuntu tutorials not debian, there&#8217;s separate ubuntu instructions for a reason.

there are a lot of changes between versions as well, so look for instructions for the version your using.

up to you, the worst that can happen is you have to start over. the more you do it the more you learn.

---

### Post by papakota on 2015-06-14
Thank you **all** for your replies!

Unfortunately, to find **an in-depth and thorough** video tutorial is not as easy as it seems. There're tons of tutorials about Ubuntu (say, there's one at Lynda), but most of the time, it's just some 5-6 minutes clips, covering *basics *for beginners. But let me give you one example to be more specific. He teaches about Samba clients. The command (he uses Debian) he enters in his terminal is:

aptitude install smbclient

I know that usually in Ubuntu's terminal I use apt-get install command, so it's different.

It's this tutorial:

[http://www.linuxcbt.com/products_linuxcbt_deb6x_edition.php](http://www.linuxcbt.com/products_linuxcbt_deb6x_edition.php)

They also have tutorial about Ubuntu, but the author for some reason didn't make it as deep and thorough as Debian tutorial.

---

### Post by bab1 on 2015-06-14
> **papakota said:**
> The command (he uses Debian) he enters in his terminal is:

aptitude install smbclient

I know that usually in Ubuntu's terminal I use apt-get install command, so it's different.
the aptitude command is not Debian specific.  It is available in Ubuntu also.  If you are not sure of a command's availability you can see whether there is a man page```
man aptitude 
```...or check Synaptic for availability.  In this case the package aptitude is available from the repos.  Aptitude is a alternative to apt-get.  Both work with the APT package manager.

---

### Post by tgalati4 on 2015-06-15
To get your money's worth for that tutorial, you would need to install Debian 6.whatever on a spare machine and go through the commands step-by-step.  There are too many differences for all of the topics covered to be useful for Ubuntu.  You could write a tutorial with the same depth describing the differences between Debian 6.x and a more current version of Ubuntu (like 14.04) but that would be a large undertaking.

So the answer to your original question is no, you can't blindly use a tutorial written for Debian 6.x and have it work on Ubuntu.  Perhaps 80% will work, but it's the 20% that will drive you crazy.  So set up Debian 6.x and go through the tutorial.  Then if you really want to use Ubuntu, your knowledge will help perform the same (or similar) steps.  Search the forums for issues as they come up.

---

### Post by kagashe on 2015-06-15
Debian 6 is old, however, it is supported upto Feb 2016.  Debian 8.1 is the latest. Debian 8.1 has Linux Kernel 3.16 which is the kernel in Ubuntu 14.10.

---

### Post by papakota on 2015-06-15
> **tgalati4 said:**
> 
So the answer to your original question is no, you can't blindly use a tutorial written for Debian 6.x and have it work on Ubuntu.  Perhaps 80% will work, but it's the 20% that will drive you crazy.  So set up Debian 6.x and go through the tutorial.  Then if you really want to use Ubuntu, your knowledge will help perform the same (or similar) steps.  Search the forums for issues as they come up.

Thanks for your reply!

Are you trying to tell me that before I repeat on my Ubuntu machine the steps that are being taken in that course, I should first double-check if those steps applicable to Ubuntu 14.04?

---

### Post by papakota on 2015-06-15
> **kagashe said:**
> Debian 6 is old, however, it is supported upto Feb 2016.  Debian 8.1 is the latest. Debian 8.1 has Linux Kernel 3.16 which is the kernel in Ubuntu 14.10.

Well, I'm even older than both of them and you're probably too :-)
DOS commands I was using in 1990 still work fine on my current Windows 7 machine, don't they?

---

### Post by mc4man on 2015-06-15
If by found you mean lying around somewhere then some of it would be generic & some debian 6 specific (that's why the co makes various versions.
If found on internet to purchase then why not get the 14.04 ubuntu version or more recent debian version?

---

### Post by papakota on 2015-06-15
> **mc4man said:**
> If by found you mean lying around somewhere then some of it would be generic & some debian 6 specific (that's why the co makes various versions.
If found on internet to purchase then why not get the 14.04 ubuntu version or more recent debian version?

Thanks for the reply!

Like I said, their Ubuntu tutorials are not so deep for some reason. They're mostly aimed at the beginners in Linux. Their SLES and Debian tutorials are more thorough and deep for some reason. 
Yeah, I meant "lying around somewhere" kinda thing... And how would I know what's Debian specific? Is it really such a thing that a command would work on Debian 6.x and won't on Ubuntu 14.04 I'm not asking for your opinion, opinions vary. If you could provide me with at least ONE example, I'll appreciate that! You know, some people say that 99% would work, some say 80%...

---

### Post by kagashe on 2015-06-15
> **papakota said:**
> Well, I'm even older than both of them and you're probably too :-)
DOS commands I was using in 1990 still work fine on my current Windows 7 machine, don't they?
I don't mind your comments. Here is the link for same Tutorial for Debian 8
[LinuxCBT Deb8x Edition]("http://www.linuxcbt.com/products_linuxcbt_deb8x_edition.php")

I suggest you install Debian 8 and use the Tutorial on it.

Kamalakar

---

### Post by papakota on 2015-06-15
> **kagashe said:**
> I don't mind your comments. Here is the link for same Tutorial for Debian 8
[LinuxCBT Deb8x Edition]("http://www.linuxcbt.com/products_linuxcbt_deb8x_edition.php")

I suggest you install Debian 8 and use the Tutorial on it.

Kamalakar

Thanks for your reply! Hope I didn't offend you with my comments before! 

**It makes sense what you're saying**, generally speaking, BUT... 
a.) I tried Debian before Ubuntu, and I'd much rather stick to Ubuntu. Just one example -- I couldn't even change the screen's brightness on Debian. Can do that with easy on Ubuntu. I'm NOT saying here that it's impossible to fix that issue on Debian, but apparently it doesn't work on Debian out of the box. And I don't need an extra hassle;
b.) I don't have that Deb8.x tutorial physically.

---

### Post by monkeybrain20122 on 2015-06-15
> **papakota said:**
> Hello!
                              ...Can I just  blindly use on modern Ubuntu system what they showed on older Debian  system? 

It is probably a bad idea in general to copy and paste commands *blindly*. :)

---


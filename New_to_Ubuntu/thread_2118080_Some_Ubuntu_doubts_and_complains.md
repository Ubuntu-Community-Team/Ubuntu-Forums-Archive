---
title: "Some Ubuntu doubts and complains"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by armaman on 2013-02-20
Hello, I have some doubts about the Ubuntu OS.

I have used it some times with mixed feelings and results.

First, is Ubuntu really that safe? I mean, for out-of-box using. (I will use Ubuntu mainly for web-surfing, text and maybe Gimp with a tablet.)

I will keep the Windows for high-end applications such as Autocad.

Second, in the last two times I used Ubuntu, in two differents computers, a annoying problem happened: It wouldn't shutdown. The screen would go black, but the "on led" and "hard disk led" were on and the computer would never shutdown! It keep going and going and going... Why?

Thanks in advance!

---

### Post by slickymaster on 2013-02-20
> **armaman said:**
> Hello, I have some doubts about the Ubuntu OS.

I have used it some times with mixed feelings and results.

First, is Ubuntu really that safe? I mean, for out-of-box using. (I will use Ubuntu mainly for web-surfing, text and maybe Gimp with a tablet.)

Please read this threads and the Community Wiki page. They more than answer your question.
[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")
[Do I need a Firewall for Ubuntu?]("http://ubuntuforums.org/showthread.php?t=1871177")
[DoINeedAFirewall]("https://help.ubuntu.com/community/DoINeedAFirewall")

---

### Post by armaman on 2013-02-20
Thanks. I will.

And about the shutdown issue? Any ideas?

---

### Post by slickymaster on 2013-02-20
With what kernel of Ubuntu did that happen? Did the computers run Nvidia driver?...

It's impossible to give you a straightforward answer because of the number of things that could been causing you that problem.

---

### Post by DiabolicalClaptrap on 2013-02-20
As it stands, Ubuntu is fairly secure OOB. That's because Linux was designed with security in mind. But that doesn't mean you shouldn't implement a layered defense. The security of your system depends on the choices you make. Of course, those choices will be different for everybody. Id' suggest researching programs if you're unsure. Here's another link you can take a look at.

[GIMP vulnerabilities]("http://www.cvedetails.com/vulnerability-list/vendor_id-9605/Gimp.html")

Edit: Like the user above me stated, it's impossible to tell what your issue with shutdown was/is without more information. It could be a number of things, including a program that refuses to die, power management settings, a missing gfx driver etc. I'd also suggest searching this forum. Your problem may seem whacko but chances are its [happened]("http://ubuntuforums.org/showthread.php?t=1466589") [URL="http://ubuntuforums.org/showthread.php?t=1986705"]before.
[/URL]

---

### Post by bigmonmulgrew on 2013-02-20
I had a couple of teething problems when I first tried ubuntu about 8 years ago.

Had a problem with multi monitor support back then, don't let these issues put you off you will find the forum guys very helpful.

To help you though we are going to need more information.
Which version are you using (12.04, 12.10 etc)
What hardware are you using.
Have you connected to the internet and ran the updates.
Tried anything so far?

It might be a good idea to put your hardware spec and ubuntu version in your signature for now

---

### Post by grahammechanical on 2013-02-20
> the computer would never shutdown! It keep going and going and going... Why?

Do you want the non-technical answer or the technical answer?

Non-technical answer = Don't know. Had it myself from time to time. I wait and then I hit the power button. Linux is a very robust OS. It always reboots.

Technical answer = It is too technical to explain. :)

Linux (and it is Linux not Ubuntu that runs the Shutdown process) has to follow certain rules to shutdown the OS and the machine. It has to stop various processes. Sometimes it gets stuck waiting for a process to stop.

Linux is under constant development. Updates change things. Modifications to the desktop change things. These changes have to be written to configuration files. I think that it sometimes requires a boot - shutdown or two for the OS to get into a pattern of clean loading and shutting down.

But hey, it is not as if we pay good money for Ubuntu. And I have yet, in five years had the Blue Screen of Death. Do you still get that with Windows? Do you still have to wait for the first Service Pack to get the OS that you paid for?

---

### Post by bigmonmulgrew on 2013-02-20
> **grahammechanical said:**
>  Do you still have to wait for the first Service Pack to get the OS that you paid for?

You mean some people are happy with the first service pack?

---

### Post by deadflowr on 2013-02-20
I've suffered from the multiple users logged in bug:

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/855556]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/855556")

---

### Post by armaman on 2013-02-20
Thanks to everyone.

> To help you though we are going to need more information.
Which version are you using (12.04, 12.10 etc)
What hardware are you using.
Have you connected to the internet and ran the updates.
Tried anything so far?

It might be a good idea to put your hardware spec and ubuntu version in your signature for now 

I'm using an Intel i7 2670QM 2,2 GHz, 6GB ram and and yes a Nvidia GT 630M, with a onboard Intel Graphics Card.

Ubuntu version: 12.04

I think it got worse after the updates!:confused:


> But hey, it is not as if we pay good money for Ubuntu. And I have yet, in five years had the Blue Screen of Death. Do you still get that with Windows? Do you still have to wait for the first Service Pack to get the OS that you paid for? 

Hmm... actually I haven't got any BSOD since Win XP.

---

### Post by JayKay3OOO on 2013-02-20
Windows 7 is as reliable as Linux although it does suffer more from fragmentation and there are a lot more poorly written apps for Windows not to mention it suffers from it's own success. If Linux was as popular as Windows then it would have as many if not more security attacks by unemployed teenagers as well.

Linux is secure, but don't **assume** it's secure. You could be one click away from disaster. 

I've only ever had one virus in Windows and that was because I was looking into hacking when I was an unemployed teenager. Security is about common sense more than anything. If I had a virus in Linux I'd never know as most are not destructive they sit there logging your passwords without you knowing. I don't run a virus checker. Windows viruses can't infect Linux though.

---


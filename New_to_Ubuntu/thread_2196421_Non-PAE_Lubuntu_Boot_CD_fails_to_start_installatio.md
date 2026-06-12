---
title: "Non-PAE: Lubuntu Boot CD fails to start installation"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by electriccat on 2013-12-29
Hi,

when I try to install lubuntu on my Thinkpad, I get the message, that my cpu does not support pae and the installation does not continue.
I am a litle bit angry because I downloaded and burned lubuntu to cd because I read that it would be perfect for "older" machines. My machine is a 1,7 Ghz Pentium Mobile with 2 GB Ram and I can install Windows 7 on this machine (must be stone-age software).

Edit:

So now I found out that the ubuntu has problems with pentium m processors. I followed then

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

and tried to install

[TABLE]
[TR]
[TD] 12.04 Precise Pangolin 
[/TD]
[TD][/TD]
[TD][/TD]
[TD] [32 bit non PAE]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/non-pae/mini.iso") [/TD]
[/TR]
[/TABLE]

I went through the installation process and after step 7

> 
[LIST=1]
[*]You need a wired Ethernet connection 
[*]At the "boot:" prompt, press the Enter key. 
[*]Select "Install" or "Command Line Install". 
[*]Select your language & country/territory. 
[*]Detect your keyboard layout (you will be asked to press some keys.) 
[*]Specify hostname for your system (for use on the network.) 
[*]Choose your archive mirror for downloading the base system from. 
[*]Partitioning - Most will simply want 'Guided - use entire disk'. [See [note 2]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#notes")] for other options. 
[*]Updates - Select 'No Automatic Updates' [See [note 3]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#notes")]. 
[*]Let it install GRUB onto the disk. [See [USB]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall#usb")]. 
[/LIST]


nothing happened. I only see a pink screen.

To find out if my thinkpad is the problem I installed in a VM (VMware) and got the exact same. See here:

[IMG]http://s1.directupload.net/images/131229/3s9s7omm.png[/IMG]


**[SIZE=4]Why is it still so difficult to install a simple linux?[/SIZE]**

---

### Post by sudodus on 2013-12-29
Welcome to the Ubuntu Forums :-)

I have such a Thinkpad (mine is a T42), and I have developed a system to use fake-PAE to provide a solution. See this link

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---

### Post by electriccat on 2013-12-29
Hello,

thanks for your answer. I have an R40. But the how-to seems too complicated for me. I am not an IT Professional. My Experience is enough to make simple installations, but not more. Sad to throw the thinkpad away, but It's not the worlds end.

---

### Post by sudodus on 2013-12-29
It is not difficult to install according to Lubuntu fake-PAE. Just some steps, that are different from what you have done before. You can ask, if something is not clear, and step by step you'll succeed. It is really too bad to trash working computers. I'll try to explain as clearly as possible.

---

### Post by mörgæs on 2013-12-29
@Electriccat , did you notice that the guide mentioned that Bodhi Linux works without any modifications?

---

### Post by sudodus on 2013-12-29
> **electriccat said:**
> Hi,[B][SIZE=4]

Why is it still so difficult to install a simple linux?[/SIZE][/B]

Because you selected a difficult method. There are several simpler methods.

Or install something else than Ubuntu (but maybe developed from Ubuntu as suggested by mörgæs: ***Bodhi***. Another alternative is ***LXLE***).

I suggested ***Lubuntu fake-PAE*** which is different from the method you tried. I can also suggest the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), which is designed to be simpler and safer than the standard installer. And it allows installing into computers with Pentium M and Celeron M. Help yourself in the menu of methods, and select the one you think suits you!

---

### Post by electriccat on 2014-01-01
> **mörgæs said:**
> @Electriccat , did you notice that the guide mentioned that Bodhi Linux works without any modifications?


Hello,

thanks you for all the replies. I am now trying it with Bodhi Linux.

---


---
title: "Total noob failing miserably with installing Kubuntu"
date: 2018-01-20
forum: New to Ubuntu
---

### Post by C5DQPkzzN5 on 2018-01-20
Hi!
I am trying to install Kubuntu as the sole OS on my new laptop, but I can't get it to work. I downloaded the ISO and put it on a USB using both rufus and unetbootin (not at the same time, not that stupid XP). I changed the boot order so it boots off the USB and everything seemed groovy. But when I boot into it I come to this screen that says "GNU GRUB version blablabla..." at the top and I am presented with 3 options: "Start Kubuntu", "OEM install (for manufacturers)" and "Check disc for defects". I've tried all three options, the last one just tells me that everything is OK while the first 2 take me to a terminal which I believe is called "tty1" and it asks me for a username and password. Using the username "kubuntu" and no password seems to work but not really sure what to do after that. I've been googling solutions for a solid 5+ hours and I'm pretty sure somethings not right.

Not sure if the information is useful but it's a Lenovo Thinkpad T470p I'm trying to install it on.
Thanks for any help!

---

### Post by SeijiSensei on 2018-01-20
Maybe you don't have the right image?  Try downloading this: 

[http://cdimage.ubuntu.com/kubuntu/xenial/daily-live/current/xenial-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/xenial/daily-live/current/xenial-desktop-amd64.iso)

It should boot into a graphical desktop and offer you a choice to "Try" or "Install" Kubuntu.  The first runs off the boot image and makes no changes to your hard disk; it's basically a "test drive."  If everything works, you can double-click the "Install" icon on the desktop.  Or you can just proceed directly to installation.

---

### Post by C5DQPkzzN5 on 2018-01-20
What's wrong with the ISO from their own site [https://kubuntu.org/getkubuntu/](https://kubuntu.org/getkubuntu/) ???

Also that link is downloading really slowly, like 50kb/s

---

### Post by C5DQPkzzN5 on 2018-01-20
Well, it started downloading faster now but I still didn't receive any graphical desktop.

---

### Post by yancek on 2018-01-20
How old/new is your Lenovo Thinkpad?  Did you download the 32bit or 64bit? If the 64 bit, is your hardware 64bit?  Did you do an md5 checksum on the downloaded iso before using rufus and unetbootin?

---

### Post by C5DQPkzzN5 on 2018-01-20
The laptop is brand new, I got it yesterday. I downloaded the 64bit version since it's already running on 64bit Windows. And I didn't check the MD5 checksum beforehand, but I did a SHA256 checksum now and it checked out (they only had SHA256 checksums to check on their site [https://kubuntu.org/alternative-downloads](https://kubuntu.org/alternative-downloads))

Edit: Gonna throw in some more checks because that last sentence didn't have enough of them, check check check check.

---

### Post by Autodave on 2018-01-20
Are we to assume that you still have Windows on the HD? If so, did you disable "fast boot" in the BIOS?

---

### Post by C5DQPkzzN5 on 2018-01-20
I've already disabled fast boot in Windows under the power options. But I've had a quick look through the BIOS options now and can't seem to find anything relating to fast boot.

Edit: And yes, I still have Windows on the HD

---

### Post by Geoffrey_Arndt on 2018-01-21
Try using "Etcher" to create a boot-able usb flash-stick . . . . works well and is easy/fast.   More reliable than some other tools in my view.

[https://etcher.io/](https://etcher.io/)

---

### Post by yancek on 2018-01-21
> I've already disabled fast boot in Windows under the power options

Does the explanation at the link below sound like what you have done when booted to windows 10?  If so, then I doubt that is the problem.  More likely the iso wasn't written to the usb properly for whatever reason.  Windows 10 should be UEFI so you should verify that and make certain Kubuntu is UEFI or you will have problems booting after install.

[https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/](https://www.howtogeek.com/243901/the-pros-and-cons-of-windows-10s-fast-startup-mode/)

Haven't installed the most recent Kubuntu but I've never seen a need to enter a user name on booting the install media nor a password.  The short video below shows what you should see.

[https://www.youtube.com/watch?v=q00FzfRWNvg](https://www.youtube.com/watch?v=q00FzfRWNvg)

---

### Post by C5DQPkzzN5 on 2018-01-21
> Try using "Etcher" to create a boot-able usb flash-stick . . . . works well and is easy/fast. More reliable than some other tools in my view.

[https://etcher.io/](https://etcher.io/)
 
Tried it, same result as before

> 
Does the explanation at the link below sound like what you have done when booted to windows 10?  If so, then I doubt that is the problem.


Yes, that is exactly the same guide as I used. I doubted its use as well but I saw it in some thread at around hour 4 and was ready to test just about anything.

> 
More likely the iso wasn't written to the usb properly for whatever reason.  Windows 10 should be UEFI so you should verify that and make certain Kubuntu is UEFI or you will have problems booting after install.


I have checked, it's UEFi. And I haven't just made the bootable USB once, I have done it atleast 3 times with both Rufus and UNetbootin and now once with Etched. I have re-downloaded the iso file each time, I have tried different version of Kubuntu, I have even bought a new USB just in case.

> 
Haven't installed the most recent Kubuntu but I've never seen a need to enter a user name on booting the install media nor a password.  The short video below shows what you should see.


Yes, I've seen that in a couple of videos and guides, can't seem to get it to appear. All I get is this tty1 terminal window. If I leave it alone for a while it starts doing this (in this picture I haven't even entered the username and password, I've just let it sit)

[https://drive.google.com/open?id=1INOrn7OrdtLf5fBQU9sb0IoQTLUg8Zf0](https://drive.google.com/open?id=1INOrn7OrdtLf5fBQU9sb0IoQTLUg8Zf0)

---

### Post by Geoffrey_Arndt on 2018-01-22
What video system is on the laptop - - is it NvidiaGeForce 940MX?    You may have to use a boot option during the install . . . . like "nomodeset" so that you can get a low-level gui and install the nvidia drivers.

---

### Post by C5DQPkzzN5 on 2018-01-22
Yes, that's my graphics card. I googled and found this, would this work?

[https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics](https://askubuntu.com/questions/760934/graphics-issues-after-while-installing-ubuntu-16-04-16-10-with-nvidia-graphics)

---

### Post by Geoffrey_Arndt on 2018-01-22
Would not recommend that link for nomodeset.

...............................................................................................................

Here's some info:

You need to invoke the boot parameter via editing grub - - so you get a vesa based gui and then can use the ubuntu settings manager to install the "additional drivers" needed.

[https://support.reliablesite.net/kb/a240/how-to-set-nomodeset-into-the-grub-bootloader-debian-and-ubuntu-intel-core-i7-3770.aspx](https://support.reliablesite.net/kb/a240/how-to-set-nomodeset-into-the-grub-bootloader-debian-and-ubuntu-intel-core-i7-3770.aspx)

Also, see below for examples:
[B]
Original grub[/B]
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**
GRUB_CMDLINE_LINUX=""

**Modified grub**

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"**
GRUB_CMDLINE_LINUX=""



Here's another method (looks interesting, but I haven't tried yet - - still, it's worth a try)

[https://www.youtube.com/watch?v=qCjPjE_8yl8](https://www.youtube.com/watch?v=qCjPjE_8yl8)

---

### Post by oldfred on 2018-01-22
You should not need to permanent add nomodeset.
You need it when you first boot both live installer and after install. And then until you install correct nVidia driver from Ubuntu repository.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

If Windows is UEFI, you do want to install Ubuntu in UEFI boot mode.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by C5DQPkzzN5 on 2018-01-22
[SIZE=2]Tried both methods, ended up in the tty1 terminal in both cases. If I'm reading your suggestions correctly I'm supposed to end up with some GUI after reboot (using [COLOR=#000000]Geoffrey Arndt's method) or after selecting "Start Kubuntu" in the grub menu (using oldfred's method). The only thing that's different I do the "replace quick splash with nomodeset" thing that oldfred suggested I get a load of startup text with green OKs before ending up in tty1. This hasn't happened before.[/COLOR][/SIZE]

---

### Post by oldfred on 2018-01-22
Without quiet splash, you see the boot process which sometimes can show other errors.

Still seems like a video issue.
Do you end up at this terminal or some error?
ubuntu@ubuntu:

---

### Post by oldfred on 2018-01-22
Without quiet splash, you see the boot process which sometimes can show other errors.

Still seems like a video issue.
Do you end up at this terminal or some error?
ubuntu@ubuntu:

Have you updated UEFI to latest version from Lenovo?
Some with SSD (Samsung among others) also needed SSD firmware update.

---

### Post by C5DQPkzzN5 on 2018-01-22
You know what guys, I think this is all a bit too complicated for me, I give up. Thank you very much for your help and I am very sorry for having wasted your time :(

---

### Post by Geoffrey_Arndt on 2018-01-24
Not as complicated as it seems . . . but if you watch 3 or 4 youtube videos about dual-booting windows and ubuntu you'll get the gist (the basics).

Also, there is of course another better option . . . . most likely you didn't install your windows system (99.5% don't) - - so, next time you're in the market for a PC, get it with Ubuntu or another Linux distro pre-installed.    Then the setup takes about 10" and is no more complicated than setting up a phone.

See my sig below for links to pre-installed linux systems.    I use System76 but there are many companies that now offer Linux hardware for sale.

---


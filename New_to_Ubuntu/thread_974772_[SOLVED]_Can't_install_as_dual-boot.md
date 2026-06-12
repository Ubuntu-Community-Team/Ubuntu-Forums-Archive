---
title: "[SOLVED] Can't install as dual-boot"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by tapasray on 2008-11-07
I have an Acer Aspire 5003WLMi laptop and am trying to install 8.10 in the dual-boot configuration. The ISO I have burned should be good, because the downloaded file passed the md5 test. When I insert the CD and choose the option for a separate installation alongside the Windows XP that's already there, the machine restarts as it should. When I enter the BIOS by pressing F2 during boot, change the boot option to CD, save the setting and go forward, the machine still loads Windows instead of 8.10 from the CD. This keeps happening, no matter how many times I try. In the help pages I saw instructions for creating a bootable floppy with sbminst in such cases, but my machine does not have a floppy drive. Is there something else I can do? Would really appreciate some help.

---

### Post by Sealbhach on 2008-11-07
You could try the Wubi installer.

Sounds like something is not working right in your BIOS i.e. it's not doing what you tell it to do, which is very annoying.

[http://wubi-installer.org/](http://wubi-installer.org/)

This will install from within windows. Not quite the same as a dual boot but not a bad option.


.

---

### Post by tapasray on 2008-11-07
Thanks! I'll try that.

Just noticed you wrote that it installs within Windows. I did that with 8.04 some months ago, but didn't use it, so uninstalled it. Now I really need a dual-boot system, because my XP is beginning to be unstable and I can't afford that - have some critical things for the next few months.

---

### Post by Sealbhach on 2008-11-07
It uses the Windows boot manager, so when you restart, you can choose to go into Windows or Ubuntu. Have a look at this:

[http://blogs.zdnet.com/hardware/?p=1570](http://blogs.zdnet.com/hardware/?p=1570)

After installing, when you boot up, you get a screen like this:

[IMG]http://blogs.zdnet.com/hardware/images/hardy_heron_in_windows_06_sm.jpg[/IMG]

Wait for other opinions though, if you're not sure.

.

---

### Post by TeXtonyx on 2008-11-07
I have an idea, but don't know if it will work, I'm bringing it up
in case it sparks an idea among the other posters.

Download the 8.10 iso. Unpack it to disk with PowerIso or Alcohol 120 
and mount it on a virtual drive, then start the installation.
A similar idea is if you have a desktop maybe you can set up a
Workgroup and do a network install. I heard somebody mention that in
regard to the alternate cd. I'll look it up on the Search now.

There are installs where you connect to an (internet) server and 
do a complete installation while maintaining the connection. I
think that would workaround having no cd. [ a net install]

---

### Post by mc4man on 2008-11-07
A lot of machines don't respond to changing the boot order in bios, it needs to be changed in the 'boot menu' or something similarly named.
Many times that's F12 (usually you'll see your options displayed briefly during initial boot.

I'd just power up, try F12 (or what's displayed) then insert the disc before making selection.

If you can do that and it still boots to windows then ck. and make sure you burned a boot disc vs. data disc

---

### Post by TeXtonyx on 2008-11-07
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I just checked and 8.10 is supported.
Introduction

"UNetbootin allows for the installation of various Linux/BSD distributions to a partition or USB drive, so it's no different from a standard install, only it doesn't need a CD. It can create a dual-boot install, or replace the existing OS entirely.

The current version has built-in support for the following distributions, though installing other distributions is also supported:

    * Ubuntu (and official derivatives)
          o 6.06 LTS
          o 6.10
          o 7.04
          o 7.10
          o 8.04 LTS
          o 8.10

---

### Post by tapasray on 2008-11-07
> **Sealbhach said:**
> It uses the Windows boot manager, so when you restart, you can choose to go into Windows or Ubuntu. Have a look at this:

[http://blogs.zdnet.com/hardware/?p=1570](http://blogs.zdnet.com/hardware/?p=1570)

After installing, when you boot up, you get a screen like this:

[IMG]http://blogs.zdnet.com/hardware/images/hardy_heron_in_windows_06_sm.jpg[/IMG]

Wait for other opinions though, if you're not sure.

.


I am familiar with this screen. Used to get it when I had 8.04 inside XP. Now I need 8.10 along with XP, as a standalone OS.

---

### Post by niccholaspage on 2008-11-07
Try [Unetbootin]("http://unetbootin.sourceforge.net/").

---

### Post by tapasray on 2008-11-07
Thanks, TeXtonyx. I have downloaded and burned the ISO to a CD after checking the md5 sum. Don't know anything about virtual drive, etc. Will read up a bit first.


> **TeXtonyx said:**
> I have an idea, but don't know if it will work, I'm bringing it up
in case it sparks an idea among the other posters.

Download the 8.10 iso. Unpack it to disk with PowerIso or Alcohol 120 
and mount it on a virtual drive, then start the installation.
A similar idea is if you have a desktop maybe you can set up a
Workgroup and do a network install. I heard somebody mention that in
regard to the alternate cd. I'll look it up on the Search now.

There are installs where you connect to an (internet) server and 
do a complete installation while maintaining the connection. I
think that would workaround having no cd. [ a net install]

Thanks, mc4man. I'll try this. Yes, the disk I have burned is a boot disk. It starts booting all right, but then things go into a loop the way I mentioned in my original post.


> **mc4man said:**
> A lot of machines don't respond to changing the boot order in bios, it needs to be changed in the 'boot menu' or something similarly named.
Many times that's F12 (usually you'll see your options displayed briefly during initial boot.

I'd just power up, try F12 (or what's displayed) then insert the disc before making selection.

If you can do that and it still boots to windows then ck. and make sure you burned a boot disc vs. data disc

Thanks, niccholaspage. I'll try this.

> **niccholaspage said:**
> Try [Unetbootin]("http://unetbootin.sourceforge.net/").

TeXtonyx, thanks a lot! I'll check this out.


> **TeXtonyx said:**
> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

I just checked and 8.10 is supported.
Introduction

"UNetbootin allows for the installation of various Linux/BSD distributions to a partition or USB drive, so it's no different from a standard install, only it doesn't need a CD. It can create a dual-boot install, or replace the existing OS entirely.

The current version has built-in support for the following distributions, though installing other distributions is also supported:

    * Ubuntu (and official derivatives)
          o 6.06 LTS
          o 6.10
          o 7.04
          o 7.10
          o 8.04 LTS
          o 8.10

---

### Post by talsemgeest on 2008-11-07
Before you try that, you should try to find the boot menu. When starting up, the same time that you would tap F2 to go to the bios, try either F8 or F12 (it depends on the motherboard). Once you get to the boot menu, select cd-rom (with the cd in the drive ;) ) and that should let you boot.

---

### Post by tapasray on 2008-11-08
Thank you, mc4man. This worked very well.



> **mc4man said:**
> A lot of machines don't respond to changing the boot order in bios, it needs to be changed in the 'boot menu' or something similarly named.
Many times that's F12 (usually you'll see your options displayed briefly during initial boot.

I'd just power up, try F12 (or what's displayed) then insert the disc before making selection.

If you can do that and it still boots to windows then ck. and make sure you burned a boot disc vs. data disc

---


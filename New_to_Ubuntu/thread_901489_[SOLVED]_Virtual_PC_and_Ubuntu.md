---
title: "[SOLVED] Virtual PC and Ubuntu"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by nlraley on 2008-08-26
I know that this is a nightmare for most people, but I'm taking a Linux class and am playing around with various versions and Ubuntu was one I really wanted to give a try.

Anyways, after following this link:
[http://techblissonline.com/install-ubuntu-804-virtual-pc-2007-microsoft/]("http://techblissonline.com/install-ubuntu-804-virtual-pc-2007-microsoft/")
I was able to get it up and running.

It boots up fine and dandy, although I'm not able to set my screen resolution above 800x600.  I went to try and update the drivers for my nvidia GeForce 8800GTX Ultra video card; however, I have no hardware listed in that section.

Any clues as to why?

I'm thinking the lines in the guide may be the culprit here, they had me do the following:

> At installation Enter Safe graphics mode and then press F6 and delete the part that says “quiet splash -” and replace it with “vga=791 noreplace-paravirt”

Then click try Ubuntu.
Then after it loads install.  After install it had me do this:
> Reboot
Once it gets to GRUB, interupt the boot and add the “noreplace-paravirt” to the kernel boot line. 

    * Press “esc” while grub is visible
    * You should now see 3 entries to select from. Leave the first one “Ubuntu 8.04, kernel 2.6.24-16-generic” selected and press “e”
    * On the next page, select the second entry that reads “kernel /boot/vmlinuz…” and press “e” again
    * You will see a command line that ends with “xforcevesa“. Hit “space” and add “noreplace-paravirt” (without the quotes) to that line and press “enter”
    * You will be taken back to the previous selection screen with the entry “kernel /boot/vmlinuz…” still selected. Now press “b” and it should boot correctly
*NOTE*  In this step the kernel /boot/vmlinuz wasn't exactly in the same order and the next step didn't have the xforcevesa part in it but I added to the line anyway.

And finally they had me do this to get it to automatically boot this way without me having to change it when loading GRUB every time:
> 
    * Once Ubuntu has loaded, open a terminal window (Applications –> Accessories –> Terminal) and on the command line enter “sudu nano /boot/grub/menu.lst”
    * Enter your password and page down to near the bottom and locate the “kernel /boot/vmlinuz…” in the “Ubuntu 8.04, kernel 2.6.24-16-generic” section
    * Move the cursor to the end of the line after xforcevesa and add “noreplace-paravirt” (no quotes) 
      Ctrl + O to write out, enter to accept the name, Ctrl + X to close


Is this not allowing me to use my hardware with virtual pc?  Or am I missing something else?

And thanks for the help in advance, just started playing with linux last night and so far it seems like it is going to be really fun to tinker with.

---

### Post by Dedoimedo on 2008-08-26
Hello,

Video support in virtual machine is not that good, yet.

Most virtualization software only supports limited 3D and will generally install their own equivalent of the basic vesa drivers or alike.

If you're looking for a solid virtualization product, wait for VMware Workstation 6.5.

[http://www.chipx86.com/blog/?p=250](http://www.chipx86.com/blog/?p=250)

Dedoimedo

---

### Post by Daveski on 2008-08-26
> **nlraley said:**
> 
It boots up fine and dandy, although I'm not able to set my screen resolution above 800x600.  I went to try and update the drivers for my nvidia GeForce 8800GTX Ultra video card; however, I have no hardware listed in that section.

Any clues as to why?


Yes, your virtual machine is using a virtual video card - this is why the generic vesa driver is being used. There IS no nVidia card as far as the virtual machine is concerned.

You should dual-boot if you want to use your real hardware.

---

### Post by nlraley on 2008-08-26
Gotcha, was figuring it could be something like that.

Any idea how to get a larger screen res?  800x600 is painfully large.

---

### Post by nlraley on 2008-08-26
Scratch that, think if I set the display option to use the host systems resolution I should be good.

---

### Post by nlraley on 2008-08-26
Actually, that won't work.  I forgot that you have to install virtual machine addons to force the screen resolution.  Are there any other workarounds for this?

Would VM Ware allow me to do this?  Think I can get a creator to create the virtual machine from sourceforge and then run up using one of the free parts for it right?  I had one instructor say the reason we aren't using it is b/c the school didn't want to have to pay for it but my other instructor mentioned something like what I sad above as being a free workaround.

Main reason I was doing this was my Linux instructor told us we can't install Ubuntu on Vitrual PC without a ton of headaches and two I've really been wanting to play around with it.  Was going to couple Ubuntu in with my Suse class and pick up both systems and probably swap over to Ubuntu after I get more familiar with Linux.

When I do that I'll probably have dual boot so I can still do my DirectX 10 gaming, or at least virtualize the Windows OS and have Ubuntu being my main OS.

---

### Post by jimv on 2008-08-26
If you're using Microsoft's Virtual PC, you're making things harder on yourself than you need to.  Use Sun's VirtualBox instead.  It works better, and provides good support for Linux guest OS's.

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by VitaLiNux on 2008-08-26
> **nlraley said:**
> Gotcha, was figuring it could be something like that.

Any idea how to get a larger screen res?  800x600 is painfully large.
Maybe if you try Sun xVM VirtualBox and after installing it and your Ubuntu virtual machine, load Ubuntu and try the "Guest Additions" feature. It does emulate your hardware resolution above  800x600. It's done the trick for me, I haven't used Virtual PC, though...

---

### Post by nlraley on 2008-08-26
Main problem is school uses Deep Freeze, so I'd always have to keep a copy of the other virtualization software I use and reinstall it each time I switch classes.

The main reason aside from that is my school is heavy on .NET applications and programming so I still have to keep the windows based operating system to push out the programming.

---

### Post by nlraley on 2008-08-26
Anyone else have any ideas how to get the resolution changed in virtual pc before I ditch it and go with either vm ware or Sun's xVM?

---

### Post by nlraley on 2008-08-26
Well, I figured it out after some more digging.  I now have my resolution much better, not able to use beryl/comp fuzion, but the desktop is in a much more workable manner.

If anyone else catches this post looking for help doing the same thing, here are the links I found to pretty much walk you through it.  Hope they help.

**Installing Ubuntu:**
[http://techblissonline.com/install-ubuntu-804-virtual-pc-2007-microsoft/]("http://techblissonline.com/install-ubuntu-804-virtual-pc-2007-microsoft/")

**Setting up different resolutions:**
[http://techblissonline.com/ubuntu-804-set-default-resolution-1024-768-virtual-pc-2007/]("http://techblissonline.com/ubuntu-804-set-default-resolution-1024-768-virtual-pc-2007/")

---

### Post by starcannon on 2008-08-26
Be sure to click on Thread Tools up to the right of your window here, and Mark as Solved.

Nice job, and thanks for following up with the answer.

---

### Post by Dedoimedo on 2008-08-26
> **nlraley said:**
> Main problem is school uses Deep Freeze, so I'd always have to keep a copy of the other virtualization software I use and reinstall it each time I switch classes.

The main reason aside from that is my school is heavy on .NET applications and programming so I still have to keep the windows based operating system to push out the programming.

Hello,

Then use this:
[http://www.mojopac.com/](http://www.mojopac.com/)

Install it to a portable harddisk, then in the virtualized environment, install VirtualBox, and then inside it Ubuntu or anything else.

This is a PROVEN method, I'm using it.

Host: XP SP3 > MojoPac (also XP SP3, of course) > VirtualBox > Ubuntu, all running from WD 250GB passport.

BTW, the faster the external hard disk, the better.

Cheers,
Dedoimedo

---

### Post by Daveski on 2008-08-27
> **Dedoimedo said:**
> Hello,
Then use this:
[http://www.mojopac.com/](http://www.mojopac.com/)


Huh - they use the word 'Freedom' but this is at the top of their EULA:

> **By downloading and installing the MojoPac Freedom Software, you hereby consent to (i) RingCube&#8217;s monitoring and collection of statistical data based on any of your activities while implementing or using the RingCube Freedom Software and (ii) receiving ads and other promotional materials that appear as notices on the desktop of your personal computer.  In no event will RingCube monitor or collect the following information:  passwords, credit card information or other financial information, your name or your address.**

---

### Post by Dedoimedo on 2008-08-27
Hello,

I've been using the product for a year. Never EVER seen one ad or anything. Furthermore, if you block the parent program by your firewall in the host machine, nothing goes "home."

Besides, the man wants a solution to running Ubuntu on a system that runs Deep Freeze. I've given it to him.

Dedoimedo

P.S. You can even check the guide on me site if you're interested. And if you've read anything I have written so far, you'll notice I'm very conscious of security, privacy and such. Therefore, any product that passes the "Dedoimedo test of annoyability," I believe it's safe to use. Still, your and everyone's choice, the ultimate freedom.

---

### Post by Daveski on 2008-08-27
> **Dedoimedo said:**
> 
Besides, the man wants a solution to running Ubuntu on a system that runs Deep Freeze. I've given it to him.

P.S. You can even check the guide on me site if you're interested. And if you've read anything I have written so far, you'll notice I'm very conscious of security, privacy and such. Therefore, any product that passes the "Dedoimedo test of annoyability," I believe it's safe to use. Still, your and everyone's choice, the ultimate freedom.

Absolutely - and thanks for the link to the software. I just got scared away by the sweeping statement in the EULA that I would have 'consented' to.

---


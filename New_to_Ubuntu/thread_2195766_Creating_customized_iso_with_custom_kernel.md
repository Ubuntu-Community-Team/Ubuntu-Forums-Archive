---
title: "Creating customized iso with custom kernel"
date: 2013-12-26
forum: New to Ubuntu
---

### Post by joaocrespo on 2013-12-26
First i dont know if this is the the right section for this thread, but there seemed to have none so ...

Anyway i´m trying to install Ubuntu in an Pentium-M with no sucess (it freezes after selecting the install option in the menu), and after some messing around ( other distros and trying to tweak some boot parameters) the problems all seem to be related to PAE and ACPI, so i decided to try creating a custom ISO with my own custom kernel created specially for this machine.

Creating the kernel is for me the easy part, because i´ve done it in the past, but putting it in an ISO is the hard one (i´m looking preferebly to tools that allow me to install the kernel .deb into the ISO, or create my own ISO from a virtualized environment).

After some Googling around i learned about some neat tools to edit ISO´s, but all have their problems:

[Reconstructor](http://en.wikipedia.org/wiki/Reconstructor) seems like a good option, but the website is down.

[Remastersys](http://www.remastersys.com/) Seems another, but the author quited 

[UCK](http://sourceforge.net/projects/uck/) UCK doesn´t seem to have the options i want.

I´m open to sugestions and ideas.

Best Regards

---

### Post by ian-weisser on 2013-12-26
Is the goal to install a complete Ubuntu system with the custom kernel on the machine? If so, there are lots of other options.
Does it boot from USB? If so, you can bootstrap a working system onto a USB stick from another machine, test it, then copy it onto the hard drive. My old systems required a lot of testing like that.

Or is the goal to boot from the .iso every time?

---

### Post by joaocrespo on 2013-12-26
Yes, booting from USB is an option.

So you´re sugesting creating a working system (with the required tweaks) , put it in an USB stick, boot, run and install from there?

Seems like a great idea, do you have links to documentation on the subject that i can check? (preferebly an for dummies version lol)

---

### Post by ian-weisser on 2013-12-26
Well, here is how I would go about it. I'm not saying it's the best way or the most efficient. Essentially, we build a custom kernel on a working x86 machine and use a USB stick to try it on the Pentium machine

1) Try a current install image on the Pentium-M machine. It probably won't work, but the error message should tell you exactly which services need to be disabled in your custom kernel config. A good image to use is the Mini ISO at [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) . It's quite small.

2) Install a current version of Ubuntu onto a USB stick. A real install, not merely a Live environment. The Mini ISO is good for this, too. See [http://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator]("http://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creatorfor") for several ways to install a real Ubuntu system (not a Live image) to a USB stick. 

3) Use a working x86 machine to create the custom kernel. You said you have done this before.

4) Replace the kernel on the USB stick with the custom kernel. Try booting the Pentium-M from the USB stick. Usually, this means you must edit the bootloader settings to point to the new kernel.

5) If the new kernel doesn't boot, and you can figure out why, then repeat steps 3 and 4 until you get a bootable system.

6) Copy the bootable system, including the custom kernel, onto the hard drive.

7) Boot from the hard drive. Edit some of the /etc/udev/rules files to ensure hardware rules for the previous x86 system are removed so your network interfaces have sane values. Look through the dmesg logs to find other possible hardware problems. Use the package manager to add to your new system.

There are variations, like opening the case and moving the hard drive instead of using a USB stick.

---

### Post by joaocrespo on 2013-12-26
I´m going to try that, thanks for the advice

---

### Post by mörgæs on 2013-12-26
This might be of interest:
[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

---


---
title: "Inability to get past Grub screen and into Ubuntu 11.04"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by JmsnA on 2011-09-19
Hi, I recently did a dual installation on my HP laptop between Windows 7 and Ubuntu 11.04. I followed the directions on this site [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/) except I did not notice page 2 mentioned where to install Grub 2, nor did I see any message about choosing where to place it so I just hit install. I received a message stating the installation might fail and restarted. 

Upon turning on my laptop, I do not see a screen that gives me an option to boot between Ubuntu or Windows 7, so I can only assume Windows 7 was written over which at this point doesn't matter to me anymore. The problem is, I cannot get past the Grub loading screen.
It starts off like this [spoiler][IMG]http://i55.tinypic.com/2jfy4g5.jpg[/IMG][/spoiler]

Now, the memory checks and I selected both have both turned up normal. So I select UbUbuntu under the menu for the generic install and get this [spoiler][IMG]http://i54.tinypic.com/etsmtg.jpg[/IMG][/spoiler] The cursor just keeps blinking, the caps locked light flashes on and off and everything else does as well. I try hitting esc and any other assortment of buttons I can think of but it stays like this indefinitely. I am forced to hold down the power button and switch off to escape. 

Next I select the option to boot Ubuntu in recovery mode. Of course I get this screen [spoiler][IMG]http://i52.tinypic.com/2ai4gtx.jpg[/IMG][/spoiler] As stated with the Ubuntu load option, everything blinks continually and it is impossible to escape this screen without pressing the power button.

I know in the Grub 2 loader you have an option of putting some kind of coding in before selecting either option, and they give u a list of possible commands but I do not know what commands to put in. I want to load from CD/ROM and just reinstall everything from the Ubuntu CD I have but the computer does not boot from this drive at all. Either i don't know what commands to put in the Grub 2 loader, or the laptop is just unable to boot from CD as a result of the botched Ubuntu install. 

To conclude this, I am unable to boot from CD and reinstall and I am unable to get into Ubuntu 11.04 past the GRUB 2 loader screen. I tried loading Windows 7 from CD and Ubuntu from CD and the computer reads neither.  I am aware I botched the installation operation by non-deliberately not noticing the last steps on page 2 of the dual boot install. I just wanna get into Ubuntu or find a way to boot from the CD-Rom drive to attempt a reinstall. Any help will be most appreciated. Much thanks in advance.

---

### Post by Blasphemist on 2011-09-19
When you first turn on the system, you should see prompts to access bios and maybe one for a boot device menu. This is before grub comes up. When this grub comes up it is already trying to boot from the hard drive. You need to boot from the installation cd. In bios you set the cd drive at the top of the list of boot devices and in the boot device menu (if your computer has one) you can arrow to the cd and press enter.

You should boot to the cd and choose try ubuntu from its boot menu, also a grub menu. When ubuntu comes up, verify your internet connection by running firefox and coming back here to the forums. Then download the boot-repair program and run it. Press create boot info summary and copy the url it gives you. Then post that url in this thread so we can look at it.

Here is a command you can enter from a terminal in the live cd session to install boot-repair. If it prompts you for a password, just press enter. The terminal can be found in the application menu in the live cd session.
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```
The boot repair program may well be able to recover your system boot but we need to take a look at what the current state of it is before telling you how to do that.

---

### Post by JmsnA on 2011-09-19
Much thanks for your response! I was unable to get a BIOS selection screen unfortunately, it just jumped right to GRUB

Update- I managed somehow to break free of Grub by typing in "exit" in the command line which you have the option of accessing when GRUB prompts for a selection. I am proceeding to do a full re-installation of Ubuntu right now.

---


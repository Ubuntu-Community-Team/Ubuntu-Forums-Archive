---
title: "Weird graphics when i click the login button after installing Ubuntu 15.10 Gnome"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by Margon on 2015-10-27
Hello. this my first post here. Yesterday i downloaded ubuntu mini-iso and installed it on my desktop computer. i selected only the gnome software when i prompted to during the installation and everything is ok except 1-2 issues. 

The first is that every time it boots or shutting down it displays text messages which is something i dont like to see. i checked the grub configuration file and the command about the quite boot is enabled. However it continus always to display those text kernel messages. 

The second issue has to do with graphics. To be more specific every time i try to login to the system imediattely after i click the login button the sceen displays corrupted background and messy colors. i guess that this isnt a hardware problem as it appears only at the specific action.(Only when i try to login to the system) After 10 seconds everything is ok. 

The version of Ubuntu is 15.10 and the Gnome is 3.16

I am not too much experienced with Linux yet but i just felt in love with Gnome and Ubuntu.

---

### Post by Vladlenin5000 on 2015-10-27
Hi and welcome.

What graphics card are we talking about?

---

### Post by Margon on 2015-10-28
> **Vladlenin5000 said:**
> Hi and welcome.

What graphics card are we talking about?

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series]

---

### Post by Bucky Ball on 2015-10-28
*Threads merged.*

If you post something by mistake please report and staff will take care of it for you. :)

When you say you installed the Gnome software after the mini install, what exactly was that? Gnome desktop only? Ubuntu Gnome default machine profile from the tasksel during the mini install?

Incidentally, I get strange screen splashes after login. I have a monitor attached, though, and figure it is just part of the process. If everything is ok afterwards, I wouldn't worry about it (apart from the fact you find it unsightly). 

To get rid of the text at boot or shutdown you can add 'quiet splash' to the kernel line and I think that will get rid of it.

---

### Post by Margon on 2015-10-28
First of all thanks for replying and your useful advices. 

As for the Gnome Installation i installed the Ubuntu Gnome default machine during the installation process. 
 And yes after login everything is fine and work like a charm. Mostly i find it somehow visual frustrating . 

Now about the Kernel text messages my etc/default/grub file contains these lines:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```
 

I am not expert but i think this is the right setup to NOT display the kernel messages. However i cant get rid of them during the boot up process. !!!!!

---

### Post by Bucky Ball on 2015-10-28
> **Margon said:**
> 
I am not expert but i think this is the right setup to NOT display the kernel messages.

You appear to be right. Got me stumped.

Just curious. If you were after Ubuntu Gnome, why did you go through the mini.iso install rather than installing it directly from [here]("http://ubuntugnome.org/")? 

Mini install is for problematic installs where you can't get a GUI installer to work or you want to customise the install. If you want a regular Ubuntu flavour, just install it (for instance, if you use the mini.iso and then install ubuntu-desktop, there is no point using the mini.iso in the first place as installing ubuntu-desktop is equivalent to installing Ubuntu. Just install Ubuntu! :))

I only use the mini.iso. It installs the Ubuntu kernel only, I ignore tasksel, reboot and you log in to a terminal and you install the rest. I go for xfce4, a lightweight desktop environment, and whatever other apps/software I want/need, which isn't a lot (my installs generally end up between 6-9Gb). 

(PS: I have added code tags to your terminal output. See the last link in my signature. :))

---


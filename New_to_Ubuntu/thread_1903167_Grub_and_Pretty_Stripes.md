---
title: "Grub and Pretty Stripes"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by Jeheto on 2012-01-01
Hello,

I am a fairly competent computer geek that just recently installed Ubuntu 10.10 in a dual boot setup with Windows 7.

Ubuntu itself works beautifully. I am thoroughly enjoying it. However, I can't boot into Windows 7.

The boot manager (which I believe is called Grub2 for Linux) does not appear for me. After my computer displays the "Hit DEL for BIOS" screen and detects the drives, it moves into what I assume is the Grub. I see no text, only flashing stripes. Sometimes they are beautiful colors, other times just black and white. They're very pretty and all, but while they dance I can't see any text or options. After a time they are replaced by the log in screen. From there, everything works perfectly.

Some Notes:
     -My Windows 7 stuff is fine. It is located on a separate partition on the same drive. I can access it from the Home Folder in Ubuntu.
     -I do have up-to-date Nvidia drivers for Ubuntu.
     -Similar "stripe" problems have occurred to other users with Nvidia cards, though I haven't found one where the stripes happen in the Grub.

I've learned quite a bit trying to troubleshoot the problem. I've learned how to install files via terminal, how to use PPA (kindof), and how navigate through Ubuntu. I would very much like to access my Windows 7 though.

Please reply as soon as possible.

---

### Post by kansasnoob on 2012-01-01
On my Nvidia box I usually have to run the command:

```
gksudo gedit /etc/default/grub
```

And then remove the comment (#) I highlighted here:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
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
**[COLOR="Red"]#[/COLOR]**GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


Be sure to click on Save when you're done, and then run:

```
sudo update-grub
```

You may also find that you'll need to change the "splash" resolution after that's done but lets go one step at a time.

---

### Post by Jeheto on 2012-01-02
Thank you very much! That fixed everything.

---

### Post by dFlyer on 2012-01-02
Please mark as solved.

---

### Post by kansasnoob on 2012-01-02
> **Jeheto said:**
> Thank you very much! That fixed everything.

Really .......... everything :confused:

I usually also have to adjust the plymouth/splash resolution.

Just shout if you need more help, you can even PM me :)

---


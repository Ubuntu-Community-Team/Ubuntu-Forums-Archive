---
title: "login for dual boot"
date: 2012-03-24
forum: New to Ubuntu
---

### Post by jimbo160 on 2012-03-24
I set another computer with Ubuntu 9.04, and it did good on setup. When i would turn my computer on, i had a choice of Windows, Ubuntu, or recovery, useing Windows xp. I did the same setup useing Windows 7, and Ubuntu 11.10, on this computer, but, on my startup, i get the Ubuntu colored screen, with about 6 different choices. I finally figured out which would give me what i wanted. This would be ok for me, but i have 2 grand kids, that this could be a problem. I am trying to find out if there is a way to change this login choices, of not so many. 
                                                          Jimmy

---

### Post by kc1di on 2012-03-24
you will have to uninstall any linux kernals that are old and not in use.
Here is a webpage tells you how to do it:

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/")

---

### Post by miegiel on 2012-03-24
You can hide things like the *memory check* option and the *recovery mode* options of every kernel. But hiding that stuff will make it harder to access them when you need them. Personally I'd go for setting the default to what your grand kids want to use and set the timer short (but long enough to interrupt).

Documentation is here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

See GRUB_DISABLE_LINUX_RECOVERY=true in the doc. The memory check options should be mentioned there too somewhere, but I couldn't find them fast enough.

NOTE: Grub starts counting the menu options at 0. So 0 is the top menu option and 1 the second ;)

---

### Post by jimbo160 on 2012-03-24
I can see that the timer can be set at....[I]/etc/default/grub.....How, or where can i find this?
[/I]

---

### Post by miegiel on 2012-03-24
> **jimbo160 said:**
> I can see that the timer can be set at....[I]/etc/default/grub.....How, or where can i find this?
[/I]

You can edit it by running
```
gksudo gedit /etc/default/grub
```
in a terminal.

Don't forget to run
```
sudo update-grub
```
to make the changes take effect.

---

### Post by jimbo160 on 2012-03-24
mmmmmm i can read all this, but do not understand what it means. copy each in a terminal, then click enter? What is a terminal?

---

### Post by miegiel on 2012-03-24
> **jimbo160 said:**
> mmmmmm i can read all this, but do not understand what it means. copy each in a terminal, then click enter? What is a terminal?

It's what windows people (in this part of the world) call a "dos window".
See here for more [https://en.wikipedia.org/wiki/Terminal_emulator](https://en.wikipedia.org/wiki/Terminal_emulator)

Since it's easier and shorter to say how to do things in a terminal than to tell people how to navigate the [gui]("https://en.wikipedia.org/wiki/Graphical_user_interface") to do the same things, it's common in this forum to help people that way. Besides gui's change all the time (new versions or because users tinker with them) and it would be hard for someone with a different interface to help someone by telling them where to click.

It's also easier to avoid mistakes when copy+pasting a way to do something to a terminal.

In ubuntu 9.04 you can find the terminal in the programs menus, in 11.10 you can click on the ubuntu icon and search "term".

---

### Post by jimbo160 on 2012-03-24
Sorry to be so long, i had to go cut the grass. pardon my ignorance, but, i do not know which ubuntu icon you are referring to. There is one at the top of the forum page, but no where to search "term". I have none, i can see on the desktop? Which you talking about?
   I never used dos in windows, so i am unfamiliar with that also, but do know what it is.

---

### Post by jimbo160 on 2012-03-24
I manage to find this, but, do not understand it. there is no words of windows..............
# If you change this file, run 'update-grub' afterwards to update
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
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

### Post by miegiel on 2012-03-24
I'm not behind my machine all day (and all night) either :D

Let's try this (should work on every machine I think).
[LIST]
[*]Press Alt + F2
[*]In the box type *xterm* and click *run*
[/LIST]
Now you should have a black window with some text saying *your_username@your_machine:~$* and a blinking cursor. That text is called the prompt.
[LIST]
[*]Paste this ```
gksudo gedit /etc/default/grub
``` in the terminal and hit enter.
[*]A window will open and ask you for your password. After entering your password an editor will open with the */etc/default/grub* file.
[*]Now you can edit the file and, for example, change the timer from 10 seconds to 3, 4 or 5 seconds, or whatever you think is fast enough but not to fast.
[*]When you're done, save and exit and go back to the terminal.
[*]Paste this ```
sudo update-grub
``` in the terminal and hit enter. In this step the changes to the configuration get "implemented" into *GRUB*. You will be asked for your password again.
[*]When the prompt comes back you're done and you can close the terminal and reboot to see if the boot menu does what you want.
[/LIST]

Some things to consider:
[LIST=1]
[*]When you enter a password in linux you should be aware that you are about to make changes to the "system". Be careful not to break things! For example, if you would type all kinds of rubbish into the */etc/default/grub* file you machine might not even boot to windows.
[*]Before changing the *GRUB_DEFAULT=0* line, you should boot up and pause at the boot menu and count exactly which boot option you would like to be started by default. And don't forget the first boot option is numbered 0 and the second is 1, etc.
[*]Sometimes (when the kernel is updated for example) entries are added to the boot menu. If you have changed *GRUB* to boot windows and the windows boot option is moved down a line, you will need to redo all this.
[*]There is a [wikipedia]("https://en.wikipedia.org/wiki/Main_Page") entry for almost every technical term (wikipedia is an even better friend than google).
[/LIST]

---

### Post by mal1958 on 2012-03-24
> **jimbo160 said:**
> Sorry to be so long, i had to go cut the grass. pardon my ignorance, but, i do not know which ubuntu icon you are referring to. There is one at the top of the forum page, but no where to search "term". I have none, i can see on the desktop? Which you talking about?
   I never used dos in windows, so i am unfamiliar with that also, but do know what it is.

If you are in 9.04 to 10.04 or 10.10 and above and have the Gnome Desktop, then look to the top of the screen.  You will see a bar there that has Applications, Places and System.   Click on App, then the top choice and follow down to terminal.

---


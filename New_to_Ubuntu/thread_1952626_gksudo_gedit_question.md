---
title: "gksudo gedit question"
date: 2012-04-04
forum: New to Ubuntu
---

### Post by JXR on 2012-04-04
I've graduated from Installation & Upgrades" to "Absolute Beginner Talk"...;)

A reply to my previous post where I was struggling with enabling my laptop keyboard instructed me 

gksudo gedit /etc/default/grub

Since this seems a fairly important file, I don't want to mess it up,

I need to insert an instruction that, on boot, enables the keyboard (I'm using a USB keyboard to get by this problem). The instruction goes something like:
        **[COLOR=red][FONT=Verdana]noacpi [/FONT][/COLOR]**
        [B][COLOR=red][FONT=Verdana]pci=noacpi

[/FONT][/COLOR][/B]How, and where in the grub.cfg, do I correctly insert the command, and how should the line of code read? 

Thanks
[B][COLOR=red][FONT=Verdana]

[/FONT][/COLOR][/B]

---

### Post by jerome1232 on 2012-04-04
Before your go editing that file with boot options test them out, repeatedly hit shift during the boot up to get a grub menu. Highlight the main Ubuntu boot entry and hit "e" to edit the boot line, add those options to the end, hit ctrl+x to boot with your edits.

If it gets the desired result then you can hack up your boot options


The line will look like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR="Red"]noacpi pci=noacpi"[/COLOR]
```


So the entire file should look something like

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
[COLOR="RoyalBlue"]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noacpi pci=noacpi"[/COLOR]
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

Then run update grub to make the changes have an affect.

```
sudo update-grub
```

---

### Post by JXR on 2012-04-05
Thanks for your EXTREMELY CLEAR explanation.

I had tried the code in the grub menu before but it did not succeed in activating the keyboard. Apparently it didn't "take" when I hit Cntl x (to execute the boot). 

But I was told it would work if, after I'd gotten Ubuntu up and running I modified the file.

Now what's strange is (despite restarting a couple times) that in the terminal, after inputting: 
gksudo gedit/etc/default/grub

Despite asking me for/then accepting my password to "execute administrative tasks" it is not bringing up the window it did the first time showing the file (as you specified). Is there a reason it isn't bringing up the file anymore, and what can I do about it?

---

### Post by Elfy on 2012-04-05
> **JXR said:**
> gksudo gedit/etc/default/grub...

Try a space between gedit and /etc

It's trying to run gedit/etc/default/grub :)

```
gksudo gedit /etc/default/grub
```

---

### Post by JXR on 2012-04-05
Thanks, that worked!! (I should've caught that. Sorry)

HOWEVER, as I'm sure you suspected, the modification to the GRUB file DID NOT cause the keyboard/mouse pad to be activated. So for the time being, I'm stuck with having to use an outboard USB keyboard/mouse to run Linux (not Windows which enables the keyboard, on this dual boot).

I did get my gedit question answered and will mark this post "Solved" but will start a new thread asking if anyone has any other ideas how to enable the keyboard on a Dell Inspiron 2650 laptop after Unbutu has been successfully installed.

Many thanks.

---


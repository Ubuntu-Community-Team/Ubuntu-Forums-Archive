---
title: "Green User Dumb Q ALERT!! Cannot exit Command line at start up!!!"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by buttertooth on 2013-01-29
The story goes like this--- I created a new user log in for my mom ,she was getting used to the UBUNTU operating system, pushed some combination of CTRL-something and restarted the computer in command line that I cannot exit out of.  I have tried ctrl-alt-f7 and every combination I can find and nothing works.  I even tried -- switching users back to myself, rebooting, etc..  Every time it restarts it goes back to command line and says

branden@branden-vgn-cr131e:/home/debrastansberry$

please give me some magic to get my laptop back!!!!! 

Thank you so much in advance.  Even though I know you think I'm a dumbass.

Branden

---

### Post by buttertooth on 2013-01-29
I don't even know if what I'm asking for makes sense!  I have really enjoyed linux for the past 3 years and this is the first problem I've had.  Please help!

---

### Post by ckunzler on 2013-01-29
what permissions did she have?

---

### Post by buttertooth on 2013-01-29
I gave her the least possible

---

### Post by buttertooth on 2013-01-29
Here is a photo of what my screen looks like.

---

### Post by DuckHook on 2013-01-29
What happens with:

```
sudo start lightdm
```

---

### Post by buttertooth on 2013-01-29
start: job is already running: lightdm

---

### Post by DuckHook on 2013-01-29
Oops. Made my suggestion before I saw your latest post.

1. Do you recall what you did?
2. Try typing exit. (Likely won't work but worth a try.)
3. Do:
```
sudo update-grub
```4. Reboot

If this doesn't work, let's see how grub is configured:

```
nano /etc/default/grub
```

---

### Post by buttertooth on 2013-01-29
It says GNU nano 2.2.6 and then a menu below.  How do I know how it's configured?  Sorry for being ignorant.  I'm over my head.

---

### Post by buttertooth on 2013-01-29
> **DuckHook said:**
> Oops. Made my suggestion before I saw your latest post.

1. Do you recall what you did?
2. Try typing exit. (Likely won't work but worth a try.)
3. Do:
```
sudo update-grub
```4. Reboot

If this doesn't work, let's see how grub is configured:

```
nano /etc/default/grub
```

BTW, Thank you for taking the time to help.

---

### Post by DuckHook on 2013-01-29
From first forum principle on sticky about seeking help:

"There are no stupid questions. You're not a stupid person simply because you do not know how to do something, or do not have the answer to a question. Everyone was a green user at one point in time."

It's hard to correct this if you are stuck on a command line uploading photos, so let's do it the other way around and look at my grub to use as a point of comparison:

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
```...so a typical grub shouldn't look too complicated (some configuration files are horrendous). Any line with a # mark denotes a comment so can safely be ignored. You see that only six lines in my grub file are relevant. The critical line is:

GRUB_CMDLINE_LINUX_DEFAULT=

...and the values that follow. If they are anything other than "quiet splash", please wrtite them down and post back here.

---

### Post by DuckHook on 2013-01-29
> **buttertooth said:**
> BTW, Thank you for taking the time to help.

No prob. I might have to bail on you for tonight, though. It's getting late where I am and this old codger needs his beauty rest. Quite willing to pick up again tomorrow morning (well, it's already morning here, but you know what I mean)

Let's see what the next 15 minutes can do.

---

### Post by buttertooth on 2013-01-29
THank you Duck Hook!  I updated the grub and rebooted again.  It worked this time for some reason. It took me back to the regular log on screen and I was able to successfully log back in.

Thank you again!

---

### Post by DuckHook on 2013-01-29
Glad it worked. Please mark thread "solved" and happy Ubuntuing!

---


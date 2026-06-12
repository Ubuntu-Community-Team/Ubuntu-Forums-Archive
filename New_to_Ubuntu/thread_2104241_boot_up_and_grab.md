---
title: "boot up and grab"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by drdob on 2013-01-12
Ubuntu 12.04 lts 
I have put Ubuntu on my laptop, I have put it as the only one on the h/d. When I had it as a duel boot up , you had on “grab”, your 'main' boot up, and then a opportunity to boot up to the last good boot up. How can I do this when it is the only one? Thank you

---

### Post by sandyd on 2013-01-12
> **drdob said:**
> Ubuntu 12.04 lts 
I have put Ubuntu on my laptop, I have put it as the only one on the h/d. When I had it as a duel boot up , you had on &#8220;grab&#8221;, your 'main' boot up, and then a opportunity to boot up to the last good boot up. How can I do this when it is the only one? Thank you

Run this in the terminal:
```

gksudo gedit /etc/default/grub
```

Place a # in front of
```

GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
```
so that it looks like
```

#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=false
```

Save the file
run
```

sudo update-grub
```

There will now be a 10 second timeout for you to choose the kernel you want.

That is adjustable by increasing/decreasing GRUB_TIMEOUT, which is set to 10 by default.

---

### Post by drdob on 2013-01-13
thank you for you help. i will do this):P

well i tried but it did not work,please be gental with me i am new to all this ;) this what i did in turmanal with the grub file.
# If you change this file, run 'update-grub' afterwards to update
-----n
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

#GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=false
#GRUB_TIMEOUT=10
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

Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


thank you dr dob

---

### Post by sandyd on 2013-01-13
oops
must have been typing fast - run the below in the terminal and it should be fine
```

sudo update-gurb
```

---

### Post by drdob on 2013-01-13
sorry still not working all i got was :
Searching for GRUB installation directory ... found: /boot/grub
/etc/default/grub: line 2: -----n: command not found

---

### Post by Impavidus on 2013-01-13
What's that line```
-----n
``` doing there? Line 2 should only contain a comment:```
# /boot/grub/grub.cfg.
```You must have hit some key whilst editing.

Replace line 2 of /etc/default/grub (the one with -----n) with the comment I gave you (or any other comment; it's a comment, so it doesn't matter), save the file and run```
sudo update-grub
```

---

### Post by John_Swing on 2013-01-13
During the countdown you have to press ESC or MAJ to show grub.

---

### Post by drdob on 2013-01-13
sorry folks all i get is below:
/usr/sbin/grub-mkconfig: 30: /etc/default/grub: Uncomment: not found
i will put the 'page' as it is
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg. 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=false
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

Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"sudo

thank you all for your help i feel a right twit:redface:
but the boot may be on the othe foot if we were talking about Medieval history!!drdob

---

### Post by audiomick on 2013-01-13
> **drdob said:**
> sorry folks all i get is below:
/usr/sbin/grub-mkconfig: 30: /etc/default/grub: Uncomment: not found
i will put the 'page' as it is
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg. 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=false
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
[COLOR="Red"]
Uncomment to get a beep at grub start[/COLOR]
#GRUB_INIT_TUNE="480 440 1"sudo


The line in red should have a hash at the front of it. This thing # .
When that is at the start of a line, it is ignored when the file is run. If the hash is missing, the machine will see it as a command, which that line obviously isn't.

Don't forget
```
sudo update-grub
``` when you have finished.

To go back to your first post: If there is only one operating system on the machine, grub doesn't show by default. With a fresh install, there will only be one Linux entry to choose from, until the kernel gets updated. Once the kernel has been updated, as happens from time to time, the grub menu would show an number of entries, the top one of which is the newest kernel. As long as the grub menu isn't showing and you don't do anything to change the behaviour, like, for instance, showing the menu and choosing an earlier one, the machine will always boot by default to the latest kernel.

---

### Post by drdob on 2013-01-13
done it  :D=D> and test it it works!!!! thank you all very much drdob

---


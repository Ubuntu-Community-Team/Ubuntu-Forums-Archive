---
title: "various boot batch files"
date: 2007-01-31
forum: Programming Talk
---

### Post by tocleora on 2007-01-31
Ok, this is what I want to do... I want to create a batch file that if I run it instead of "sudo reboot".  I'm thinking something similar to:

reboot -windows
this would change in grub to make windows the primary boot so I don't have to wait for ubuntu to restart, then select windows to play games. (hope that makes sense)

reboot -beryl
Since I don't run gdm and have an xorg.conf currently that gives me the options between dual monitor or single monitor, I want this to tell gdm to start on boot and then replace my xorg.conf with a beryl compatible configuration.

reboot -normal
Would change grub to make ubuntu the primary boot option, would change my xorg.conf back to the one that gives me the dual boot options, would make sure gdm is not going to start on boot.  I may need this to not actually reboot since I will more than likely be in xwindows and not be able to get to exit to a command prompt.  So it would just make the proper changes and then I can reboot from the gui.

I'm assuming I'll do this with a batch file, With the grub.conf seems easy if I know how in the grub.conf file to make windows the primary then I could have two I could just copy whichever one to the right place, same with the xorg.conf file, but I don't know how to tell it to turn grub start on boot on or off, is this in a conf file as well?  Any information would be appreciated, thanks in advance.

---

### Post by tocleora on 2007-01-31
I think I've figured out the grub part and already had the xorg part, so I guess now I just need to know what configuration file (if any) or what I would set/change to turn gdm boot at start on and off.  Anyone?

EDIT: To be able to do it from a batch file. ;)  I downloaded sysv-rc-conf and bum but it appears neither have command line options...

---

### Post by tocleora on 2007-01-31
Alright, in case anyone else is curious, this is how I've gotten it to work so far.  This is a script I put in /usr/bin called lreboot.  I just run it by calling "sudo lreboot".

```

#!/bin/sh

echo "LreBoot Menu Options..."
echo "1. Reboot into Windows"
echo "2. Reboot into Linux, No GDM"
echo "3. Reboot into Linux, No GDM, run sysv-rc-conf"
echo "4. Reboot into Linux, GDM"
echo "5. Reboot into Linux, GDM, run sysv-rc-conf"
echo "Q. Exit"
echo -n "Which Option? "
read optionnum

case $optionnum in
	1)
		cp /etc/X11/xorg.dual /etc/X11/xorg.conf
		cp /boot/grub/menu.windows /boot/grub/menu.lst
		reboot
		exit 
		;;
	2)
		cp /etc/X11/xorg.dual /etc/X11/xorg.conf
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		reboot
		exit
		;;
	3)
		cp /etc/X11/xorg.dual /etc/X11/xorg.conf
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		sysv-rc-conf
		reboot
		exit
		;;
	4)
		cp /etc/X11/xorg.original /etc/X11/xorg.conf
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		reboot
		exit
		;;
	5)
		cp /etc/X11/xorg.original /etc/X11/xorg.conf
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		sysv-rc-conf
		reboot
		exit
		;;
	*)
		exit
		;;
esac

```

I've tested all but #1, and they seem to work well.  menu.ubuntu has two entries in it, linux & windows, with default set to "0".  menu.windows is the same with the default set to "1".  xorg.original is the original xorg.conf before I added dual support.  xorg.dual has the dual support.  sysv-rc-conf is what I call to turn gdm on or off in the boot sequence.  This is the pain one as it runs an application I have to physically set gdm on or off.  But at least it's a little more automated than it was before.  #1 especially, as if I'm rebooting but have to pee really bad ( :D ), I can now just select option 1 and I don't have to wait for grub to come up! :)  

So if anyone knows either how to:

A. Run XGL without GDM

or 

B. How to set the GDM to run (or not run) on Boot from a command line

I'd appreciate it. :)

---

### Post by tocleora on 2007-01-31
GOT IT!

It seems sysv-rc-conf has command line options, so I've shortened the script and tested it, works great!

```

#!/bin/sh

echo "LreBoot into..."
echo "1. Windows"
echo "2. Ubuntu (Command Prompt)"
echo "3. Ubuntu (XGL)"
echo "Q. Exit"
echo -n "Which Option? "
read optionnum

case $optionnum in
	1)
		cp /etc/X11/xorg.dual /etc/X11/xorg.conf
		cp /boot/grub/menu.windows /boot/grub/menu.lst
		sysv-rc-conf gdm off
		exit 
		;;
	2)
		cp /etc/X11/xorg.dual /etc/X11/xorg.conf
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		sysv-rc-conf gdm off
		exit
		;;
	3)
		cp /etc/X11/xorg.original /etc/X11/xorg.conf
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		sysv-rc-conf gdm on
		exit
		;;
	*)
		exit
		;;
esac

```

I've taken reboot out as at least 2 of the options could be ran from within xwindows.   I guess I could add a second question that asks if I want to reboot... Anyway hope this helps anyone else that might want to do something similar!

---

### Post by tocleora on 2007-01-31
Last message on this topic (unless someone responds), promise. :)

I went ahead and updated the script to ask if I want to reboot or not.  I also added messages so I know exactly what's going on.  Here's the updated version if anyone is interested in it.

```

#!/bin/sh

echo "LreBoot into..."
echo "1. Windows"
echo "2. Ubuntu (Command Prompt)"
echo "3. Ubuntu (XGL)"
echo "Q. Exit"
echo -n "Which Option? "
read optionnum

case $optionnum in
	1)
		echo " o copying dual session xorg.conf..."
		cp /etc/X11/xorg.dual /etc/X11/xorg.conf
		echo " o copying windows primary grub conf..."
		cp /boot/grub/menu.windows /boot/grub/menu.lst
		echo " o turning off gdm on boot..."
		sysv-rc-conf gdm off
		;;
	2)
		echo " o copying dual session xorg.conf..."
		cp /etc/X11/xorg.dual /etc/X11/xorg.conf
		echo " o copying ubuntu primary grub conf..."
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		echo " o turning off gdm on boot..."
		sysv-rc-conf gdm off
		;;
	3)
		echo " o copying original xorg.conf..."
		cp /etc/X11/xorg.original /etc/X11/xorg.conf
		echo " o copying ubuntu primary grub conf..."
		cp /boot/grub/menu.ubuntu /boot/grub/menu.lst
		echo " o turning on gdm on boot..."
		sysv-rc-conf gdm on
		;;
	*)
		;;
esac

echo -n "Do you want to reboot? [y/N] "
read rebootnum
case $rebootnum in
	Y)
		reboot		
		exit 
		;;
	y)
		reboot
		exit
		;;
	*)
		exit
		;;
esac

```

I should also mention that once leaving Windows, it will still be the primary in grub so you would want to watch for that (hope *that's* not when I need to pee!) and optionally run lreboot again next time you reboot even if you're going back into linux.  ultimately if you don't need to pee, you would just select the one that ubuntu is primary on and then you wouldn't have to worry about it. ;)

[FIN.]

---


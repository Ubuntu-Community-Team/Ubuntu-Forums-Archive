---
title: "Want to control screen brightness"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by boof1988 on 2008-11-09
I'd like to be able to control the screen brightness of the notebook computer in the sig. below.

Using a method at [louboldt.com](http://louboldt.com/ilinuxmisc.htm#lshw), here is the (I believe) video card info for the machine:

```
id:	display:0
description: 	VGA compatible controller
product: 	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	2
bus info: 	pci@0000:00:02.0
version: 	03
width: 	        32 bits
clock: 	        33MHz
capabilities: 	msi pm vga_controller bus_master cap_list
configuration:	latency	= 0
```

I have searched around the forums and am still clueless.  See a lot about Nvidia but couldn't find anything that helps me understand how to control (if it's even possible) the screen brightness of my box.

[COLOR="Blue"]Have tried the default (installed) "brightness applet" and it doesn't control the brightness.[/COLOR]

Any help is much appreciated.

---

### Post by dark_harmonics on 2008-11-09
Did you see this post? :[http://ubuntuforums.org/showthread.php?t=649621](http://ubuntuforums.org/showthread.php?t=649621)

He is talking about kubuntu at first but does mention ubuntu. I am assuming you've tried the function keys on your laptop. There is probably some sort of controlling module for that. Are there any obvious errors on your dmesg output that might point in the right direction? 

For wireless hardware switches there is a file entry that you can toggle, but i dont know about brightness. For my Macbook Pro i had to install a special module to allow ubuntu to control my brightness. 

If none of this helps you should post your computers model name and number so that we can help you do some more in depth searches.

*EDIT*: Found this post too that looks interesting: [http://ph.ubuntuforums.com/showthread.php?t=451781](http://ph.ubuntuforums.com/showthread.php?t=451781)

Sorry if im not real specific but im just a user like you who has to guess his problems out lol.

---

### Post by boof1988 on 2008-11-09
> **dark_harmonics said:**
> Did you see this post? :[http://ubuntuforums.org/showthread.php?t=649621](http://ubuntuforums.org/showthread.php?t=649621)

He is talking about kubuntu at first but does mention ubuntu. I am assuming you've tried the function keys on your laptop. There is probably some sort of controlling module for that. Are there any obvious errors on your dmesg output that might point in the right direction? 

For wireless hardware switches there is a file entry that you can toggle, but i dont know about brightness. For my Macbook Pro i had to install a special module to allow ubuntu to control my brightness. 

If none of this helps you should post your computers model name and number so that we can help you do some more in depth searches.

*EDIT*: Found this post too that looks interesting: [http://ph.ubuntuforums.com/showthread.php?t=451781](http://ph.ubuntuforums.com/showthread.php?t=451781)

Sorry if im not real specific but im just a user like you who has to guess his problems out lol.

Thanks for the fast reply...  I have tried the keyboard controls and they don't seem to work (<fn> + <F6> and <fn> + <F7>).  Thanks for the links... will take a look at them.

My box:
Toshiba A105-S4274
```

id:	        bs-laptop
description: 	Computer
product: 	Satellite A105
vendor: 	TOSHIBA
version: 	PSAA8U-0EQ034
serial: 	<XXXXXXXXX>
width: 	        32 bits
capabilities: 	smbios-2.31 dmi-2.31 smp-1.4 smp
```

I just typed in
```
dmesg
```
and I tried to look through it, what "words" should I look for?

Thanks again

---

### Post by dark_harmonics on 2008-11-09
Found this too: [http://linuxhappy.wordpress.com/2007/12/17/brightness-on-toshiba-tecra-a9-using-restricted-drivers-on-ubuntu/](http://linuxhappy.wordpress.com/2007/12/17/brightness-on-toshiba-tecra-a9-using-restricted-drivers-on-ubuntu/)

Im not sure on the dmesg command. I know its alot of jumble but sometimes at the end there is an obvious error message. I guess I'm just not ubuntu techie enough to know which modules would handle brightness or we could grep them from the output with dmesg| grep modulename

---

### Post by boof1988 on 2008-11-09
> **dark_harmonics said:**
> Found this too: [http://linuxhappy.wordpress.com/2007/12/17/brightness-on-toshiba-tecra-a9-using-restricted-drivers-on-ubuntu/](http://linuxhappy.wordpress.com/2007/12/17/brightness-on-toshiba-tecra-a9-using-restricted-drivers-on-ubuntu/)

Im not sure on the dmesg command. I know its alot of jumble but sometimes at the end there is an obvious error message. I guess I'm just not ubuntu techie enough to know which modules would handle brightness or we could grep them from the output with dmesg| grep modulename

Thanks for the links.  Finding the links is one of the hard parts for me... I never know what to look for and then when I do find stuff I can't pick which ones are of any use.

Most of the stuff I have seen, mentions "nVidia".  What is nVidia?  Is it the hardware or the software (drivers that "do stuff" with the hardware)?  I'm reading and trying out the nVidia stuff but I'm not sure if it will help me or not.

Here's some info from my machine (for review):

```
bs@bs-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

And:

```
id:		display:0
description: 	VGA compatible controller
product: 	Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	2
bus info: 	pci@0000:00:02.0
version: 	03
width: 		32 bits
clock: 		33MHz
capabilities: 	msi pm vga_controller bus_master cap_list
configuration:	latency	= 0

id:		display:1
description: 	Display controller
product: 	Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
vendor: 	Intel Corporation
physical id: 	2.1
bus info: 	pci@0000:00:02.1
version: 	03
width: 		32 bits
clock: 		33MHz
capabilities: 	pm bus_master cap_list
configuration:	latency	= 0
```

Edit:  Found [this](http://ubuntuforums.org/showthread.php?t=975990&highlight=integrated+graphics+controller) thread, which may be useful.

---

### Post by dark_harmonics on 2008-11-09
You should not be following any nvidia threads because from your output, you are using intel drivers. I saw a lot of "hurrays!" on the second link i edited into my first post up there. If you browse to the end of that thread alot of people were experiencing some success.

---

### Post by dark_harmonics on 2008-11-09
Check here too: [http://ph.ubuntuforums.com/showthread.php?t=767219&page=3](http://ph.ubuntuforums.com/showthread.php?t=767219&page=3)

When i go under my /etc/acpi folder there is a brightness script for up and down. I wonder if maybe there is a /sys device somewhere that we can change. I am going to look on my system to see but its really not a good test. 

I so wish i was sitting at your computer right now to test!

Edit:

I went to my /sys folder and ran a find command:

```
sudo find -name "*brightness*"
```

and the results were:

./devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
./module/video/parameters/brightness_switch_enabled


I wonder what would happen on yours?

---

### Post by boof1988 on 2008-11-09
> **dark_harmonics said:**
> Check here too: [http://ph.ubuntuforums.com/showthread.php?t=767219&page=3](http://ph.ubuntuforums.com/showthread.php?t=767219&page=3)

I'll check that in a minute.

> **dark_harmonics said:**
> When i go under my /etc/acpi folder there is a brightness script for up and down. I wonder if maybe there is a /sys device somewhere that we can change. I am going to look on my system to see but its really not a good test. 

I so wish i was sitting at your computer right now to test!

Thanks for showing me how to search.  Here's a search of my /etc/acpi:

```
bs@bs-laptop:/etc$ sudo find -name "*brightness*"
./acpi/suspend.d/50-tosh-save-brightness.sh
./acpi/thinkpad-brightness-down.sh
./acpi/events/sony-brightness-down
./acpi/events/panasonic-brightness-down
./acpi/events/sony-brightness-up
./acpi/events/asus-brightness-up
./acpi/events/tosh-brightness-down
./acpi/events/video_brightnessup
./acpi/events/asus-brightness-down
./acpi/events/panasonic-brightness-up
./acpi/events/thinkpad-brightness-up
./acpi/events/video_brightnessdown
./acpi/events/tosh-brightness-up
./acpi/events/thinkpad-brightness-down
./acpi/video_brightnessup.sh
./acpi/resume.d/50-tosh-restore-brightness.sh
./acpi/video_brightnessdown.sh
./acpi/thinkpad-brightness-up.sh
bs@bs-laptop:/etc$
```

Can you tell me which one you think might be a brightness script like you mentioned on your system?

> **dark_harmonics said:**
> I went to my /sys folder and ran a find command:

```
sudo find -name "*brightness*"
```

and the results were:

./devices/platform/applesmc.768/leds/smc::kbd_backlight/brightness
./module/video/parameters/brightness_switch_enabled

I don't get anything in the /sys directory:

```
bs@bs-laptop:/sys$ sudo find -name "*brightness*"
bs@bs-laptop:/sys$ 

```

There were a whole lotta files (with *brightness*) in a different directory, will look again.


> **dark_harmonics said:**
> I wonder what would happen on yours?

Will keep looking.  Thanks again for showing me how to search for files in terminal.

[COLOR="Blue"]Edit:  Trying the method in [this](http://ubuntuforums.org/showthread.php?t=673946#1) link:[/COLOR]

---

### Post by boof1988 on 2008-11-09
I have found the following... which I think are (some) of the script that controls the brightness of the screen.  If I can figure out what key is needed for "event=hkey VAL[DZ] 00000001 00000140", maybe I can figure out how to control the brightness.

```
bs@bs-laptop:/etc/acpi/events$ cat tosh-brightness-down
event=hkey VAL[DZ] 00000001 00000140
action=/etc/acpi/toshbright.sh down
bs@bs-laptop:/etc/acpi/events$ 
```
this...
```
bs@bs-laptop:/etc/acpi/events$ cat tosh-brightness-up
event=hkey VAL[DZ] 00000001 00000141
action=/etc/acpi/toshbright.sh up
bs@bs-laptop:/etc/acpi/events$
```
and this...
```
bs@bs-laptop:/etc/acpi$ cat toshbright.sh
#!/bin/sh

BRIGHTNESS=$(( `grep brightness: /proc/acpi/toshiba/lcd | cut -d: -f2` + 0 ))
MAXBRIGHT=$(( `grep brightness_levels: /proc/acpi/toshiba/lcd | cut -d: -f2` - 1 ))

if [ "x$1" = "x" ]; then
   echo $BRIGHTNESS / $MAXBRIGHT
elif [ "x$1" = "xdown" ]; then
   if [ "x$BRIGHTNESS" != "x0" ]; then
      BRIGHTNESS=$(( $BRIGHTNESS - 1 ))
      echo 'brightness : '$BRIGHTNESS > /proc/acpi/toshiba/lcd
   fi
elif [ "x$1" = "xup" ]; then
   if [ "x$BRIGHTNESS" != "x$MAXBRIGHT" ]; then
      BRIGHTNESS=$(( $BRIGHTNESS + 1 ))
      echo 'brightness : '$BRIGHTNESS > /proc/acpi/toshiba/lcd
   fi
else
   echo >&2 Unknown argument $1
fi
bs@bs-laptop:/etc/acpi$ 
```

---

### Post by dark_harmonics on 2008-11-09
Try running that script that you found with :

```
sudo /etc/acpi/toshbright.sh up

```

The ones i had didnt do anything interesting for me but we arent on the same hardware.

---

### Post by boof1988 on 2008-11-11
> **dark_harmonics said:**
> Try running that script that you found with :

```
sudo /etc/acpi/toshbright.sh up

```

The ones i had didnt do anything interesting for me but we arent on the same hardware.

Thanks for the help and such.

I tried to run the script as shown here:

```
bs@bs-laptop:~$ sudo /etc/acpi/toshbright.sh up
grep: /proc/acpi/toshiba/lcd: No such file or directory
grep: /proc/acpi/toshiba/lcd: No such file or directory
/etc/acpi/toshbright.sh: 20: cannot create /proc/acpi/toshiba/lcd: Directory nonexistent
bs@bs-laptop:~$
```

Will look around a bit more and try to understand what the script does.  One other thing I might try is to use the script lcdbryt that's in the other thread you posted.

I'm hoping something will eventually work cause the brightness is blinding me.:)

---


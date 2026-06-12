---
title: "HOWTO: USB Logitech mouse and 800 cpi with udev"
date: 2004-11-14
forum: Outdated Tutorials &amp; Tips
---

### Post by p!=f on 2004-11-14
**What is this good for?**
 This will double your mouse resolution from 400 to 800 cpi to make it more precise. It's very usefull if you spend some time by playing games, working on graphics or you just love moving your mouse around and around...
         
         **Requirements**:
         * USB bus
         * Logitech Mouse
         * Alexios Chouchoulas [LMCtl]("http://www.bedroomlan.org/%7Ealexios/coding_lmctl.html") 
(Download the Debian package attached here to get the support for MX310 and MX510 mice)
(Original Debian package [available]("http://www.bedroomlan.org/%7Ealexios/files/SOFTWARE/lmctl/lmctl_0.3.2_i386.deb"))
         
         **Notes:**
 * Mouse used in this HOWTO is (or maybe was) the basic USB wheel mouse in the Logitech product line (M-BJ58 Wheel mouse) so I suppose MX series should be supported and working without a glitch.
         * There's also [Logitech Mouse Applet]("http://freshmeat.net/projects/logitech_applet") from Brad Hards (more devices supported) but I prefer LMCtl over it. 
         
         Download and install lmctl_0.3.2_i386.deb. If you use the one attached here you have to ```
gzip -d  lmctl_0.3.2_i386.deb.gz
``` it first. After that run *lmctl* with --help parameter to get the list of available parameters, especially -4, -8 and --sms ones.
         
* **Basic operations** *

         Scan USB bus for supported Logitech mouse:
         ```

         [~] > sudo lmctl -s
         002.001: 0000:0000 Not a Logitech device
         001.002: 046d:c00e Wheel Mouse Optical (M-BJ58) Caps: RES
         001.001: 0000:0000 Not a Logitech device
         
```
         
         Get the status of your mouse:
         ```

         [~] > sudo lmctl -i
         001.002: 046d:c00e Wheel Mouse Optical (M-BJ58) Caps: RES
         		Resolution (RES): 400 cpi
         
```
         
         As you can see your mouse is probably running with 400 cpi. Something you want to change. 

**I want to ask something first. What does CAPS and RES mean? I also have SMS there.**
CAPS are special capabilities available on your mouse. RES means resolution and SMS means that your mouse is SmartControl ready.

         Setting up 800 cpi and SmartControl/Cruise control...
*Note: Setting up SmartControl on this mouse is useless, it's used just for demonstration purposes.*
         ```

         [~] > sudo lmctl -8 --sms
         001.002: 046d:c00e Wheel Mouse Optical (M-BJ58) Caps: RES
         		Resolution set to 800 cpi
         
         [~] > sudo lmctl -i
         001.002: 046d:c00e Wheel Mouse Optical (M-BJ58) Caps: RES
         		Resolution (RES): 800 cpi
         
```
         
         Now enjoy the smoothness. Great isn't it?
      
      **I restarted my computer and my mouse is crawling again. How do I start it automagically on boot?**
There're at least three choices to pick up from.
* a script put in /etc/rc.boot which configures the mouse every restart (obsolete)
* via hotplug (won't be described here)
* via udev which is easier to set up than hotplug (recommended)

* **Setting the mouse up everytime you plug/unplug the mouse using a udev rule** *

Check another file attached here - *logitech-mice.rules.txt*. This udev rule contains support for the following mice:
* Wheel Mouse Optical
* MouseMan Traveler
* MouseMan Dual Optical
* MX300 Optical Mouse
* MX310 Optical Mouse
* MX500 Optical Mouse
* MX510 Performance Optical Mouse
* iFeel Mouse (silver)

Download, rename it to logitech-mice.rules... ```
 [~/downloads] > mv -v logitech-mice.rules.txt logitech-mice.rules
`logitech-mice.rules.txt' -> `logitech-mice.rules'

```
... and put in
/etc/udev/rules.d/
```

[~/downloads] > sudo mv -v logitech-mice.rules /etc/udev/rules.d/
`logitech-mice.rules' -> `/etc/udev/rules.d/logitech-mice.rules'

```
List the directory to see we need to tweak permissions...
```

[/etc/udev/rules.d] > ls -l
-rw-r--r--  1 pef  pef  716 2004-12-01 00:20 logitech-mice.rules
lrwxrwxrwx  1 root root  13 2004-10-05 14:59 udev.rules -> ../udev.rules
lrwxr-xr-x  1 root root  12 2004-11-29 13:51 z_hal-plugdev.rules -> ../hal.rules

```
```

[/etc/udev/rules.d] > sudo chown root.root logitech-mice.rules

```
```

[/etc/udev/rules.d] > ls -l
-rw-r--r--  1 root root 716 2004-12-01 00:20 logitech-mice.rules
lrwxrwxrwx  1 root root  13 2004-10-05 14:59 udev.rules -> ../udev.rules
lrwxr-xr-x  1 root root  12 2004-11-29 13:51 z_hal-plugdev.rules -> ../hal.rules

```
This should be sufficient. You may try to replug your mouse now to check if it works.

* Executing on boot using a script
*This is the obsolete approach. If you replug your mouse the settings will be lost. Use udev way instead.*

      Create a directory /etc/rc.boot ...
      ```

      sudo mkdir /etc/rc.boot
      
```
      Create and edit a file inside this newly created directory called ie. logitech-mouse...
      ```

      sudo nano -w /etc/rc.boot/logitech-mouse
      
```
      ... and put _this_ inside ...
      > 
      #!/bin/sh
      echo "Tunning Logitech mouse..."
      lmctl -8 --sms
      
    ... finally give your script appropriate permissions so it can be executed
      ```

      sudo chmod u+x /etc/rc.boot/logitech-mouse
      
```
      *Note: There's no need to use sudo because every script in /etc/rc.boot directory is run under root privileges.*

**I want my old settings back! How?**
Delete the /etc/udev/rules.d/logitech-mice.rules or /etc/rc.boot/logitech-mouse file (depends on the configuration you selected - udev or a script) and run...
```

         [~] > sudo lmctl -4 --no-sms

```

---

### Post by zenwhen on 2004-11-15
Along with the thumb button guide, this make my Logitech MX500 function just as it would with the Logitech drivers in Windows. 

I'm getting everything I paid for when I bought the mouse. Imagine that.

---

### Post by unikum on 2004-11-22
This doesnt work for me. After reboot its back to 400 cpi.
I have doublechecked everything.

---

### Post by p!=f on 2004-11-23
[QUOTE=unikum]This doesnt work for me. After reboot its back to 400 cpi.
I have doublechecked everything.[/QUOTE]

I just love this kind of post. :) "My printer doesn't print". More informations next time.

What's your mouse?
Can you get 800 cpi from your mouse just using CLI?
Did you really doublecheck everything? Is your startup script executable?

---

### Post by unikum on 2004-11-23
Logitech mouseman optical dual.

I can get 800 with sudo lmctl -8 --sms

What do you mean with CLI?

I did type sudo chmod u+x /etc/rc.boot/logitech-mouse but when i check its doesnt seems to have been executable.... I dont know... -rwxr--r--


Text in logitech-mouse:
```
      [~] > cat /etc/rc.boot/logitech-mouse
      #!/bin/sh
      echo "Tunning Logitech mouse..."
      lmctl -8 --sms
```

---

### Post by p!=f on 2004-11-23
CLI stands for Command Line.
-rw**x**r--r-- = as you can see it has the executable permission given to a user.

Can you try to run the script manually?
```

sudo /etc/rc.boot/logitech-mouse

```
If it works it should be working at the boot. Wierd...

Could you also list /etc/rc.boot directory and post it here?
```

ls -l /etc/rc.boot

```

And finally, post the output of
```

sudo lmctl -i
sudo lmctl -s

```

---

### Post by wallijonn on 2004-11-26
I downloaded the lmctl.deb package.

root terminal:
```
dpkg -i lmctl_0.3.2_i386.deb
lmctl --help
lsusb
lmctl -s
lmctl -i

```
It would seem that my Logitech MX510 is not supported:
```

# lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 046d:c01d Logitech, Inc.
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
# lmctl -s
004.001: 0000:0000 Not a Logitech device
003.001: 0000:0000 Not a Logitech device
002.002: 046d:c01d Unknown or Unsupported Logitech device
002.001: 0000:0000 Not a Logitech device
001.001: 0000:0000 Not a Logitech device
#

```

---

### Post by p!=f on 2004-11-26
As a description says
> 
lmctl can configure vendor-specific options on Logitech USB mice (or dual-personality mice plugged into the USB port). A number of recent devices are supported. The program is mostly useful in setting the resolution to 800 cpi on mice that boot at 400 cpi (such as the author’s MX-500), and disabling SmartScroll or Cruise Control for those who would rather use the two extra buttons as ordinary mouse buttons.

Strange your mouse is not recognized. Anyway, you may try this:
```

sudo lmctl -p c01d -8 --sms

```

If it doesn't work, try to use Logitech Mouse Applet (see link in the first post).

---

### Post by wallijonn on 2004-11-26
that would be ```
sudo lmctl -p 046d:c01d -8 --sms
```

It did not return an error message. But it still lists the MX510 as an unknown device. 

The Logitech Applet readme file states that the MX510 & MX500 are both M-BP81A devices.

---

### Post by p!=f on 2004-11-26
[QUOTE=wallijonn]that would be ```
sudo lmctl -p 046d:c01d -8 --sms
```

It did not return an error message. But it still lists the MX510 as an unknown device. 

The Logitech Applet readme file states that the MX510 & MX500 are both M-BP81A devices.[/QUOTE]
If it did not return any error, could you confirm with ```
sudo lmctl -i
``` that your mouse has 800cpi turned on?

---

### Post by wallijonn on 2004-11-27
```

#sudo lmctl -i
002.002: 046d:c01d Unknown or Unsupported Logitech device
```

---

### Post by p!=f on 2004-11-27
[QUOTE=wallijonn]that would be ```
sudo lmctl -p 046d:c01d -8 --sms
```
[/QUOTE]
Not really...
```

[~] > sudo lmctl -p 046d:c00e -8 --sms

[~] > sudo lmctl -p c00e -8 --sms
001.002: 046d:c00e Wheel Mouse Optical (M-BJ58) Caps: RES
        Resolution set to 800 cpi

```
[quote=wallijonn]
The Logitech Applet readme file states that the MX510 & MX500 are both M-BP81A devices.
[/quote]
There must be the typo.
MX500 = M-BP81A 
MX510 = M-BS81A

I've added the support for MX510 and recompiled the package. See attachement.
Packed with gzip to be able to post it here. 
Hope it helps.

---

### Post by wallijonn on 2004-11-27
[img]http://www.ubuntuforums.org/images/icons/icon14.gif[/img]

Thank you for your recompiled package. I downloaded it, started a Root Terminal, then
```


# [COLOR=Red]gunzip lmctl_0.3.2_i386.deb.gz[/COLOR]
# [COLOR=Red]sudo dpkg -i lmctl_0.3.2_i386.deb[/COLOR]
# [COLOR=Red]lmctl -i[/COLOR]
[COLOR=Blue]
002.002: 046d:c01d MX510 Performance Optical Mouse (M-BS81A) Caps: RES SMS
        Resolution (RES): 400 cpi
        SmartScroll (SMS): on[/COLOR]
# [COLOR=Red]lmctl -8 --sms[/COLOR]
[COLOR=Blue]002.002: 046d:c01d MX510 Performance Optical Mouse (M-BS81A) Caps: RES SMS
        Resolution set to 800 cpi
        SmartScroll enabled
[/COLOR]

```
[img]http://www.ubuntuforums.org/images/icons/icon14.gif[/img]

.

---

### Post by BMWolf on 2004-11-27
First off this works so great and i'm loving Ubuntu! I wish i could use Ubuntu for everything. 

Unfortunately, when i reboot the script does not work. I can see something about an "error code 1" as it boots up but, i don't know how to freeze the screen during boot or where the boot log(if any) is located, to get a better look. It's not too hard to use the shell to get it back up but, i would prefer to do this at boot. Any suggestions?

ps. I'm new to linux.

all my info:
```
cat /etc/rc.boot/logitech-mouse
#! /bin/sh
echo "Tunning Logitech mouse..."
lmctl -8 --no-sms
```
```
~ $ sudo /etc/rc.boot/logitech-mouse
cat /etc/rc.boot/logitech-mouse
#! /bin/sh
echo "Tunning Logitech mouse..."
lmctl -8 --no-sms
Tunning Logitech mouse...
001.003: 046d:c01d MX510 Performance Optical Mouse (M-BS81A) Caps: RES SMS
        Resolution set to 800 cpi
        SmartScroll disabled
```
```
~ $ ls -l /etc/rc.boot
total 4
-rwxr--r--    1 root     root           94 2004-11-27 19:25 logitech-mouse
```
```
~ $ sudo lmctl -i
001.003: 046d:c01d MX510 Performance Optical Mouse (M-BS81A) Caps: RES SMS
        Resolution (RES): 800 cpi
        SmartScroll (SMS): off
```
```
~ $ sudo lmctl -s
005.004: 04b8:0007 Not a Logitech device
005.001: 0000:0000 Not a Logitech device
004.001: 0000:0000 Not a Logitech device
003.003: 04fa:2490 Not a Logitech device
003.001: 0000:0000 Not a Logitech device
002.004: 04b8:0005 Not a Logitech device
002.001: 0000:0000 Not a Logitech device
001.003: 046d:c01d MX510 Performance Optical Mouse (M-BS81A) Caps: RES SMS
001.001: 0000:0000 Not a Logitech device
```

---

### Post by wallijonn on 2004-11-28
Why did you include lmctl -8 _[COLOR=DarkRed]--no-sms[/COLOR]_?

[COLOR=Green]Applications -> System Tools  -> Root Terminal[/COLOR]
```

#[COLOR=Red] sudo gedit logitech-mouse[/Color]

```
{copy / paste the following into the new window}
```

[color=red]
#!/bin/sh
echo "Tuning Logitech mouse..."
lmctl -8 --sms[/COLOR]

```
{exit /save}
```

# [COLOR=Red]sudo chmod u+x logitech-mouse[/COLOR]
# [COLOR=Red]sudo mkdir /etc/rc.boot[/COLOR]
# [COLOR=Red]sudo cp logitech-mouse /etc/rc.boot[/COLOR]
# [COLOR=Red]exit[/COLOR]

```
{reboot}

The only thing I can think of is that when you created the logitech-mouse shell script you did not include the # in the first line. 

.

---

### Post by p!=f on 2004-11-28
[QUOTE=BMWolf]
```
cat /etc/rc.boot/logitech-mouse
#! /bin/sh
echo "Tunning Logitech mouse..."
lmctl -8 --no-sms
```
[/QUOTE]
#! /bin/sh = wrong syntax. Should be without spaces (#!/bin/sh).
Also you might want to use --sms parameter to benefit of the SmartScroll/Control.

---

### Post by BMWolf on 2004-11-28
Hey guys, thanks for the replies! 

I had put a space between the "#!" and "/bin/sh awhile back to see if it would work. i wasn't familiar with shell scripts and when i did a seach someone had pasted "#! /bin/sh", so I thought I'd give it a try. Needless to say, I forgot to change it back. I had put no-sms into the script because I never use those buttons. I was going to map them to something else, like open a terminal or firefox. I know they don't work by default but I thought i'd include it anyway. 

I did figure it out though. I had to remove the "cat /etc/rc.boot/logitech-mouse". I assume it's only use was to print the text within "logitech-mouse" to the screen at boot. so now everything works.

Thanks a bunch guys! now if i can just get cd burning to work i'll be set. ;)

---

### Post by x03 on 2004-11-30
MX500 mouse here, this is all I get  :confused: 

003.001: 0000:0000 Not a Logitech device
002.001: 0000:0000 Not a Logitech device
001.003: 03f0:3c02 Not a Logitech device
001.001: 0000:0000 Not a Logitech device

---

### Post by p!=f on 2004-11-30
[QUOTE=x03]MX500 mouse here, this is all I get  :confused: 

003.001: 0000:0000 Not a Logitech device
002.001: 0000:0000 Not a Logitech device
001.003: 03f0:3c02 Not a Logitech device
001.001: 0000:0000 Not a Logitech device[/QUOTE]
> 
001.003: 03f0:3c02 Not a Logitech device

HP printer connected in that port? 
Is your mouse connected to PS/2 port?

Logitech devices starts with 046d...
```

[~] > lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

```

---

### Post by wallijonn on 2004-11-30
[SIZE=3][QUOTE=BMWolf] I had to remove the "cat /etc/rc.boot/logitech-mouse".[/QUOTE]

That's why I put my code up, so that people can just copy / paste. Yeah, it threw me the first time I saw the original code. Glad you got it going. Yeah, I cleaned mine up, just in case... Someone is bound to ask me whether they should include the "#" in the script files... which is why I use multi-colours. 

btw, p!=f did a great job. I appreciated his write-up on how to set it up so that it runs at boot-up time as much as the script itself. 

.
[/SIZE]

---

### Post by x03 on 2004-11-30
[QUOTE=p!=f]HP printer connected in that port? 
Is your mouse connected to PS/2 port?

Logitech devices starts with 046d...
```

[~] > lsusb
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 046d:c00e Logitech, Inc. Optical Mouse
Bus 001 Device 001: ID 0000:0000

```[/QUOTE]

EDIT: I just forgot to hook it into USB :( haha, it was hooked up to the little converter thing that came with it to connect to PS/2.

002.003: 046d:c025 MX500 Optical Mouse (M-BP81A) Caps: RES SMS
        Resolution set to 800 cpi
        SmartScroll enabled

Thanks for the HOWTO's guys!! All of these really help out people that are new to linux.

---

### Post by p!=f on 2004-11-30
[QUOTE=wallijonn][SIZE=3]
btw, p!=f did a great job. I appreciated his write-up on how to set it up so that it runs at boot-up time as much as the script itself. 
[/SIZE][/QUOTE]
Thank you. Glad to read that. :)

---

### Post by p!=f on 2004-11-30
Please reread the first post again. I made some changes you may find useful.

---

### Post by BMWolf on 2004-12-03
p!=f thanks for the great write-up! The udev way seems to be the best solution yet.

i have a problem though. Everything is working just fine but when i reboot it fogets. once logged in i can unplug my mouse and then plug it back in and everything is back to normal(800dpi). am i supposed to also use the boot script method as well? i'm using the version that supports the 510. any help you guys can provide would be great. i assume it has something to do with permissions, but i have no idea what needs changed.

---

### Post by p!=f on 2004-12-04
[QUOTE=BMWolf]p!=f thanks for the great write-up! The udev way seems to be the best solution yet.
[/quote]
Thanks

[QUOTE=BMWolf]
i have a problem though. Everything is working just fine but when i reboot it fogets. once logged in i can unplug my mouse and then plug it back in and everything is back to normal(800dpi). am i supposed to also use the boot script method as well? i'm using the version that supports the 510. any help you guys can provide would be great. i assume it has something to do with permissions, but i have no idea what needs changed.[/QUOTE]
Looks like a bug or something in udev. When you restart udev ```
 sudo /etc/init.d/udev restart

```
after the boot it will work...

---

### Post by wallijonn on 2004-12-31
How do you check the settings in /udev? (Other than just typing them out)

---

### Post by Buffalo Soldier on 2005-01-31
[QUOTE=p!=f][LMCtl]("http://www.bedroomlan.org/%7Ealexios/coding_lmctl.html")[/quote]
anyone else having problem accessing that URL?

---

### Post by p!=f on 2005-01-31
[QUOTE=Buffalo Soldier]anyone else having problem accessing that URL?[/QUOTE]
Me. :) I'll rewrite this HOWTO to use logitech_applet instead.
LMCTL is still available at [http://freshmeat.net/projects/lmctl/](http://freshmeat.net/projects/lmctl/) just in case.

---

### Post by gizero on 2005-02-19
I just noticed something weird: the lmctl package that is attached to the initial post in this thread detects my MX310 mouse correctly, but if I download the same version (0.3.2) from the official homepage it tells me I have an unknown or unsupported Logitech device. An md5sum on the two .deb packages (after uncompressing the attached .deb.gz file of couse) showed that they're not the same. So where did you get the attached Debian package, and why is it working better than the original?:-)

---

### Post by p!=f on 2005-02-19
[QUOTE=gizero]I just noticed something weird: the lmctl package that is attached to the initial post in this thread detects my MX310 mouse correctly, but if I download the same version (0.3.2) from the official homepage it tells me I have an unknown or unsupported Logitech device. An md5sum on the two .deb packages (after uncompressing the attached .deb.gz file of couse) showed that they're not the same. So where did you get the attached Debian package, and why is it working better than the original?:-)[/QUOTE]

I added support for MX310 and MX510 mice into the code and recompiled. ;)

---

### Post by jubei on 2005-04-22
Originally Posted by BMWolf
i have a problem though. Everything is working just fine but when i reboot it fogets. once logged in i can unplug my mouse and then plug it back in and everything is back to normal(800dpi). am i supposed to also use the boot script method as well? i'm using the version that supports the 510. any help you guys can provide would be great. i assume it has something to do with permissions, but i have no idea what needs changed.

[QUOTE=p!=f]Thanks


Looks like a bug or something in udev. When you restart udev ```
 sudo /etc/init.d/udev restart

```
after the boot it will work...[/QUOTE]

I still cant get my mouse to go 800cpi on startup. I have to unpug it and plug it back in to get it to work.

Can anyone help?

---

### Post by jubei on 2005-04-28
[QUOTE=jubei]Originally Posted by BMWolf
i have a problem though. Everything is working just fine but when i reboot it fogets. once logged in i can unplug my mouse and then plug it back in and everything is back to normal(800dpi). am i supposed to also use the boot script method as well? i'm using the version that supports the 510. any help you guys can provide would be great. i assume it has something to do with permissions, but i have no idea what needs changed.



I still cant get my mouse to go 800cpi on startup. I have to unpug it and plug it back in to get it to work.

Can anyone help?[/QUOTE]

OK to answer my own question. I found a much easier way to enable 800 cpi mouse in kde that might work for you too.

open a terminal, eg konsole and enter the command
sudo kcontrol
click peripherals
click mouse
click the tab at the end labeled "your mouse name" (eg mine says MX300 Optical Mouse)
under the Sensor Resolution panel select 800 counts per inch
apply the changes, my resolution was changed immediately

Jubei

---

### Post by Caboto on 2005-07-17
Sorry for bumping up old threads, but i found this how-to via searching and tried it immediately. Worked fine indeed, until it comes to a reboot. I've used the udev methode and plugging the mouse out and in again, sets her to 800dpi. Not quite sure what i've done wrong...

Even with the suggested 
```
sudo /etc/init.d/udev restart
```
there's no better result. Still at 400dpi after rebooting. 
I've tried to mixed the script and udev way. So i've mkdir rc.boot in /etc/ and put logitech-mice.rules in it (changed the owner, too). Put even that don't get me the wanted effect... After startup it's still at 400dpi. :(

Any more suggestions? I don't know anything else to do :/


PS: I'm using Gnome (on Hoary), so there's no resolution setting like in KDE (see one post above).

---

### Post by Chris on 2005-07-18
The MX518 does not appear to be recognized.

001.005: 046d:c01e Unknown or Unsupported Logitech device.

Can lmctl be patched to support the 1600 DPI of the MX518?

---

### Post by Chris on 2005-07-18
I found a set of SuSE patches that seem to work.   I had to apply them by hand since the patch wouldn't apply for some reason (probably slightly different source base).  It's easy though because the changes are simple.

[http://projects.cynapses.org/SuSE/DIFFS/](http://projects.cynapses.org/SuSE/DIFFS/)

001.005: 046d:c01e MX518 Optical Mouse (M-BS81A) Caps: RES
        Resolution (RES): 1600 cpi

---

### Post by sirro on 2005-07-19
im running ubuntu x64
i get this
package architecture (i386) does not match system (amd64)

i want this working bad plz help i searched around and looks like suSE is the only one with a lmctl.*.*.*64bit.rpm........can i install rpm stuff???? i dont think so but if there is a way of converting one to the other....probably fundamentally different huh... ](*,)

---

### Post by Caboto on 2005-07-19
There's an entry in the unofficial Ubuntu Starter guide right [here](http://ubuntuguide.org/#convertrpmtodebfiles). So, I'm not quite sure, if there could be any problem...

---

### Post by sirro on 2005-07-19
no im an idiot...you ./configure and make and its working in 64.

RATHER THAN DOUBLE POST!

i figured how to use the dpkg thats attached to this how to but it still sez that its c01d unknown or unsupported logitec device....i know youve added support for 510 in your attached pkg but it still gives c01ld unknown or unsupported logitech device.....................btw i need this for my aim. ut in windows im at 40-50% accuracy linux im lucky to get 14-17%

---

### Post by citizenr on 2006-07-18
s there something similar for MS mouses? intellimouse for examlple?

---

### Post by Dazza on 2006-07-19
Can anyone help me with this? I am stuck with an Mx510 and have no idea how to get it working, I have no idea what applet to download or how to use the tar.gz files.

Thanks.

---


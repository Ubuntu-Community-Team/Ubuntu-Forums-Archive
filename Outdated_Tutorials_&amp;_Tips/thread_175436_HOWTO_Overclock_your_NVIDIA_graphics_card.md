---
title: "HOWTO: Overclock your NVIDIA graphics card"
date: 2006-05-13
forum: Outdated Tutorials &amp; Tips
---

### Post by Carrots171 on 2006-05-13
Disclaimer: Overclocking may shorten the life of your graphics card, damage/destroy your graphics card, or void the warranty of your graphics card. I am not responsible if your card [explodes]("http://video.google.com/videoplay?docid=5393904704265757054") or is otherwise damaged. Use this HOWTO at your own risk. 

1. Enable Coolbits. You don't need Coolbits to overclock but in my experience it does help. You must have at least the 7664 drivers for this to work. There's a guide on enabling Coolbits here:
```
http://www.phoronix.com/scan.php?page=article&item=197&num=1
```

2. Download Nvclock. Don't download the one from Universe; it's outdated. Instead, download the source from the Nvclock website:
```
http://www.linuxhardware.org/nvclock/#download
```

3. Extract Nvclock 
```

cd [path to where you downloaded the file]
tar -xzvf nvclock0.8b2.tar.gz
cd nvclock0.8b2

```

4. Compile Nvclock
```

./configure
make
sudo make install

```

5. Running Nvclock and overclocking
You can run the Nvclock interface using the command:
```

nvclock_gtk

```
Or this command if you are using Kubuntu: (I haven't tested this)
```

nvclock_qt

```
When Nvclock starts up, click on "overclocking", choose "2D+3D Clocks" from the drop-down menu, and start overclocking. Be sure to keep "Test speeds before applying" ticked. I would suggest bumping both the core clock and the memory clock up slowly and playing some of your 3D games to test for stability and artifacts. If your card has a temperature sensor, you can keep an eye on your card's temperature by clicking on "hardware monitoring" in Nvclock.

You can overclock your card through the console, too. In fact, overclocking through the console allowed me to reach higher clock speeds because the graphical interface doesn't let you go too high. Use the command to view information about your card:
```

nvclock -i

```
And this command to overclock: 
```

nvclock -n [new core mhz] -m [new memory mhz] -f 

```
You only need "-f" if the clock speeds you're setting are above a certain amount. 

The clock frequencies will reset back to the original values when you restart your computer, so every time you restart/turn your computer on, you'll have to overclock. Of course, you can create a startup script or something to overclock for you when your computer boots up, but I don't recommend it because overclocking may cause your system to hang and you might get stuck with a computer that always crashes on startup. ](*,) 

Have fun! (And don't blow up your graphics card!)

---

### Post by HydroDiOxide on 2006-07-07
Is it possible to run nvclock at startup so that it adjusts my fanspeeds automatically?

---

### Post by Pausanias on 2006-07-07
Note that CoolBits is disabled by NVIDIA corporation for mobile GPUs. And nvclock is not able to set the clock speed on many GPUs, like mine (Quadro FX Go1400).

---

### Post by Carrots171 on 2006-07-08
> **HydroDiOxide said:**
> Is it possible to run nvclock at startup so that it adjusts my fanspeeds automatically?

Yes it is.

---

### Post by mrazster on 2006-07-08
Forget this post...

---

### Post by HydroDiOxide on 2006-07-09
So, how would I do this?

---

### Post by PingunZ on 2006-07-09
nice guide but I'm not gonna follow it cause I don't game on Ubuntu ( cs is the only reason for dual boot ) Is there any tool to overclock your cpu ( amd 64 ) or change your fanspeed ?

Keep up the good work man :)

Grtz PingunZ

---

### Post by yetanothersteve on 2006-08-20
There is no need to use a third party application to overclock your NVIDIA graphics card, nvidia provides the tools and you just have to activate them.

To activate the Overclock menu in the nvidia-settings panel, change your /etc/X11/xorg.conf to add in support for the Coolbits "Option" of "1". Back up xorg.conf first of course.
```
Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option  "Coolbits"      "1"
EndSection
```
Then restart X (ctrl-alt-backspace or for a cleaner experience log off and then ctrl-alt-backspace)

Then run nvidia-settings and note the new clock frequencies menu item. Select it and do an auto-detect of your 3D Clock Frequencies. Write down the returned values, you can apply them but they will not stick past this X-Session. No need to run in overclock mode while reading these forums, eh?

[screen shot of nvidia-settings with overclock enabled]("http://coding.home.comcast.net/ScreenshotNVIDIAXServerSettings.png")

Next, alter or create a startup script for your game or other application that you would like to run while overclocking the card. Here is my example for launching doom3.

```
#!/bin/sh
# Needed to make symlinks/shortcuts work.
# the binaries must run with correct working directory

# Steve added, overclock values from 
nvidia-settings --assign="GPU3DClockFreqs=381,861"
# End Steve added

cd "/home/ouz/games/doom3/"
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:.
#exec ./doom.x86 "$@"   # the exec means stop executing this and execute something new, but we want the nvidia-settings to run again after doom, so drop the exec
./doom.x86 "$@"

# Steve added, return to normal clocks after game
nvidia-settings --assign="GPU3DClockFreqs=300,700"
# End Steve added
```

Or you could just run the ```
nvidia-settings --assign="GPU3DClockFreqs=381,861"
``` from a command line before the game and ```
nvidia-settings --assign="GPU3DClockFreqs=300,700"
``` after the game.

**Big Note: The frequencies listed were for my GeForce6800XT. You really should Auto Detect appropriate values for your own card.**

If for some reason you feel the need to overclock 2D the command line for that is ```
nvidia-settings --assign="GPU2DClockFreqs=300,700"
```  Keep in mind that the last assignment for memory speed, either 2D or 3D, will apply it to both 2D and 3D as there cannot be separate memory speeds.

To see all of your nvidia attributes, the command line for that is ```
nvidia-settings -query all
```

---

### Post by fatsheep on 2006-09-05
I'm using Coolbits to overclock my XFX 6600 GT and it works great except for one detail:

Everytime I restart, my overclock is erased and I have to reset it!  Is there any way to get around this?

---

### Post by ~LoKe on 2006-09-06
I'm not really sure what numbers to be changing, and I don't think it would be a good idea to start guessing.  Here is my nvclock -i output:

> loke@x04d:~$ nvclock -i
-- General info --
Card:           nVidia Geforce 4 MX420
Architecture:   NV17 A5
PCI id:         0x172
GPU clock:      333.000 MHz
Bustype:        AGP

-- Memory info --
Amount:         64 MB
Type:           128 bit DDR
Clock:          333.000 MHz

-- AGP info --
Status:         Enabled
Rate:           4X
AGP rates:      1X 2X 4X 
Fast Writes:    Disabled
SBA:            Unsupported

-- VideoBios information --
Version: 04.17.00.45
Signon message: NV17 P73 Engineering VBIOS

Any suggestions for safe settings?

---

### Post by vasaka on 2006-09-06
and how can i unlock pipelines? I now for shure that two of locked pipes on my 6800LE are working.

---

### Post by glotz on 2006-09-06
Captain obvious to the rescue! Plz? ](*,) > ~/nvclock0.8b2$ ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.


I have quite virginal dapper install and it *seems to me* that I have gcc-3.3-base and gcc-4.0-base installed. :-k

**EDIT:** Oh kay, now I'm feeling silly: sudo aptitude install build-essential gcc helped...

But now I've got a fresh new problem for you guys: ./configure: no x!> 
[...]

checking for gtk+-2.0 >= 2.4.0... checking for X... no
configure: no X Window System found

[...]

NVClock build summary:
----------------------
- Commandline version enabled
- NV-CONROL support disabled
- GTK2 GUI disabled
- QT GUI disabled

Now wtf does that mean? (lol, I *know* I've got X!! :lol:)

---

### Post by HAARP on 2006-09-06
```
NVClock build summary:
----------------------
- Commandline version enabled
- NV-CONTROL support enabled
- GTK2 GUI disabled
- QT GUI disabled

```

To enable gtk2 GUI support, get libgtk2.0-dev from the repos.

---

### Post by glotz on 2006-09-06
Schweet baby Jesus! It works! Thanks a gzillion! :mrgreen:

---

### Post by ~LoKe on 2006-09-06
> **HAARP said:**
> ```
NVClock build summary:
----------------------
- Commandline version enabled
- NV-CONTROL support enabled
- GTK2 GUI disabled
- QT GUI disabled

```

To enable gtk2 GUI support, get libgtk2.0-dev from the repos.

libgtk2.0-dev:
 Depends: libpango1.0-dev but it is not going to be installed
 Depends: libcairo2-dev but it is not going to be installed

:(

---

### Post by Carrots171 on 2006-09-22
> **vasaka said:**
> and how can i unlock pipelines? I now for shure that two of locked pipes on my 6800LE are working.

I've unlocked eight pipelines on my 6800XT. First press CTRL+ALT+F1. 

If you're using Ubuntu, follow these instructions (use at your own risk; it worked for me):

```
sudo /etc/init.d/gdm stop
``` to stop X. 
```
sudo rmmod nvidia
``` to remove the Nvidia module.
```
sudo nvclock -P 1111 -f
``` to unlock all the piplelines.
```
sudo nvclock -V 111111 -f
``` to unlock the vertex units.
```
sudo modprobe nvidia
``` to load the Nvidia module back up
```
sudo gdm
```to start X.

If you're using Kubuntu, use 
```
sudo /etc/init.d/kdm stop
``` to stop X
and ```
sudo kdm
``` to start it. (I haven't tested this because I don't use Kubuntu).

After you reboot the piplelines will become locked again. You can set up your system to run these commands at startup but I'm not sure how. (If anyone knows, please post).

---

### Post by HAARP on 2006-09-23
I've uploaded a deb-archive with the newest version so you don't need to compile anymore.
It's the command line version + the GTK version.

---

### Post by spockrock on 2006-09-23
BTW I do not think this works under XGL, ummm it might work with the latest nvidia beta drivers, with aiglx, but I think anyone trying to boost their XGL performance is out of luck.

---

### Post by fatsheep on 2006-09-23
Earlier in this topic I asked if there was a way to apply overclocking settings automatically at bootup.  Since then, I have found a way and have made a guide:

[http://www.ubuntuforums.org/showthread.php?t=254397](http://www.ubuntuforums.org/showthread.php?t=254397)

Section 3, part 2 (end of the first post) covers that.

---

### Post by BitTorrentBuddha on 2006-10-22
This doesn't seem to work with the 9625 driver with integrated Aiglx. My nvidia-settings doesn't even have the overclocking section and whenever I try to move the slider on nvclock_gtk it slides back down before prompting me to keep the settings and when I try and use the terminal options I get:```
$ nvclock -n 380 -m 680
Requested memory clock:         680.000 MHz
Requested core clock:           380.000 MHz

Adjusted Coolbits 3D clocks on a nVidia Geforce 6200
Memory clock:   658.000 MHz
GPU clock:      351.000 MHz
```
The device section of my xorg.conf looks like such:```
Section "Device"
    Identifier     "NVIDIA Corporation NV40? [Unknown nVidia Card]"
    Driver         "nvidia"
    Option "Coolbits"  "1"
EndSection
```

---

### Post by ~LoKe on 2006-10-22
Ubuntu can't seem to identify my card.  It's an XFX nVidia 7300GT.  Anything I can do to get it to detect it?  It's working just fine and all, but it's not displaying the name and all that.

---

### Post by fatsheep on 2006-10-22
> **~LoKe said:**
> Ubuntu can't seem to identify my card.  It's an XFX nVidia 7300GT.  Anything I can do to get it to detect it?  It's working just fine and all, but it's not displaying the name and all that.

If it's working good then I wouldn't worry about it...

---

### Post by ~LoKe on 2006-10-22
> **fatsheep said:**
> If it's working good then I wouldn't worry about it...

Yeah, it's not a problem, would just like it to identify properly.

---

### Post by BitTorrentBuddha on 2006-12-29
Has there been any solution to my problem of not being able to change settings, I just gave this another try because I'm starting to do games on Ubuntu, however I am still unable to change the gpu or memory clock, it simply goes back to the default when I press "change speeds." Using the CLI, I am unable also unable to change speeds, I even tried underclocking to see if that worked. ```
$ nvclock -n 380 -m 680
Requested memory clock:         680.000 MHz
Requested core clock:           380.000 MHz

Adjusted Coolbits 3D clocks on a nVidia Geforce 6200
Memory clock:   658.000 MHz
GPU clock:      351.000 MHz

$ nvclock -n 350 -m 657
Requested memory clock:         657.000 MHz
Requested core clock:           350.000 MHz

Adjusted Coolbits 3D clocks on a nVidia Geforce 6200
Memory clock:   658.000 MHz
GPU clock:      351.000 MHz
```
Any help? The manufacturer is PNY if that is of any concern, the card is a GeForce 6200 with 128mb and AGP interface.

---

### Post by ahaslam on 2007-03-12
> **Carrots171 said:**
> You only need "-f" if the clock speeds you're setting are above a certain amount.

Can a similar thing be done with *nvidia-settings --assign*, or will I need nvclock to achieve 650,800 ?

Tony ;)

---

### Post by ahaslam on 2007-03-14
NVclock SVN it is ;)

[SIZE="1"](0.8 doesn't support the 7950gt)[/SIZE]

---

### Post by ahaslam on 2007-03-16
Even nvcolck wont allow me to clock to 650,800 (even via the lowlevel backend) :(
I have an aftermarket cooler & it's easily capable of this, anyone got any ideas? 

Tony.

---

### Post by Chriis on 2008-04-11
Sorry,Can i?

I've installed Nvclock 0.8b2 but it doesnt reconise my VC 
it's a 8800gts 512

btw i'm on 64bits 

any ideas, is it normal?


Thanks

---

### Post by ahaslam on 2008-04-11
I'm now using the same card. I just use the nvidia-settings frequency adjustments. You'll just need to enable coolbits within your xorg.conf.

---

### Post by nebu on 2008-04-12
isnt overclocking a gfx card dangerous....

if i overdo the settings... can i end up frying my gfx card???

---

### Post by ahaslam on 2008-04-13
> **nebu said:**
> isnt overclocking a gfx card dangerous....

if i overdo the settings... can i end up frying my gfx card???

It's only risky if you push the voltage too high. If you don't do any hardware mods it'll be fine. The worst that'll happen is a system freeze, that's basically telling you there's not enough current for that clock.

---

### Post by Vadi on 2008-04-13
Still though, if you aren't sure, don't do it. Because then you'll only have yourself to blame.

---

### Post by SnakeHips on 2008-12-09
Thought i'd have a little dabble and see if I could tweak my video card ..... was quite surprised at the reply lol ........... scroll down


pete@desk:~$ nvclock -i
-- General info --
Card: 		nVidia Geforce 6200
Architecture: 	G4A A1
PCI id: 	0x221
GPU clock: 	351.000 MHz
Bustype: 	AGP

-- Pipeline info --
Pixel units: 2x2 (11b)
Vertex units: 3x1 (111b)
HW masked units: None
SW masked units: None

-- Memory info --
Amount: 	256 MB
Type: 		64 bit DDR
Clock: 		531.562 MHz

-- AGP info --
Status: 	Enabled
Rate: 		8X
AGP rates: 	4X 8X 
Fast Writes: 	Disabled
SBA: 		Enabled

-- Sensor info --
Sensor: GPU Internal Sensor
GPU temperature: 53C

-- VideoBios information --
Version: 05.44.a2.07.52
Signon message: PNY GeForce 6200 AGP

pete@desk:~$ nvclock -n 370 -m 600
Warning!
You entered a core speed of 370.000 MHz and NVClock believes 0.000 MHz is the maximum!
This error appears when the entered speed is 25% higher than the default speed.
If you really want to use this speed, use the option -f to force it.

---

### Post by vulturesrow on 2008-12-09
Maybe I skimmed over the answer, but how do you use nvclock to adjust your fan speed? 

BTW, I'll let you know why Im asking , because my problem might be symptopmatic of a deeper issue. Long story short, the fan on the card only runs during bootup. After I get past the GRUB menu, the fan doesnt come on. Id like to see if I can get it to run using nvclock (or any other utility) to help my overheatin woes (I play World of Warcraft on my Ubuntu partition). 

Thanks

---

### Post by ahaslam on 2008-12-10
If you don't mind sitting next to a wind tunnel:

```
nvclock -fF auto
```

---

### Post by mastergunner on 2009-05-10
Guys I know I am bringing up an old thread but I cant get nvclock to configure. Below is what I am getting. Need some help and I really appreciate it.

brad@brad-desktop:~/Desktop/nvclock0.8b4$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for library containing getopt_long... none required
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking getopt.h usability... yes
checking getopt.h presence... yes
checking for getopt.h... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+-2.0 >= 2.4.0... checking for x11... configure: error: "X11 required for nvcontrol support"
brad@brad-desktop:~/Desktop/nvclock0.8b4$ makw
bash: makw: command not found


I am running Kubuntu so why is it saying I do not have X11 support. Really strange.

---


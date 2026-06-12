---
title: "HOWTO: Enable DMA for a device"
date: 2005-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by de4th on 2005-05-01
If you have problem with cd/dvd's playback you have to enable DMA.
So open a console and type "sudo gedit /etc/hdparm.conf" (without "") and add these lines at the end of the file.

```
/dev/cdrom {
	dma = on
}
```

Where "/dev/cdrom" you can add your device. Then restart your pc (don't know if there's a script that does the same... ) and play again the dvd!

Have fun ;)

PS1. Sorry for my bad english
PS2. If you see smth wrong reply

---

### Post by mrbass on 2005-05-02
This is part of the script I wrote for ubuntu addon zip

```

echo "CD-ROM current DMA mode"
sudo hdparm -i /dev/cdrom | grep "PIO modes"
sudo hdparm -i /dev/cdrom | grep "DMA modes"
echo "DVD-ROM current DMA mode"
sudo hdparm -i /dev/dvd | grep "PIO modes"
sudo hdparm -i /dev/dvd | grep "DMA modes"
echo "* signifies the current active mode"
read -p "Turn on DMA for CD-ROM and/or DVD-ROM? [Y/n/q]"
if [ "--$REPLY" == "--q" -o "--$REPLY" == "--Q" ]; then exit 0; fi
if [ "--$REPLY" == "--y" -o "--$REPLY" == "--Y" -o "--$REPLY" == "--" ]; then
sudo hdparm -d1 /dev/cdrom
sudo hdparm -d1 /dev/dvd
echo "CD-ROM current DMA mode"
sudo hdparm -i /dev/cdrom | grep "PIO modes"
sudo hdparm -i /dev/cdrom | grep "DMA modes"
echo "DVD-ROM current DMA mode"
sudo hdparm -i /dev/dvd | grep "PIO modes"
sudo hdparm -i /dev/dvd | grep "DMA modes"
else
echo "Skipped"
fi

```

---

### Post by arcilite on 2005-05-02
Can the dma be enabled for my usb hard drive? Transfer speed seems pretty damn slow for me currently.

---

### Post by de4th on 2005-05-02
Maybe u have usb 1.1! Connect it to usb 2.0 and will go faster
:cool:

---

### Post by orlandu on 2005-06-09
The above advice didn't work for me to begin with - I got an error as follows:

setting using -dma to 1 (on)
HDIO set dma failed: operation not permitted
using dma = 0 (off)

This was eventually fixed (via some obscure googling) by removing all ide-* entries from modules (or modules.conf - I've done this in 2 different distributions) and rebooting. After that, hdparm could be used to set dma as normal.

I'm not sure exactly why this was needed, but at a guess it may have something to do with my only disk being SATA (my DVD drive is IDE primary master, /dev/hda).

Perhaps this will prove useful to others!

---

### Post by Firetech on 2005-06-09
Be a bit careful with enabling DMA on older CD-players, they can (and probably will) break, or just not work right.
Enabling DMA on my CD recorder (I would guess it's about 5 years old), seem to have been the reason that my computer got totally stuck twice... Last time it got stuck in BIOS while "Auto-detecting Secondary Master" (Which is the CD). This, AND some strange messages in the syslog about "ATAPI timeout" and "disabling DMA", makes me think DMA was a bad idea...
Think twice about the age of your CD player (I guess DVD playes aren't affected by this...) before enabling this.
There is a reason why there is an option in the kernel for not enabling DMA on CD-ROMs, and why the stock ubuntu kernel has this enabled.

---

### Post by kleeman on 2005-06-09
Don't forget this thread as well (Earned me brownie points  :-P )

[http://www.ubuntuforums.org/showthread.php?p=93238#post93238](http://www.ubuntuforums.org/showthread.php?p=93238#post93238)

---

### Post by bonifacio on 2005-06-09
I have a problem (don't know if it's really a problem) that I posted on this thread that I need answer...
[http://www.ubuntuforums.org/showthread.php?t=40582](http://www.ubuntuforums.org/showthread.php?t=40582)

Ok here's the text for those of you too lazy to click on the link:  :p 

> 

After setting dma on in hdparm.conf

At startup after "Setting disc parameters..."

/dev/hdc: No such file or directory

Why?

Other than that the device seems to work as normal 

Also I searched, scoured, irc'ed and googled but could not find any leads on how to enable DMA on a USB DVD burner.

---

### Post by darkaudit on 2005-06-09
I used the command line version at the end of hdparm.conf and got the same error for my DVD burner. *BUT* DMA was enabled as intended. When I commented the line out, DMA was not turned on at boot.

So what is happening here?

---

### Post by bonifacio on 2005-06-09
man says:
> hdparm  provides  a  command line interface to various hard disk ioctls supported by the stock Linux ATA/IDE  device  driver  subsystem.

So I interpret it as only applicable to such device but NOT(?) USB device?

---

### Post by Silvio Moioli on 2005-06-10
bonifacio: exactly.

---

### Post by royg1234 on 2005-06-24
I have a DVD+/-RW drive and a regular DVD drive.  How do I tell what paths these are in?  Through the file browser I see a:
[list]
[*]cdrom [this has a shortcut icon next to it]
[*]cdrw
[*]dvd
[*]dvd1
[*]dvdrw
[/list] 

These all have shortcut icons next ot them.  Is there something like "fdisk -l" that I can use?

---

### Post by skoal on 2005-06-24
If you recompile your kernel, if you have these kernel options set:

CONFIG_GENERIC_ISA_DMA=y
CONFIG_ISA_DMA_API=y
CONFIG_BLK_DEV_IDEDMA_PCI=y
# CONFIG_BLK_DEV_IDEDMA_FORCED is not set
CONFIG_IDEDMA_PCI_AUTO=y
# CONFIG_IDEDMA_ONLYDISK is not set
CONFIG_BLK_DEV_IDEDMA=y
# CONFIG_IDEDMA_IVB is not set
CONFIG_IDEDMA_AUTO=y

It will enable DMA on all your drives without the use of hdparm.  Of course, a lot of distros (like Ubuntu) don't enable this kernel option for a good reason.  Know your hardware...

* NOTE: I believe it's just the last 2 options which need to be set for this to occur.

\\//_

---

### Post by pacz on 2005-07-15
I tried adding the correct module for my board (piix) at the top of /etc/modules, but it caused my system to hang.  After scouring google hits and bugzilla, I found a solution.  Apparently you have to add the module to the top of /etc/modules, but you also have to add it to /etc/hotplug/blacklist, so that it doesn't start too soon.

I had tried doing all sorts of things with hdparm, but I had to do the above before hdparm would work.

However, it took a very long time for me to find that solution, so I'll post it big and bold here in case anybody else was having as much trouble as I was:

[B]last resort solution:
add the module (piix, via82cxxx, AMD74xxx, etc) to the top of _/etc/modules_, but you also have to add it to _/etc/hotplug/blacklist_[/B]

---

### Post by No6 on 2005-07-15
I've had this problem also. The quickest and easiest way I found to fix it was to rename the script in the /etc/rcS.d dir so it didn't run too soon. I renamed it S71hdparm. This ran the script after the CDs are available.

Simple yet effective.

HTH

---

### Post by greenwom on 2005-07-15
I've followed threads and enabled DMA for my dvd-drive, It plays the DVDs now but the video is choppy and breaks.  I haven't even tried to burn anything on that drive yet.  
Do I have to specify a speed setting for the drive somewhere?  
 :roll:

---

### Post by SKLP on 2005-07-15
thx

---

### Post by Stabicron on 2005-07-17
I have an interesting problem. I have a Plextor 708A DVD+/- RW/CD-RW combo drive. Doing the hdparm command *with cdrom* works. But adding the /dev/cdrom dma=on stuff in hparm.conf does not *it keeps saying device not found at boot*. I have also tried substituting cdrom with hdc, same thing happens. This is kind of annoying especially when i wish to burn a cd in linux, if dma is not enabled it burns like a snail. Anyone have an idea of what I should do? Have thought about wether its possible to make a script that runs on start with the hparm command, but since I have no idea how to do that *is still learning* I guess that will have to wait.

---

### Post by TheRockit on 2005-07-17
I am having a problem playing DVD's on a Panasonic DVDrom. The disc autoloads, puts an icon with the correct title name on my desktop, the player opens and then just sits there unresponsive. Eventually I will close the player and have to acknowledge and error saying it needs to be forced.

I added the suggested line to the end of my hdparm.conf (which by the way has a lot of text in it, I am assuming any line preceeded by a # is remarked out?) and restarted the unit but there is not change in my problem. Any advice on the steps to take? I am totally new at command line editing for devices and such- since about 1997 I have been stuck in the 'other' OS and would consider myself a newbie all over again concerning manual configurations! 

Thanks  :roll:

---

### Post by Mauleye on 2005-07-18
I did it ... had some problems already discussed here (had to add amd46-stuff to modules). But now I have another interesting problem: My DVD-Burner (Plextor PX716) just burns trash ... I don't know if this is because of the dma-activation but it's definitly possible.

Anyone have the same probs?

---

### Post by ounn on 2005-07-18
Hi there.

I also had many problems with dma. I use to saw dvds like slow motion.
After reading many howtos i stay with the idea that i had to load some modules at startup. I have tried many options sugested somewhere here in the forum and finaly managed a way to turn on dma  \\:D/ 

What i did:

load this and just this modules  (replace yours modules at /etc/modules with this ones):

```
amd74xx
lp
mousedev
psmouse
```

amd74xx is beacause i have a amd, if you have intel you probably need another module that i dont know.

than add this line at the bottom of /etc/hdparm.conf

```
/dev/dvd {
	dma = on
}
```


and its all. Just reboot and you can see and burn yours dvds.

About the error on boot about "/dev/dvd not found" i also have that "warning" but just ignore him.


ounn

---

### Post by frodon on 2005-07-31
[QUOTE=ounn]
What i did:

load this and just this modules  (replace yours modules at /etc/modules with this ones):

```
amd74xx
lp
mousedev
psmouse
```
[/QUOTE]
Wow it completly solve my problem  :-P 
 A big big big thank you !!!!!!  \\:D/

---

### Post by mstlyevil on 2005-08-27
[QUOTE=ounn]



load this and just this modules  (replace yours modules at /etc/modules with this ones):

```
amd74xx
lp
mousedev
psmouse
```

amd74xx is beacause i have a amd, if you have intel you probably need another module that i dont know


ounn[/QUOTE]

 You are my new God! I have been puzzled by this problem for a week. I just added that line to my modules file and bang! I could enable my dma on both my cd rw and dvd rom.  I worship the ground you walk on. Thanx.  \\:D/

---

### Post by arnieboy on 2005-10-21
[QUOTE=ounn]Hi there.

I also had many problems with dma. I use to saw dvds like slow motion.
After reading many howtos i stay with the idea that i had to load some modules at startup. I have tried many options sugested somewhere here in the forum and finaly managed a way to turn on dma  \\:D/ 

What i did:

load this and just this modules  (replace yours modules at /etc/modules with this ones):

```
amd74xx
lp
mousedev
psmouse
```

amd74xx is beacause i have a amd, if you have intel you probably need another module that i dont know.

than add this line at the bottom of /etc/hdparm.conf

```
/dev/dvd {
	dma = on
}
```


and its all. Just reboot and you can see and burn yours dvds.

About the error on boot about "/dev/dvd not found" i also have that "warning" but just ignore him.


ounn[/QUOTE]
is your system an AMD64? or a 32 bit AMD system?

---


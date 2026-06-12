---
title: "HOWTO: Run DVD Decrypter with Wine for backing up DVDs"
date: 2005-04-15
forum: Outdated Tutorials &amp; Tips
---

### Post by shakin on 2005-04-15
This how-to is pretty long because it also walks you through changing your dvd drive's setup to work with Wine and installing and configuring wine itself. Even if you don't want DVD Decrypter but are having Wine configuration problems or want to install Internet Explorer and Windows Media Player, this how-to will help you get it working (delete your ~/.wine directory before starting if you want to follow the Wine config in this how-to because yours isn't working).


SECTION 1: Configure your DVD-RW or DVDROM drive.


First, we setup your DVD-RW drive (or DVDROM if you just want to decrypt DVDs and not burn them) so it will be recognized in Wine. If someone knows a downside to making it run in scsi emulation mode, please tell me so I can add a warning about it.

1. Run:
```

$ cat /etc/fstab

```
And find your dvd-rw drive's device in the output. Eg: hdd

An example might be: /dev/hdd /media/cdrom1 udf,iso9660 ro,user,noauto  0 0
where your DVD-RW/DVDROM is mounted on /media/cdrom1.

2. Edit the kernel boot paramaters (make a backup first):
```

$ sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

$ sudo gedit /boot/grub/menu.lst

```
Add 'hdx=ide-scsi' to the end of your kernel line, where 'x' is your dvd-rw drive's device. The correct line is probably the first kernel line (example below) that is not commented with a '#' in front.

Example kernel line including 'hdd=ide-scsi':
```

kernel          /boot/vmlinuz-2.6.10-5-k7 root=/dev/hdb1 ro quiet splash hdd=ide-scsi

```
Do not just copy my example because it probably won't work for your computer. Just edit yours, which will be similar. The recovery mode grub boot option will let you go to the console and restore your menu.lst file if this change prevents your computer from booting.

3. Add the ide-scsi module to the module list that your kernel loads, otherwise your kernel will not know how to read from the drive anymore.
```

$ sudo gedit /etc/modules

```

Add the module 'ide-scsi' to the bottom of the list. Example completed /etc/modules file below:

```

ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse
sbp2
sr_mod
ide-scsi

```

4. Reboot your computer so the ide-scsi settings take effect. After it reboots you should be able to mount CDs and DVDs. Check to make sure you can mount them so we know it's working.


SECTION 2: Install and configure Wine.


Now let's install and configure Wine. If you have Wine already running, skip to the next section where we install DVD Decrypter.

1. Open your apt-get sources file:

```

$ sudo gedit /etc/apt/sources.list

```
Add this line to the end of the file: deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

That will give you the repository for the latest version of Wine and related tools.

2. Install Wine and the configuration utility:
```

$ sudo apt-get update

$ sudo apt-get install winetools

```
Installing winetools will get you Wine and libwine. We will use winetools to configure Wine.

3. Configure Wine:
```

$ winetools

```
Go through the winetools GUI config. It will help you install various necessary bits to make Wine work better. You do not need to complete the IE 6 installation unless you want IE and Windows Media Player. You can also skip the Arial and other font installations because they're broken anyway (bad download location). Hopefully winetools is self-explanatory so I will not go into more details. When it's done, continue with this how-to. Even if winetools gives you some errors, just keep going with as much as possible.


SECTION 3: Installing DVD Decrypter


1. Go to the [DVD Decrypter](http://www.dvddecrypter.com/index.php?act=download) web site and download the latest version. Continue below after cd-ing to your download directory.

2. Run the DVD Decrypter setup (filename will change if you have a newer version of DVD Decrypter):
```

wine SetupDVDDecrypter_3.5.4.0.exe

```
Go through the DVD Decrypter setup wizard. Accepting the defaults is fine.

3. Run DVD Decrypter:
```

$ wine ~/.wine/fake_windows/Program\ Files/DVD\ Decrypter/DVDDecrypter.exe

```

In the Source dropdown box within DVD Decrypter you should see your DVD-RW/DVDROM selected. If not, return to section 1 and make sure you have scsi emulation working correctly. 

To make running DVD Decrypter easier, add it to your Gnome menu using the [menu editor](http://ubuntuforums.org/forumdisplay.php?f=67).

---

### Post by alphazero on 2005-04-15
Thanks for this mate! I've been tinkering with Wine/Dvd Decrypter for a while but never got it to pick up the DVD drive until now.

---

### Post by kagou on 2005-04-16
Why not use free tools like dvdrip ? dvdrip work like a charm

---

### Post by jonny on 2005-04-16
Yeah, I'll vouch for dvdrip.  It's in the marillat repositories (see the ubuntu guide for advice on adding these repositories) so you can install it with a few mouse clicks.  It works perfectly out of the tin.

But I've never used DVD Decrypter - perhaps it has loads of extra features or a really good user interface?

---

### Post by shakin on 2005-04-16
[QUOTE=jonny]Yeah, I'll vouch for dvdrip.  It's in the marillat repositories (see the ubuntu guide for advice on adding these repositories) so you can install it with a few mouse clicks.  It works perfectly out of the tin.

But I've never used DVD Decrypter - perhaps it has loads of extra features or a really good user interface?[/QUOTE]

It has a great interface and provides a good feature set. There were a lot of people not able to install dvdrip because apt couldn't find transcode (see [this thread](http://ubuntuforums.org/showthread.php?t=27269) for a solution). I started writing this how-to before that thread was started.

Besides, a lot of people used to using DVD Decrypter on Windows will like being able to use it on Linux. I'm also not sure, does dvdrip support burning .img files?

---

### Post by MetalMusicAddict on 2005-04-16
This is a great HOW TO. I use DVD Decrypter in windows and it is the best ripper. IMHO :) Thanx. Now if I could only get Audiograbber to see the CD-ROM in wine. :)

---

### Post by shakin on 2005-04-16
[QUOTE=MetalMusicAddict]Now if I could only get Audiograbber to see the CD-ROM in wine. :)[/QUOTE]

Use the same steps for your CDROM as you did for your DVD-RW to make it run with scsi emulation. You won't need to edit /etc/modules again, so just add something like 'hdc=ide-scsi' in your menu.lst file like you did for the DVD-RW device.

---

### Post by bored2k on 2005-04-16
[QUOTE=jonny]Yeah, I'll vouch for dvdrip.  It's in the marillat repositories (see the ubuntu guide for advice on adding these repositories) so you can install it with a few mouse clicks.  It works perfectly out of the tin.

But I've never used DVD Decrypter - perhaps it has loads of extra features or a really good user interface?[/QUOTE]
 Thoggen has just about any features dvd decrypter has. Dont get me wrong, decryp is mighty powerful, maybe a little bit too powerful for Windows users ;) *LOL*. But try this linux native:
[http://thoggen.net/screenshots/](http://thoggen.net/screenshots/)

[[IMG]http://img88.echo.cx/img88/9841/progressdialog8nz.th.jpg[/IMG]](http://img88.echo.cx/my.php?image=progressdialog8nz.jpg)

[center][size=2]Remember kids, We're doing legal *backups* here![/size][/center]

---

### Post by MetalMusicAddict on 2005-04-16
I got Audiograbber to see the CD-ROM! :) But I get a ASPI error. :( Any Ideas? I got DVD Decrypter workin fine. I wish Thoggen was in the repo. It looks nice. ;)

---

### Post by bored2k on 2005-04-16
[QUOTE=MetalMusicAddict]I got Audiograbber to see the CD-ROM! :) But I get a ASPI error. :( Any Ideas? I got DVD Decrypter workin fine. I wish Thoggen was in the repo. It looks nice. ;)[/QUOTE]
 Thoggen:
[http://prdownloads.sourceforge.net/thoggen/thoggen_0.3_i386.deb?download](http://prdownloads.sourceforge.net/thoggen/thoggen_0.3_i386.deb?download)

Then
sudo dpkg-i thoggen_0.3_i386.deb

And whats wrong with linux native audio rippers anyway?

---

### Post by MetalMusicAddict on 2005-04-16
[QUOTE=bored2k]And whats wrong with linux native audio rippers anyway?[/QUOTE]

None of them give me the same control as Audiograbber or EAC.

---

### Post by shakin on 2005-04-16
[QUOTE=MetalMusicAddict]I got Audiograbber to see the CD-ROM! :) But I get a ASPI error. :( Any Ideas? I got DVD Decrypter workin fine. I wish Thoggen was in the repo. It looks nice. ;)[/QUOTE]

Maybe you can try installing the ASPI layer under Wine. I've never tried it. Try [these ones](http://www.download.com/Adaptec-ASPI-Drivers-Windows-98-Me-NT-2000-XP-/3000-2098_4-10219041.html). I found them with Google so I don't know if they'll work.

---

### Post by MetalMusicAddict on 2005-04-17
So it looks like in the end this was a trade off. I got DVD Decrypter and Audiograbber workin but it screws up how the drive gets mounted for other apps. Also audiograbber "kinda" worked. I got ASPI to work but it kept getting errors. :(

This is a awesome HOW TO though and anyone who likes DVD Decrypter should try. :)

---

### Post by gbil on 2005-04-18
> **bored2k]Thoggen has just about any features dvd decrypter has. Dont get me wrong, decryp is mighty powerful, maybe a little bit too powerful for Windows users  said:**
> http://thoggen.net/screenshots/[/url]

[[IMG]http://img88.echo.cx/img88/9841/progressdialog8nz.th.jpg[/IMG]](http://img88.echo.cx/my.php?image=progressdialog8nz.jpg)

[center][size=2]Remember kids, We're doing legal *backups* here![/size][/center]

If you want to backup a DVD to another DVD, you can't user thoggen since it only encodes ogg files and also doesn't support subtitles. So it is useless.

---

### Post by csanchezotero on 2005-04-18
I am having problems with DVD Dycrypter recognising my DVD drive.  I have followed each step exactly bearing in mind that my dvd drive is hda rather than hdd.  I would really like to get this working.

Is anyone able to provide further help?

---

### Post by shakin on 2005-04-18
[QUOTE=csanchezotero]I am having problems with DVD Dycrypter recognising my DVD drive.  I have followed each step exactly bearing in mind that my dvd drive is hda rather than hdd.  I would really like to get this working.

Is anyone able to provide further help?[/QUOTE]

In DVD Decrypter are there any drives listed in the dropdown box? If you have another CD or DVD drive (read only is fine), set that to run in scsi emulation as well and see if it shows up.

Also, does your DVD drive still work in Linux apps?

---

### Post by csanchezotero on 2005-04-18
The dropdown box comes up with 'No devices detected' and thats it.

The drive currently works fine under linux.  I have must mounted the Ubuntu install CD without problems.

Here is my fstab:

> carlos@grnbeast:~ $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda3       /home           ext3    defaults        0       2
/dev/sdb1       /mystuff        ext3    defaults        0       2
/dev/sda1       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


And here is my grub options:

> title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro quiet splash hda=ide-scsi
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sda2 ro single hda=ide-scsiinitrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-3-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/sda2 ro quiet splash hda=ide-scsi
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title           Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.8.1-3-386 root=/dev/sda2 ro single hda=ide-scsi
initrd          /boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


And here is my modules file:

> sd_mod
psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
nvidia
ide-scsi


Any suggestions?

---

### Post by martinez9049 on 2005-04-18
first off thanks for the write-up. everything works great until going throught setup for wine. while im going through the base install it exits because it can't find wineboot. what could this be?

thanks,
ismael m

---

### Post by jonny on 2005-04-18
Well, I don't particularly want DVD Decryptor.  But I did want Wine, and could never get it to work - it kept crashing out and the documentation on the Wine web site is intimidating, to say the least.

Now I have IE (with Shockwave  :grin: - no Linux plugin for this) and I've been successfully running a stack of informational Windows-only CDs (sadly, I have to view too many of these in my line of business).

I think the Wine section should be proposed for the unofficial ubuntu guide.  Excellent.

---

### Post by Nez7165 on 2005-04-18
Hi this is good i have my dvd rewriter mounted on the scusi now i have a problem when i put disks in it dose not mount them to the desk top and my dvd writer will only write cd's not dvds could you maybe help with that problem.

---

### Post by ignavia on 2005-04-19
Can I assume the same procedure will work to get DVD Shrink to run? Or is there a Linux-native program that will let me copy *just the movie* to a new DVD. Pop it in, movie plays. No menus, no forced previews, no need to press play, just the movie, like in the good ol' early VHS days.

---

### Post by csanchezotero on 2005-04-19
>  	Can I assume the same procedure will work to get DVD Shrink to run? 

Should do, although I haven't got DVD Dycrypter to work yet.

Here is a useful website that shows you how to install certain apps under wine.
[http://frankscorner.org/index.php](http://frankscorner.org/index.php)

---

### Post by fthomas64 on 2005-04-21
For those of you having some difficulty getting drives recognized, after following the original post's directions, you might want to try this. 

1. Open DVD Decrypter. 
2. Click Settings | I/O
3. Check "ASPI",and hit OK. 

When I originally installed, it was set to "SPTI - Microsoft". After selecting ASPI in I/O, everything magically worked, albeit somewhat slowly. 

Also, I made sure that devices in $HOME/.wine/dosdevices were set up correctly. I didn't use winetools, but I assume this does the job correctly. 

For reference, I've had some trouble with newer versions of wine (all that's available through the normal repositories) so I installed Wine 20050211, which runs everything I need quite well.

---

### Post by JesseJames on 2005-05-05
dvd dec.  still not detecting drives. :(

When system is rebooted after modprobe ide-mod hdc=ide-scsi 
FATAL ERROR ide_mod not found.

can i add hdc=ide-scsi hdd=ide-scsi in grub's kernel line? I have only tried hdc but not detected.
devices: 
/dev/hdc /media/cdrom0  DVD-RW (for burning)
/dev/hdd /media/cdrom1  DVD-ROM (region free for reading)

 ](*,)

---

### Post by KLineD on 2005-05-05
[QUOTE=ignavia]Can I assume the same procedure will work to get DVD Shrink to run? Or is there a Linux-native program that will let me copy *just the movie* to a new DVD. Pop it in, movie plays. No menus, no forced previews, no need to press play, just the movie, like in the good ol' early VHS days.[/QUOTE]

For DVD Shrink I had to follow an extra step besides getting the drive recognized. Here's how:

If you are trying to install DVD Shrink under wine and at the end you get this:
Access violation at address 400CC5FC. Write of address 41F20000

The thing is a problem with riched20.dll so a native version has to be used. I'm not sure if it's legal to link to a download of a windows dll so just google it up. Copy it to C:\Windows\System (you know, the fake one) and then install it with
```
WINEDLLOVERRIDES="riched20=n" wine dvdshrink32setup.exe
```

And that takes care of the error.
Hint: [For a more detailed explanation...](http://forums.suselinuxsupport.de/lofiversion/index.php/t13951.html)

---

### Post by mrbass on 2005-05-06
yeah riched20.dll is definitely needed.  Thanks.  Here's my graphical guide based on this guide and one over on doom9.org and read quite a few man pages.
[http://mrbass.org/linux/ubuntu/dvdshrink/](http://mrbass.org/linux/ubuntu/dvdshrink/)

On a fresh ubuntu install winetools just wouldn't install...so I went the just the wine install and no config need except for version=win2k so you can OPEN DISC in dvdshrink and decrypt with it.

Also someone mention to me they got Video Preview in DVDShrink working with quartz.dll   yeah it works and all but screws up left side of dvdshrink so I pretty much gave up.  You need directshow (comes with directx)...good luck installing that in wine.
[http://www.mrbass.org/linux/ubuntu/dvdshrink/quartz.png](http://www.mrbass.org/linux/ubuntu/dvdshrink/quartz.png)  to show you what I mean.

---

### Post by mrbass on 2005-05-07
ok stupid me....all you have to do is Maximize and Unmaximize dvdshrink's window each time you open it to fix grey left panel...no biggie.
Anyway I've completely modified my guide based on that and also wine paths and setup.  Should work now. Can't believe I spent this much time on this...but now it's working just great.

---

### Post by happyraul on 2005-05-07
I'm having problems with getting Wine configured.  I get the following error when running winetools:

```
wine: cannot find 'wineboot'
Wine failed with return code 1
no suitable Wine directory found...
Wine 0
wine is executed as wine
Parameters are --new
Wine is not configured yet!
```

Anyone know what I should do?

---

### Post by mrbass on 2005-05-07
install winesetuptk instead and use that to configure wine.

---

### Post by ddhytz on 2005-05-08
This is a bit off subject. Any program to convert a .VOB file (DVD) to .RM or .RMVB file (real player format)?

---

### Post by projectle on 2005-05-08
Forgive me for what may seem an absurdly idiotic question, but why use DVD Decryptor in Wine when you could just use the Natively Linux DVD::RIP? 

DVD::RIP is a dvd ripper, decryptor, transcoder, resizer, renderer, distributed server, and recorder.

Plus, it is one hell of a lot faster than DVD Decryptor running natively under windows...

---

### Post by mrbass on 2005-05-08
sure that's a legitimate question.  Only problem with dvd::rip is you can't backup titles like Resident Evil 2, Little Black Book, Spanglish, and quite a few other ones.  Why because they have fake vob errors to thrwart copying.  It's called ARccOS [http://www.sonydadc.com/products.copy.arccos.go](http://www.sonydadc.com/products.copy.arccos.go)

On the windows side there is DVD Decrypter that handles ARcoSS as DVD Shrink can't.  Also on-the-fly decryption ones that handle this new copy protection include DVD43 (free) or ANYDVD ($).   

Now what you could do is just use DVDShrink and backup your DVDs and if "DVD Shrink has encountered an error" then most likely you have an ARcoSS protected DVD and need to use DVD Decrypter.

---

### Post by jpl on 2005-05-20
Since I don't want scsi emulation, I tryed all ways to detect CD-Roms and found that  I can use dvddecrypter without scsi adding

; DVD Decrypter
[AppDefaults\\DVDDecrypter.exe\\Version]
"Windows" = "nt40"

or "nt351" to ~/.wine/config.

and choosing SPTI as  i/O. After 2 devicecontrol errors all drives are found  :razz: 

Also I can access DVD reader from dvdshrink defining the right links on dosdevices as CDROM (with winecfg).
I'm using Hoary with wine 20050310 from backports (it seems that 20050419 is broken. Winetools don't work right and winelib.so.1 link or lib is missing.)

Please confirm the solution. I don't know if I did something else to make it work.

Now I only miss Nero label creator. Is there some Linux clone ?

 \\:D/ 

JP

---

### Post by mrbass on 2005-05-21
ok I'll try this one more time to see if I can't get it working without SCSI emulation but my hopes aren't too high.

Right now scsi emulation works decent just slow because DMA isn't on for SCSI I don't believe.  I guess we'd have to recompile to kernel to turn it on.

Read this snippet on gentoo forums
"Run the kernel configuration tool. Under, the IDE set up chose:-
SCSI emulation support
Be sure to set up DMA for your IDE chip set here too because hdparm won't be able to control them.

Under the SCSI Set Up. choose:-
legacy /proc/scsi/ support
SCSI generic support
SCSI CDROM support
Turn Off
Probe all LUNs on each SCSI device "

---

### Post by mrbass on 2005-05-21
sweet thanks for that tip...I'm gonna totally revamp my guide as your right dvddecrypter does not need SCSI emulation

.wine/config
as long as your [Version] specifies
nt40
then the STPI-Microsoft works

thanks for the huge tip.  Also note nt40 also allows dvdshrink to read the dvd directly also 
if you previously enabled SCSI emulation basically you

- remove the hdd=ide-scsi in /boot/grub/menu.lst
- remove ide-scsi in /etc/modules
- gedit .wine/config
change w2k or winxp to nt40
- cd .wine/dosdevices
rm d:
ln -s /media/cdrom d:

done

---

### Post by jpl on 2005-05-22
So glad to know that works!
Actually I'm using "Windows" = "winxp" to run dvdshrink (better interface stability).
I can access CD-ROM directly if I delete the old drive links and create new ones with winecfg, defining them as CD-ROM.
The original links has some HardDisk "flag" that makes them invisible to dvdshrink.

Tried to burn a dvd with decrypter and it looks like it worked but the dvd was trash.
Gnomebaker and graveman also gave me problems detecting and burning. I needed to use Nautilus to burn my iso right.

I found the Label creator I need - it's called glabels and it's almost perfect.

Guess I'm satisfied.
My next fight will be with modem on Linux and fax software.

See you!

---

### Post by Bomper on 2005-05-23
dvddecrypter and  dvdshrink icons in my ubuntu (GNOME) :

  /home/your_user/.kde/wine/

---

### Post by awtomlinson on 2005-05-25
i don't understand why people need to use both dvd decrypter & dvd shrink.  seems to me that my favorite app, dvd shrink, will do everything that dvd decrypter does & more.  anyway, will someone please write a gpl linux native clone of dvd shrink?  i know that there are many such linux programs available, but none of them come even remotely close to dvd shrink.  come on guys, linux software is superior in every other category.  its 2005, linux needs a native, gpl dvd shrink clone!!!!!!!

---

### Post by betrayed on 2005-05-25
well I don't think shrink is that grat of an app.  I am sort of a purist when it comes to quality of my discs. So if I am doing a back up i go through the cce approach.  I would really like to see a free cce for linux. :)

---

### Post by MetalMusicAddict on 2005-05-25
[QUOTE=awtomlinson]i don't understand why people need to use both dvd decrypter & dvd shrink.  seems to me that my favorite app, dvd shrink, will do everything that dvd decrypter does & more.  anyway, will someone please write a gpl linux native clone of dvd shrink?  i know that there are many such linux programs available, but none of them come even remotely close to dvd shrink.  come on guys, linux software is superior in every other category.  its 2005, linux needs a native, gpl dvd shrink clone!!!!!!![/QUOTE]
Decrypter will let you pull out parts of the DVD. Shrink just lets you re-author.

And I dont know about this:
[QUOTE=awtomlinson]linux software is superior in every other category.[/QUOTE]

---

### Post by wolf321 on 2005-08-11
I got DVDDecrypter recognizing my drive, but I keep getting the message that "Disc is Empty", when there is obviosouly a disk in the drive! AAAArgh....been at this for awhile now.   ](*,) 

Any suggestios?

thanks in advance.

---

### Post by Sutur on 2007-01-25
After many horrible hours of trying to fix this wretched problem, I have found an answer that should work.

I tried ide-scsi emulation, but it didn't do squat.

I tried editing the config file in the ~/.wine folder to force wine into nt40 mode, but once again DVD Decrypter failed me.

Fundamentally, all I needed to do was run winecfg, and add DVD Decrypter under nt40 compatibility in the Application tab, rather than editing the config file manually. It turns out I didn't actually have a config file, and that I had to make it.

Other than that I made sure all the links in ~/.wine/dosdevices were pointed to the correct devices.

I really hope this helps someone because more often than not it's just a tiny little hiccup that stands in the way of your success...

---

### Post by linux4909 on 2007-12-13
I dont have the same number of Modules as the rest of you do. 
i am running Ubuntu GG, 7.10 on a Gateway. 

when i type commad:
> $ sudo gedit /etc/modules
my output is:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ide-scsi

however, was still able to run DVD Decrtyper when i went to Tools>Settings>I/O>and selected the first ASPI option. am i supposed to have the same number of modules as the rest of you do?my drive handles Dual Layers. is this an issue?

---

### Post by resthavener on 2008-12-17
For getting DVD decrypter to see the drive, simple answer worked for me (assumes Ubuntu is finding it).  Get hold of (Google) frogaspi.dll, rename it to winaspi.dll and stick it in \Windows\System32 (I guess anywhere on the path will do).  Many thanks to France's finest.  

Next proceed in an orderly fashion to Decrypter's menu - Tools/Settings/IO and click on ASPI in the interface list.  By the time you leave the menu the drive should be there displayed in the box.

---

### Post by bburtin on 2009-11-10
For the record, I just installed DVD Decrypter in Ubuntu 9.10, and it was really easy:

[LIST=1]
[*]Install Wine in Ubuntu Software Center
[*]Run SetupDVDDecrypter_3.5.4.0.exe
[*]Start DVD Decrypter from the Wine menu
[*]Open Preferences and choose ASPI in the I/O tab
[/LIST]

---

### Post by Automat2 on 2009-11-18
I have installed DVDFab decrypter and run it under Wine. The program loads well.

The problem I found is that if I want to rip a DVD >4.5GB to my external HDD (1TB), encoding at DVD9 1:1 -the free non-expiring option of DVDFab, a message pops up: "Z drive not large enough to save your file".

This message does not appear if I want to download the file to the HD or if I select DVD5 encoding.

And also, if I select ASPI on the I/O menu, it does not find the DVD on the drive.

---

### Post by Automat2 on 2009-11-19
> **Automat2 said:**
> I have installed DVDFab decrypter and run it under Wine. The program loads well.

The problem I found...

All sorted when I assigned the correct link to the HDD on Wine. (winecfg).

---

### Post by drdos2006 on 2010-03-11
Adding additional information from  bburtin

   1. Install Wine in Ubuntu Software Center
   2. Run SetupDVDDecrypter_3.5.4.0.exe
   3. Start DVD Decrypter from the Wine menu
   4. Open Preferences and choose ASPI in the I/O tab

I am running Ubuntu 9.10 Desktop (64bit)

Choose number 1
2  From the terminal, copy the exe file into /home/{user}/{hidden files}/.wine/drive_c so that the dvd decryptername.exe file can be seen by dvd decryptername.exe
 with 
sudo cp /home/{user}/.wine/drive_c  /home/username/Downloads/dvd decryptername.exe

Choose number 3
Add the dvd decryptername.exe to install
Choose number 4
regards
[edit]
I also found for a couple of other Windows programs I had to run from the terminal in order for them to install.
e.g.
cd to the /home/{user}/.wine/drive_c folder 
and run 
wine the_program.exe
to install.
[/edit]

---

### Post by yuval_harpaz on 2010-05-17
Dear ubuntu community
I am trying to run DVD decrypter on wine.
I followed instructions as given here 

my DVD is on /dev/scd0 so my kernel line looks like this now:

kernel /boot/vmlinuz-2.6.24-27-generic root=UUID=731ba5fc-4fac-480a-b654-5ff6e691b961 ro quiet splash scd0=ide-scsi

I also added ide-scsi to the list /etc/modules
It didn't work, the decrypter says the device is not detected.
can you help me here please?

---

### Post by frodowiz on 2010-05-27
> **fthomas64 said:**
> For those of you having some difficulty getting drives recognized, after following the original post's directions, you might want to try this. 

1. Open DVD Decrypter. 
2. Click Settings | I/O
3. Check "ASPI",and hit OK. 



i feel like such an idiot. this was my problem too. i multiboot ubuntu's and my secondary ubuntu runs dvd decryptor and dvd shrink  wonderfully. my primary didnt and i must have read everything on the internet to find out why. after reading and trying the above and seeing it find my dvdrecorder on my main system, i went to my secondary system and took a ganger at the settings. doh.  they are set like this. 

well, from all the reading i still came away with some  nice stuff to try out (thoggen). 
i would also like to take this time to give a shout out to  every one of my linux brothers and sisters. the newbies that read these posts need to see the incredible people and support that lives in the linux world. i dumped windows a year ago and cant fathom going back. the freedom, the kindness, the oddball humor - i appreciate all of 
 you.

any newbies out there- stick around. it can be rough going at first. looking for linux replacements for windows software you are familiar with, knowing what to ask and where,when how to ask it. your best friend is google with the word ubuntu and your question together. the power of the  software, ffmepg, mencoder, the graphics libraries, there is so much to work with you could make your own software, your own way then give back for the next person who comes along with the same question/problem you had.

right now i am working on a script to simplify and gui-ify the setup of nfs for newbies. after a year i feel its time to give back. im not the programmer i thought i was :) but dang   it is fun.

once again, thank you all, especially the ones who did stick around. without you, linux would still be a wish.

---

### Post by pous on 2010-09-06
hi to all, i've been trying to install dvd deecrypter through wine but have failed since it doesn't recognise the dvd-rw... 

i've been trying to use this how-to, but i'm still quite new to using terminal code, etc. and dont understand very well the istructions... could anyone explain them a little plainer for a noob?? after the first command i found my dvd to be listed as */dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0* but got lost after that.

i'd appreciate any help, thanks!

---

### Post by Origin_Unknown on 2010-09-09
guys,

if i run 


 cat /etc/fstab

I don't see anything relating to my DVDrw - could it be because it's external?

---

### Post by mc4man on 2010-09-09
Don't have dvdd but do use ImgBurn (same author)
Open dvdd and ck under the tools -> settings (?) and see if there is an I/O tab. (should be in there somewhere

Then change from the default of SPTI to ASPI-WNASPI32.DLL and your drive(s) should be found by dvdd

---

### Post by Origin_Unknown on 2010-09-09
cheers mc4man

---


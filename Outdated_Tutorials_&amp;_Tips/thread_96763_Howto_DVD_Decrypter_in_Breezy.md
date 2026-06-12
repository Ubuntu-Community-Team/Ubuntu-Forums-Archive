---
title: "Howto DVD Decrypter in Breezy"
date: 2005-11-29
forum: Outdated Tutorials &amp; Tips
---

### Post by aragorn2909 on 2005-11-29
If your like me, the only reason to have Wine installed is to run two programs; DVD Decrypter and DVD Shrink.  In Hoary, thanks to MrBass, this was a simple issue.  Breezy, however, is a completely different breed.  The problem though, does not lie with Breezy, it rests with Wine.  Even with the help of [this]("http://www.ubuntuforums.org/showthread.php?t=78611&highlight=wine+decrypter+breezy") thread, it seems that many, including myself, were having problems that could not (for the time being) be overcome.  This also kept me from upgrading to Breezy from Hoary.  Not any longer. 

This is based on a very *fresh* Breezy install:
Download libwine from [here]("http://packages.debian.org/stable/libs/libwine")

Download wine from [here]("http://packages.debian.org/stable/otherosfs/wine")

Lastly, dowload winesetuptk from [here]("http://packages.debian.org/stable/otherosfs/winesetuptk") 

Now that we have the necessary packages, we can begin to install them.  In the terminal, navigate to the folder where you just downloaded the 3 packages.  In order, ```
sudo dpkg -i libwine_0.0.20050310-1.1_i386.deb
```
*dont worry about the error, we'll correct that in a second*
```
sudo dpkg -i wine_0.0.20050310-1.1_i386.deb
```
*dont worry about the error*
```
sudo dpkg -i winesetuptk_0.7-1.1_i386.deb
```

Run the update utility on the Gnome-panel (or run update through synaptic, this corrects the dependency error)
Open synaptic, find the 3 wine packages youve installed, and highlight each one->Package->Lock Version

Find MrBass' instructions [here]("http://www.mrbass.org/linux/ubuntu/dvdshrink/"), follow them, and you should be all set.  A perfectly working DVD Decrypter and DVD Shrink in Breezy.  :)

---

### Post by poiuytr on 2006-01-09
I don't know what you mean by the following:

"Run the update utility on the Gnome-panel (or run update through synaptic, this corrects the dependency error)."

What is "the update utility"?

Thanks in advance for any clarification.

---

### Post by endersshadow on 2006-01-09
Run in the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

The update utility is just that red circle icon in your notification area which informs you of pending updates to your system.

---

### Post by poiuytr on 2006-01-09
Thanks very much for clarifying.  I know about apt-get.  I just never heard it referred to by that shorthand in the past, and wasn't sure if it was something else being referred to.

---

### Post by delsdog on 2006-01-27
It appears that the pages quoted for the files no longer works, and unless I'm reading the reason incrorrectly it never will again, so can someone point me in the direction of another place to get these files, as I have just done a reinstall and would quite like to set up DVD Shrink again.

---

### Post by finnhiggins on 2006-01-28
Try googling the package names - worked for me.

---

### Post by delsdog on 2006-02-10
That's exactly what I did, and sorted everything out fine. Thanks anyway though.

---

### Post by Robor on 2006-02-10
Well, it appears as though the last attempt to install DVD Decrypter worked despite the previous errors.  However, when I run it I get this in the DVD Decrypter log:

[i]I 15:43:21 DVD Decrypter Version 3.5.4.0 started!
I 15:43:21 Microsoft Windows 95
I 15:43:21 Initialising ASPI...
I 15:43:21 Searching for SCSI / ATAPI devices...
W 15:43:21 No devices detected![/i]

I've got a DVD in the drive and it's mounted (it's on the desktop).  Also, when I try to  *"Make sure in DVD Decrypter Setttings under I/O tab STPI - Microsoft is checked."*  the option is greyed out.

---

### Post by Robor on 2006-02-10
Back DVD Decrypter dumping to a black screen and having to do a 'startx' to get back to the desktop.  :confused:

---

### Post by Robor on 2006-02-10
[QUOTE=aragorn2909]If your like me, the only reason to have Wine installed is to run two programs; DVD Decrypter and DVD Shrink.  In Hoary, thanks to MrBass, this was a simple issue.  Breezy, however, is a completely different breed.  The problem though, does not lie with Breezy, it rests with Wine.  Even with the help of [this]("http://www.ubuntuforums.org/showthread.php?t=78611&highlight=wine+decrypter+breezy") thread, it seems that many, including myself, were having problems that could not (for the time being) be overcome.  This also kept me from upgrading to Breezy from Hoary.  Not any longer. 

This is based on a very *fresh* Breezy install:
Download libwine from [here]("http://packages.debian.org/stable/libs/libwine")

Download wine from [here]("http://packages.debian.org/stable/otherosfs/wine")

Lastly, dowload winesetuptk from [here]("http://packages.debian.org/stable/otherosfs/winesetuptk") 

Now that we have the necessary packages, we can begin to install them.  In the terminal, navigate to the folder where you just downloaded the 3 packages.  In order, ```
sudo dpkg -i libwine_0.0.20050310-1.1_i386.deb
```
*dont worry about the error, we'll correct that in a second*
```
sudo dpkg -i wine_0.0.20050310-1.1_i386.deb
```
*dont worry about the error*
```
sudo dpkg -i winesetuptk_0.7-1.1_i386.deb
```

Run the update utility on the Gnome-panel (or run update through synaptic, this corrects the dependency error

[b]This is where I ran into a problem.  Here's what I get at this point:

robor007@HOME-T42-UBUNTU:~/Desktop/Downloads/Wine$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  libwine wine
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.[/b]

---

### Post by Robor on 2006-02-10
Okay, here's what I've determined.  If I un/re-install Wine and such and launch DVD Decrypter without running the Wine setup it will launch but find no devices.

If I un/re-install Wine and run the Wine setup then launch DVD Decrypter it bombs out of X.

Any suggestions/ideas on where to look?  I can't even launch from the command line and look for errors because when I restart X any previously open apps are closed.  :confused:

---

### Post by Robor on 2006-02-11
Bump for some help on this   :confused:

---

### Post by Robor on 2006-02-11
Still stuck here.  Any suggestions?  Thanks!  :)

---

### Post by aragorn2909 on 2006-02-12
Robor: Ok, the error concerning wine and libwine being kept back is ok, this is what we want here.  Secondly, did you follow MrBass' instructions?  I have done this many times on many different distros, and it has worked perfectly.  For DVD Decrypter to work properly, your wineconfig has to indicate "nt40" as the operating system instead of "win98".  You have done this?  (I always saved this until last, after installing dvd shrink).  Let me know, I'll try to help as much as I can.

A

---

### Post by Robor on 2006-02-12
Yep, I did read MrBass' instructions and edit the ~/.wine/config file to change win98 to nt40 in the Version section.  I tried with and without that edit and it bails to a black screen with no command prompt.  I have to ctr-alt-bksp to get back to the system.  Also, in MrBass' instructions he mentions using the 'STPI - Microsoft' I/O option.  That is greyed out for me regardless of using winesetup or not and having a DVD in the drive or not.

---

### Post by Robor on 2006-02-13
Okay...  A followup just in case someone else runs into this frustrating problem.  Here's what I did to get my DVD burner detected by DVD Decrypter...

Check this link:  [http://ubuntuforums.org/archive/index.php/t-27369.html](http://ubuntuforums.org/archive/index.php/t-27369.html)

Number one, I was trying to install winetools and use couldn't find it.  Also tried using winesetup (winesetuptk) to configure Wine when I should've been using 'winecfg' that was installed with Automatix.  Big DUH on my part!  ;)  Anyway, I let it autodetect my devices and set it to simulate WinNT40 then followed the instructions below.

rm d:
ln -s /media/cdrom d:

After that I launched DVD Decrypter and set it to 'STPI - Microsoft' under the I/O tab.  It detected my device and read my DVD.  Unfortunately, all I have available with me is a Fedora Core 4 DVD so I can't test operation or speed.  I'll follow up later tonight after work.  

Thanks!

---

### Post by Robor on 2006-02-13
Great.  What was working has now stopped working.  I was able to rip a DVD to my HD with DVD Decrypter and then used DVD Shrink resize it but when I went to use DVD Decrypter to burn it I got the same previous error:

I 19:15:08 DVD Decrypter Version 3.5.4.0 started!
I 19:15:08 Microsoft Windows NT Workstation 4.0 (4.0, Build 1381 : Service Pack 6a)
I 19:15:08 Initialising SPTI...
I 19:15:08 Searching for SCSI / ATAPI devices...
W 19:15:09 No devices detected!


Why did it work then stop?  This makes no sense.  I made no changes between it working and finding no devices again.  I'm lost here.

---

### Post by aragorn2909 on 2006-02-14
Robor:  I'm not sure as I've never used Automatix (not even using Ubuntu at the moment), but my howto refers specifically to wine version 20050310 and only that version.  If Automatix installs a newer version, than I see where your problems are coming from.  Like I said in my first post, I *only* need wine for Decrypter and Shrink, and version 20050310 works flawlessly.  If you really want Decrypter to work and aren't concerned with anything else, remove all traces of any newer wine version and stick with 20050310.  I have tested this method on about 4 different distros, and it has worked without fail everytime.  Use the files I link to and MrBass' instructions *only*, and it *will* work.

---


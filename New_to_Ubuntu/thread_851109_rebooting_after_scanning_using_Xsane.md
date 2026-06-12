---
title: "rebooting after scanning using Xsane?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Bach Concentus on 2008-07-06
Hi everyone,

I'm new to Linux. My first impression is that it is marvellous.

I have a problem, though, with scanning. I have succesfully connected my scanner and at first that was a remarkable thing. I did not have to do anything - just connect the scanner and everything seemed to work perfectly. But when I augment the resolution above 250 dpi, the programme blocks. In other words, after the scanning was finished, a window opened but without the menu balk on the top nor the standard linux balk at the downside of the page. This means I coudn't close the window. When I tried to save via ctlr+S, everything became grey - no opther option than to reboot. Same remark when I tried to close via the menu 'File'. I first thought that it was due to the printer (I have tried first a CanonScan N 650 U) but the same problem occurred when using a HP Scanjet 4070. Does anyone knows this problem or could help me please?
THanks for your help.
Best
BC

---

### Post by apswartz on 2008-07-08
Try this from the commandline...


```
scanimage -x 215 -y 297 --mode Color --progress --format=tiff --resolution 300dpi > test.tif
```

This will help see if it is a problem with xsane or the backend.

---

### Post by ZabiGG on 2008-07-08
Just a quick (and might-sound-stupid) question... Do you intend to have what you are scanning printed commercially? If not, why would you want to scan at more than 150 dpi (home or small office printer resolution), unless you want to zoom out the result big time?

Cheers,

Z.

---

### Post by apswartz on 2008-07-09
> **ZabiGG said:**
> Just a quick (and might-sound-stupid) question... Do you intend to have what you are scanning printed commercially? If not, why would you want to scan at more than 150 dpi (home or small office printer resolution), unless you want to zoom out the result big time?

Certainly not a stupid question. I personally scan old photographs for archival purposes. I scan them at 300dpi and store them in a lossless format for that reason. While 150dpi (or less) may be fine for online work and websites there are certainly times higher resolutions are to be desired.

---

### Post by Bach Concentus on 2008-07-09
thanks fo this suggestion! the only thing, i don't know where to find the command line... :-) as i wrote, i'm a complete and absolute beginner...

---

### Post by Bach Concentus on 2008-07-09
well, yes, i need fairly high resolution for i'm working on a ph.d. including scanned pics of old handwritten scores.

---

### Post by apswartz on 2008-07-09
> **Bach Concentus said:**
> thanks fo this suggestion! the only thing, i don't know where to find the command line... :-) as i wrote, i'm a complete and absolute beginner...

Oops! Sorry about that.

There should be a menu item (either in utilities or system) that says Console (I use Kubuntu which is a little difference than Ubuntu). When you run that program you will get a command line.

---

### Post by apswartz on 2008-07-09
If you going to do a lot of scanning you may just want to do it with a shell script instead of a gui. I use this script to scan a whole page at a time. 

```
#!/bin/bash
stamp=`date +%s`
filename=/home/alan/scanned_images/image_${stamp}.tif

scanimage -x 215 -y 297 --mode Color --progress \
   --format=tiff --resolution 300dpi > $filename

echo
echo 'done'
echo
```

Of course replace 'alan' with your username and make sure you have a directory named 'scanned_images' 

Once you create the script save it with a name like 'scan' and make it executable...

```
chmod +x scan
```

Then from the console (commandline) run...

```
./scan
```

each time you wish to scan a page.

---

### Post by ZabiGG on 2008-07-09
@aps

Great advice about the script, thanks ;)


@bach

The "console" in Gnome is called Terminal

Click Accessories, you should find it.

You can also click on "Look here" in my signature below for starter info about Ubuntu/Linux. There is a great and user-friendly Terminal for beginners thread in there that might get you started nicely...

Z.

---

### Post by CEB2nd on 2008-07-09
> **Bach Concentus said:**
> Hi everyone,

I'm new to Linux. My first impression is that it is marvellous.

I have a problem, though, with scanning. I have succesfully connected my scanner and at first that was a remarkable thing. I did not have to do anything - just connect the scanner and everything seemed to work perfectly. But when I augment the resolution above 250 dpi, the programme blocks. In other words, after the scanning was finished, a window opened but without the menu balk on the top nor the standard linux balk at the downside of the page. This means I coudn't close the window. When I tried to save via ctlr+S, everything became grey - no opther option than to reboot. Same remark when I tried to close via the menu 'File'. I first thought that it was due to the printer (I have tried first a CanonScan N 650 U) but the same problem occurred when using a HP Scanjet 4070. Does anyone knows this problem or could help me please?
THanks for your help.
Best
BC

Are you talking about the viewer window that opens when the scan completes?

Try disabling visual effects before you open XSane.

Right-click your desktop > change desktop background > visual effects > none

---


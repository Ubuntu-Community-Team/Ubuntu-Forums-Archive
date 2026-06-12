---
title: "HOWTO: Use Webshots with wine"
date: 2007-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by Martje_001 on 2007-11-03
**Step 1:**
*Install wine*
Install wine via "system --> Administration --> Synaptic Package Manager" or follow the instrucions on [WineHQ]("http://www.winehq.org/site/download-deb").

**Step 2:**
*Install Webshots*
Go to [webshots.com]("http://www.webshots.com/samplers/") and download your webshots to the desktop. Open it with wine and go through the next-next windows.

Install it in "C:\Program Files\Webshots\"

[B]
Step 3:[/B]
*Make script*
Go to "Applications --> Accessoires --> Text Editor" and paste the following code in it:
```
#!/bin/bash
cd /tmp
echo "$1" > wbsht
sed -i -re 's/\//\\/g' wbsht
argument1=`cat wbsht`
argument2=`echo z:`
argument3=`echo -n $argument2
echo $argument1`
rm wbsht
wine "C:\Program Files\Webshots\Launcher.exe" "$argument3"
```
And save it.

**Step 4:**
*Download your photos.*
Go to Webshots.com and download your photo. Firefox asks you if you want to open it, or save it. Choos open ands click 'browse' and choose the script you've saved in step 3.

**Step 5:**
*Install UWC.*
Download UWC [here]("http://sourceforge.net/project/downloading.php?group_id=159047&filesize=1502847&filename=UWC-1.6.6-setup.exe&20985888"). And install it just like webshots.

**Step 6:**
*Run UWC.*
Go (in UWC) to Conversion --> Batch conversion. Select '+folder' and choose '"My Documents --> Webshots Data".
Select a destination folder, and click** let's convert!**
[B][COLOR="Red"]
Edit: Since an update webshots doesn't work anymore. Here is an workaround (run this in a terminal):[/COLOR][/B]
```
cd ~/.wine/drive_c/windows/system
wget http://www.dll-files.com/dllindex/download.php?mfc42download0VMfWEdMdO -O mfc42.zip
unzip mfc42.zip
rm mfc42.zip
cd ~
```

---

### Post by manoynmonic on 2008-02-15
Will this work to upload photos to my webshots account as well?  Winehq, and a go at it in PCLOS led me to believe that one could only view existing photos...

Thanks for the script, will try this out next week when I get some time!

MN

---

### Post by Martje_001 on 2008-02-17
It does work here!

Edit: Hmmm, it **worked** here.. sorry but it doesn't work.

---

### Post by adam0509 on 2008-02-17
can you make a [www.playonlinux.com](www.playonlinux.com) script ? Thanks !

---

### Post by Martje_001 on 2008-02-17
I'm sorry, but: what does that mean?

Edit: Hmm, ok, I see. But isn't that only for games?

---

### Post by manoynmonic on 2008-03-21
> **Martje_001 said:**
> **Step 1:**

Edit: Since an update webshots doesn't work anymore. Here is an workaround (run this in a terminal):[/COLOR][/B]
```
cd ~/.wine/drive_c/windows/system
wget http://www.xs4all.nl/~mgj1/mfc42.dll
```

Thanks for the edit, but webshots still crashes when I try to upload a photo.  Any ideas?

---

### Post by Martje_001 on 2008-03-22
Can I see the output in a terminal?

---

### Post by newbieforever on 2008-03-22
hem, im in a hurry,

please pardon me if someone already posted something similar:

i prefer veeeery much **ultimate webshots converter** [http://uwc.apinc.org]("http://uwc.apinc.org/")

anyway you use webshots, uwc is better according to me, you have really all your picture as normal jpg organized in folder and arguments, same as webshots, and you can do what you want with them, there is no logo inside the picture

you have single or batch conversion, and it works with any type of webshots extensions (both free and premium membership), seamlessly

it work fine in wine, but there is also linux (kde based actually) version
both versions are actively maintained 

as im a newbie i didnt manage to install linux version with gnome, and if someone could help with a step by step help i would be glad and thankful...

i donated something to uwc, i love it...

nbfe

__________

---

### Post by newbieforever on 2008-03-22
> **newbieforever said:**
> hem, im in a hurry,

please pardon me if someone already posted something similar:
__________

yes, it was so! :-)
any way i simply run the installer in latest wine, no matter about dlls and so on... may be im lucky this time...

please see the attachments...

bye

nbfe

---

### Post by micdhack on 2008-11-30
In this guide it should be also included how to make webshots change your desktop picture.
Webshots changes windows wallpaper to look at a file in a location 
> c:\windows\profiles\micdhack\Application Data\Webshots\The Webshots Desktop\Webshots Wallpaper.bmp
Which is actually under linux
> /home/micdhack/.wine/drive_c/windows/profiles/micdhack/Application Data/Webshots/The Webshots Desktop/Webshots Wallpaper.bmp
where micdhack is your linux account username

Simly drag and drop this file to the wallpaper menu an voila. every time that webshots changes a picture your desktop is changed too.

BTW the script for opening files from mozilla doesnt work...can you help fix it?
if i run the script from terminal for example sh web_launch file.wbz it works.

---

### Post by ronron261 on 2009-10-11
@ xzcallaway

is there a 64-bits version of netpix?

---

### Post by shields on 2009-11-07
Great app!

Is there a way to add new albums to retrieve pics from the net? For example, if I wanted it to go online and pic up some Steeler wallpaper or some Honda wallpaper, is there a way to create an album that would do that?

Thanks!

---


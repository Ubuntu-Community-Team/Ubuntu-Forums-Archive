---
title: "Tiny Fonts in Google Earth"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by nickhk on 2008-09-12
I have installed Google Earth, but the fonts are so small I cannot read anything. Any idea how to fix this?

---

### Post by acidsolution on 2008-09-12
Its working fine and readable in mine ?
whats your screen resolution??

---

### Post by SunnyRabbiera on 2008-09-12
what version of google earth are you running?
the linux version or the wine version?

---

### Post by rustutzman on 2008-09-12
Have you setup your machine for dual display? I had this happen when I set a second monitor for HD screen resolution. That caused my main monitor to display the mini fonts at logon and in some programs.

Russ

---

### Post by nickhk on 2008-09-12
Hi all, 

I am using the linux version not wine version. My screen resolution is 1024 x 768 - and everything is working fine - no problems. Only Google Earth has microscopic fonts.

---

### Post by SunnyRabbiera on 2008-09-12
> **nickhk said:**
> Hi all, 

I am using the linux version not wine version. My screen resolution is 1024 x 768 - and everything is working fine - no problems. Only Google Earth has microscopic fonts.

you may want to try it in wine, the linux version still needs work.

---

### Post by EarloftheWest on 2008-09-12
Can't remember, but isn't GoogleEarth for Linux just the Windows version with a Wine Wrapper?
I believe that there is an option on the 'start' menu that allows you to adjust the size of the fonts in GoogleEarth.

---

### Post by helai on 2008-09-20
please go to yours terminal,then input as below:

here lenovo should be changed to yours computer name

```
sudo gedit /home/lenovo/.config/Google/GoogleEarthPlus.conf
```


then change GuiFontSize=12 or larger as you like ,if you can't find it ,please add this sentence below the content "Render"

Helai

---

### Post by Gavin77 on 2008-10-18
Thanks helai for that fix.  Sudo isn't needed though.

---

### Post by RedRat on 2008-12-16
Use your file management tool (Nautilis or Thunar, etc) and edit GoogleEarthPlus.conf with a text editor:
 ~/.config/Google/GoogleEarthPlus.conf

than edit the lines below adding what I have here:
SecondaryFontVersion2Family=Bitstream Vera Sans
SecondaryFontVersion2Size=12
SecondaryFontVersion2Style=0
SecondaryFontVersion2Weight=75

By default Arial will be the font in those lines. For reasons known only to Google, the Arial font face does not render quite as well as the Bitstream font. You can play with the font size, I found 12 is good but depending on your resolution, you might need 14. Most importantly, **also changing the font weight from 50 to 75 very definitely improved the appearance of the tool bar**. 

I must Thank  dandart and philinux for their help since I was as lost as you.

---

### Post by logos34 on 2008-12-22
> **helai said:**
> please go to yours terminal,then input as below:

here lenovo should be changed to yours computer name

```
sudo gedit /home/lenovo/.config/Google/GoogleEarthPlus.conf
```


then change GuiFontSize=12 or larger as you like ,if you can't find it ,please add this sentence below the content "Render"

Helai

thanks! fixed it for me

---

### Post by aalhamer on 2009-10-06
Dear All,

I have tried every suggestion and ended up in failure, the solution to my small font problem with google earth 5 was simply to change the settings of my QT4. I know it pissed me off too.

go to your desktop
Follow to and open System> Preferences> QT 4 Settings
click on the font tab and choose the desired size. I run a 1360 resolution 18 aria was perfect.

I hope this solves the problems of many.

---

### Post by Francewhoa on 2010-03-21
[B]This how to has been relocated to [http://ubuntuforums.org/showthread.php?p=9004673](http://ubuntuforums.org/showthread.php?p=9004673)
[/B]

---

### Post by Francewhoa on 2010-03-21
Deleting my double post.

---

### Post by RedRat on 2010-03-21
Hey thanks. The qtconfig approach worked for me!

---

### Post by felixcorrales on 2010-08-22
I had to set fonts size to 48.   System> Preferences> QT 4 Settings> Fonts> Point Size> 48. 


/32 inch monitor, HD.
/ubuntu 10.04.
/nvidia gt220.
/google earth linux 5.2.1.1547 bin file.

:p

---


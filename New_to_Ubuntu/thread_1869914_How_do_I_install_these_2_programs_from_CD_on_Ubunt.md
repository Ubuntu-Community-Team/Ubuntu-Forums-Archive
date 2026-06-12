---
title: "How do I install these 2 programs from CD on Ubuntu?"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by timcd100 on 2011-10-26
I'm an absolute beginner who just downloaded Ubuntu 11.10 a few days ago. I downloaded it from this site: [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) and used the first bitTorrent link. 

When I put in the CD for Encyclopedia Brittanica ([http://www.amazon.com/gp/product/1615354336](http://www.amazon.com/gp/product/1615354336)) and click the CD icon, then click the autorun.exe file it gives me this error message:

Archive:  /media/BritannicaDVD/autorun.exe
[/media/BritannicaDVD/autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/BritannicaDVD/autorun.exe or
          /media/BritannicaDVD/autorun.exe.zip, and cannot find /media/BritannicaDVD/autorun.exe.ZIP, period.

The product description says Platform:**** Windows Vista /  7 /  2000 /  XP, Mac OS X. Does this mean it won't work with Ubuntu?
---------------------------------
---------------------------------
Also, when I try to install, from the CD, the driver for this wifi antenna [http://www.amazon.com/gp/product/B001O9X9EU](http://www.amazon.com/gp/product/B001O9X9EU) (ie when I click any of the exe files like above) it gives me the following message. 

****NOTE: this product's description says this: Includes driver for Windows 2000, XP 32/64, Vista 32/64, Windows 7,  Linux (2.4.x/2.6.x), Mac (MacOS 10.3 - 10.5) For MAC OS 10.6.7 and later  version, we suggest AWUS036NHR, AWUS036NH, AWUS036NEH, AWUS051NH.****

Archive:  /media/AWUS036NH/autorun.exe
[/media/AWUS036NH/autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/AWUS036NH/autorun.exe or
          /media/AWUS036NH/autorun.exe.zip, and cannot find /media/AWUS036NH/autorun.exe.ZIP, period.

I'm using an HP laptop, AMD E-350 1.7 GHz.

---

### Post by MG&amp;TL on 2011-10-26
About the CD:

No, anything that does not specifically say that it won't work with ubuntu, will not. You might want to look at wine(a program that enables you to run some windows programs):

1. Press Ctrl-Alt-T
2. Type:

```
sudo apt-get install wine
```

and consult the wine appdb to see if your program works:

[http://appdb.winehq.org/]("http://appdb.winehq.org/")

Then run the setup program in wine.

About the driver: type "additional drivers" into the unity bar, then see if there's anything of use in there.

---

### Post by haqking on 2011-10-26
> **timcd100 said:**
> I'm an absolute beginner who just downloaded Ubuntu 11.10 a few days ago. I downloaded it from this site: [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) and used the first bitTorrent link. 

When I put in the CD for Encyclopedia Brittanica ([http://www.amazon.com/gp/product/1615354336](http://www.amazon.com/gp/product/1615354336)) and click the CD icon, then click the autorun.exe file it gives me this error message:

Archive:  /media/BritannicaDVD/autorun.exe
[/media/BritannicaDVD/autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/BritannicaDVD/autorun.exe or
          /media/BritannicaDVD/autorun.exe.zip, and cannot find /media/BritannicaDVD/autorun.exe.ZIP, period.

The product description says Platform:**** Windows Vista /  7 /  2000 /  XP, Mac OS X. Does this mean it won't work with Ubuntu?
---------------------------------
---------------------------------
Also, when I try to install, from the CD, the driver for this wifi antenna [http://www.amazon.com/gp/product/B001O9X9EU](http://www.amazon.com/gp/product/B001O9X9EU) (ie when I click any of the exe files like above) it gives me the following message. 

****NOTE: this product's description says this: Includes driver for Windows 2000, XP 32/64, Vista 32/64, Windows 7,  Linux (2.4.x/2.6.x), Mac (MacOS 10.3 - 10.5) For MAC OS 10.6.7 and later  version, we suggest AWUS036NHR, AWUS036NH, AWUS036NEH, AWUS051NH.****

Archive:  /media/AWUS036NH/autorun.exe
[/media/AWUS036NH/autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/AWUS036NH/autorun.exe or
          /media/AWUS036NH/autorun.exe.zip, and cannot find /media/AWUS036NH/autorun.exe.ZIP, period.

I'm using an HP laptop, AMD E-350 1.7 GHz.

from the links provided:

Platform: Windows Vista / 7 / 2000 / XP, Mac OS X

Though it may work using WINE, i dont have any direct experience of this product other than Linux is not on the supported platforms

.exe are windows executables, WINE may support them but you will have to look at that

---

### Post by audiomick on 2011-10-26
OK, you can't install any files of the type .exe at all in any Linux OS (or MacOS ). They are only for windows.

Don't know what you can do about the Brittanica. Don't know if they have a Linux version. Maybe someone else knows if it perhaps would run in Wine?
[http://en.wikipedia.org/wiki/Wine_%28software%29](http://en.wikipedia.org/wiki/Wine_%28software%29)

Wine is available in the software centre, I believe. I have never used it, though, so I can't help there.

As far as your wi-fi drivers go, as I said, the .exe is no help. Is there not a "read me" or something on the CD with instructions about the Linux driver?

---

### Post by MG&amp;TL on 2011-10-26
[http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397]("http://www.alfa.com.tw/in/front/bin/ptlist.phtml?Category=105397")

If you're lucky.

You got the cd from the alternate site? Why? Do you have a desktop environment?

---

### Post by audiomick on 2011-10-26
> **MG&TL said:**
> 
You got the cd from the alternate site? Why? 

I think that page is the way to the bit torrent that the OP referred to. It doesn't mean that he used the alternate installer, I believe.

---

### Post by Mark Phelps on 2011-10-26
Here's the WineHQ page:  [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6538]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=6538")

Scroll to the right of the page and click on the Test Results to see what others have done.

And in future, check the WineHQ before you attempt to install any Windows app.  It could save you a lot of time.

---

### Post by MG&amp;TL on 2011-10-26
> **audiomick said:**
> I think that page is the way to the bit torrent that the OP referred to. It doesn't mean that he used the alternate installer, I believe.

Oh. okay, scratch that. Thanks. :)

---

### Post by oldos2er on 2011-10-26
Depends on which version you have, but I wouldn't expect it to run: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6538](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6538)

---

### Post by timcd100 on 2011-10-27
> **MG&TL said:**
> About the CD:

No, anything that does not specifically say that it won't work with ubuntu, will not. You might want to look at wine(a program that enables you to run some windows programs):

1. Press Ctrl-Alt-T
2. Type:

```
sudo apt-get install wine
```and consult the wine appdb to see if your program works:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Then run the setup program in wine.

About the driver: type "additional drivers" into the unity bar, then see if there's anything of use in there.

Thanks for the help guys. But when i try to install wine and get to this dialog box :"END USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE" and I press ENTER nothing happens. It gives the option for <OK> but nothing happens even if I click it with the cursor.

---

### Post by MG&amp;TL on 2011-10-27
Does it look like this? (random image, not relevant to subject in particular)

[http://www.google.co.uk/imgres?q=ncurses+interface&um=1&hl=en&client=opera&sa=N&rls=en-GB&channel=suggest&tbm=isch&tbnid=JXVhF8SrEaeQbM:&imgrefurl=http://harishankar.org/blog/entry.php/biaweb-ncurses-interface-screenshots&docid=XnalBEVxP52AnM&imgurl=http://harishankar.org/blog/images/screens/biaweb/BiaWeb-main.png&w=640&h=408&ei=l56pTvfzBY268gOA_vWGDA&zoom=1&iact=rc&dur=500&sig=113880833687312894665&page=1&tbnh=101&tbnw=159&start=0&ndsp=19&ved=1t:429,r:18,s:0&tx=80&ty=75&biw=1366&bih=587]("http://www.google.co.uk/imgres?q=ncurses+interface&um=1&hl=en&client=opera&sa=N&rls=en-GB&channel=suggest&tbm=isch&tbnid=JXVhF8SrEaeQbM:&imgrefurl=http://harishankar.org/blog/entry.php/biaweb-ncurses-interface-screenshots&docid=XnalBEVxP52AnM&imgurl=http://harishankar.org/blog/images/screens/biaweb/BiaWeb-main.png&w=640&h=408&ei=l56pTvfzBY268gOA_vWGDA&zoom=1&iact=rc&dur=500&sig=113880833687312894665&page=1&tbnh=101&tbnw=159&start=0&ndsp=19&ved=1t:429,r:18,s:0&tx=80&ty=75&biw=1366&bih=587")

If so, that's a curses interface. You press the TAB key until the red bit is on the OK button, then press RETURN

---


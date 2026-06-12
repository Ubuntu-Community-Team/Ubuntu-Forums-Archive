---
title: "Canon Pixma MG3220 - no color?"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by reginaterrae on 2013-07-15
Hi, all.  There doesn't seem to be a driver available for this printer, so I used the one for the MG3100 (as someone did in this thread - [http://ubuntuforums.org/showthread.php?t=2073046](http://ubuntuforums.org/showthread.php?t=2073046)).  Unlike that user, my test page came out all grayscale.  Help?  

EDIT: *sigh* I also just realized I still have it connected via USB, and it's not finding it wirelessly. I have no idea what the URI is, or even if that's the right term for what I need to tell it so it will find the thing wirelessly.

(I installed Ubuntu via Wubi.  The printer works fine on the Windows side. I can even print - in color - from my Droid, using Google Cloud Print).

There must be some website that gives instructions to us REAL Absolute Beginners....  I love the concept of Linux. I hate the commercialism of Windows, but AGH how do I figure out how to use it??

---

### Post by pdc on 2013-07-16
Hi there reginaterra; 

Canon Europe provide drivers for the 3200series devices................ 

so if you go here

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994521&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994521&page=1&type=download)

you download the [COLOR="#008000"]cnijfilter-mg3200series-3.80-1-deb.tar.gz
[/COLOR]
as with all the drivers Canon are releasing; there is the same format; but if I suggest some commands

(if you copy and paste into a terminal.........I suggest using the top line of a terminal.........ie [COLOR="#008080"]File[/COLOR] at top-left and along to [COLOR="#008080"]Edi[/COLOR][COLOR="#008080"]t[/COLOR] and thence to [COLOR="#008080"]Paste[/COLOR])

> [COLOR="#FF0000"]cd Downloads[/COLOR]

> [COLOR="#FF0000"]tar -zxvf cnijfilter-mg3200series-3.80-1-deb.tar.gz[/COLOR]

> [COLOR="#FF0000"]cd cnijfilter-mg3200series-3.80-1-deb[/COLOR]

> [COLOR="#FF0000"]sudo ./install.sh[/COLOR]

............that should give you the driver installed

Canon provide a utility to change settings on the printer: if you copy and paste

> [COLOR="#FF0000"]cngpij -P MG3200USB[/COLOR]

that should give you an interface to tweak things.........set up a launcher to have an icon to click............let me know if you want a how-to for this

_____________________________________________________________

SCANNER: Canon provide [COLOR="#0000FF"]**ScanGearMP**[/COLOR] to run your scanner

go here [http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994543&page=1&type=download)

to get the [COLOR="#008000"]scangearmp-mg3200series-2.00-1-deb.tar.gz[/COLOR] 

If you close; and open your terminal, and run the commands as above; substituting scangearmp-mg3200series-2.00-1-deb.tar.gz it should install [COLOR="#0000FF"]**ScanGearMP**[/COLOR]

run it with 

> [COLOR="#FF0000"]scangearmp[/COLOR]

and again create a launcher

________________________________________________

happy to give more details if not enough provided to be of help

---

### Post by reginaterrae on 2013-07-17
Thank you so much!  Sorry to be a little slow responding.  I haven't been able to try your suggestions yet, but will within the next few days and I'll post back on how it works for me.

except....  I don't even see how to get to the terminal!  This seems weird, but where's the command line?

---

### Post by pdc on 2013-07-18
> I don't even see how to get to the terminal! This seems weird, but where's the command line? 

check this out

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

all you ever wanted to know about the terminal!!

---

### Post by reginaterrae on 2013-07-18
Bless you! That will take me far.  

I know the intro to "absolute beginners" says "there are no stupid questions", but I feel like one of those users who doesn't even try to figure it out on their own first -- like I should be able to figure some of this stuff out myself.  But thanks to you all on ubuntuforums.org, maybe I will get the hang of this, and escape Microsoft eventually!

---

### Post by reginaterrae on 2013-07-18
OK, the default for downloads was "open with archive manager", which screwed me all up.... anyway I finally re-downloaded and chose "save file", and then the rest worked.

And i have a test page printed in color!  Yay!  Haven't tried scanning yet. I'll let you know how it works!

---

### Post by reginaterrae on 2013-07-18
> **pdc said:**
> 
that should give you an interface to tweak things.........set up a launcher to have an icon to click............let me know if you want a how-to for this
________________________________________________

happy to give more details if not enough provided to be of help

This ... I would appreciate it.  I did that and chose "usb" but actually I want this printer to work wirelessly, so I need to be able to tweak things....


I remember first getting Windows at work, about 25 years ago, and how annoying I found it and wished I could have DOS command-line control back.  I'm sure I can do this, if I can just be patient enough with myself to learn it!  Very grateful for your help.

---

### Post by pdc on 2013-07-18
> but actually I want this printer to work wirelessly, so I need to be able to tweak things....

...............the printer needs to be connected.........wirelessly............to your router first.............. then you can run the install of the printer driver where you opt for a wireless install;

...........I would recommend a USB install first; use the printer and then research a wireless connection

if you follow the scangearmp instructions, you can use the scanner side too: it also works well

---

### Post by reginaterrae on 2013-07-19
? It's connected to my router, not wirelessly but via Ethernet.  The router is what connects wirelessly to the computer.  Right?  I'm able to print wirelessly on the Windows side, and even from my Droid phone via Google Cloud Print.  I'm sure I'll want the scanner sometime, but actually most images I want to transfer to the computer are already on a digital camera or phone, so it's not as useful as it used to be.  I have phone apps to send docs to my bank, my insurance company, and even Samsung for when I recently had to send my camera for warranty service....

All right, I've decided I am going to jump into this thing with both feet and LEARN LINUX.  I can be productive in Windows meanwhile, for anything I haven't figured out yet in Linux.  I really want to understand it and take back the control of my computer.  It's kind of exhilarating!  These forums are awesome -- pdc, you're the best, you've gotten me started.  Now I'm beginning to study this, one of the links on that Using the Terminal thread you pointed me to: [http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224)   

More recently than switching from DOS to Windows, I remember how gratifying it was to use SQL to query our very large, multiple databases at my old job -- they were actually still on one of those fossil giant *mainframe* computers up to 7 or 8 years ago!  And how sorry and frustrated I was when they finally transitioned to Crystal reports, and I didn't have access to create reports, so I couldn't just go in and look for information on the fly any more.  I'm lazy, but I despise dumbed-down computing ... learning Linux will be good for my brain!  (I installed "gbrainy", but to hell with that, I'll exercise my brain with something useful) :D

Anyway, thanks again, pdc, for the encouraging help.

---

### Post by pdc on 2013-07-20
>  It's connected to my router, not wirelessly but via Ethernet.

well then when you run the install script, it should offer you 

1) USB or 
2) network

and if you select network, it should find the printer

If you want to delete the drivers you have already installed, the command from MG3200 series guide is 

> [COLOR="#FF0000"]sudo cnijfilter-mg3200series-pkgconfig.sh --uninstall[/COLOR]

you would then re-run the commands, and the install.sh script will offer you as above; and you can select network

If you want to verify what I say, go here

[http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994555&page=1&type=download](http://www.canon.co.uk/Support/Consumer_Products/products/Fax__Multifunctionals/InkJet/PIXMA_MG_series/PIXMA_MG3240.aspx?DLtcmuri=tcm:14-994555&page=1&type=download)

if you open with Archive Manager and [COLOR="#0000FF"]Extract[/COLOR] to your desktop, you open the file index.html and it opens in Firefox; it blinks to show you it has loaded in Firefox

---

### Post by pdc on 2013-07-20
> It's connected to my router, not wirelessly but via Ethernet.

I don't think so

[http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/photo_all_in_one_inkjet_printers/pixma_mg3220#Specifications](http://www.usa.canon.com/cusa/consumer/products/printers_multifunction/photo_all_in_one_inkjet_printers/pixma_mg3220#Specifications)

it can be usb or wireless

Standard Interface	Wireless LAN (IEEE 802.11b/g/n)
Hi-Speed USB

---


---
title: "Currently testing live version of ubuntu:D (First session)"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by Kestol on 2008-05-08
So here i am.. Running the live version of ubuntu...
Ok.. It's not as fast as it should be.. But well.. It is running through my CD drive.. So that is ok:)

I noticed a few things and of course some questions came up :D

1. Why do the password **** dots have such a huge size? :P (Little thing)
2. Visual effects cant be activated:S.. Because i'm running the live version?
3. How do i check my geforce go 7400 has been detected and is funtioning proberly?
4. I cant mark a sentence or something using shift home if i am at the ending of a sentence:S

Quick Question: After trying the Live version.. Nothing is stored on my laptop? right.. No ubuntu files or temp files? All are cleared.. Right?

That's all for now.. Testing it more atm;)

---

### Post by Joeb454 on 2008-05-08
I'm pretty sure #2 and #3 are related. It's probably because your graphics card drivers are not enabled that the Visual Effects cannot be enabled :) And I don't think you can install the drivers on a Live Session (as they require a reboot).

And Live CD's leave no files on your laptop that I'm aware of, I've never found any :)

---

### Post by Kestol on 2008-05-08
okay... Thanks for the answer:)

But still:

I cant mark a sentence or something using shift home if i am at the ending of a sentence:S

and 

I cant write a "@" using ctrl+alt... I have to use the button Alt Gr for that.. Why?

---

### Post by Joeb454 on 2008-05-08
Sounds like you've not got the correct keyboard layout set. From the Menu Bar at the top of your screen, click System > Preferences > Keyboard

You should be able to change the layout from there :)

---

### Post by Fenris_rising on 2008-05-08
it may not have detected your keyboard correctly or if you did it manually you may have misinformed it of the type.

---

### Post by Kestol on 2008-05-08
Well i went to keyboard preferences and choosed my layout by country...
Since "Denmark" stood there i believed it was correct...
And i tryed to add and run the test where u see a virtual keyboard...
Every button worked as it should...
But still the commands ctrl+shitf+2 dont give me = @
And the shift+home button cant mark a line... :S

---

### Post by Joeb454 on 2008-05-08
Hmm that is odd...do you have a different keyboard you could try to see if this solves the problem, if it doesn't we can rule out a faulty keyboard :)

Also I thought most places was Shift + 2 for the @ symbol, not Ctrl + Shift + 2. That said I've never been to Denmark ;)

---

### Post by Kestol on 2008-05-08
Well.. I dont have a spare keyboard atm... But still the combinations works under Vista  :)

But well... shift+2 gives " on a danish keyboard.. 
But it should work.. Unless danish keyboards arent supported fully... But i dont believe that either.. Since the danish buttons "æøå" work perfectly...

---

### Post by Joeb454 on 2008-05-08
Ah....

Are the character's 2 " AND @ on the same key?

If so then that is why Alt Gr is necessary - on my number 4 key I have $ and &#8364; (the latter requires Alt Gr)

---

### Post by Kestol on 2008-05-08
Yes they are on the same key... :)
That is why is wanted to use ctrl+alt
since that combination works under Win:)
But i believe it doesnt work under linux then? and i have to use alt gr instead :)

---

### Post by Joeb454 on 2008-05-08
I think Alt Gr is the best way to do it for now (for a start it's less keys ;)) I believe that would also work under Windows.

I'm slightly inclined to believe it is a software modifier for Windows as well, though I will look into seeing if you can change it under Ubuntu :)

---

### Post by hyper_ch on 2008-05-08
Swiss German keyboard:

AltGr - 2 for @
AltGr - e for &#8364;
AltGr - 1 for |

---

### Post by Kestol on 2008-05-08
Before u said the reason i couldnt activate visal effects was because my graphic card cant be detected proberly in the live version...

But where am i able to check that?
Where can i c if my graphic card is accepted and detected?

---

### Post by hyper_ch on 2008-05-08
you got a nVidia card... they are little hassle normally... and besides, it works right now, right? Just not to its full potential...

---

### Post by Joeb454 on 2008-05-08
I think you would be able to find it under System > Administration > Hardware Drivers :)

Also you could do ```
lspci
``` in a terminal, though there is a lot of text to read if you do that :p

---

### Post by Kestol on 2008-05-08
Well... Yes i got a Nvidia card.:)
But i dunno if it works as it should...
Since i dont know where to c if Ubuntu has detected my card proberly and uses it proberly... I can run a screen resolution of 1280x800...

---

### Post by Kestol on 2008-05-08
I went to the hardware drivers menu... But it says no proprietary drivers are i use :(

and where can i write the code u gave???
I cant seem to find a terminal :confused::lolflag:

---

### Post by Joeb454 on 2008-05-08
Applications > Accessories > Terminal :)

---

### Post by GreenB on 2008-05-08
yeah, you are right, i can't use the Ctrl+shift+2 to ma a @ , then i did learn something new today(and its on a danish keyboard), but i havn't had any trouble with the shift+home (or shift + arrow or end) to mark text, unless i am working in emacs.
when it comes to the the geforce it looks like it's supported but it might be a bit buged, try to take a look at the [nvnews ]("http://www.nvnews.net/vbulletin/showthread.php?t=112769")
and i think you have to install ubuntu before you can get the compiz visual effect to work, but anyhow, i dont think you are going to regret installing ubuntu, it's a very nice system...

---

### Post by Kestol on 2008-05-08
AAAH... This is what i get...

> ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
06:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
06:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ 


My graphic card is listed.. But why isnt it listed in the hardware menu then?

---

### Post by Joeb454 on 2008-05-08
I'd imagine it's just because you are running from the Live CD. It would be pointless getting you to install drivers on the Live CD - as graphics drivers will require a reboot to be installed.

If you reboot you'll be back where you started ;)

---

### Post by Kestol on 2008-05-08
Ok thx:)

But got a serious problem now!!!
I wanted to shut down the OS.. and well i did...
But now it seems as it has frozen on the screen where u see the ubuntu logo and a status bar beneath it...

It's frozen on the right side around 1/3 of the status bar...
And also the num lock light is blinking all the time...

Why? xD

Seems like i have to do a hardreset of my comp or what it is called... But well it shouldnt hurt anythin on my comp since nothing is being used right???

---

### Post by Joeb454 on 2008-05-08
It shouldn't.

I don't know why the numlock light would flash either, are there any messages on the screen? Usually there would be one asking you to take out the disc and close the tray (if any)

---

### Post by Kestol on 2008-05-08
nope... No messages... Only the logo+ubuntu word.. And the statusbar with 1/3 orange fill on the right side...

---

### Post by Kestol on 2008-05-08
Btw...

Is flash supported in Linux+firefox?
Does it run as smooth as it should?

---

### Post by Joeb454 on 2008-05-08
It is supported, and it runs ok :)

Though most people (including myself) have found it to run a lot better on Windows (still using Firefox/Flash 9). I think there's a bug open at Adobe about this though

---

### Post by Kestol on 2008-05-08
Well..As long as most flash things work without lag i'm happy :D

Btw.. 
I've read alot about wine... But well.. I've been to WineHQ or what the site it's called.. And it tells about some games appz that work out of the box with wine... With that.. Do they mean i dont have to use any codes or commands to get those programs working?

---

### Post by shae on 2008-05-08
You will still have to use terminal to install a game.  After that you can make a launcher.  But using wine is easy:

```
wine /path/to/installer.exe
```

---

### Post by Joeb454 on 2008-05-08
You don't **have** to use the terminal to run exe files.

98% of Wine installs I've done have all allowed me to simply double click the exe files :)

---


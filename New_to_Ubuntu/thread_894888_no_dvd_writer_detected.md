---
title: "no dvd writer detected"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by ferari on 2008-08-19
does anybody knows why when i try to burn a dvd i get the message no dvd writer detected. i'm currently using a hp pavilion ze4300 equipped with an internal dvd rom.

and if nothing else works would purchasing an external drive be an option for me?

---

### Post by halitech on 2008-08-19
open a terminal and type in
```
hdparm -i /dev/dvd
```
it should bring back (hopefully) information like this

```
daryl@ubuntu:~$ hdparm -i /dev/dvd

/dev/dvd:

 Model=HL-DT-STDVD-RAM GSA-H22L                , FwRev=1.00    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

daryl@ubuntu:~$ 

```

---

### Post by nicedude on 2008-08-19
I looked up your laptop and it looks like it just has a DVD/CDRW combo drive,  A DVD ROM drive is a DVD reader only while the CDRW means it can burn CD's and burn rewritable CD's. So it looks like you don't have a DVD burner just a DVD reader.

And yes buying a portable DVD burner would be the easiest option for a laptop to add this functionality to it.

---

### Post by ferari on 2008-08-19
> **nicedude said:**
> I looked up your laptop and it looks like it just has a DVD/CDRW combo drive,  A DVD ROM drive is a DVD reader only while the CDRW means it can burn CD's and burn rewritable CD's. So it looks like you don't have a DVD burner just a DVD reader.

And yes buying a portable DVD burner would be the easiest option for a laptop to add this functionality to it.



Thanks, this makes alot of sense and something i was thinking bout doing sooner or later, looks more like sooner.

---

### Post by ferari on 2008-08-19
> **halitech said:**
> open a terminal and type in
```
hdparm -i /dev/dvd
```
it should bring back (hopefully) information like this

```
daryl@ubuntu:~$ hdparm -i /dev/dvd

/dev/dvd:

 Model=HL-DT-STDVD-RAM GSA-H22L                , FwRev=1.00    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode

daryl@ubuntu:~$ 

```

sorry,not familiar with opening a terminal. how do you open?

---

### Post by halitech on 2008-08-19
Applications - Accessories - terminal

---

### Post by nicedude on 2008-08-19
To open a terminal you can go to Applications -> Accessories -> Terminal

I would drag that terminal icon up to the top menu bar and thereby create a shortcut as well so it is always handy :-)

---

### Post by halitech on 2008-08-19
> **nicedude said:**
> I would drag that terminal icon up to the top menu bar and thereby create a shortcut as well so it is always handy :-)

I thought of that as I clicked on post, seems like something new people seem to use a lot around here :)

---

### Post by nicedude on 2008-08-19
I thought of that as I clicked on post, seems like something new people seem to use a lot around here

I dont understand what you mean? do you mean only newbies use the terminal? Or that dragging something to the top menu bar is a newbie way of making a shortcut? Its the easiest way to make a shortcut I know of since it takes sub one second to do, if you have a millisecond way to make shortcuts please let me know :-)

---

### Post by halitech on 2008-08-19
what I meant was when people ask for help in here (normally new people but not always) they get an answer that requires them to open a terminal so having it as a shortcut on the top menu makes sense so they have quick easy access to it :)

I added a bunch but I use the right click on the tool bar and add to option cause I had a few apps I wnated up there :)

---

### Post by ferari on 2008-08-19
> **nicedude said:**
> To open a terminal you can go to Applications -> Accessories -> Terminal

I would drag that terminal icon up to the top menu bar and thereby create a shortcut as well so it is always handy :-)

thanks,I think i did it correctly and after it searching got message-no match found..

---

### Post by nicedude on 2008-08-19
Oh I see what you meant now, I thought you were calling me a noob ( which I kinda am but a very intelligent noob :-) ). I create launchers too if the program in question I want to use isn't in one of the pulldowns and instead requires launching in a terminal. I also love nautilus scripts manager which gives me right click access to scripts I write so that I can do cool stuff quick like launching my wifi into managed or monitor mode with or without faked MAC etc.

---

### Post by halitech on 2008-08-19
> **ferari said:**
> thanks,I think i did it correctly and after it searching got message-no match found..

huh? no match found? unless you only have a cd rom/burner it should have at least given info about the dvd reader part of things

---

### Post by halitech on 2008-08-19
> **nicedude said:**
> Oh I see what you meant now, I thought you were calling me a noob ( which I kinda am but a very intelligent noob :-) ). I create launchers too if the program in question I want to use isn't in one of the pulldowns and instead requires launching in a terminal. I also love nautilus scripts manager which gives me right click access to scripts I write so that I can do cool stuff quick like launching my wifi into managed or monitor mode with or without faked MAC etc.

no, I wouldnt do that without knowing you better ;)  I don't like stuff on my desktop but I find they are nice and neat up there and I only have about 6 things I use alot so thats all I keep handy, everything I just go to the menu for.

---

### Post by nicedude on 2008-08-19
If you got a no match found with hdparm -i /dev/dvd then your device probably isn't called dvd, to see what yours is called you could look in /dev/ and see what yours is called

RUN THIS IN TERMINAL AND IT WILL OPEN UP YOUR DEV FOLDER
nautilus /dev

without root write access of course so you won't mess anything up by looking. When you see what your drive is called you can just substitute the dvd in /dev/dvd for whatever your device is called and get some output from that command but I am 99% sure you have a read only DVD drive. 

Does your drive read DVD's correctly? If not then that is a problem.

---

### Post by ferari on 2008-08-19
> **nicedude said:**
> If you got a no match found with hdparm -i /dev/dvd then your device probably isn't called dvd, to see what yours is called you could look in /dev/ and see what yours is called

RUN THIS IN TERMINAL AND IT WILL OPEN UP YOUR DEV FOLDER
nautilus /dev

without root write access of course so you won't mess anything up by looking. When you see what your drive is called you can just substitute the dvd in /dev/dvd for whatever your device is called and get some output from that command but I am 99% sure you have a read only DVD drive. 

Does your drive read DVD's correctly? If not then that is a problem.

does this information help some?

Drive	D:
Description	CD-ROM Drive
Media Loaded	No
Media Type	CD-ROM
Name	MATSHITA UJDA720 DVD/CDRW
Manufacturer	(Standard CD-ROM drives)
Status	OK
Transfer Rate	Not Available
SCSI Target ID	0
PNP Device ID	IDE\CDROMMATSHITA_UJDA720_DVD/CDRW_______________1.01____\5&2A87669&0&0.0.0
Driver	c:\windows\system32\drivers\cdrom.sys (5.1.2600.2180 (xpsp_sp2_rtm.040803-2158), 48.38 KB (49,536 bytes), 8/29/2002 4:00 PM)

---

### Post by halitech on 2008-08-19
info from windows? ;)

that to me makes it look like a dvd reader and cd burner

---

### Post by ferari on 2008-08-19
> **halitech said:**
> info from windows? ;)

that to me makes it look like a dvd reader and cd burner

yes windows. so does that confirms that i do need to get a dvd burner.
ty

---

### Post by nicedude on 2008-08-19
Yes ferri that confirms that you have a DVD read only drive which means it won't burn DVD's it should however be able to read DVD's. So if you want to burn DVD discs then you will need to buy a portable DVD burner to do so.

---

### Post by halitech on 2008-08-19
> **ferari said:**
> yes windows. so does that confirms that i do need to get a dvd burner.
ty

no, you dont "need" to get a burner but if you have any movies to burn or large files to back up it might be an idea ;)

---


---
title: "dvd drive doesn't recognize dvds?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by alloftheabove on 2008-07-25
Hello, it's been a while since I've had a problem worth posting here.  I have the unfortunate problem that my dvd-ram drive recognizes cds, data, music, and even can be used to boot off a cd with no problems.  However, it will not recognize blank dvd-r media or any other kind of dvd.

It is a LG HL-ST-DT GMA-4020B

If there is need for typing in a command or two into terminal than I'm sorry that I can't do it yet, I forgot which commands people use here...So I just need a gentle reminder.  I will be on the rest of the day.

Oh, and I heard somewhere that you can flash cd and dvd drives?  Region-free?  Does that even apply here ( although I do live in the us... )?

EDIT:  What does dvd-ram even mean??

---

### Post by LowSky on 2008-07-25
[http://www.digit-life.com/articles2/lg4020/index.html](http://www.digit-life.com/articles2/lg4020/index.html)
thats the drive correct? I checked LG's website and nothing comep about it..very odd!
But that review does state it can play and write DVDs...hmmm

to answer one question
DVD-RAM was a type of rewritable DVD, like -RW, and +RW. Although no definative victor the RAM version was the biggest loser, as few use or support the fomat.
More info here
[http://en.wikipedia.org/wiki/DVD-RAM](http://en.wikipedia.org/wiki/DVD-RAM)

---

### Post by alloftheabove on 2008-07-25
Thank you for answering my question.  And when I have my dvd-ram drive selected in k3b, and I check its properties, it says it can write dvd-r(w) discs.  Odd.

---

### Post by LowSky on 2008-07-25
Its not odd as the device can and should support it and a few others shown here
> Specification 

Interface: E-IDE/ATAPI 
Read speed: 
CD-ROM/R: 32x Max. 
CD-RW: 24x Max.  
DVD-ROM: 10x Max.  
DVD-R/RW: 8x Max.  
DVD+R/+RW: 8x Max.  
DVD-RAM: 2x, 1x 

Write speed: 
CD-RW: 8x, 4x  
CD-R: 12x, 8x, 4x  
DVD-RW: 1x  
DVD-R: 2x, 1x  
DVD-RAM: 2x, 1x 

Formats supported: 
DVD: DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW, DVD-RAM 
CD: CD-ROM, CD-ROM XA, CD-DA, CD-Extra, CD-Text, CD-R (Orange Book Part 2), and CD-RW (Orange Book Part 3), Supports High Speed Disc Media, Reads Photo CD (Single and Multi-Session), Reads CD-I and Video CD  

You could have a bad drive or bad discs, but it could also be the data cable that hooks the drvie to the motherboard.

---

### Post by alloftheabove on 2008-07-25
No, I tried both data cables, it does the same thing.  How can it read cds and not dvds?  Very curious....

---

### Post by alloftheabove on 2008-07-25
Is there such a thing as locking a drive for certain formats?

---

### Post by LowSky on 2008-07-25
What kind of DVDs, Movies? You may just need a simple plugin for that
For movie playback open up a terminal window and type the commands (or copy and paste) one after the other

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install w32codecs
```

reboot computer and see if everything works

---

### Post by alloftheabove on 2008-07-25
No I mean recognizing that there's even a blank dvd in the drive.  It recognizes any kind of cd but it won't recognize dvds period.

---

### Post by alloftheabove on 2008-07-25
Could there be some sort of settings file on the dvd drive or on ubuntu that might prevent recognizing dvds?

---

### Post by alloftheabove on 2008-07-25
I need to bump.

---

### Post by sydbat on 2008-07-25
This happened to me too. Turned out to be the DVD drive failed...physically. Would recognize CD's but not DVD's. I dual-boot with XP and checked...same thing. I had to buy a new DVD-RW. Not a big deal, as they are really affordable ($32 for a Samsung Lightscribe 20X)...unless it's at Futureshop/Best Buy, then it's minimum $100...

Oh yeah, my borked DVD-RW was the exact same as yours. I wonder if there was a bad batch that got out??

---

### Post by alloftheabove on 2008-07-25
Well I guess I'll have to save up my money then...

---

### Post by vdawg on 2010-01-20
I'm having the exact same issue.

Mine is an LG DVD/CD writer combo : HL-DT-ST DVD-RAM GSA-H55N

Here's the dmesg output
```

[    2.243956] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GSA-H55N 1.05 PQ: 0 ANSI: 5
[    2.247937] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.247939] Uniform CD-ROM driver Revision: 3.20
[    2.248028] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.248067] sr 2:0:0:0: Attached scsi generic sg1 type 5


```

When I put in a cd it detects them fine but nothing on dvds :(

Sucks royally coz I just burned a dvd only a few days ago!

---

### Post by mikechant on 2010-01-20
If I remember correctly, DVD operations use a seperate laser (different frequency) to CD operations, so this sort of failure is not that rare.
At least replacements are really cheap these days (less than $30/£20 last time I looked).

---

### Post by silentmonkey on 2010-02-28
I have a similar issue with a HL-DT-ST DVD-RAM GSA-T20N in my ASUS notebook.

However!  I can read/write to some/most blank DVDs and my problem is with the drive being able to recognise DVDs which have region protection - I can actually watch 'open region' DVDs without issue.

(Have you got a Region 0 DVD you could try to see if we have the same problem?)

Also, I have found through extensive testing that I can actually read *some* region protected DVDs.  These tend to be very old, though - I just got a 1999 Region 1 DVD working, for example.

I don't know at which point exactly these drives are having trouble and giving up, as I don't know a lot about the initial reading process, but perhaps this information will be helpful to someone one day =)

---

### Post by Abhinav K Sahdev on 2010-04-21
I have a pioneer DVD-RW DVR k-16 on my compaq presario v5202tu . the dvd drive does not give any response when i insert a dvd in it but when i put a cd it shows it as blank disk . i have tried with differnet video audio disks . same everywhere. in windows i tried to install an open region firmware on it. i even upgraded my bios. no response. but i tried to write with it on a blank cd an iso of about 5 mb . 4 mb data was written . i tried my friend's compatible working dvd drive with my laptop. surprisingly it did not work and showed same behaviour as this drive. on ubuntu 9.04 ( i m using 9.10) it could SOMEtimes read and write. its like it slowly died. what can be done about this .
<I M REALLY FRUSTRATED>

---


---
title: "[SOLVED] DVD input/output error"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Commander_Bob on 2008-05-29
I need to convert a DVD for an iPod but when I try to copy it I get an input/output error. I tried making an iso but the iso does the same thing. Also when I try to play the dvd the video is messed up. I am using Ubuntu 8.04.
Thanks,
Justin

---

### Post by OffAxis on 2008-05-29
Could be a bad disc or a filthy lens on the DVD player.

Have you tried a different DVD? Did it work?

---

### Post by didac on 2008-05-29
If you use Kubuntu, you can try [http://www.roadkil.net/downloads/unstopcp.gz](http://www.roadkil.net/downloads/unstopcp.gz) which will make an iso image of your dvd. The bad sectors will still be bad sectors, you'll still get garbage at times, but you can now convert the dvd to iPod.

If you have Ubuntu, and wine installed, you can get the windows version at [http://roadkil.net/download.php?File=unstopcp](http://roadkil.net/download.php?File=unstopcp)

---

### Post by Commander_Bob on 2008-05-29
I have tried it with six different DVDs, same problem. I will go and try it on my brothers computer. He has Ubuntu 7.10 so I won't know if it is a 8.04 problem or not.
Thanks,
Justin

---

### Post by Commander_Bob on 2008-05-29
I did not try the other computer yet but I tried a different movie and it works fine. The movie Talladega Nights works fine but I need to get Grey's Anatomy on for a friend, it has six discs all do the same thing. Any ideas on how to fix this?
Justin

---

### Post by mc4man on 2008-05-29
> Also when I try to play the dvd the video is messed upif you get your playback squared away then things should work. You could try installing vlc and then ck. that you have libdvdcss2 installed. If not add medibuntu to sources if not there already and install it.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Commander_Bob on 2008-05-29
Got it to work! Well I did nothing...

I had libdvdcss2 installed but I just got a notice from the update manager to update it! Now everything works perfect! Encoding the movie to mp4 now.

Thanks,
Justin

---

### Post by ravidborse on 2011-12-29
Hi All(Solved in my case)

  - To Resolve Below Error related to my Sony DVD-RW Just Remove your DVD-RW player.
  - In UBUNTU(10.10) you will get error related to Power Calibration Area Error. But in Fedora you
will get like shown below. You can use the below steps as mentioned below to resolve the error.
  - Open it with the screwdriver(Its very Easy). Now you can see the Reader-Writer Lense . 
  - [B]Take any solution(Prefer Alcoholic or the solution you use it to clean LCD) and cotton. 
  - Use a cotton swab and something like alcoholic solution(small) to gently wipe the lens. Just a quick scrub will do. [/B]
  - Dry the laser pickup lens with the other end of the swab.Keep it 10-15 Mins to dry that lens. 
  - Do this carefully Please. I have done it on my own risk. you can also. below is the error
  - **Write the CD/DVD at the very Lowest Speed.**


```
DVD-RW Sequential

Devices
-----------------------
SONY DVD RW AW-G170A 1.74 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 2.0.2
KDE Version: 4.5.5 (KDE 4.5.5)
QT Version:  4.6.3
Kernel:      2.6.33.3-85.fc13.i686.PAE

Used versions
-----------------------
growisofs: 7.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 2.0x1352KBps.
          0/669122560 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
=== last message repeated 20 times. ===
:-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/sr0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=4gms -use-the-force-luke=tracksize:326720 -dvd-compat -speed=2 -use-the-force-luke=bufsize:32m
```

---

### Post by overdrank on 2011-12-29
Hi and welcome, please view the date of the thread. Old thread = Closed thread.

---


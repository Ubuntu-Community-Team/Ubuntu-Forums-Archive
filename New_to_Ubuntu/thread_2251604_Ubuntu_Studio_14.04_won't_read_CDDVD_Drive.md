---
title: "Ubuntu Studio 14.04 won't read CD/DVD Drive"
date: 2014-11-05
forum: New to Ubuntu
---

### Post by dennispmccann on 2014-11-05
I started with 14.04 Trusty Tahr, upgraded to 14.10 Utopic Unicorn, then installed Ubuntu Studio 14.04. Alll in a month. Had the same problem with all 3. I simply can't read CD/DVD Discs. The drive is mounted, the discs spin up...then just stop. In 14.04 TT, it would tell me the discs were blank. in 14.10 and studio 14.04, it just does nothing. I've in stalled all the codecs I can find, but it didn't help. Any ideas?

---

### Post by sudodus on 2014-11-05
Welcome to the Ubuntu Forums :-)

There could be many causes of your problem: Hardware, software, aggressive copy protection.

- Can you read the same CD/DVD in another computer?
- Can you read the same CD/DVD in another operating system (Windows or MacOS)?
- Can you read some other kind of CD/DVD, for example an Ubuntu install disk as opposed to a multimedia disk (music or movie), or vice versa?

Maybe it works if you install the 'restricted extras'

```
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install lubuntu-restricted-extras
...
```

---

### Post by dennispmccann on 2014-11-05
I can read the disks on other computers, and in other Operating Systems (Windows, Mac). I can't read any disks at all in Ubuntu Studio 14.04. For the record, my drive is a TSSTcorpCDDVDW TS-L633Y TF20, and this is what the system tells me: Device /dev/sr0: no medium present

I already have all the restricted etras, but I don't think the problem is codecs. It won't even read a data CD.

---

### Post by sudodus on 2014-11-05
I have a TSSTcorp CDDVD SN-208AB(PM), and it works well with all versions of Ubuntu.

Did you check with Windows in this very computer? It is rather common  that optical drives fail (mechanically or electronically).

If it works with Windows, I think you are right. The problem seems to be that the Ubuntu family operating systems do not have drivers that cooperate with your optical (CD/DVD) hardware.

Did you try the previous LTS version, that is still supported, 12.04 LTS? It might work better, particularly if the CD/DVD hardware is old.

---

### Post by dennispmccann on 2014-11-05
It worked with Windows 8 a month ago before I switched to Ubuntu, so yeah, I think it might be a driver issue. I haven't tried 12.04, but I'm really happy with Ubuntu Studio 14.04 - and the real kicker is that I just want to get the data off these disks and then jettison them. I'm saving everything in flac or mkv on a 3Terabyte HDD. I guess I might have to use a different computer to do that, unless I can find a driver that works.

---

### Post by sudodus on 2014-11-06
You could boot for example ***Xubuntu 12.04 LTS*** from a USB pendrive and see if you could read from the optical drive.

You could also boot from other linux distros. ***Knopplix*** is known to be very good at recognizing hardware, so it is a good alternative in this case. Knoppix is made to run live or persistent live and to be used for 'repair jobs'.

Otherwise  I suggest to use a different computer, because it is probably not worthwhile to install Windows for this task. (And the hardware *might* be faulty.)

---

### Post by dennispmccann on 2014-11-06
This or any task... Good suggestions, but here's the wirdness that happened last night:  I popped some disks into my wife's computer. She's running Ubuntu  (not Studio) 14.04.1. Neverthess, same modules, codecs, and so on.

And the disks work. Well, for the most part.

4 DVD-R disks read just fine, but here's the weirdness - a 2 Disk CD-R  bootleg (Lou Reed!) .... Disk 2 read fine. Disk 1 says it's blank. Those  discs were burned at the same time using the same computer...

So what does this tell me? My Optical Drive is kaput (or maybe just dirty), hers works... and the universe is screwing with me.

---

### Post by coldcritter64 on 2014-11-06
Check the manufacturers website for firmware upgrades for that particular model of drive. 

I had a very similar case a few years ago with a drive acting nearly identical to what you are describing, was ok in vista etc but Ubuntu could not read the disks. A manufacturers firmware upgrade got Ubuntu working after that, but I did have to use vista to flash the drives firmware (the manufacturer only supplied windows tools). Good luck.

---

### Post by saphil on 2014-11-06
I had a situation where Kubuntu would read the disk, but the installed version of Ubuntu couldn't see the drive.

---

### Post by Feenix3k on 2015-02-20
My issue is with 14.10, it will play music cds. But not  video discs, it eathe plays the fbi warning and then stop. Or it says it can not read the disc if the dvd has no menu on the disc.

---

### Post by sudodus on 2015-02-21
@Feenix3k,

Did you install the **restricted-extras**? (See post #2)

Some DVDs have such copy protection systems, that a legally bought copy will not play in a linux computer. I don't know if it works better in Windows. But it works in a dedicated DVD player (that is not a computer).

---

### Post by typos1 on 2015-03-15
I ve had CD problems (cant burn cds as it does not recognise blank media as blank even though they ARE blank) since 14.04, they persist in 14.10, I thought my drive was shot.

My mum has ubuntu as well and she is having similar problems, just went round to sort it, it wont recognise any discs at all. 

Its not her drive or mine, its ubuntu - I googled the problem and there are loads of similar posts all over the net.

Think it should be registered as a bug.

I ve been using ubuntu for 6 years, I love it, I ve converted my mum to it, I m always annoying my friends when I go on about how good it is compared with their windows rubbish, or their overpriced Apple stuff, but even a died in the wool convert like me is noticing that ubuntu is becoming, well cr*p lately, its slow, dim-witted, laggy, buggy, disc drives dont work properly, there are loads of error messages when the machine is shut down (this on my mum's too, thought it was just my machine needing a fresh install, but hers does it as well). Things are going wrong, too many Canonical people concentrating on Touch maybe ? (although its still taken 4 years for that to properly surface).

---


---
title: "kickstart"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by Hacked N Nacked on 2012-04-08
i think i know the problem But not the answer  Help Please ..  how if possible do i remove fd0 i think its secret iso's from kickstart from what I read can i delete it and if so how?  Thanks

---

### Post by CharlesA on 2012-04-08
fd0 is usually a floppy drive.

---

### Post by Hacked N Nacked on 2012-04-08
ok so I have been hacked now can I remove /dev/loop0 and  fd0 isn't there some cmd to to do this

---

### Post by CharlesA on 2012-04-08
> **Hacked N Nacked said:**
> ok so I have been hacked now can I remove /dev/loop0 and  fd0 isn't there some cmd to to do this
The /dev directory and /proc directory are created at boot. Both /dev/loop0 and /dev/fd0 are part of the OS and shouldn't be messed with.

In short - you haven't been hacked.

Is this related to your [other thread]("http://ubuntuforums.org/showthread.php?t=1954293")?

---

### Post by Hacked N Nacked on 2012-04-08
Yes other thread related
right I deleted All partitions reinstalled vista then used boot DVD for latest ubuntu not the one in testing
Never installed went to disk manager and there was only my harddrive listed then 700mb whole disk squashfs auto mounting at dev  I looked in the 700mb disk thing there loads of scripts like make new dev none of them I own so can't format it also a ssd 288mb I don't have a floppy drive or SSD so I think I should not see These or have them  
Should I
Also the dns I'm using auto connect is not my ISP  so I think I got hacked

---

### Post by CharlesA on 2012-04-08
The squashfs entry is because you are booted off the install cd (also known as a livecd). Not sure what 288MB partition would be, but I know Vista does create a boot partition when it is installed.

What DNS service is shown?

There isn't any reason to believe you were hacked.

---

### Post by Hacked N Nacked on 2012-04-08
I can see the DVD drive that's a different drive 
the dns is 194.168.4 100 primary 194.168.8.100 secondary
I phoned my ISP and it's not there's 
just installed it now so I'll try and get screen shot posted if possible

---

### Post by CharlesA on 2012-04-08
That's virgin media's DNS.

[http://virgin.lithium.com/t5/Fibre-optic-broadband-cable/194-168-4-100/m-p/166839](http://virgin.lithium.com/t5/Fibre-optic-broadband-cable/194-168-4-100/m-p/166839)

---

### Post by Hacked N Nacked on 2012-04-09
Thank you Charles
so can you tell me why the Log is empty?
Also can you tell me if it's a legit iso?
Md5.c396dd0f97bd122691bdb92d7e68fde5
ubuntu-11.10-desktop-i386.iso
is that correct ?
And computer  janitor is empty also
the 700 mb USB disk is gone and the SSD to. 
Thanks again ! 
and sorry for being a complete NOOB 

NOOB

---

### Post by CharlesA on 2012-04-09
You can verify the md5sum here: [http://releases.ubuntu.com/oneiric/MD5SUMS](http://releases.ubuntu.com/oneiric/MD5SUMS)
c396dd0f97bd122691bdb92d7e68fde5 *ubuntu-11.10-desktop-i386.iso

Which log is empty?

---

### Post by Hacked N Nacked on 2012-04-09
The only one I find in installed apps
 . Log file viewer.
Is this correct I searched and only one I can find
if there is others how do I view them please
thanks Again !

---

### Post by CharlesA on 2012-04-09
Log file viewer should show you a list of logs on your local machine.

---

### Post by Hacked N Nacked on 2012-04-10
Thanks
ohh well I guess I'm OWNED then 
I reinstalled 11.10 wiping vista with md5 checked
Iso and still no logs
thanks Valis !!
I think I'll just give it up as a bad job.
thanks Charles A

---

### Post by CharlesA on 2012-04-10
If it's a clean install you should be fine.

---


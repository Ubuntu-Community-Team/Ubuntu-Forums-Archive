---
title: "DVD burning"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by 3dmatrix on 2013-08-12
I am facing problem while burning DVD. Its a strange problem, I am able to burn data CDs and have even able to burn CDs of downloaded iso but when i burn a DVD iso it does everything well and i can even visibly make out that it has been burnt but it is not readable. And the DVD becomes useless. I have ubuntu 12.04 and Ubuntu 13.04 on the same computer but face the same problem with both.

---

### Post by SlugSlug on 2013-08-12
try k3b instead

---

### Post by 3dmatrix on 2013-08-12
I have tried K3B, Brasero and Xfburn but they all face the same problem.

---

### Post by Benjamin Schizophrenia on 2013-08-12
maybe it's a hardware problem

---

### Post by mastablasta on 2013-08-12
it could be the dvd reading lense is faulty. i had similar problem on windows XP. there was no other solution but to replace the drive. they are cheap anyway...

---

### Post by varunendra on 2013-08-12
Have you tried minimum supported speed (4x or less)? Different brands of DVDs?

Laptop drives are weak by nature (they have to operate at low power), so if that is a laptop drive, it can be a problem too.

By the way, if the system can boot from USB, that is a better option anyway. If it can't, you can use "Plop" to boot a USB (burn the plop iso to a cd > boot with it > boot the Ubuntu live USB).

---

### Post by 3dmatrix on 2013-08-12
The drive can read all other DVDs and can also boot from them. It can even write data CD ! But the faulty DVDs written by the drive are not readable by other comp also. So there is some problem in writing not reading. I wish to know if such a parcial fault (can write data CD/DVD but not burn iso) can be possible ? I also tried burning an iso using Puppy linux but faced again the same problem. But i was able to burn an iso of simplicity linux (on cd). Can there be a problem with the amount of data that needs to be written ? Data DVDs and Simplicity linux iso are smaller in data size than Ubuntu / Mint. I have tried minimum writing speed but the problem persists.

---

### Post by varunendra on 2013-08-12
> **3dmatrix said:**
> Can there be a problem with the amount of data that needs to be written ?

No, it's not the amount of data. It's the nature of the operation that is a problem and is quite common.

Burning is always harder than reading a disc and both reading/writing are easier with CDs than with DVDs.

Burning requires a lot more power than reading a disc, and burning a DVD is much more harder than burning a CD, not due to the amount of data, but due to the physical properties of the material used plus the density of data which is about 6 times more than that of a CD (thus requiring 6 times more precision on the "Laser eye"). That's why burnt CDs usually last much longer than burnt DVDs.

A drive can perfectly read CD/DVDs for years, but even a new drive may fail to write correctly if it is getting weak (has done a lot of burning in a short amount of time) or can't get enough power for the burning operation (often returning "Power calibration error").

So what you are describing matches perfectly with a problem that is actually quite common with optical disc burners.

---

### Post by whitesmith on 2013-08-12
Sounds like bad media or defective hardware. Modern CDs hold <= 700 MB. Have you tried burning from a terminal? Check out [https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso) to rule out possibility that your burning SW is incompatible with your hardware.

---

### Post by 3dmatrix on 2013-08-12
> **whitesmith said:**
> Sounds like bad media or defective hardware. Modern CDs hold <= 700 MB. Have you tried burning from a terminal? Check out [https://help.ubuntu.com/community/MountIso](https://help.ubuntu.com/community/MountIso) to rule out possibility that your burning SW is incompatible with your hardware.

But it was the same software and hardware combination that was doing the job since more than 20 months !


.

---

### Post by 3dmatrix on 2013-08-12
> **varunendra said:**
> No, it's not the amount of data. It's the nature of the operation that is a problem and is quite common.

Burning is always harder than reading a disc and both reading/writing are easier with CDs than with DVDs.

Burning requires a lot more power than reading a disc, and burning a DVD is much more harder than burning a CD, not due to the amount of data, but due to the physical properties of the material used plus the density of data which is about 6 times more than that of a CD (thus requiring 6 times more precision on the "Laser eye"). That's why burnt CDs usually last much longer than burnt DVDs.

A drive can perfectly read CD/DVDs for years, but even a new drive may fail to write correctly if it is getting weak (has done a lot of burning in a short amount of time) or can't get enough power for the burning operation (often returning "Power calibration error").

So what you are describing matches perfectly with a problem that is actually quite common with optical disc burners.

Varunji, thanx for your advise. It seems my drive has become old. Buddha ho gaya ! But its just some 18 to 20 months old comp. Anyway, is there any temporary way like cleaning the lens etc that may help for some more time ? Actually i use the drive just for burning different linux distro iso and trying them out. In that case do you have any suggestion for doing the same on any SD Card ? Some software that could 'burn' any iso on a SD card. And will my comp be able to boot through a SD card ? It can do so through a USB pendrive. But last time i tried booting puppy linux through my SD card, but it did not work.

---

### Post by DuckHook on 2013-08-12
> **varunendra said:**
> ...a problem that is actually quite common with optical disc burners.Did not know this. Have experienced a number of these issues over the years, but this is the first time I have had the mystery solved so succinctly and completely. Thanks for sharing.

---

### Post by varunendra on 2013-08-12
> **3dmatrix said:**
> Buddha ho gaya !
Haha.... nice to meet a Hindi speaking friend around here :D

Age of the system/drive does not matter. What matters is its quality and how much writing it has done. A drive can last tens of years if is rarely used and just for reading 'Healthy, scratch-free' discs. But can expire within a few weeks if it has to do a lot of writing on DVDs. Even reading operation on too many dusty, old and scratched DVDs can dramatically reduce the life of the laser eye of an optical drive.

> is there any temporary way like cleaning the lens etc that may help for some more time ?
Cleaning the lense may help sometimes. It did for me once or twice. But handling the internal parts is not recommended unless you are familiar and comfortable with such things. Use a diluted non-petroleum product or just air pressure to cleanse the lense (and the reflective mirror/prism beneath it too, if it is easily accessible). I preferred nail-polish remover to clean optical discs/laser eye.

> do you have any suggestion for doing the same on any SD Card ? Some software that could 'burn' any iso on a SD card. And will my comp be able to boot through a SD card ? It can do so through a USB pendrive. But last time i tried booting puppy linux through my SD card, but it did not work.
SD cards should be able to boot. However, if it is an MMC card *(multimedia card, that is detected as "/dev/mmcblk**x**" or something similar instead of "/dev/sd**xx**")*, then a recent discussion in a thread here suggests that it may not bootable : [http://ubuntuforums.org/showthread.php?t=2159487&page=2](http://ubuntuforums.org/showthread.php?t=2159487&page=2)

Usually the first recommendation is "Unetbootin" to create live USB cards/flash drives. I personally prefer the native "Startup Disk Creator" application to do that. There are many other similar tools for both Linux and windows that let you create live USBs with live cd/dvd images.

---

### Post by varunendra on 2013-08-12
> **DuckHook said:**
> Did not know this. Have experienced a number of these issues over the years, but this is the first time I have had the mystery solved so succinctly and completely. Thanks for sharing.

You're welcome ! Glad you liked it. :)

---

### Post by 3dmatrix on 2013-08-13
> **varunendra said:**
> Haha.... nice to meet a Hindi speaking friend around here :D

Age of the system/drive does not matter. What matters is its quality and how much writing it has done. A drive can last tens of years if is rarely used and just for reading 'Healthy, scratch-free' discs. But can expire within a few weeks if it has to do a lot of writing on DVDs. Even reading operation on too many dusty, old and scratched DVDs can dramatically reduce the life of the laser eye of an optical drive.


Cleaning the lense may help sometimes. It did for me once or twice. But handling the internal parts is not recommended unless you are familiar and comfortable with such things. Use a diluted non-petroleum product or just air pressure to cleanse the lense (and the reflective mirror/prism beneath it too, if it is easily accessible). I preferred nail-polish remover to clean optical discs/laser eye.


SD cards should be able to boot. However, if it is an MMC card *(multimedia card, that is detected as "/dev/mmcblk**x**" or something similar instead of "/dev/sd**xx**")*, then a recent discussion in a thread here suggests that it may not bootable : [http://ubuntuforums.org/showthread.php?t=2159487&page=2](http://ubuntuforums.org/showthread.php?t=2159487&page=2)

Usually the first recommendation is "Unetbootin" to create live USB cards/flash drives. I personally prefer the native "Startup Disk Creator" application to do that. There are many other similar tools for both Linux and windows that let you create live USBs with live cd/dvd images.

Thanx buddy, lots of info. Well, i do not need to use the optical drive too much. As i mentioned, i just burn some iso to try different linux distros. So for that i would try using Unetbootin. Can Ubuntu's 'startup disk creator' make usb pen drives bootable even for non-ubuntu based iso ? Eg, can it use mint / fedora iso to make a USB drive / card bootable ? 

The second reason why i still use optical drive is to burn large printable files on a cd and transfer it to other (client's or public) PC. In such a case the chances of a virus infecting my system is not there as the optical drive is read only. but in a USB drive that is not the case. Some people suggested using the LOCK feature of SD cards. But that feature is not available in every card. So is there any better and more secure option ?

---

### Post by varunendra on 2013-08-14
> **3dmatrix said:**
> Can Ubuntu's 'startup disk creator' make usb pen drives bootable even for non-ubuntu based iso ? Eg, can it use mint / fedora iso to make a USB drive / card bootable ? 
Never tried that so can't say for sure. Better use the tools that are dedicated for that purpose and are able to customize the booting to suit the target distribution.

As for keeping safe from viruses, using a read-only media is the safest and using a live Linux USB is the next safest (but relatively cumbersome) option. I don't know of any better option.

I never plug-in my external drive in someone's computer unless they let me boot their system with the live or installed version of linux on it. However, pluging in other people's drives in 'my' computer is never a problem since I am permanently using Linux (Ubuntu) now. So even if it has viruses on it, they are just plain data files for my system that can't do any harm unless I intentionally try [really hard]("http://www.gnu.org/fun/jokes/evilmalware.html") to run them somehow ;). For systems of my friends and relatives, I always keep some live USBs handy.

---

### Post by 3dmatrix on 2013-08-14
Thanx Varun !

---

### Post by whitesmith on 2013-08-20
The critical question  you must  answer is this: what has changed? If something worked for 20 months, it defies logic to imagine it failing by itself. *Something* else has changed. You and you alone can answer what this variable is.

---

### Post by 3dmatrix on 2013-08-20
> **whitesmith said:**
> The critical question  you must  answer is this: what has changed? If something worked for 20 months, it defies logic to imagine it failing by itself. *Something* else has changed. You and you alone can answer what this variable is.

Not You and You alone can answer But
God and God alone can answer  OR
Samsung and Samsung alone can answer
because no one except me has access to my laptop. No children, no pets no other human of any size, shape etc.   :)
Regarding my use, as i mentioned earlier i do not have much use of that part of my laptop. I occationally burn some iso and try some distros.
So i am least interested in cracking my head what might have changed in the hardware because it is beyond my ability to decifer. Regarding the software part, if we get the same error from different OS on that same comp then do you think it is still a software error ? So if it is not a software problem then it has to be a hardware problem and ofcourse if it is so then we should not discuss that topic here because in most cases hardware solutions are not provided here.

---


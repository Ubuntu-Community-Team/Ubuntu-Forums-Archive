---
title: "Suggestions for dual-booting Win 8.1 and Ubuntu?"
date: 2014-02-21
forum: New to Ubuntu
---

### Post by jteichma on 2014-02-21
I installed ubuntu about 50 times trying to get it to work side by side with Win 8.1.  I really wanted it to work but each time it failed.  The last time I tried to install 13.10 alongside (thrilled I got the option), but every time ubuntu loads its characteristic color but never goes further.  As much as I like your OS I'm about to give up.  Any suggestions?

---

### Post by fdrake on 2014-02-21
check my post in your prev threat. It doesn'seem so bad . we just need more information in order to help you. [http://ubuntuforums.org/showthread.php?t=2206566](http://ubuntuforums.org/showthread.php?t=2206566)

---

### Post by sudodus on 2014-02-21
Welcome to the Ubuntu Forums :-)

Microsoft uses UEFI to make it hard to run anything else alongside Windows (dual boot or multiple boot). You can't blame Ubuntu for that. Try with help from the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

There might also be problems with the graphics chip/card or wifi chip/card. In that case try a boot option, start with ***nomodeset*** according to this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

and maybe after that try to install a proprietary driver.

Please specify your computer, and it will be easier to give relevant advice :-)

- Brand name and model
- graphics chip/card
- wifi chip/card
- Hard disk drive and/or SSD

---

### Post by monkeybrain20122 on 2014-02-21
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

Microsoft uses UEFI to make it hard to run anything else alongside Windows (dual boot or multiple boot).


Exactly. It would be a bliss if you get rid of Windows. :)

---

### Post by oldos2er on 2014-02-21
Doesn't appear to be an Ubuntu support request; moved to Ubuntu, Linux & OS Chat.

---

### Post by illuzian on 2014-02-21
On a side note UEFI is an open standard and brings with it some security benefits that are worth having.

Just because it's Microsoft doesn't immediately mean we should jump on the "it sucks" wagon as the premise of UEFI is justified.

---

### Post by jteichma on 2014-02-22
Can anyone help? I don't know what I might be doing wrong.

I have an Intel SSD, don't know if it is UEFI partition.  I couldn't set up secure boot but I think that is because my board didn't support it.

I set up windows 8.1 first on part of the 160Gb disk and left the other part as initialized but not partitioned (shows as Available).  I know Ubuntu can run fine on this computer as I can run it off the stick OK, but on SSD it is another story....

I keep installing and re installing Ubuntu 13.10 to the SSD (using the i386 version as I'm using an intel I7 4770 processor).  First I used a stick, then from a DVD drive.  It installs perfectly with no errors, but Ubuntu won't run.

Grub menu comes up after installation and reboot as expected.  The pointer in the menu to my Win8.1 installation works fine.  If I click on the Ubuntu link however, nothing happens... just that "Ubuntu color" on the screen and then it falls back shell saying it took longer to load than expected and complains that it can't find a whole bunch of files.  

Any ideas or help would be appreciated.  I'd really like to get this to work on my computer.

Thanks.

---

### Post by Vladlenin5000 on 2014-02-22
for starters you're using the 32-bit version (i386) which absolutely **doesn't** work in that scenario (UEFI - dual-booting Windows 8). You must use the 64-bit version (yes, it says "amd", so what?) and you should start reading what the forum mods have been linking in your other thread like this one [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)  
Of course, needless to say anther thing you shouldn't do is opening multiple threads for the same issue. Reported as duplicate.

---

### Post by jteichma on 2014-02-23
Thanks Vladlenin,

I tried the amd64 version first and that didn't work either.  As I said, the i386 version runs fine off the stick which is UEFI.  Didn't mean to over/duplicate post.  Just the situation changed.  Thanks.

---

### Post by jteichma on 2014-02-23
useful link thanks.

---

### Post by QIII on 2014-02-23
*Threads **Merged.***

---


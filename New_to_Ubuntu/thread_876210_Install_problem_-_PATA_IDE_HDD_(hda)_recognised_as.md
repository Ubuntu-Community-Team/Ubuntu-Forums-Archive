---
title: "Install problem - PATA IDE HDD (hda) recognised as SCSI (sda)"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by mikadelic on 2008-07-31
Hi,

I am trying to install Ubuntu 7.10 on a Dell Dimension 8250. I have to use this version of Ubuntu for my application.

I have tried installing several times and trawled through google and ubuntuforums with no specific solution for me (a few close but no luck). 

In the partition install step (4 of 7) it recognises my 120GB PATA IDE HDD as a SCSI (sda).

The problem arises after I click install, it sets up the swap space fine but after that it stalls at 5% on the Partitions formatting while *"Creating ext3 file system for / in partition #1 of SCSI1 (0,0,0)..."*. It has never gone beyond this with all my attempts. More often than not it stalls with blinking keyboard lights.

I have tried the following with no luck:
- Manual Partitioning (in step 4 of 7)
- Installing boot loader to (hd0), /dev/sda, /dev/sda1 (in advanced options in 7 of 7)
- Disabling boot loader install in the advanced tab
- Leaving it overnight to account for a 120GB format
- tried Ubuntu 7.04 with the same problem

Firstly, im guessing it should be recognising the HDD as hda, and then this would cause problems if I let it install a boot loader at hd0. But I have disabled boot loader and also tried it with different sda addresses with no luck.

Appreciate any help as i'm new to Ubuntu,

M

---

### Post by saj0577 on 2008-07-31
Hows olds the computer?
I had this problem on a computer a few weeks befoe the HD died.



Saj

---

### Post by bobnutfield on 2008-07-31
It is quite normal for your hard disk to be labled /dev/sda (since about 2.6.12, I think).  I had a similar problem a while back and it turned out to be bad sectors on my disk.  But, that conclusion cannot be made yet.  Try formating your drive with Gparted with the ext3 file system, then re-try the install.

---

### Post by mikadelic on 2008-07-31
Saj - PC is from early 2004. Its a WD HDD...

bobnutfield - just attempted a gpart format and the system stalled after 2-3 minutes. Maybe the HDD is dying or has bad sectors.

I installed XP earlier today no problems...

---

### Post by bwang on 2008-07-31
What error messages do GParted give you? Do you have another OS installed? I had this problem once, and booting into the other OS, rebooting and using the "Install" option at the LiveCD startup screen fixed it.

---

### Post by mikadelic on 2008-07-31
I dont have any other OS on the HDD nor do I want/need one.

The screen freezes with no on-screen error and the keyboard lights are blinking which tells me its dead.
As I mentioned previously when I tried formatting the entire 120GB HDD with an ext3 partition it freezed the same as when installing, i.e. screen stalls and blinking keyboard lights.
After spending more time with Gpart I got an ext3 partition onto 20GB of the 120GB HDD. So I tried install again on this as 20GB is fine for my application. I manually added a 3GB swapspace and when I hit install it actually got past the initial freeze point (mentioned in my first post) but throws up an error about 1 minute later saying that this error is attributed to faulty CD/DVD or HD.

Like I said earlier XP installs fine on this...

Can someone confirm where I can install my boot loader for my situation? (i.e. PATA IDE HDD being recognised as sda) If I leave it at (hd0) is it going to cause problems?

Regards,

M

---

### Post by saj0577 on 2008-07-31
Well I had that drive it lasted me 2 years it started playing up then i got the ticking noise.

Yeah it worked fine with XP but not ubuntu or fedora.

Im not sure if anyone else has mentioned it but try getting a gparted live cd and running gparted and formatting it in that?


I could format mine for the first 40gb but then when i told it to format anymore thne 40gb it would freeze and say there was a problem creating the file system...Few weeks later HDD died.

Saj

---

### Post by cariboo on 2008-07-31
Go to your hard drives manufaturers web site and download their diagnostic tools and test the hard drive, this way you can confirm whether it is good bad or indifferent.

Jim

---

### Post by bobnutfield on 2008-07-31
I believe this is clearly a sign of bad sectors.  Windows will install over bad sectors (I've done it), but it cause problems later, even on Windows. Grub should be installed on the MBR (hd0).  But I would strongly recommend a new drive.

---

### Post by mikadelic on 2008-07-31
Just carried out a WD Dianostics test and the HDD passed it for a bad sector check (after an XP install followed by 45mins of diag)!

I believed it was the HDD also, but at the moment its XP - 1, WDDIAG - 1, Ubuntu - 0!

Any final suggestions appreciated, if not I will cut my losses and locate another PC...

Cheers for the feedback,

Mike

---


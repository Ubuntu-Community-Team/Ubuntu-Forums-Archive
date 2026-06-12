---
title: "Computer does not see, Ubuntu instation disk."
date: 2012-01-17
forum: New to Ubuntu
---

### Post by Zundap on 2012-01-17
p { margin-bottom: 0.21cm; }  Hi everyone, i wonder if anyone could help with the following problem.
 
I have just fitted a new hard drive and i tried to install ubuntu on to  it, but the computer does not see the the ubuntu install disk at all. My  other computer that has ubuntu installed on it already, picks up the  disk immediately with no problem at all.
 
So I then tried installing Windows XP on to the new hard drive and the  computer picked that up straight away  and it installed with out a  hitch.
 
The computer i am having trouble with is a desk top, Acer Aspire T180  OA7Z. (With Empowering Technology) My guess is that the empowering  Technology bit, is just a gimmick to con people in to thinking they are  getting something extra. **Am i wrong on that?** The CPU is a AMD  3000+ the hard drive is a 80 GB SATA.  I have set the boot order to pick  up the DVD device as first boot option. 
 
Thanks in advance for any replies.

---

### Post by Jack the R on 2012-01-17
This may not help you but I've been attempting an install on an older computer, and setting the boot order in the BIOS wasn't enough.  I also had to hold down the esc key, at just the right moment, and bring up a second boot order menu.  If I selected the cdrom here too, it would boot into the live cd.

Also, I have two cdroms on that system, and only one will boot the live cd.

---

### Post by Double.J on 2012-01-17
Hi there, is it dvd-r? some older machines can only boot -r not +r?

---

### Post by Zundap on 2012-01-17
> **Jack the R said:**
> This may not help you but I've been attempting an install on an older computer, and setting the boot order in the BIOS wasn't enough.  I also had to hold down the esc key, at just the right moment, and bring up a second boot order menu.  If I selected the cdrom here too, it would boot into the live cd.

Also, I have two cdroms on that system, and only one will boot the live cd.

Thanks Jack, i will check that out and see if it works for me, i'll post back with the result.

---

### Post by QIII on 2012-01-17
Forgive me for asking the obvious, but is your XP install medium a CD or a DVD?  Does your other machine have a DVD player?  On the older machine you are trying to install to, do you have a CD and not a DVD reader?

---

### Post by saneearth on 2012-01-17
If the drive is appropriate for the media, you may still have to burn another disc from the .iso. It is not as bad as things used to be, but some ROM's just do not like certain media.

---

### Post by Zundap on 2012-01-17
> **gnu/mirow said:**
> Hi there, is it dvd-r? some older machines can only boot -r not +r?

Thanks gnu, The reader is a DVD RW,  has been in stalled by myself after i bought  the computer. Is that what your referring to?

---

### Post by Zundap on 2012-01-17
> **QIII said:**
> Forgive me for asking the obvious, but is your XP install medium a CD or a DVD?  Does your other machine have a DVD player?  On the older machine you are trying to install to, do you have a CD and not a DVD reader?


Thanks QIII, I don't know whether its a DVD or CD to be honest, i don’t know which it is.  I definately do have a DVD reader, in fact it is Re Writer also.

---

### Post by Zundap on 2012-01-17
> **saneearth said:**
> If the drive is appropriate for the media, you may still have to burn another disc from the .iso. It is not as bad as things used to be, but some ROM's just do not like certain media.

Thanks sanee, but could you tell me what an ISO is?

---

### Post by Double.J on 2012-01-17
> **Zundap said:**
> Thanks gnu, The reader is a DVD RW,  has been in stalled by myself after i bought  the computer. Is that what your referring to?

Hi there this is useful as we know it should boot DVD's. by +/-r I was referring to the disks you have to burn on? it'll say on the disk/packaging.

[QUOTE=Zundap]Thanks sanee, but could you tell me what an ISO is?[/QUOTE]

The iso is the file you downloaded from ubuntu and burned to the disk. it should look like this
> 
ubuntu-11.10-desktop-i386.iso


A couple of other things, your other machine, if you restart it with the disk in it, does it boot off the DVD, or just read it in ubuntu?

If it doesn't boot, have a look on the CD and see if you have a file on there ending in .iso?

---

### Post by Zundap on 2012-01-18
> **gnu/mirow said:**
> Hi there this is useful as we know it should boot DVD's. by +/-r I was referring to the disks you have to burn on? it'll say on the disk/packaging.



The iso is the file you downloaded from ubuntu and burned to the disk. it should look like this


A couple of other things, your other machine, if you restart it with the disk in it, does it boot off the DVD, or just read it in ubuntu?

If it doesn't boot, have a look on the CD and see if you have a file on there ending in .iso?

It boots up and runs perfectly in the other machine, that's what i find so puzzling.

---

### Post by Double.J on 2012-01-18
Hi,

You could try a 1GB USB stick.. though if you're having problems booting the disk drive, this may not work also!

If re-downloading, re-burning and using a different format of disk and trying a CD instead of DVD still don't work, then I'd suggest trying the [alternate CD]("http://www.ubuntu.com/download/ubuntu/alternative-download") as it uses a different, text based installer?

Hope it helps!

---

### Post by Zundap on 2012-01-19
> **gnu/mirow said:**
> Hi,

You could try a 1GB USB stick.. though if you're having problems booting the disk drive, this may not work also!

If re-downloading, re-burning and using a different format of disk and trying a CD instead of DVD still don't work, then I'd suggest trying the [alternate CD]("http://www.ubuntu.com/download/ubuntu/alternative-download") as it uses a different, text based installer?

Hope it helps!

I'll give it a go, but i will have to get a USB stick first, i will post back with the result. Thanks again gn for all your help advice and , thanks again top every one else also.

---


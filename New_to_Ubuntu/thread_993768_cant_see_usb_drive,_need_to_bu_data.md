---
title: "cant see usb drive, need to b/u data"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by jumpingjaxs on 2008-11-26
pleease help, im going in mad circles for a problem that im sure has a simple solution (but i am very new to this).

i have no operating system installed on my hd (i got rid of windows because of some sudden major problems and want to switch to linux).
im using ubuntu 8.04 live disk, and i want to backup the data on my hd to an external usb drive before fully installing ubuntu.

however i dont know how to backup my data using this ubuntu livedisk..
i typed  
sudo fdisk -l 
in the terminal box but only my regular hd shows up. the external usb drive is not listed. its brand new and the light indicates its working fine.

what do i need to do?

---

### Post by ash_nug on 2008-11-26
How did you get rid of windows exactly?

Are you sure you have files still left on the HDD to backup?

---

### Post by dark_harmonics on 2008-11-26
You should use gparted to create the partition on the external HD. It should mount automatically after that.

---

### Post by colintivy on 2008-11-26
Hi! folks,

I have a similar situation with a 20GB 2.5" IDE drive in an Akasa external enclosure. The drive has a complete Win98SE plus all sorts of bits and pieces on. This drive was originally in my laptop and was replaced with a 30GB new clean drive to allow 8.04 to be installed which works well. I intend to reformat external drive to ext3 and use it for backup purposes and, perhaps, to try another distro later.

Perhaps this thread might allow some more discusion. The use of gparted would not come amiss.

Regards,

colintivy  :-)

---

### Post by jumpingjaxs on 2008-11-26
ash_nug: in sept my comp crashed and i couldnt load win xp or access any of my stuff. my drive was corrupted. after much unsuccessful research on my own, a tech helped me resolve the issue - we used knoppix live cd to transfer my stuff to a safe empty drive he had, reformat my drive (i chose not to reinstall windows), and then transfer my data back to my newly-cleaned drive.
im borrowing ubuntu live cd from a friend, and with it i can see whats on my drive.

dark_harmonics: what does it mean 'create the partition'?

also, how can i find out what filesystem my drive has?

thx for your continued assistance =)

---

### Post by colintivy on 2008-12-07
Hi folks,

This thread seems to have died with quite a lot of further advice required. Is there anyone out there who can continue it? Big thick books (Official Ubuntu Book 3 and Beginning Ubuntu Linux 2) are very quiet as well.

colintivy :-\

---


---
title: "cant run 18.04 lts from stick"
date: 2018-09-20
forum: New to Ubuntu
---

### Post by bfloyd4445 on 2018-09-20
it always boots to GNU GRUB version 2.02. Then saysminimal bash-line editing is supported. For first word , \Tab lists possible commandcomletions. Anywhere else Tab lists possible device or file completions.

grub> _

anyone know what i should do| This is on new hardware with nfts and win 10 pro on one partition of wd blue 55gig solid stae hd

thanks 
B

---

### Post by Autodave on 2018-09-20
Have you tried shutting off *fast boot *in the BIOS?

---

### Post by yancek on 2018-09-20
> This is on new hardware with nfts and win 10 pro on one partition 

A little more information please.  You can't install Ubuntu or any Linux on an ntfs filesystem so did you create free or unallocated space on the drive prior to attempting to install Ubuntu?  That would be necessary.  You haven't properly installed the Grub bootloader which is why you have the error.  Ubuntu actually has an official site explaining how to dual boot with windows 10, see the link below.  If you can't boot the Ubuntu install usb, you probably need to check various options in the BIOS.  In any case, I would definitely suggested reading the page at the link below before beginning. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by bfloyd4445 on 2018-09-29
> **Autodave said:**
> Have you tried shutting off *fast boot *in the BIOS?

yes, i learned that if you don't you won't ever be able to access ntfs partisans requiring reformatting the disk and starting over. I decided to use two ssd's one for win10 pro and one for Ubuntu. With slow boot i can easily select which os i wish. After one week i like Ubuntu a lot even though i have yet to learn my way around.
Thanks for the suggestion:)

---

### Post by bfloyd4445 on 2018-09-29
> **yancek said:**
> A little more information please.  You can't install Ubuntu or any Linux on an ntfs filesystem so did you create free or unallocated space on the drive prior to attempting to install Ubuntu?  That would be necessary.  You haven't properly installed the Grub bootloader which is why you have the error.  Ubuntu actually has an official site explaining how to dual boot with windows 10, see the link below.  If you can't boot the Ubuntu install usb, you probably need to check various options in the BIOS.  In any case, I would definitely suggested reading the page at the link below before beginning. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

thanks much for the help. I just bought a second ssd drive and installed UBUNTU ON IT. I set the bios for slow boot. After a week i am liking Linux much better than win even though I'm totally ignorant and still lost trying to find my way around like i was in total darkness with only my cell phone light to show me the way.:smile: .......I am having trouble sometimes getting it to even boot to the bios. I have the ntfs ssd set as first boot and the Linux as 2nd but sometimes nothing happens. I'll eventually figure it out but this is temporary anyway as i plan on just one os in the future. gonna go check out the link you provided. Thanks again
best wishes
b

---

### Post by bfloyd4445 on 2018-10-02
yes but each operating system has its own ssd there not installed on the same drive. Thanks for
 for the link i will do some reading
v

---


---
title: "reformating internal hard drive"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by rockford86 on 2011-10-28
i need to reformat my harddirve to ntfs so i can install win 7. i tried with both disk utility and gparted and am errored because "drive in use" right, i only have the one so what do i do?

---

### Post by garyed on 2011-10-28
You could download Gparted live, burn to CD  & then boot from the CD

---

### Post by critin on 2011-10-28
Have you tried a live ubuntu?  Gparted is there.

---

### Post by Mark Phelps on 2011-10-28
> **rockford86 said:**
> i need to reformat my harddirve to ntfs so i can install win 7. i tried with both disk utility and gparted and am errored because "drive in use" right, i only have the one so what do i do?

No matter what app you use, you'll have to boot from CD/DVD or USB -- and run the app from there.

Don't know if the Ubuntu Desktop CD still includes GParted, but if it doesn't then use the Disk Utility.

And ... only REMOVE the current partitions.

THEN, boot from the Win7 DVD and allow the Window Installer to format the partition.

It works out in the long-run better that way.

---

### Post by CharlesA on 2011-10-28
You can just install Win7 on it and remove the partitions from within the installer.

Way simpler to do that.

---

### Post by Mark Phelps on 2011-10-29
> **CharlesA said:**
> You can just install Win7 on it and remove the partitions from within the installer.

Way simpler to do that.

Ordinarily, I would agree.  But there have been quite a few posts here where folks wanted to install Win7 on their PCs and the presence of Linux filesystem partitions confused Win7.

I can't confim this myself, as I would not attempt such an install, as I use separate drives for the different OSs.  Found out that it works out better in the long-run that way.

---

### Post by CharlesA on 2011-10-29
> **Mark Phelps said:**
> Ordinarily, I would agree.  But there have been quite a few posts here where folks wanted to install Win7 on their PCs and the presence of Linux filesystem partitions confused Win7.

I can't confim this myself, as I would not attempt such an install, as I use separate drives for the different OSs.  Found out that it works out better in the long-run that way.
I can't confirm it either, but I do know that if you let the Windows installer create the partitions, it creates a 100MB boot partition for windows. If you create the partition before hand, it doesn't make that partition.

---

### Post by amjjawad on 2011-10-29
> **rockford86 said:**
> i need to reformat my harddirve to ntfs so i can install win 7. i tried with both disk utility and gparted and am errored because "drive in use" right, i only have the one so what do i do?

If I understood your post correctly, then you can NOT format your HDD while you are using it. However, if you want to format a partition in your HDD which is NOT in use at that moment, then yes, you can.

As everyone suggested, better to run GParted from Ubuntu Live-CD.

@Mark, yes, GParted is still included in the Live-CD but it's not after you install Ubuntu.


@OP
So, are you trying to get rid of Linux or you just want to Dual-Boot?

---


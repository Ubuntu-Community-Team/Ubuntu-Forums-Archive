---
title: "Issue installing"
date: 2014-05-25
forum: New to Ubuntu
---

### Post by rhawnied2 on 2014-05-25
Hi

I am trying to install ubuntu on a second hard drive that is empty from a disc I burned.  All I get is a message telling me there is no operating system. 

Thanks for your help!

---

### Post by robin7 on 2014-05-25
When you boot from the Ubuntu Live DVD or USB drive, you can use the INSTALL icon and be sure to specify the empty hard drive.  It may have a name like sda/6 or something so be sure you're installing it to the proper hard drive. If that spare hard drive is installed to your computer, re[placing the other, then it's easy.  Then just swap hard drives!

---

### Post by Bashing-om on 2014-05-25
rhawnied2; Hi !

Well,
Are you dual booting with Windows 8 such that UEFI is a factor ?
Did you check the hash sum of the .iso file ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Did you Burn the .iso to disk at a slow rate as an "image" ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Did you boot the liveDVD to "try ubuntu" mode ?
Did you verify the disk from the boot options menu "check disk for defects" ?

If all the above is in the affirmative, going to have to get particular as to what is.

What machine, what hardware , how much ram ,- in particular the graphics ? .. Best to get you booting the liveDVD to "try ubuntu" mode and take the issue from there.

It is ubuntu
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by rhawnied2 on 2014-05-25
There is nothing else just a black screen that says No operating system installed

---

### Post by rhawnied2 on 2014-05-25
I unplugged the other hard drive so it was just the one

---

### Post by QIII on 2014-05-25
Assuming you did not change any settings in your UEFI/BIOS, you will still need to do a UEFI install of Ubuntu for this to work.  Don't change your mobo settings or you will probably find that Windows won't boot.

Did you install Ubuntu that way?

---

### Post by rhawnied2 on 2014-05-25
Sorry I'll explain.  I am only running Ubuntu.  I was trying to install it on a second bigger drive that I got a few years ago but had trouble with it then.  Then I didn't have the internet so it didn't get fixed.  Now I'm back and everything is out of date so I'm upgrading.  I wanted to use the new bigger drive full time with this one as back up but I can't get it working.  I just have a black screen with Missing Operating System.  I checked the copy of ubuntu I got and made sure it is an image.

---

### Post by rhawnied2 on 2014-05-25
I'm not sure what all you need to know is but It a P4, 80Gb (old) 320Gb(new one), 2Gb ram, on board graphics I don't know what the ram for that is.  It's an old computer.

---

### Post by Impavidus on 2014-05-26
Are you sure the bios has been set to boot from the live disk? Because it seems that is has been set to only try to boot from the empty hard drive, resulting in that error. Enter the bios and check/set as appropriate. Else you may have a bad burn.

---

### Post by 3rdalbum on 2014-05-26
What are you trying to do at the moment: install Ubuntu to the hard disk, or boot from an already a installed Ubuntu on that disk?

---


---
title: "Ubuntu installation along side windows 10 problems."
date: 2016-08-15
forum: New to Ubuntu
---

### Post by heroicjokester on 2016-08-15
Hi,
I'm currently a windows user (windows 10) I wanna learn linux so to get the feel of the OS im trying to install Ubuntu 16.04 along my windows 10.
I have an Acer aspire E5-573G with i3 processor and 8 gb ram. I've loaded an USB drive made it bootable with the ubuntu_16.04.iso and when I try to boot it first I get the orangish purplish ubuntu screen then it goes black and always stuck there.

I read a few threads about hitting the down arrow key and using nomodest but that doesn't work for me. Im always stuck on that black screen and the installation or even live boot doest work.

And my system only boots in Legacy mode, and when I try to boot it in UEFI mode it doesnt detect any OS not even my windows 10.
Is there any way I can run both ubuntu and windows 10 side by side?
Thanks In Advance :D

---

### Post by yancek on 2016-08-15
Was windows 10 pre-installed?  If so, then in all likelihood it is using UEFI and you need to boot Ubuntu in UEFI mode to install.
If you installed windows 10 then it isn't necessarily UEFI.

Did you do an md5 checksum on the Ubuntu iso after downloading, before putting it on the usb?
Can you try booting the usb on a different computer to see if it works.  Eliminates the above problem.
Your problem could be the graphics but more likely a bad download or bad installation to the usb.  
What software did you use to put Ubuntu on the flash drive?

---

### Post by grahammechanical on 2016-08-15
> I read a few threads about hitting the down arrow key and using nomodest

That is not the advice that I give. My advice is: At the first purple screen with the icons of a human & a keyboard press Enter. Then select a language. The default is English. At the underlying screen then we press F6. A small menu will appear at the bottom right of the window. Now, select nomodeset. We can select more than one of these boot options and you may need more than one.

See this wiki page at the heading: Changing the CD's Default Options. Go to section 6 - F6.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

You will notice that it is the F6 key that will allow use to edit the boot command for the live session by hand. No mention of a down arrow key. So, I am not clear if you have been following the correct instructions. Maybe you have. Maybe you need to select more than nomodeset.

Regards

---

### Post by heroicjokester on 2016-08-15
@yancek Yes I checked the md5 checksum and it all looks good.
I used Rufus tool to make my usb bootable
My windows 10 is running on legacy mode only and like I said if I change it to UEFI my system doesnt even detect any OS on the hard drive
and what do you mean by a graphic problem?

---

### Post by heroicjokester on 2016-08-15
> **grahammechanical said:**
> That is not the advice that I give. My advice is: At the first purple screen with the icons of a human & a keyboard press Enter. Then select a language. The default is English. At the underlying screen then we press F6. A small menu will appear at the bottom right of the window. Now, select nomodeset. We can select more than one of these boot options and you may need more than one.

Regards

Yes I did that sorry the video which I found on youtube told me to hit the down arrow key guess they both do the same thing. Selecting nomodest alone didnt solve the problem and I did a bit more research and tried using nomodest with nolapic but still no luck. I dont understand what actually the problem is?
Should I reinstall my win10 in UEFI mode and then proceed with ubuntu's installation in UEFI mode will this solve the problem?

---


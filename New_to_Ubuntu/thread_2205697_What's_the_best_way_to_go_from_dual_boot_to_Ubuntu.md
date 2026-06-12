---
title: "What's the best way to go from dual boot to Ubuntu only?"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by Bill Kolshorn on 2014-02-15
Hi Folks. Newbie here and not terribly computer savvy. I am running a dual boot with Windows 7 Home Premium and Ubuntu 13.10 on a Toshiba laptop A665D with 4GB memory. I installed 13.04 via a disk that I downloaded and then upgraded to 13.10 with a download. Things seem to be going okay with Ubuntu (printer and scanner work, music and photos work, internet works, backlighting on keyboard does not work). Windows is agonizingly slow, so I thought I would try to go all Ubuntu. Should I wipe my hard drive (Dban) and install a fresh build of Ubuntu or wipe out Windows with an install of Ubuntu by downloading and burning a new Ubuntu disk? If the latter, can I do that from the Ubuntu install I already have, and if so, how? I can't seem to find an answer on the forums. Thanks for any advice and remember, newbie here.

---

### Post by Vladlenin5000 on 2014-02-15
A fresh installation using up all drive space regardless of the partitioning choice would be preferable of course. However, you can do it easily from the one you already have simply by deleting the Windows partition(s) and resizing the Ubuntu ones if you want. The next step would be updating/reconfiguring grub in order to reflect the changes but that isn't mandatory. The only issue you'll have is a Wndows entry listed that's no longer exists.

For the first part - managing partitions - *gparted* should be enough.
For the second part just run ```
sudo update-grub
```

---

### Post by Jonathan Precise on 2014-02-15
Yes. However, resizing the root partition using GParted might corrupt it and render the install unusable. Before preforming the operation, use Clonezilla to back-up the partitions. Is this an EFI-machine? If so, use the 64-bit disk.

---

### Post by bc.haynes on 2014-02-15
Hello, Bill K.,  I would suggest that you use Ubuntu a little longer (maybe 'til 14.04 LTS comes out) and see if you run into any problems (don't know how long you have used it). 14.04 is Long Term Support, and you shouldn't have to upgrade the distro for a long time. I have had some problems (minor), but I intend to stay with Ubuntu. I have said that twice in the past, but this time I am certain. [[color=red]Linux Is Not Wondows[/color]](http://linux.oneandoneis2.org/LNW.htm), be really sure before wiping your Windows disc that Windows is not for you. Best of luck, whatever you do. Ben

---

### Post by grahammechanical on 2014-02-15
You will see posts on this forum asking for help from users who say that they removed Windows and now they want it back. Make sure that you are not one of them.

We can download an ISO image in ubuntu and it is easy to burn it to DVD or USB memory stick. Open the File Manager and right click on the ISO image file and select Write to Disk and if we have a DVD in the optical drive then Ubuntu will be burnt to the DVD.

Regards.

---

### Post by bc.haynes on 2014-02-15
Thanks, grahammechanical
I did not know I could do the Right-click trick. I learned something new today.

---

### Post by linux4me on 2014-02-15
There's one other thing I recommend you do before you get rid of Windows, if you do, and that's to make sure you have a Windows recovery disk made if one didn't come with your laptop just in case you do ever need to reinstall Windows. With some Toshiba laptops, there is actually a recovery partition used to do a recovery rather than a disk, and if you wipe it, you have no way to bring Windows back. Even then, I think they include a utility within Windows to create a physical recovery disk.

---

### Post by Bill Kolshorn on 2014-02-15
Thanks for your comments and advice. Perhaps, as suggested, I should wait for 14.04. It's not that much longer. I have had some issues recently with some installs. The message when installing said the download wasn't complete. Somehow I got around that, but I really appreciate your advice.

---

### Post by Sef on 2014-02-15
> ...[COLOR=#000000]Clonezilla to back-up the partitions.[/COLOR]

It is always a good idea to back up your disk with Clonezilla. This way in case anything happens you can reinstall your OS(es) easily.

---

### Post by monkeybrain20122 on 2014-02-16
> **Jonathan Precise said:**
> Yes. However, resizing the root partition using GParted might corrupt it and render the install unusable. Before preforming the operation, use Clonezilla to back-up the partitions. Is this an EFI-machine? If so, use the 64-bit disk.

This is true. So use clonezilla (or my preference fsarchiver) to make a clone of the Ubuntu partition. Then wipe the hard drive, reformat it and restore the clone to the whole system.

---


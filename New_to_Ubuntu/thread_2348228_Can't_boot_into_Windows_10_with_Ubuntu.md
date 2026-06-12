---
title: "Can't boot into Windows 10 with Ubuntu"
date: 2017-01-01
forum: New to Ubuntu
---

### Post by lunar.crest on 2017-01-01
[LIST]
[*]I installed Ubuntu alongside Windows 10 and everything worked fine for a couple hours. Eventually It showed me a message in Windows 10 that said the computer needed to restart to fix some driver errors. After that it wouldn't boot back up and the only thing that would is Ubuntu.
[/LIST]

---

### Post by wildmanne39 on 2017-01-01
Please create a thread in wireless and networking for the wifi issue, we do not allow  more then one issue per thread it causes to much confusion for the people helping and the ones searching for answers, and I recommend editing the title of this thread to just include the boot issue.
Thanks

---

### Post by lunar.crest on 2017-01-01
It won't let me change the title. Should I just delete the post and make a new one?

---

### Post by wildmanne39 on 2017-01-01
I will edit the title for you.
Thanks

---

### Post by oldfred on 2017-01-01
For Boot issue.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by lunar.crest on 2017-01-02
I downloaded the two files:
-->boot-repair-disk-64bit.iso
-->boot-repair-disk-64bit.iso.part
copied both of the files onto a blank CD and dried to run it. 
I'm not sure what to do next cause when the instructions said to (Launce Boot-Repair, then click the "Recommended Repair" button.)
The only file that will open it the first one and it becomes unresponsive immediatly after opening.

---

### Post by Geoffrey_Arndt on 2017-01-02
"Copied" . . . "Tried to run" . . . . not how it's done.

You only need a single iso file from the Sourceforge website . . . that 64 bit iso needs to be "burned" to a disk as an "iso image file" using standard disk burning software.    It cannot be copied to a disk and run.    In Ubuntu, the disk burning program is called "Brasero".     Be sure to burn it at the slowest speed allowed.

Then, be sure your PC firmware (UEFI or Standard Bios) is set up to boot from external disks (cd/dvd) or usb-stick.

Good Luck . . . .

---

### Post by lunar.crest on 2017-01-02
When I installed Ubuntu I did it from a usb. After that I had to take it out for the Grub to show up.
After I burn the iso image onto the disk do i just run it like normal or is there something special I need to do?

---

### Post by oldfred on 2017-01-02
Easier just to use Ubuntu live installer in live mode and add Boot-Repair to it.
the ISO is now older with Boot-Repair.

Just add ppa, update system, and then run Boot-Repair.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lunar.crest on 2017-01-03
When I restart the computer with the flashdrive in it gives me the options
--Try Ubuntu without installing
--Install Ubuntu
--OEM install (for manufacturers)
--Chack disc for defects
I know nothing of how to use anything in Ubuntu. Is there any way you can explain it to make it simpler to understand?

---

### Post by yancek on 2017-01-03
You indicated that you were able to boot the installed Ubuntu.  What is suggested in post #10 above, is that you follow the instructions for adding the boot repair to the live system on the usb which is explained at the link posted.   Select the Try Ubuntu option and boot to the Desktop and go to the boot repair site and use their instructions.

---

### Post by eionmac on 2017-01-07
As long as you separate  "swap"  "/ " (root) and "/home" on different partitions then just overwrite the old LTS distro with the new one. proviso you must install as same user name and password regards eionmac

---


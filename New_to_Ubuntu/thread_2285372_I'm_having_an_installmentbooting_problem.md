---
title: "I'm having an installment/booting problem"
date: 2015-07-05
forum: New to Ubuntu
---

### Post by Brkzldr on 2015-07-05
Hello,
I'm new to Ubuntu and also installing new OS's on my computer. I have an old MacBook Pro which I decided to disk partition and set the other half with Ubuntu. I used MS-DOS (FAT) for the partition that I named UBUNTU. Also for installation I used UNETbootin and rEFIT. I watched this video to do so... [https://youtu.be/ssKpGeJ--UY](https://youtu.be/ssKpGeJ--UY) . Everything seemed to be okay. I started the computer holding down "alt". The rEFIT popped up as it should do. Clicked on the Boot Linux from UBUNTU. Selected Install UBUNTU from the list that came up. But after showing some lines very similar to these [http://students.fim.uni-passau.de/~schieder/nouveau.jpg](http://students.fim.uni-passau.de/~schieder/nouveau.jpg) it all suddenly stops. BTW the first few lines that come up say "No controller found" and "no bios dp data" "invalid descriptor for config index 0: thype = 0x2, lengt h = 3" Sometimes it even just gets stuck over there. I've tried it many times but couldn't get any further. I have quite a small knowledge about these stuff so if someone could help, keeping in mind that I don't know much, it would be great. Still, thank you for reading. Have a nice day

---

### Post by grahammechanical on 2015-07-05
What happens when you select Try Ubuntu? Are you able to get a Ubuntu live session?

How far does the Install Session get? Do you get to the screen with the dialog that says Preparing to Install Ubuntu?

What CPU does this machine have? 32 bit or 64bit? Is it an Intel CPU or some other manufacturer? What version of Ubuntu did you download? What was the file name?

Regards.

---

### Post by Geoffrey_Arndt on 2015-07-05
Also,did you say you used MS-Dos (FAT) partition and named it Ubuntu?  If so, Ubuntu will not install to a "Windows" file system.   Linux has it's own file structure and file systems.   The file system most recommended for starters is ext4.    If you use unetbootin or Pendrive Linux [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)  then you'll have a good start.

PS:  I just watched the video in your link . . . I am presuming the usb stick was setup with the FAT file system (FAT32),  which is OK, but on the Hard Disk, the partition for any Linux including Ubuntu should be a Linux file system such as:
>  ext4 ext3 ext2 reiser xfs btrfs etc.  (maybe I'm not reading OP's note correctly??).   

PPS:   (late edit)  I think this last step (as shown in video, was presented pretty quickly.   But, if you did reformat as vid instructs, then do as graham suggests re providing system specs.

---

### Post by Brkzldr on 2015-07-05
Well I used "nomodeset" during boot and I achieved to get to some place. I see the Ubuntu desktop. I tried using the Install Ubuntu app. I'll explain it later in this reply later on. My computer is a MacBook Pro Mid 2009. 15" with Intel Core 2 Duo 2,8 GHz processor 4 GB RAM and Nvidia Geforce 9600M GT with half gig memory. While using the installer inside Ubuntu, btw I suppose it's running from the USB, because when I restart the computer rEFIT kicks in and asks me to either boot from Macintosh HD or boot Ubuntu on UBUNTU (disk partition that I created to install Ubuntu). The problem is when I start the installer, it asks me what I am aiming to do. I click on "other" because if I click on install ubuntu alongside mac OS, it tries to install ubuntu on the USB thumb drive. So I select "other" and find the right disk partition in the list. The name of the partition doesn't appear on the list yet I can find it because it's formatted in MS-DOS FAT and in the list only two parts show FAT32 and the smaller of them is the USB thumb drive. So I select it and format it once again. I've tried formatting it in FAT32 but it didn't work out so I saw other people formatting it in something else which sounded like FT2 or something like that. At this time I cannot remember so please forgive me for that. It's not journaled, of that I am sure. So it gives me some error messages that this cannot be undone and so on. It also tells me that /cdrom doesn't function or read properly. I know that my CD mechanism doesn't work. It's been the same since almost I bought it. I don't remember ever using it. This message is shown twice for some reason. The installer then somehow keeps on. And at this moment I'm stuck with a screen stating "detecting file systems" for the last hour and currently I am too tired to keep on with it and I have a flight tomorrow. I wish I could have done it today. Anyway. Thank you very much for your help and interest even if you cannot answer or if you answer but your solution doesn't work out for me. Thanks

---


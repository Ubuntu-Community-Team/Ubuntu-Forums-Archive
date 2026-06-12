---
title: "hd0 cannot get c/h/s values"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by Tekorito on 2012-05-26
I've downloaded Ubuntu 11.04 LTS ISO image and burned to disc. Installed it to a 20GB hard disc which went perfectly. On reboot, I get the above message and something about GRUB.
I'm a complete newbie at Linux and have to admit, this is not an encouraging introduction. 
Can anyone please give me any clue where I've gone wrong? Please avoid Linuxese!
Asus A8N5X Mobo
Dual core AMD processor
Ample memory
20GB Maxtor drive.

Many thanks.

---

### Post by carl4926 on 2012-05-26
Boot the live cd of what I think you must mean 12.04 not 11.04

Open a terminal and post the result of

```
sudo fdisk -l
```

---

### Post by Tekorito on 2012-05-26
Thak you for replying Carl4926,
Quite right, 12.04.
Sorry, but you have already lost me. I have only:
- the ISO image CD, which if I start as a boot CD tries to reinstall over the existing installation, and
- the installation on hard disc which sits with 'Grub rescue' blinking at me. Entering your sudo command does nothing.
Many thanks for any help - the forum postings provide me with no intellegible clues.

---

### Post by carl4926 on 2012-05-26
When you boot the CD you should get an option to try ubuntu or install ubuntu.
If you don't see that try hitting Esc as the cd boots, you should see the language selector and later the 2 options

Let me tell you what I'm thinking might be the problem. The partitions for ubuntu must be Linux partitions, ideally in the ext4 format. I'm thinking yours might not be and may perhaps be NTFS?

---

### Post by Tekorito on 2012-05-26
Hello again,
When I installed Ubuntu, the programme spotted that Windows was already installed but I allowed it to delete those partitions and do a clean Linux install in partitions it claimed it was creating.
Anyway, I worked out how to use the CD as you described and tried the terminal command. The result was long winded but the essence is:

Disk /dev/sda: 20.5 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders ... ...
Disk identifier: 0x00010e1a

It went on to show three partitions:
Device        Boot     ...      ...          id        System
/dev/sda1      *        ...      ...        83       Linux
/dev/sda2                                     5        Extended  
/dev/sda3                                    82       Swap/Solaris    

I hope this helps.
Many thanks.

---

### Post by carl4926 on 2012-05-27
You mean you used the top option here
[http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/4_install_custom.jpeg](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/4_install_custom.jpeg)
?

Did you change the bootloader setting?
[http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg](http://www.su2root.ukfsn.org/files/Ubuntu/ubuntu_11.10/9_choose_grub.jpeg)
Default is sda
Not sda1 or sda2, just sda

This drive? is it only small at 20GB
Is it a standard SATA internal HD

I'd consider re-installing, but I'd wipe the HD (might be worth creating a new partition table) with Gparted and manually create the partitions
swap 2GB
ext4 18GB for the installation
No need to have an extended.

---

### Post by Tekorito on 2012-05-27
Yes, I used the top option. However, I didn't see the second screen - that one never appeared. 
The disc is an older IDE drive.
I'll download Gparted and give your suggestion a go.
I did manage to explore the CD live version and very much liked what I saw - makes me more determined to get this problem resolved!

---

### Post by Tekorito on 2012-05-28
OK. I cleaned the disc and created partions as suggested. Reinstalled, having a look at all options, into what appeared to be sda. There was one menu which I did not understand in which it asked about the type of disc and then something which gave me options of /, /root, etc. The upshot was that I ended up with the same message, "hd0 cannot get c/h/s values". Clearly sda is not where it installed. If you have any more pointers carl4926, I'd be very grateful.

---

### Post by carl4926 on 2012-05-28
Try default install
Let Ubuntu erase and use entire disk
Leave everything to defaults for grub

---

### Post by Tekorito on 2012-06-02
Tried that plus two variants and I still have the same message. Also tried a different hard disk just in case ... ...
The upshot is I don't have enough time for this. For all of its sins, Windows installs each and every time and boots. None of this nonsense. Only when Linux sorts out these serious shortcomings is it ever going to become more mainstream.
A great pity.

---


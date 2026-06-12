---
title: "Computer won't start past the Asus screen"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by hebdave on 2014-02-27
Hi all just when I thought all was going so well ! I am new to ubuntu and new to disk imaging. After some advice and reading on these subjects I felt I could do it okay. I did a successful restore with redo backup for all my computer partitions all in one go. I also managed to do Clonezilla today as a ubuntu partition restore for sda6. So I thought as these two went so well I could rely on redo backup if anything went wrong for a complete disk overwrite and restore- I even tested it and it had worked as I say. 

Today I tried to restore a windows complete system image of the c drive with aeomi backupper as I had not tested this partition by itself. Note this is including bootloader , tables etc and is **not** the data only image(I do have this though as well). This caused the grub to send up an error on reboot and not allow getting to the multi-boot screen. I thought rather than spend two days trying to figure out even more about linux or grubs it would be quicker to restore the full disk using redo backup which **as described** reinstates all the computer with **everything** like boot loaders and tables included. This image that had worked before now decided not to work at all however. It should overwrite everything including any grub problems I assume. So I tried the image again and this time it **did succesfully restore** the image. But......
when I reboot it now will not go past the ASUS screen. Instead it keeps going round in circles with the re-booting sound and back to the Asus screen again and again. Is the once** easily restored image now bad** or is the computer suffering from boot issues or is it something else? and more importantly who should I go to and ask about this ?

I could potentially try and restore the clonezilla ubuntu partition image if it will suddenly join in some way with the redo image making the whole computer work as one again (excuse my beginners language). Or I could use a complete image of the entire disk made by aeomi backupper from the live environment( similar to redobackup) if that might work ?

I do have a hirens boot cd that works via yumi and parted magic and Ultimate boot cd. I have never used restore tools before other than the imaging tools above and windows system restore that comes with a PC when it comes as factory. I can use yumi and boot into any tool including a ubuntu live cd. I don't know what to select as I've never had too before and am new to linux  as of 1 month ago. I just put them all there for an emergency one day. 

I wonder if the disk is damaged if it reboots and reboots repeatedly - I just don't know?! I am praying one of you might help me out 'literally'- the good news is it cannot get any worse than it is so feel free to help me at will :rolleyes:.

Also as it is hard to know what information to give - would you want a smaller post ? The danger here is you will have less information to go on but I can try this if you prefer. 

Many thanks !!

---

### Post by hebdave on 2014-02-28
Can someone please help if thats okay or at least tell me who to speak too ? And would it help if I simplified what I have said above ? Can I help by using disk check via mini xp. Is windows 7 being on the machine going to allow checking to work ? What command gets me a log via mini XP if you want that. Or what command via terminal would get it ? Would a log help you ? Should I reinstall from a windows recovery cd partition image I made(I have nothing else as its not bootable) ? F9 is for my current unbootable PC revovery partiton. This does not work but ESC , F2 , and one other worked. Is there a forum I should post too ?- Is windows forum now more relevant to post to if I need to re-install from scratch ? Remember I have a booting loop that goes round in circles.

Many thanks.

---

### Post by Mark Phelps on 2014-02-28
It's a wild shot ... but at this point, I would try running Boot-Repair to see, if by some miracle, that fixes the boot problem:  [http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---


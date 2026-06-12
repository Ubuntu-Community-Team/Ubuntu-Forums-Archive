---
title: "A Partition Disappeared"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by Andavane on 2008-10-26
Greeting             (gutsy)

I have a Freecom 80 Gg usb external hard drive which is divided into three partitions.
These were made before I was on Ubuntu.

It has served me well, an I use it for backing up my work to, and thereafter I use the drive to back up to my laptop, and my mate backs up a copy to his laptop as well.  I cannot take the risk of losing our data.

Last night a friend saved a file which I didn't want saved, so I plugged the drive in to go to take  a copy of the file, in order to bring it back and replace before saving again.

The file would not open. When I tried again,it opened only to display gobbledygook.

I unmounted the three partitions, disconnected the drive the plugged it in again to automount.

However only two of the partitions have mounted. The one I used has 'disappeared'.

For the time being I have made a fresh back up to a partition which is working.

I would like to have an idea of what is going on here, and whether members think I should replace the external drive.

Regards

John

---

### Post by cariboo on 2008-10-26
Can you mount the "missing" partiton maually eg:

```
sudo mount /dev/sdx3 /mnt
```

sdx3 should be whatever your external hard drive is. for example /dev/sdb3 if you external is your second hard drive.

Jim

---

### Post by randy78 on 2008-10-26
Hmmm...

What type of file was it that displayed the 'gobbledygook'(.doc, .exe, .pdf, .vbs)?

Were all of the partitions NTFS, FAT or ?

It sounds like maybe the partition identifier was overwritten by the file you didn't want saved...(but to do so would have required the file to be executed, in some way or another) Do you know if the file you did not want saved was a virus? If so, and if it was detected as a virus by an Anti-Virus application, do you know the name (Trojan.Win32.agent.akk, etc...)

Alternatively, have you tried viewing the partitions in Gparted:
sudo apt-get install gparted, or you can use a live disk.

Take Care

---

### Post by Andavane on 2008-10-27
> **cariboo907 said:**
> Can you mount the "missing" partiton maually eg:

```
sudo mount /dev/sdx3 /mnt
```

sdx3 should be whatever your external hard drive is. for example /dev/sdb3 if you external is your second hard drive.

Jim


Gentlemen,
there have been some developments:

Ubuntu continued to show nothing at all when I mounted for one of the partitions on the drive.

I then rebooted into Windows XP and plugged in to the usb drive,
to my surprise all partitions booted, although the partition in question
(called DATABAKS) did look a bit peculiar.  I have attached a shot of what is there.


>> **cariboo907 said:**
> Can you mount the "missing" partiton maually eg:

```
sudo mount /dev/sdx3 /mnt
```

sdx3 should be whatever your external hard drive is. for example /dev/sdb3 if you external is your second hard drive.

Jim
This did not work here, the command not recognised.

Oh btw it looks as if there is corruption within that sector.
Funnily enough after it had mounted in Windows, when I rebooted into Ubuntu, the drive was indeed mounted this time (the fuinny fiules in the picture were not there before.

So I am uncertain as to what to do next. I feel like blitzing all the contents of the drive anb then backing upo with grsynch again, but will wait for more feedback.

Thanks for all help

Kind regards

John

---

### Post by alphaniner on 2008-10-27
Did you ever 'fdisk -l' in Ubuntu?  I hope so, because you shouldn't go around 'sudo mount'ing stuff without first verifying the partition is right.  My bet is that the partition was 'dirty' and that's why Ubuntu would not automount it but Windows did.  It would also explain the gobbledeygook files and such.

---

### Post by Andavane on 2008-11-13
> **alphaniner said:**
> Did you ever 'fdisk -l' in Ubuntu?  I hope so, because you shouldn't go around 'sudo mount'ing stuff without first verifying the partition is right.  My bet is that the partition was 'dirty' and that's why Ubuntu would not automount it but Windows did.  It would also explain the gobbledeygook files and such.

Apologies for the rather late reply.
No I am afraid I have not done
'fdisk -l'.

I assume that this is not just a command typed in the terminal, as when I do that it just drops down.

Yes I feel you are right, that the partition is 'dirty'. It was created in Windows using their partition maker.
I have gathered that that is not a very good idea ;(

Oh dear, as I know hardly anything about all this, any suggestions as to how I can clean it all up nicely?

Kind regards

John

---


---
title: "HOW-TO: Increase performance on ext3 with dir_index"
date: 2005-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by Lovechild on 2005-05-28
dir_index is a hashed b-tree implementation for ext3, it's riskfree (Fedora has shipped several releases defaulting to it without incident), and adds a bit of performance to your filesystem.

to update an existing partitions:
0) open a terminal or enter cli
1) sudo tune2fs -O dir_index /dev/hdXY (where X indicates device, normally a and Y indicates partition, normally 1)
2a) sudo updatedb
alternatively, unmount and do
2b) sudo e2fsck -D /dev/hdXY

Wasn't that easy?

---

### Post by Kyral on 2005-05-28
Cool. I don't knwo if it WORKED, but it hasn't broken my system yet (Then again, I don't know how to tell if it worked :P)

---

### Post by henriquemaia on 2005-05-28
Is there a way to measure the perfomance gain?

Thanks a lot, though.

---

### Post by Moobert on 2005-05-28
[QUOTE=henriquemaia]Is there a way to measure the perfomance gain?

Thanks a lot, though.[/QUOTE]

sudo hdparm -Tt /dev/hdX

may do the trick

---

### Post by Lovechild on 2005-05-28
First, I'm sorry I forgot to mention

sudo tune2fs -l /dev/hdXY | grep dir_index

will show if the given partition has dir_index enabled.

Secondly, to benchmark I would use bonnie++

-edit-

I filed a bug with Ubuntu to have dir_index considered as the new default for Breezy, let's see what they have to say - bug 11284 for those interested.

---

### Post by dresnu on 2005-05-29
I get a segmentation fault when doing sudo tune2fs -O dir_index /dev/hdXY...

---

### Post by dresnu on 2005-05-29
ow! and yes I changed the X and Y to the right values  :smile: 
lol

---

### Post by cowlip on 2005-11-08
Hey, this still works great in Breezy

---

### Post by bishwo on 2006-04-16
did this in breazy and ended up unable to hibernate
could somebody help me with this cuz I realy really need hibernate.
But it did speed up my computer

---

### Post by Hikaru79 on 2006-06-02
Is the tune2fs part supposed to take only a fraction of a second to complete? I was expecting something more drawn-out :P

---

### Post by lzap on 2006-06-20
Of course it works :-)

Btw dir_index do not increase speed of continous reading, but reading many files in one directory (e.g. thousands of e-mails in my mail home directory).

---

### Post by Schuttwegraeumer on 2007-04-23
> **Lovechild said:**
> dir_index is a hashed b-tree implementation for ext3, it's riskfree (Fedora has shipped several releases defaulting to it without incident), and adds a bit of performance to your filesystem.

to update an existing partitions:
0) open a terminal or enter cli
1) sudo tune2fs -O dir_index /dev/hdXY (where X indicates device, normally a and Y indicates partition, normally 1)
2a) sudo updatedb
alternatively, unmount and do
2b) sudo e2fsck -D /dev/hdXY

Wasn't that easy?

How can I acitivate B*trees on a ext3 on a LVM Set?
This index is not setable in the aditional settings for the FS in the alternate install programm.

Can I do point 1 and 2a without unmounting?
2b is a alternative for what? Only the ubdatedb or point 1 and 2b?

---

### Post by Schuttwegraeumer on 2007-05-13
The -D option in the e2fsck command is in the man page of Ubuntu, but not in the man page of my Knoppix from 2007-01-04.
Since which version is the optimisation includet?

---

### Post by regeya on 2007-08-14
Be careful on non-x86 platforms, though.  I have a ppc machine here that corrupts the index right away.  I've yet to find the real problem, but it's damned annoying. :-P

---

### Post by foureight84 on 2007-08-16
i'm pretty sure this doesn't work.

> 
[02:16:33 AM wasabi ~]$ sudo hdparm -Tt /dev/sda1

/dev/sda1:
 Timing cached reads:   1336 MB in  2.00 seconds = 668.05 MB/sec
 Timing buffered disk reads:   62 MB in  3.02 seconds =  20.54 MB/sec


THIS IS AFTER
> 
[02:16:33 AM wasabi ~]$ sudo tune2fs -O dir_index /dev/sda1
tune2fs 1.40-WIP (14-Nov-2006)
[02:16:33 AM wasabi ~]$ sudo updatedb
[02:16:33 AM wasabi ~]$ sudo hdparm -Tt /dev/sda1

/dev/sda1:
 Timing cached reads:   1182 MB in  2.00 seconds = **591.41 MB/sec**
 Timing buffered disk reads:   62 MB in  3.01 seconds =  20.60 MB/sec
[02:16:33 AM wasabi ~]$ sudo hdparm -Tt /dev/sda1




---

### Post by achimthomas on 2008-08-19
> **Lovechild said:**
> dir_index is a hashed b-tree implementation for ext3, it's riskfree (Fedora has shipped several releases defaulting to it without incident), and adds a bit of performance to your filesystem.

to update an existing partitions:
0) open a terminal or enter cli
1) sudo tune2fs -O dir_index /dev/hdXY (where X indicates device, normally a and Y indicates partition, normally 1)
2a) sudo updatedb
alternatively, unmount and do
2b) sudo e2fsck -D /dev/hdXY

Wasn't that easy?
No, that isnt easy, because is it wrong.
the Step "2a" has nothing to do with the filesystem updatedb is not for the filesystem it is for 'locate'

The only way that work is 2b!!!
but you should write e2fsck -fD /dev/hdXY
you should check the changes in your filesystem...

--

---

### Post by FractalizeR on 2008-09-22
> **foureight84 said:**
> i'm pretty sure this doesn't work.



THIS IS AFTER

Before expecting some magic from dir_index, it is good to find out what this thing actually does. dir_index enabled decreases ONLY time spent to find a file with particular name in a directory. It DOES NOT speed up reading from a file in any way.

---


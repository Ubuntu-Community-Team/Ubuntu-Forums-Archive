---
title: "Deleting Ubuntu"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by Reuben702 on 2011-10-02
I installed Ubuntu (10.04 I think)  sometime last year and now I wanted to switch back but it wasn't in my boot list so I downloaded 11.04 and installed it.
Now whenever I start up my laptop on the boot list there is Windows 7, Windows Vista which was normal, Ubuntu 11.04, Ubuntu 11.04 Safe Mode which is normal, but now it seems that the old **10.04** is back with three different boot modes which are normal, safe mode and one other I cant remember. In total I have **8** boot modes.
I want to remove my old 10.04 version of Ubuntu **BUT** keep 11.04.
How do I do this?
I am very new to this and while I am no noob, all this is looking very confusing on youtube with partitions and all that.

Thank you.

---

### Post by Reuben702 on 2011-10-02
And to clarify, I do not only want to remove 10.04 from the boot list, I want to completely remove it from my computer as it is taking up to much space.

---

### Post by apollothethird on 2011-10-02
> **Reuben702 said:**
> And to clarify, I do not only want to remove 10.04 from the boot list, I want to completely remove it from my computer as it is taking up to much space.

Unless you browse around your partitions and see it, the boot list is the only thing you may have of it.

You can use disk utility (Dash menu -> Disk Utility) to browse your partitions and delete the partitions you don't want.  You can tell from Disk Utility which partitions are mounted and being used.  If you have access to all your data and a partition isn't mounted, then you might not miss it.

You can also run to see which partitions you're using at boot time and preserve the ones containing your important data (11:04).

Finally, keep in mind that when you perform an install, unless you specify a different partition, the other space is over written.  This is the folders:

/bin
/usr/bin
/sbin
/usr/sbin
/dev
/lib
/etc
... and some others

When performing an installing, you'll be prompted that those directories will be removed and replaced with the new OS.  So as far as I can see, there's nothing to delete on the 11:04 partition that you're using.

By the way, I'm curious.  Are you able to actually boot to the old 10.04 OS?

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Reuben702 on 2011-10-02
I just tried and 10.04 booted up fine, it would seem it is all still there.
I went into disk utility and had a look at my hard disk but iv got no idea what is all means.
I took a screen shot:
[http://imageshack.us/photo/my-images/853/screenshotzf.png/](http://imageshack.us/photo/my-images/853/screenshotzf.png/)

Also when I took a proper look at the boot list I have Ubuntu 8 as well, I installed that years ago and forgot.

So I currently have installed: Ubuntu 11.04, Ubuntu 10.04, Ubuntu 8, Windows 7, Windows Vista.

Could you help me remove 10.04 and 8 please?

---

### Post by -kg- on 2011-10-02
According to your screenshot there are two Linux installations (the two ext4 partitions and their associated swaps, in an Extended partition) and 1 Windows installation (the Primary NTFS partition) on your computer.  If you're showing all those OS selections in your GRUB menu, then they're extraneous entries in that menu, unless you have another hard drive that's not shown.

If you're showing all those OSes in your GRUB menu, then you need to boot into 11.04, launch a terminal window, and run the following command:

```
sudo update-grub
```

Once you've run that command, reboot and see if the entries are removed from the menu.  By the partitions listed on your hard drive, you should only have 3....11.04, 10.04, and one Windows selection.

On to removing 10.04...

You will need to determine which of those partitions is actually 10.04, and then delete that partition and its associated swap partition.  I see that one is 38 GB and the other is 87 GB.  Find out which is which, then delete the appropriate ones.  Once you do that, you'll want to expand the remaining ext4 partition into the free space, giving you the extra space for use.  Then reboot back into 11.04 and run the above command again.

One thing I haven't mentioned (but you likely already know)...you can't perform the expansion of 11.04 from the installation.  You'll have to do that from a Live CD/USB.

---

### Post by Reuben702 on 2011-10-02
Wow, I updated GRUB and instead of them disappearing  now I have **11**!!!
I've uploaded my boot list, forgive my camera I could only make a really small picture.

[http://imageshack.us/photo/my-images/15/0310111542.jpg/](http://imageshack.us/photo/my-images/15/0310111542.jpg/)

Thank you.

---

### Post by apollothethird on 2011-10-03
> **Reuben702 said:**
> Wow, I updated GRUB and instead of them disappearing  now I have **11**!!!
I've uploaded my boot list, forgive my camera I could only make a really small picture.

[http://imageshack.us/photo/my-images/15/0310111542.jpg/](http://imageshack.us/photo/my-images/15/0310111542.jpg/)

Thank you.

You don't have to upload pictures, you should paste text between quote tags.

You can copy text by selecting it with your mouse, then right click and click copy.  You can paste the text by right clicking where you want to paste the text and clicking paste.

A code tag is: [ code ] text here [ /code ] (without the spaces.

Will you give the output of the following:

```

cat /proc/partitions
df -v

```

The output you give us will be better than trying to look at pictures.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Reuben702 on 2011-10-03
I know how to copy/paste but the boot list is on startup of the computer so I can not use the function.
For this: cat /proc/partitions

major minor  #blocks  name

   8        0  312571224 sda
   8        1  172674438 sda1
   8        2   11633664 sda2
   8        3          1 sda3
   8        5   84924416 sda5
   8        6    2881536 sda6
   8        7   37569536 sda7
   8        8    2880512 sda8


For this: df -v

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             36979272  13760848  21339948  40% /
none                   1411216       720   1410496   1% /dev
none                   1417844       196   1417648   1% /dev/shm
none                   1417844       216   1417628   1% /var/run
none                   1417844         0   1417844   0% /var/lock

---

### Post by apollothethird on 2011-10-03
> **Reuben702 said:**
> I know how to copy/paste but the boot list is on startup of the computer so I can not use the function.
For this: cat /proc/partitions

major minor  #blocks  name

   8        0  312571224 sda
   8        1  172674438 sda1
   8        2   11633664 sda2
   8        3          1 sda3
   8        5   84924416 sda5
   8        6    2881536 sda6
   8        7   37569536 sda7
   8        8    2880512 sda8


For this: df -v

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             36979272  13760848  21339948  40% /
none                   1411216       720   1410496   1% /dev
none                   1417844       196   1417648   1% /dev/shm
none                   1417844       216   1417628   1% /var/run
none                   1417844         0   1417844   0% /var/lock

If you will put your output between code tags it'd be extremely easy for us to deal with.  I'm glad you can copy and paste.   The code tags are just as important.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Reuben702 on 2011-10-03
I know how to copy/paste but the boot list is on startup of the computer so I can not use the function.

```
cat /proc/partitions
```

major minor  #blocks  name

   8        0  312571224 sda
   8        1  172674438 sda1
   8        2   11633664 sda2
   8        3          1 sda3
   8        5   84924416 sda5
   8        6    2881536 sda6
   8        7   37569536 sda7
   8        8    2880512 sda8


```
df -v
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             36979272  13760848  21339948  40% /
none                   1411216       720   1410496   1% /dev
none                   1417844       196   1417648   1% /dev/shm
none                   1417844       216   1417628   1% /var/run
none                   1417844         0   1417844   0% /var/lock

---

### Post by apollothethird on 2011-10-03
> **Reuben702 said:**
> I know how to copy/paste but the boot list is on startup of the computer so I can not use the function.

```
cat /proc/partitions
```major minor  #blocks  name

   8        0  312571224 sda
   8        1  172674438 sda1
   8        2   11633664 sda2
   8        3          1 sda3
   8        5   84924416 sda5
   8        6    2881536 sda6
   8        7   37569536 sda7
   8        8    2880512 sda8


```
df -v
```Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             36979272  13760848  21339948  40% /
none                   1411216       720   1410496   1% /dev
none                   1417844       196   1417648   1% /dev/shm
none                   1417844       216   1417628   1% /var/run
none                   1417844         0   1417844   0% /var/lock

Your output is hard to read.  You didn't put the output that you pasted between code tags. Please notice that a code tag is made by:

[ code ]
Paste Text Here
[ /code ]

You see the brackets and word code in my text above because I placed spaces between the words.  If I remove the spaces it would look like this:

```

Paste Text Here

```Look at how my output looks when I perform the commands:

```

ljames@hera5:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  488386584 sda
   8        1  195311616 sda1
   8        2   20480000 sda2
   8        3  272593920 sda3
   8       16  488386584 sdb
   8       17  102400000 sdb1
   8       18    2048000 sdb2
   8       19  383936001 sdb3
ljames@hera5:~$ df -v
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            192245340 166336000  16143760  92% /
none                   1984416       696   1983720   1% /dev
none                   1995048       156   1994892   1% /dev/shm
none                   1995048       808   1994240   1% /var/run
none                   1995048         8   1995040   1% /var/lock
/dev/sda3            268316360 139096484 115590180  55% /mnt2/hera5data
/dev/sdb3            377910288 294491576  64221912  83% /mnt2/b3
ljames@hera5:~$ 

```I copied the text from the terminal screen.  Then I pasted it between code tags into the message.  If you would do this you would be showing kindness to us who are trying to decipher your text.  It'll make it much easier in giving support.

At a glad I'll be able to easily tell you what to do, then move own to another user having problems.

If you learn this concept, it'll make any other issues you have in the future also easy to be resolved.

I'm glad to help.  Thank you in advance for making it easier for me to help.

As for as booting, that doesn't matter.  The answer is resolved by using the output from the two commands I gave you.

By the way, if you wonder how your post is going to look before submitting it, you can click on preview.  If your code tags are correct the preview would show your pasted output in the same format as you see it on your terminal screen.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Reuben702 on 2011-10-03
Sorry I thought you just wanted me to put the code in the box
```

reuben702@reuben702-Compaq-Presario-CQ60-Notebook-PC:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  312571224 sda
   8        1  172674438 sda1
   8        2   11633664 sda2
   8        3          1 sda3
   8        5   84924416 sda5
   8        6    2881536 sda6
   8        7   37569536 sda7
   8        8    2880512 sda8
reuben702@reuben702-Compaq-Presario-CQ60-Notebook-PC:~$ df -v
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             36979272  14020512  21080284  40% /
none                   1411216       720   1410496   1% /dev
none                   1417844       112   1417732   1% /dev/shm
none                   1417844       224   1417620   1% /var/run
none                   1417844         0   1417844   0% /var/lock

```

---

### Post by apollothethird on 2011-10-03
> **Reuben702 said:**
> Sorry I thought you just wanted me to put the code in the box
```

reuben702@reuben702-Compaq-Presario-CQ60-Notebook-PC:~$ cat /proc/partitions
major minor  #blocks  name

   8        0  312571224 sda
   8        1  172674438 sda1
   8        2   11633664 sda2
   8        3          1 sda3
   8        5   84924416 sda5
   8        6    2881536 sda6
   8        7   37569536 sda7
   8        8    2880512 sda8
reuben702@reuben702-Compaq-Presario-CQ60-Notebook-PC:~$ df -v
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7             36979272  14020512  21080284  40% /
none                   1411216       720   1410496   1% /dev
none                   1417844       112   1417732   1% /dev/shm
none                   1417844       224   1417620   1% /var/run
none                   1417844         0   1417844   0% /var/lock

```

Looking at your output your root directory is in partition 7.  Also.  The only partition that you have mounted is partition 7.  This means that you are not using any of the other data on your hard drive.  You have suggested that you don't want the other data.  So if that's the case you can use disk manager to delete the other partitions.

You can boot to the other boot options and see which one gives and output for the root (which is "/").  Again, in this case it's partition 7.  If you want to keep one of the partitions that is root, then don't delete it.  Any of the partitions you don't want, just use Disk Utility to delete.

From your previous messages and this current output, partition 7 is the one that has the 11.04 installation that you want to keep.

I have other suggestions, but will try to keep this initial message short to give you a chance to grasp the concept, but this is the basic gist of what is involved.

Make sure you understand where your important data (installs) are before deleting a partition.  At present we know where Windows (sda1) is and Ubuntu 11.04 (sda7).

By the way the size of your windows partition is 177.  The size of your 11.04 partition is 37 gigs.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Reuben702 on 2011-10-03
OK so all I want to keep is Windows 7 and Ubuntu 11.04.
Could you please provide a step-by-step guide on how to remove the rest please?

Thank you.

---

### Post by apollothethird on 2011-10-03
> **Reuben702 said:**
> OK so all I want to keep is Windows 7 and Ubuntu 11.94.
Could you please provide a step-by-step guide on how to remove the rest please?

Thank you.

Use Disk Utility and select the partitions you want to delete.  Please make sure you don't delete the "Extended" partition.  That is a special partition that contains the other partitions.  Its identified by being on top.  The ones on the bottom of the Extended partitions are the ones you want to remove.  Again at present, partition 7 is the one with 11.04.  The partition number is the number you see after sda, as in sda7.

After you make changes to your partition table the numerical order will be different.  You'll probably have to repair this to boot the new order.  You can do this by running grub install from your Ubuntu Live CD.

If it doesn't boot you can run (in your case of the one hard drive):

```

grub-install /dev/sda

```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Reuben702 on 2011-10-03
I really don't want to mess anything up.
Could you please look at the picture I uploaded of Disk utility on page one and tell me which ones to delete?

---

### Post by apollothethird on 2011-10-03
> **Reuben702 said:**
> I really don't want to mess anything up.
Could you please look at the picture I uploaded of Disk utility on page one and tell me which ones to delete?

I looked at the picture.  My references was in regard to the picture.  Each of the blocks you see in the picture are partitions.  Click on one of the block and it'll tell you the partition number (ie: sda1, sda2, etc).

The partition sda1 is immediately selected in the picture.  If you want to explore options of a different partition click on one of the different blocks.  The only ones you want to be sure not to delete are, sda1 (which is Windows), sda7 (which is 11:04) and Extended (which is a container for partitions).  Any of the others have data you are trying to delete.

Feel free to ask for further clarifications.  But I'm certain if you click on the blocks and look at the various options you'll start to make sense out of the usage.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Reuben702 on 2011-10-03
There are two smaller partitions (8 and 6) which are "Swap Space".
What does this mean and should I delete them?

---

### Post by Reuben702 on 2011-10-03
[LEFT]And how do I get my Ubuntu 11.04 partition 7 to take all the space from the free space left from Ubuntu 10.04?

Thank you for all your help. 
):P
[/LEFT]

---

### Post by apollothethird on 2011-10-03
> **Reuben702 said:**
> There are two smaller partitions (8 and 6) which are "Swap Space".
What does this mean and should I delete them?

Windows will use the swap space like it was ram when the ram gets low.  Try to have about as much swap space as you have ram.  It'll improve performance.

> **Reuben702 said:**
> [LEFT]And how do I get my Ubuntu 11.04 partition 7 to take all the space from the free space left from Ubuntu 10.04?

Thank you for all your help. 
):P
[/LEFT]


The best program for changing the size of your partitions is gparted.  Select the partition you want to expand and drag the block to take up the available space using the gparted application.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---


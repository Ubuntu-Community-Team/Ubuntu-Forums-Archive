---
title: "[SOLVED] trying to delete - permission denied."
date: 2008-11-14
forum: New to Ubuntu
---

### Post by tadcan on 2008-11-14
So I was trying to use clonezilla, but I filled up my root to the max. and wasn't able to finish. I tried to do right click delete but was told access denied.

I can access root via the terminal and do it from there what command do I use. I guess the dreaded rm- rf might be needed.

---

### Post by Mardoct909 on 2008-11-14
There is a way to get nautilus to let you open files/directories as root. Nice easy graphical way to do it, or change the permissions so you can delete it as the user.  

[http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/](http://www.pendrivelinux.com/2007/10/02/how-to-open-files-as-root-via-a-right-click/)

rm as root is good enough to take out a single file, and rm -rf will take out a directory and everything within. It goes without saying, but wield them carefully. As a rule, if it isn't in the /home directory, you shouldn't touch it without knowing EXACTLY what it is..

---

### Post by Shazaam on 2008-11-14
If you want a visual version try this...
[CODE]gksudo nautilus[/CODE
This will open nautilus as ROOT.
Just remember, anything you do as root is permanent so be careful. You might want to backup the files (to cd/dvd, thumb drive, etc) before you delete anything.

---

### Post by tadcan on 2008-11-14
Thanks. I was able to delete the files in the folder, but not the folder. 

edit.I deleted the folder with shazaam's advice.

With disk usage analyzer I am still being told its 100% full. That the seize is 297GB. My whole linux partition is only about 50GB.

Edit. Ahh the high GB was because it included my external HD.

Is it normal that root is 100% full?

---

### Post by handydan918 on 2008-11-14
> **tadcan said:**
> 
Is it normal that root is 100% full?

No. Not normal, not OK.

EXT2/3 filesystems work best when at or below 90% capacity. Any higher and you seriously risk digital havoc.

---

### Post by bumanie on 2008-11-15
Output result of > df -h / > df -h /home

---

### Post by tadcan on 2008-11-15
```
tadcan@Quad:~$ df -h / 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G   37G     0 100% /
```

```
tadcan@Quad:~$ df -h /home 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G   37G     0 100% /
```

I have noticed to odd things happen. The first is when I book I should have two lines saying boot form CD/DVD. One for each drive, now only one is listed. 

In FF3, the small search bar in the toolbar doesn't work. 

Would they be examples of havoc being played with the system.

---

### Post by bumanie on 2008-11-15
Both / and /home are 100% full that is why nothing is working properly; (/ and /home are on the same partition). Post the output of > sudo fdisk -lu and we'll see if we can 'get some space' from somewhere to make a new partition and move /home to it. If you don't have extra space, you may have to copy your present partition to an external device.

---

### Post by CatKiller on 2008-11-15
> **tadcan said:**
> With disk usage analyzer I am still being told its 100% full... 

Is it normal that root is 100% full?

The disk usage analyser (Baobab) reports *usage*, not *disk space*. So it will always report / usage as 100%, since by definition everything that is used is as a subset of /. The sub-folders show the relative proportions of the amount that is used, not as relative proportions of what could potentially be used.

A lot of users get confused by this point.

So, yes, it is normal that Baobab reports / as having all the usage, and it's nothing to worry about.

It is not normal to have the / partition actually full.

EDIT: I've just noticed that your / partition is actually full.

```
sudo apt-get clean
sudo apt-get autoclean
``` are quick ways to free up some / space - they remove the downloaded package files that have been installed - the packages are cached in case you want to re-install them without having to download them again. If all your packages are installed properly, there's no reason to keep the cache.

Baobab will show you which directories have lots of usage - that might help you to make significant disk space savings. In particular, you might find that some log files have got very large. These are often in /var/log. You might also have a lot of usage that you don't need in your Home folder. Firefox cache, for example.

You said that you were using Clonezilla. Were you trying to make a copy of your / partition to an image that was also in your / partition? Removing the (partial) image that you've made will probably give you a significant chunk of space back.

---

### Post by Paddy Landau on 2008-11-15
A word of warning if you use Shazaam's method (gksudo nautilus).

When you delete, it won't actually remove the files, but instead put them into the Trash folder (i.e. deleted items).

To delete the files completely, you'll need to delete the contents of the Trash folder, too.

Go to nautilus using gksudo (gksudo nautilus), and delete all the contents of these two folders:

```
/root/.local/share/Trash/files
/root/.local/share/Trash/info
```HTH

---

### Post by CatKiller on 2008-11-15
> **Paddy Landau said:**
> A word of warning if you use Shazaam's method (gksudo nautilus).

When you delete, it won't actually remove the files, but instead put them into the Trash folder (i.e. deleted items).

That's a good point. You can bypass the Trash folder if you use Shift-Del rather than just Del.

---

### Post by tadcan on 2008-11-15
```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0008e7de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81931499    40965718+   7  HPFS/NTFS
/dev/sda2        81931500  1269761534   593915017+   f  W95 Ext'd (LBA)
/dev/sda3      1269761535  1347885629    39062047+  83  Linux
/dev/sda5        81931563  1269761534   593914986    7  HPFS/NTFS
```

Not sure if it said it there, but I know I have 55GB of unallocated space.

I also have a gparted live CD. I got this error during the loading. Buffer i/o error logical block 48082. 
I was trying to increase my NTFS, but I could only reduce them. 

I have deleted and checked the trash for the partial file from clonezilla. Not sure exactly what I did because it was the first time I tried it.

```
/root/.local/share/Trash/files
/root/.local/share/Trash/info
```

```
tadcan@Quad:~$ sudo -i
root@Quad:~# /root/.local/share/Trash/files
-bash: /root/.local/share/Trash/files: is a directory
root@Quad:~# /root/.local/share/Trash/info
-bash: /root/.local/share/Trash/info: is a directory
```

---

### Post by Paddy Landau on 2008-11-15
> **tadcan said:**
> I have deleted and checked the trash for the partial file from clonezilla. Not sure exactly what I did because it was the first time I tried it.
OK, to clear the *root* trash, one possible way is to do the following from terminal.
```
sudo rm -r /root/.local/share/Trash/files/*
sudo rm -r /root/.local/share/Trash/info/*
```To delete *your own* trash files, one possible way is to go to nautilus, choose menu options _G_o -> _D_eleted Items, and press the big button labelled "Empty _D_eleted Items".

---

### Post by tadcan on 2008-11-15
Ok I ran those commands and it worked. i.e not no error message.

Still not sure what nautilus is (averse as I am to reading manuals) I went to the trash window manager clicked on Go. But didn't see the Deleted Items, and press the big button labelled "Empty Deleted Items".

---

### Post by Paddy Landau on 2008-11-15
> **tadcan said:**
> Still not sure what nautilus is
Nautilus is the graphical file manager for Ubuntu.

One way to run nautilus is Places -> Home Folder. Another is to start terminal and type *nautilus*.

You may have a "Deleted Items" icon on your menu bar; if you have, you can just click it once to open nautilus to see your deleted items (and the "Empty Deleted Items" button).

---

### Post by metallicamike on 2008-11-15
this works like a charm:

```
sudo rm -r
``` and then drag whatever you are trying to delete (make sure to take away the quotes at the beginning and end of the directory!)

---

### Post by Shazaam on 2008-11-16
> **Paddy Landau said:**
> A word of warning if you use Shazaam's method (gksudo nautilus).

When you delete, it won't actually remove the files, but instead put them into the Trash folder (i.e. deleted items).

To delete the files completely, you'll need to delete the contents of the Trash folder, too.

Go to nautilus using gksudo (gksudo nautilus), and delete all the contents of these two folders:

```
/root/.local/share/Trash/files
/root/.local/share/Trash/info
```HTH

Thank you for adding that. Also you may need to do a shift+delete in root's trash (files and info) folders per CatKiller because if you don't nautilus will add a backup file to them.

---

### Post by tadcan on 2008-11-16
Ok I found nautiles. It takes up 73mb of space. 

What I dont understand is i am only using 9.8GB of my 36.7GB partition. So the home folder should have plenty of space to have operate properly. 

I still haven't seen a deleted 'items icon'. Could you post a screen shot so I can see it your your system?

Since I the files have deleted do I still have a problem with the /root being at 100% or is it this below.

```
tadcan@Quad:~$ df -h / 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G  9.9G   25G  29% /
tadcan@Quad:~$ df -h /home 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G  9.9G   25G  29% /
```


[quote=catkiller]The disk usage analyser (Baobab) reports usage, not disk space. So it will always report / usage as 100%, since by definition everything that is used is as a subset of /. The sub-folders show the relative proportions of the amount that is used, not as relative proportions of what could potentially be used.[/quote]

---

### Post by bumanie on 2008-11-16
You now have 25gb of space according to the above. If you like you can just do > df -hit show all partitions on the computer, including windows.

---

### Post by tadcan on 2008-11-16
```
tadcan@Quad:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              37G  9.9G   25G  29% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  208K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  2.8M  1.7G   1% /dev
tmpfs                 1.7G  104K  1.7G   1% /dev/shm
lrm                   1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile
```

I don't see windows?

I should mark this thread as solved. Its getting beyond its original question.

---

### Post by bumanie on 2008-11-16
Funny I see my windows when I put in that code. I have  a triple boot with vista/xp.

Filesystem            Size Used Avail Use% Mounted on
/dev/sda5             9.7G  3.0G  6.2G  33% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  216K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.8M 1005M   1% /dev
tmpfs                1008M  540K 1007M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6              29G  382M   27G   2% /home
/dev/sda2              31G  5.8G   25G  19% /media/XP
/dev/sda1              40G   20G   20G  51% /media/vista

I guess you should mark it as solved - you have sorted out what you wanted.

---

### Post by CatKiller on 2008-11-16
> **tadcan said:**
> Since I the files have deleted do I still have a problem with the /root being at 100% or is it this below.

You've got 71% free now. Everything should be working again.

---

### Post by Paddy Landau on 2008-11-16
> **tadcan said:**
> I still haven't seen a deleted 'items icon'. Could you post a screen shot so I can see it your your system?
Either...

[LIST]
[*]Start nautilus.
[*]Choose menu options *_G_o -> _D_eleted Items*.
[/LIST]
Or...

[LIST]
[*]Right-click your panel (where all your icons are).
[*]Select *_A_dd to Panel...*
[*]Scroll down to *Deleted Items*.
[*]Select it and press *_A_dd*.
[*]This will add a new icon to your panel, which you can click to open nautilus at your deleted items.
[/LIST]
Screenshot attached.

---

### Post by tadcan on 2008-11-16
Ubuntu is working normally now thanks.

So I'm in trash and I have a test document to delete. Here are the options under D I have to install. 

Could we be using different versions of ubuntu? I am using 8.10 32bit.

---

### Post by CatKiller on 2008-11-16
I'm not entirely sure what you're looking for. Your Trash panel icon is there in the bottom-right of your screenshot. It's also available as Trash in the side-panel of the Nautilus window of your first screenshot. From any file manager window you can select File -> Empty Deleted Items, or you can right-click on the Trash Panel applet and select Empty the Deleted Items Folder.

What exactly are you trying to achieve at this point?

---

### Post by Paddy Landau on 2008-11-17
> **tadcan said:**
> Could we be using different versions of ubuntu? I am using 8.10 32bit.
Yep, different versions. Fear not, though, because I can see them...

[LIST=1]
[*]Screenshot 1: If you have a look at the very bottom-right corner of your screen, you'll see that the Trash panel is already there! It looks like an orange rubbish bin.
[*]Screenshot 2: It's called "Trash" under your "Go" menu, and also on the left panel (as CatKiller already pointed out).
[/LIST]

---

### Post by tadcan on 2008-11-17
Ahh ok. So what happened was I was getting very pedantic since stuff wasn't _exactly_ the same as you described.

---


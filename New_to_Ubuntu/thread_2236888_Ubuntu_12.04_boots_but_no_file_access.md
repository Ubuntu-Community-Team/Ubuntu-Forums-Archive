---
title: "Ubuntu 12.04 boots but no file access"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by Greenstar110 on 2014-07-29
Apologies if this has already been covered,but am tearing my hair out and can find no immediate answer or past post.
It seems very basic. 
I have an Ubuntu 12.04 install on a PC with Gnome Classic. It boots up, and after entering the password shows logged in under my name and as administrator. Not Guest. I have tried the options of various desktops on the boot page, but all are similar.
Although the jpg is in it's usual place in the home file, my wallpaper was not displayed. I corrected that.
Applications are all there, many installed over the last couple of years, and they run.

The issue. Files are shown, but Documents, Videos etc are entirely blank, and properties shows as empty. They should have many Gb of files. All are on the same partition and hard drive as the system. Many are backed up, but have not done so for downloaded material as I have not had a usb stick big enough. I now have, but can't get to the files!
Firefox runs fine, but none of my favourites, bookmarks, etc, are shown, nor my home page - all the post install personalisations have gone.
I carried out a boot repair with CD, but no change, still the same scenario. I booted from an install CD, 12.04, and my files are shown, but 'permissions are denied', so cannot open/back them up. 

Sorry, but am a computer dyslectic, and struggle with command lines.

Any insights appreciated. What the heck is going on?

---

### Post by Bucky Ball on 2014-07-29
What happened? Did you switch it on and it was like this after having worked fine or is this a fresh install? Please give more detail about how this problem came about, please. Did you update/upgrade then the computer was like this? ;)

---

### Post by Greenstar110 on 2014-07-29
Yes, all was fine. I have had a problem with the multiple workstations - icon lost and when the screen spills over can't get to the documents on other workstations - but I got used to living with that. As I say, everything seems to work now, it's just that my files are not shown.
Now, here's something I hadn't noticed. Lower right hand corner, the desktops/workstations - icon divided into four - is now shown, and works. That was broken before I had this issue! I hadn't asked it to do an update, and past updates haven't fixed it. I wonder if my boot repair did that. How bizarre. Screenshot below.
Sorry, I need to be clear -this is an install I have had several years, and updated occasionally. I am not totally, absolutely sure my docs are on the system partition, but pretty sure, as I remember not wanting to fiddle with partitions, and chose the most straightforward install possible. Anyway, they were certainly in the 'Document', Video, Download, etc, folders.

---

### Post by ajgreeny on 2014-07-29
I am sorry if you do not want to use the terminal, but it will be a great help if you can run the command ```
ls -l /home/$USER
``` in a terminal and then show us the output from that as I am wondering if ownership of your /home folder or partition has changed to something other than yourself.

It should show a list of files and folders that looks something like this below for everything in your home:-
```
drwxr-xr-x  2 *username username*      4096 Jul 29 15:50 Desktop/
drwxr-xr-x 11 *username username*     12288 Jul 29 17:16 Documents/
drwxr-xr-x 17 *username username*     12288 Jul 29 11:50 Downloads/
```
but where I show "username" it should show your own username that you use to login.

---

### Post by Greenstar110 on 2014-07-29
OK Aj, this is what I get:
( I hope I have been really stupid and just hit a key I don't know about)
Is it significant then that I am logged in, apparently, as Tony Mitchell, and the terminal shows username as Tony? I cannot see how to log in as anything else - only the one account is shown under 'switch user account'.

---

### Post by ajgreeny on 2014-07-30
Well everything there seems to belong to you, and as you say the terminal shows you logged in as tony. Please note [COLOR=#ff0000]t[/COLOR]ony with a lower-case t, Linux is case sensitive and I don't think usernames can use uppercase letters, so make sure you always get all that correct.

You see how easy it can be to use the terminal for things such as this, and how much info we can get from a simple command like that.  Now I would like you to run the command ```
ls -l /home
``` to see if there is another user (is that possible?) where all your lost files could now be residing for some reason.

---

### Post by Greenstar110 on 2014-07-30
No, I don't mind learning. In case it matters, when I log in, I just enter my password. There is no option I see on booting to choose an account, other than top right corner, once logged in. The only possibility of other users - there is only me here - is from previous installs, as i have had several on this machine, and I do get a short list when booting.
This is the result:

tony@tony-G31M-ES2L:~$ ls -l /home
total 40
drwx------ 55 tony tony 36864 Jul 30 13:43 tony
tony@tony-G31M-ES2L:~$

---

### Post by ajgreeny on 2014-07-30
Nothing wrong there either.

So lets look for a file that you can remember the name of but that is no longer available anywhere that you can find.
First update the database of all files on the computer with ```
sudo updatedb
```
Now using a filename that you can remember but cant find use ```
locate -i *filename*
```The -i option ignores the case of letters used. Try that for a few files and if nothing is listed try using sudo for the same locate commands ```
sudo locate -i *filename*
```

---

### Post by Greenstar110 on 2014-07-30
This is what I get - no files shown?  I use the password I have used for logging in, and also installing software, etc.
tony@tony-G31M-ES2L:~$ sudo updatedb
[sudo] password for tony: 
tony@tony-G31M-ES2L:~$

---

### Post by Greenstar110 on 2014-07-30
Just to add to this, I have booted up again from an Ubuntu live CD. This shows my 245Gb hard drive, and on that a 'home' folder, within that the folder 'tony'. Properties shows only 36.9Kb in there. I can't access the folder, permissons not mine, but within should be my documents, videos, music etc, well over 100Gb of material. Should there be evidence of these? Can I access them to back up via the CD?

---

### Post by ajgreeny on 2014-07-30
OK, still using the live system open a terminal and run command **sudo -i** followed by command **nautilus** to open the file manager with root permissions (so be VERY CAREFUL).
This will allow you to search fully in those folders that you could not open before, and let you see fully what is on the computer hard disk.  It looks horribly as though all your files and folders have been deleted in some way, I'm afraid.

Show us also the output of command ```
sudo fdisk -l
``` and finally a screenshot of a gparted screen, which is on the live system would also be helpful as it may show the layout of the partitions on the machine.

---

### Post by Greenstar110 on 2014-08-01
Sorry, I did n ot notice a pge 2!
Here we are :
tony@tony-G31M-ES2L:~$ sudo -i 
[sudo] password for tony: 
root@tony-G31M-ES2L:~# nautilus 
Initializing nautilus-gdu extension
Initializing nautilus-dropbox 1.6.2
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

And then:tony@tony-G31M-ES2L:~$ sudo fdisk -l
[sudo] password for tony: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a1483

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   477947903   238972928   83  Linux
/dev/sda2       477949950   490233855     6141953    5  Extended
/dev/sda5       477949952   490233855     6141952   82  Linux swap / Solaris

Disk /dev/sdb: 15.5 GB, 15535702016 bytes
23 heads, 23 sectors/track, 57359 cylinders, total 30343168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           11312    30343167    15165928    c  W95 FAT32 (LBA)
tony@tony-G31M-ES2L:~$[ATTACH=CONFIG]255188[/ATTACH]

---

### Post by ajgreeny on 2014-08-01
Well, it looks as if all your files are now gone, I'm afraid.

I do not fully understand your description of "workstations" in post #3, but I think you mean the workspaces which are not enabled by default in unity 14.04, and I can't remember how to enable them as I do not use unity at all.  However, I see no reason why that should have anything to do with your lost files.

---

### Post by Bucky Ball on 2014-08-01
> **ajgreeny said:**
> Well, it looks as if all your files are now gone, I'm afraid.



Just to confirm that. Yep, looks like you have Ubuntu installed and that's it, unless you have a /dev/sdb device with your files on it. ;(

---

### Post by Greenstar110 on 2014-08-02
Ok, so if this is so I could do with knowing how so as to prevent reoccurrance.
There appear to be several possibilities. Is it possible to establish which?
Spontaneous deletion of all files conducted without warning by Ubuntu, or system error which has done the same. Seems rather a serious glitch which perhaps needs looking at, it would certainly put me off Ubuntu. Nothing in trash.
Someone hacked in and deleted my files. Seems unlikely, and why leave the system intact?
A virus.

What to do? I have a seemingly functional system that is customised and taken many days to set up. I am reluctant to do a complete reinstall, but how else to be sure nothing malicious remains? Similarly, if I back it all up, how to avoid copying the glitch?

The odd thing, i find, is that all the 'personal' alterations have gone. Files, and Thunderbird history and favourites, wallpaper (yet the image was not deleted, remained in home whilst the files within home vanished). The fact that two disconnected batches of things, files and favourites, are involved, makes me wonder if this is something to do with user account - is it absolutely certain those files are gone?

Incidently, I have Gnome installed - I couldn't get on with Unity.

many thanks for your comments.
Tony

---

### Post by Greenstar110 on 2014-08-02
Just to add to this .... the files can't have 'gone'. It takes time to delete something, and these were tens of gigabytes. So surely, they are 'misplaced' ... where does linux stand on file recovery?

---

### Post by Bucky Ball on 2014-08-02
Have a read here:

[http://www.howtoforge.com/data_recovery_with_testdisk](http://www.howtoforge.com/data_recovery_with_testdisk)

... and for me clues and background, here:

[https://duckduckgo.com/?q=testdisk](https://duckduckgo.com/?q=testdisk)

First of all, don't use the computer hard drive. The more you use it, the less chance you have of recovering files.

If a partition is reformatted, no, technically the data is not gone. Where it lives is, though, mark as read to write to. Therefore, if you start writing to it you will write over the data.

---

### Post by ajgreeny on 2014-08-02
> The odd thing, i find, is that all the 'personal' alterations have gone.  Files, and Thunderbird history and favourites, wallpaper (yet the image  was not deleted, remained in home whilst the files within home  vanished). The fact that two disconnected batches of things, files and  favourites, are involved, makes me wonder if this is something to do  with user account - is it absolutely certain those files are gone?
I think the loss of all your bookmarks, email, etc etc is because all those are stored in files in your /home folder or partition, and with a few exceptions of files that have perhaps been added later, your /home looks as if it has now gone and been replaced by a new /home.

When you changed from unity to the gnome-desktop, how did you do it?  That seems to be the most likely time at which this loss occurred.

---

### Post by Greenstar110 on 2014-08-02
No, I have been using gnome for a year at least. The last thing I did was watch Youtube, before logging off. All seemed well until I started up the next day.

---


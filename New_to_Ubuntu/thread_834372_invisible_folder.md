---
title: "invisible folder"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by belh4wk on 2008-06-19
hi, i'm new here but i was wondering
i just recently ('bout a week or 2) created a folder on an external usb-drive
now, i want to move some pics to it but i can't find it
so i'm thinking, i must've deleted it or so, and now, when i try to create the folder again, the system says that i can't use the name 'cause it's already in use on the drive...
which is odd to say the least because i can't find it anywhere
i haven't plugged in my hdd on a 'normal' pc or anything
the folder most certainly isn't hidden (i've tried turning on the "show hidden files" option but alas)

simply put, i created a folder, i know it's there, i know i haven't removed it, i know it's not hidden but when recreating the folder using the same name, i can't because the name is in use, although i can't find the folder ANYwhere...
any ideas as to where i could find it or 'unhide' it?

help would be very much appreciated...
i've tried looking around on this forum/google but can't seem to find anything relevant

---

### Post by Inxsible on 2008-06-19
What type of filesystem do you have on that drive?

Are you trying to create a folder from Ubuntu? If you do not have any data in the folder you could just try this from a terminal```
sudo rmdir <path to the folder>
```then try creating the folder again.

---

### Post by DGortze380 on 2008-06-19
first, please don't type rm ANYTHING (including rmdir) unless you know what the command does and what you are removing.

open a terminal, and move to your usb drive. You said you're new to linux so I'm going to walk you through it. Sorry if you already know how:


1) Open a Terminal (Accessories>Terminal)
2) You should be in your home directory ( /home/*username)
3) Type:

         ```
 cd /dev 
```

         ```
 ls 
```
   
         This will display all the files and folders in the directory /dev
         Your USB drive should be listed there, I can't tell you the name, it will vary between drives.
         If you can't find the drive try the follow:

        ```
 cat /etc/fstab 
```
       
        Your device should be listed in that file. Type q to quit.
        Once you know the name of your device and are in /dev type the following:

        ```
 cd *name_of_device 
```

       ```
 ls -al 
```

      The folder you created should now be shown in the list on the screen. check the permissions, on the very left of the screen it should say something like DRWX ---- ----. Doesn't matter if there are dashes or something replacing the dashes for what you're trying to do. Post back after you check that.

---

### Post by belh4wk on 2008-06-19
> **Inxsible said:**
> What type of filesystem do you have on that drive?

Are you trying to create a folder from Ubuntu? If you do not have any data in the folder you could just try this from a terminal```
sudo rmdir <path to the folder>
```then try creating the folder again.

that's the problem
i do have data in it...

how can i just access the drive/folder from the terminal?
(stupid question i know... i know how to do it in dos-based systems but unix is new to me)

---

### Post by Barrucadu on 2008-06-19
Try just opening a file manager there:
```
nautilus /path/to/the/folder
```

Or you could try renaming it:
```
mv /path/to/the/folder /path/to/the/folder2
```

Or even move everything out of it:
```
mv /path/to/the/folder/* /path/to/the/destination
```

---

### Post by Inxsible on 2008-06-19
> **belh4wk said:**
> that's the problem
i do have data in it...

how can i just access the drive/folder from the terminal?
(stupid question i know... i know how to do it in dos-based systems but unix is new to me)Have you tried hitting Ctrl + H, that should show you the hidden files and folders in nautilus. See if that works first.

---

### Post by belh4wk on 2008-06-19
ok, i managed to access the drive through the terminal
problem is when trying to acces the folder in question (i can see it)
it gives me an input/output error... (it actually gives me that error for that specific folder from the moment that i access the drive...)

is there a way to repair it?

---

### Post by DGortze380 on 2008-06-19
what is the exact error? it gives it to you when you cd to the drive? not when you try to cd to the folder?

try typing:
cd ..
ls -al

what are the permission for the drive?
cd to that drive. what are the permissions for the folder?

---

### Post by Dedoimedo on 2008-06-19
Hello,

Do you know the name of that folder?

If so, then please do the following:

First, type:

sudo fdisk -l

This will display all your hard disks. Identify your external hard disk (possible by size) - or by notation, if you are familiar with Linux hard disk notation.

In a nutshell, Linux notation goes likes this:

IDE drives begin with hd, SCSI (SATA) drives with sd.
Drives are numbered by letters a b c etc. Thus for example, if you only have once hard disk, it will be hda or sda. If you have two, then it will be hda, hdb or sda, sdb and so forth.

Your external drive will probably be something like hdb, hdc or maybe sdb or sdc.

Now, once you have identified the hard disk (let's say sdb), do the following:

cd /mnt
sudo mkdir temp-mount

This will be a mount point to which we will mount the hard disk.

It is NTFS, I presume?

Now, let's mount the drive to our above mount point:

For NTFS:

sudo mount -t ntfs /dev/sdb /mnt/temp-mount

For Linux ext3:

sudo mount -t /dev/sdb /mnt/temp-mount

Now, let's see what's there:

cd /mnt/temp-mount

find -type d <folder-name>

Or find -type d .<folder-name> <---- mark the dot!!

See if anything comes up. If it does, then it's there.

Simply change to it:

cd <folder name> or cd .<folder-name>

See if this helps.

Cheers,
Dedoimedo


P.S. If you can't mount the device itself, try mounting its partitions. They are listed as hda1, hda3, sdb1, sd5 etc ...

---

### Post by belh4wk on 2008-06-19
> **DGortze380 said:**
> what is the exact error? it gives it to you when you cd to the drive? not when you try to cd to the folder?

try typing:
cd ..
ls -al

what are the permission for the drive?
cd to that drive. what are the permissions for the folder?

here's what terminal outputs when ls'ing to the drive

h4wk@H4Ubuntu:/media/LACIE$ ls -a
ls: cannot access MAITE: Input/output error
.                  FOTOS       PROGRAMS                   TEKST
..                 GAMES       RECYCLER                   Thumbs.db
4041163563960.txt  GSM         SITES                      VIDS
DLZ                INCOMPLETE  sqmdata00.sqm              VIS
DLZ LIME           LEXIE       sqmnoopt00.sqm             VProRecovery
DRIVERS            MAC         STUFF
ehthumbs_vista.db  MAITE       System Volume Information
FONTS              MUSIC       TEKENINGEN

---

### Post by DGortze380 on 2008-06-19
thats odd. I'm going to have to defer to someone else here, not sure whats up. you did type ls-al in the terminal and not ls -a right? Do you know what format the drive is?

---


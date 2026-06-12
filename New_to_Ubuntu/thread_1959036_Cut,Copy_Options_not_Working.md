---
title: "Cut,Copy Options not Working"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by pras8421 on 2012-04-15
Hey,

I have ubuntu 11.10 oneric installed in my computer.

Cut,rename,move to thrash and some more options are not being highlighted,even the copy option is not working,even if I copy,I can't paste later whereas I can do all these only in Home.

I have got no idea to overcome,........

I had to stop the updating being done because of the bad internet connection.can it be the reason for this??

---

### Post by bbemmerful on 2012-04-15
Also some files require permission try [gksudo nautilus]. Copy and paste to say your themes folder in /usr/share/ or you could use the terminal.

---

### Post by pras8421 on 2012-04-19
prasanna@ubuntu:~$ gksudo nautilus
** (nautilus:2729): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension

--- Hash table keys for warning below:
--> inode/directory
--> prasanna
--> l2053
--> l2054
--> root
--> Prasanna

--- Hash table keys for warning below:
--> file:///media
--> file:///
Shutting down nautilus-gdu extension

(nautilus:2729): Eel-WARNING **: "unique eel_ref_str" hash table still has 6 elements at quit time (keys above)

(nautilus:2729): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time (keys above)
I got this,and no improvement.......

---

### Post by flurospar on 2012-04-19
From where are you trying to copy files? From your home folder? Or from system folders like /bin, /usr, /var etc?

Reinstall nautilus and see if it works:

```

sudo apt-get purge nautilus && sudo apt-get install nautilus

```

---

### Post by audiomick on 2012-04-19
> **pras8421 said:**
> prasanna@ubuntu:~$ gksudo nautilus
** (nautilus:2729): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension

--- Hash table keys for warning below:
--> inode/directory
--> prasanna
--> l2053
--> l2054
--> root
--> Prasanna

--- Hash table keys for warning below:
--> file:///media
--> file:///
Shutting down nautilus-gdu extension

(nautilus:2729): Eel-WARNING **: "unique eel_ref_str" hash table still has 6 elements at quit time (keys above)

(nautilus:2729): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time (keys above)
I got this,and no improvement.......

I get that ouput
```
mick@mick-MS-7345:~$ gksudo nautilus
Initializing nautilus-gdu extension
** (nautilus:3053): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged

--- Hash table keys for warning below:
--> l2069
--> root
--> inode/directory

--- Hash table keys for warning below:
--> file:///
Shutting down nautilus-gdu extension

(nautilus:3053): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:3053): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time (keys above)
mick@mick-MS-7345:~$ 

```

when I start an instance of Nautilus using gksudo and then close it. This is normal, and I assume that this is also exactly what you did.

> **flurospar said:**
> From where are you trying to copy files? From your home folder? Or from system folders like /bin, /usr, /var etc?

Reinstall nautilus and see if it works:

```

sudo apt-get purge nautilus && sudo apt-get install nautilus

```

This is the relevant question: where are you trying to copy to or from? Some files and folders need root permissions to be accessed. 

I am not sure that you need to reinstall nautilus. I am, at least, not yet convinced that is broken.

When you say "no improvement", do you mean that you also could not perform the operations you want to perform in the instance of nautilus that opens up after doing 
```
gksudo nautilus
```
?

If this is the case, then maybe something is broken. If not, depending on where you are trying to write to, maybe there is nothing broken.

---

### Post by audiomick on 2012-04-19
One more thing:


> **pras8421 said:**
> ...I had to stop the updating being done because of the bad internet connection.can it be the reason for this??

Were you able to cleanly cancel out of the update process? If so, there shouldn't be any problems, normally. The update manager should be able to keep track of this.

If you had to stop the process without being able to stop it cleanly, there might be a problem.

---

### Post by pras8421 on 2012-04-19
As my net is pretty slow,....it got stuck like this......

---

### Post by flurospar on 2012-04-19
Reinstall might be the way to go. Nautilus is < 3 MB, it shouldn't take much time even on dial-up.

---

### Post by pras8421 on 2012-04-19
yeah......the speed is varying from 1 kB to 10 kB.....

---

### Post by pras8421 on 2012-04-19
What does happen if i close the home that has opened with the teminal??

---

### Post by jerome1232 on 2012-04-19
It's not stuck at downloading, based on that screenshot nautilus reinstalled successfully and you have a root nautilus open.

Pertaining to your original question, as others have hinted, normally you are only allowed full access to your users home, if you need to do file operations elsewhere (really no need to, as daily operations as a desktop user don't require access to anything but your home) then you'll need to use sudo in a terminal, or gksu nautilus, and only use them when needed.

---

### Post by audiomick on 2012-04-19
> **pras8421 said:**
> What does happen if i close the home that has opened with the teminal??

By this, I assume you mean the instance of Nautilus that you opened using
```
gksudo nautilus
```

Nothing happens when you close it. It is just an instance of the file manager. The only real difference is that it is opened in such a way that you have root priviliges in there.

Because you have root priviliges in this instance of Nautilus, you should in fact close is as soon as you are finished doing whatever specific think it is that you opened that instance for. The reason for this is, if you accidently tell it to do something like erase important system files, it will just do it without asking for a password or anything. Working as a matter of course with root privilegs, as opposed to only using root privileges when you specifically need to, takes away some of the inherent security of a linux system.

---

### Post by pras8421 on 2012-04-21
In fact,Mine is Dell Inspiron(Laptop) and Windows home basic is given with it.
I unallocated  some memory from my hard drive and installed Ubuntu in the system so that I can access all the partitions. Of curse,I got Ubuntu loader instead and I was accessing all the partitions of the hard drive......
That day as I've already explained something happened and presently I,m unable to cut or copy or create new folder in it etc........

---

### Post by pras8421 on 2012-04-21
I came to know one more thing now...I can do all the operations in the drives that are in FAT32 format......As partitions in the hard drives are in NTFS format,the options ain't working........

I could copy data from any partition(only copy,because cut option is not being highlighted)to pen drive viz in FAT32(I didn't check for other formats) format and not to the same of NTFS format......
I want all the operations happen even on NTFS file system,..
How can I do that???

---

### Post by pras8421 on 2012-04-21
I came to know one more thing now...I can do all the operations in the drives that are in FAT32 format......As partitions in the hard drives are in NTFS format,the options ain't working........

I could copy data from any partition(only copy,because cut option is not being highlighted)to pen drive viz in FAT32(I didn't check for other formats) format and not to the same of NTFS format......
In a FAT32 file system all the options are working......
I want the same to be happened even on NTFS file system,..
How can I do that???

---

### Post by pras8421 on 2012-04-23
Please suggest a solution because Ubuntu is my major OS....

---

### Post by audiomick on 2012-04-23
Have a look here

[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

Perhaps you are missing the ntfs-3G driver that is mentioned there. Open the software center and type "ntfs" in the search box. See if the package is installed. If it is not, you might like to install it and see if that helps. I can't promise that this will help, but that is all I can think of at this point.

---

### Post by pras8421 on 2012-05-04
In fact,in permission options,access files was selected.I couldn't change it as create and delete files and I was getting error message.....
Finally I upgraded 11.10 to 12.04,problem got solved. .

---


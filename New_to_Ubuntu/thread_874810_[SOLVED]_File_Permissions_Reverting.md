---
title: "[SOLVED] File Permissions Reverting"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by DLLong on 2008-07-30
I am converting a series of websites over to ubuntu/zencart.  I am  new to Linux and having a great time learning.  One of the cautions from zencart is to change the file permissions for configure.php in a subdirectory. So here's what I did based upon other postings.
1.  Opened the terminal and entered "sudo nautilus".
2.  Browsed to the file in question and opened properties.
3.  Went to the Permissions tab.

Now here's the problem.  If I use the drop down for Owner, Group or Others to change the permissions from "Read and write" to anything else, I can click or select "Read only" but then it reverts back to "Read and write".  

Can you help a newbie solve this problem?

---

### Post by Diabolis on 2008-07-30
I think that is safer to do it through the terminal, rather than open a "sudo nautilus".

The commands that you'll need are: **cd, chomd, ls**

**cd**
Navigate through folders.
*ex:* cd Desktop/

**ls -l**
List the contents of a file, one per line. This will show you the permissions of each file.

**chmod**
Will change the permissions of a file.
If used recursively over a folder, it will change the permissions of a folder and the permissions of all its content.

For example if you want to remove the "write" permission, you would type the command like this:
```
chmod -w *"file name"*
```

---

### Post by vanadium on 2008-07-30
Are you working on a file system that supports unix (Linux) permissions (ext3)? Windows file systems such as ntfs and fat do not support unix permissions.

---

### Post by DLLong on 2008-07-30
I tried your suggestions.  Let me take the second reply first.  Yes, I am trying to change the file permissions on ubuntu directly.
Here's what I tried:
1.  Navigated to the directory - dave@Aspenserver3:/media/disk/WSII/zencartfurn/includes
2.  Entered in chmod -w configure.php
3.  Received this in response:  chmod:  configure.php new permissions are r-xrwxrwx, not r-xr-xr-x
============
To check permissions, I entered: ls -l configure.php 
Received this in response:  -rwxrwxrwx 1 root root 3159 2008-07-29 13:20 configure.php
So this doesn't look like anything changed.
========
Since I'm still learning, I enter the same command as #2 above with this addition suspecting that it might have to do with the root permissions:  sudo chmod -w configure.php
I received the same response as #3 above.

More thoughts?

---

### Post by Diabolis on 2008-07-30
I would try with the verbose option to see if it throws any error messages.
```
sudo chmod -v -w configure.php
```

---

### Post by eightmillion on 2008-07-30
I would do this from the command line also. But if you do do it from nautilus, I would suggest using "gksudo nautilus". I suspect that using "sudo nautilus" may be the cause of your problem.

---

### Post by DLLong on 2008-07-30
I entered in your suggestion of: sudo chmod -v -w configure.php and received this in reply.

mode of 'configure.php' change to 0577 (r-xrwxrwx) chmod:  configure.php:  new permissions are r-xrwxrwx, not r-xr-xr-x

I checked the permissions with: ls -l configure.php and received -rwsrwsrws 1 root root 3159 2008-07-29 13:20 configure.php

Thanks for your help in resolving this.

---

### Post by DLLong on 2008-07-30
I tried it with gksudo nautilus and had the same problem.  I'm in the "Permissions" tab and go to the "Others/Access" drop down.  Holding it down, it shows "None, Read only, Read and Write".  I highlight with my mouse the "Read only" and it changes but as soon as I release it, it changes back to "Read and write."

---

### Post by Diabolis on 2008-07-30
> I checked the permissions with: ls -l configure.php and received ```
-rwsrwsrws 1 root root 3159 2008-07-29 13:20 configure.php
```

As you can see, the file is owned by "root" and belongs to the group "root".

So lets try to change the ownership and then the permissions.

```
sudo chown *"your username"* configure.php
sudo chmod -v -w configure.php
```

---

### Post by decoherence on 2008-07-30
> **DLLong said:**
> I tried your suggestions.  Let me take the second reply first.  Yes, I am trying to change the file permissions on ubuntu directly.

vanadium was actually asking about the format of the drive you're using, not whether you're trying to make the change within ubuntu.

you can type 

fdisk -l

and it will tell you if you have NTFS formatted partitions.

---

### Post by Diabolis on 2008-07-30
Yeah, I assumed that you knew about file systems. Just to be 100% sure try this:
```
sudo fdisk -l /dev/sda
```

---

### Post by crwmike on 2008-07-30
> **DLLong said:**
> I tried your suggestions.  Let me take the second reply first.  Yes, I am trying to change the file permissions on ubuntu directly.
Here's what I tried:
1.  Navigated to the directory - dave@Aspenserver3:/media/disk/WSII/zencartfurn/includes
2.  Entered in chmod -w configure.php
3.  Received this in response:  chmod:  configure.php new permissions are r-xrwxrwx, not r-xr-xr-x
============
To check permissions, I entered: ls -l configure.php 
Received this in response:  -rwxrwxrwx 1 root root 3159 2008-07-29 13:20 configure.php
So this doesn't look like anything changed.
========
Since I'm still learning, I enter the same command as #2 above with this addition suspecting that it might have to do with the root permissions:  sudo chmod -w configure.php
I received the same response as #3 above.

More thoughts?

If the permissions you want are r-xr-xr-x, the command is
```
[CODE]sudo chmod 555 configure.php
```[/CODE]

---

### Post by vanadium on 2008-07-30
Please post the output here of the command

mount

---

### Post by DLLong on 2008-07-30
Sorry I was away for a while.  I got to reading your posts and then it dawned on me what you were asking.  The second drive (a former Windows drive) was probably formatted as NTFS.  I checked and sure enough, it was.  I reformatted it to ext3 and now it works perfectly.  

I will admit that I ended up pulling what little hair I have left trying to figure out why the new drive was mounted but I could not copy directories into it.  This whole "can't be an administrator" thing is driving me a little nuts.

---

### Post by JoneYee on 2008-07-30
> **DLLong said:**
> This whole "can't be an administrator" thing is driving me a little nuts.

It'll take a little getting used to fro mthe Windows World, but trust me, it'll save you enough times to be worth remembering that sudo is your friend.

---

### Post by decoherence on 2008-07-31
Glad to hear you got it working!

> **DLLong said:**
> This whole "can't be an administrator" thing is driving me a little nuts.

Well, in this particular case, it wasn't the permissions causing the problem but a characteristic of the NTFS filesystem.

But yes, getting 'permission denied' errors is frustrating to many users. RedHat's PolicyKit, which is new in Hardy, provides a solution. Future releases of Ubuntu will make better and better use of it, making administrative tasks much more straight forward. You'll still have to type in a password, but at least you won't have to re-do the command using gksudo or worse, going to the terminal.

---

### Post by raunhar on 2009-02-20
I am also facing the same problem.

Can you explain the process step by step. I have just partly switched to linux. Using Ubuntu 8.10 and zen cart 1.3.8
Need to change file permission for configure.php

---

### Post by rewlad on 2010-03-31
for some reason
chmod -w 
did not worked for me.
I've solved with more specific:
chmod o-w

---


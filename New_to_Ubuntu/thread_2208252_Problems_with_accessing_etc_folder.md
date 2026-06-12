---
title: "Problems with accessing /etc folder"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by azulflame on 2014-02-27
I am running Saucy Salamander, and am having trouble using the ```
sudo apt-get
``` command, and associated commands. Whenever I use it, I am greeted with the error message: ```
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (5: Input/output error)
```

After following advice about deleting /var/lib/apt/lists/ and replacing it with a working version, I am greeted with the error ```
rm: cannot remove &#8216;/var/lib/apt/lists&#8217;: Input/output error
```. Has anyone experienced this problem, or does someone know of a fix? Reinstalling Ubuntu, while an option, is something I'd rather avoid.

---

### Post by bc.haynes on 2014-02-27
Can you tell us what commands you used to get these errors? That may narrow it down.

---

### Post by Impavidus on 2014-02-27
This is not a "permission denied"-error, indicating a misunderstanding of the permission system, nor a "file system is read only"-error, indicating a file system mounted read only. The input/output error is usually caused by a hardware problem, like a loose cable or a failing drive.

Actually, on encountering an I/O error the root file system should automatically remount as read only, to prevent further damage.

---

### Post by slickymaster on 2014-02-27
Hi azulflame, welcome to the forums.

> **azulflame said:**
> ```
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (5: Input/output error)
```

Why don't you try to restore the missing _/var/lib/apt/lists/partial_ folder:```
sudo mkdir /var/lib/apt/lists/partial
```and afterwards run:```
sudo apt-get update
```

---

### Post by azulflame on 2014-02-28
Slickymaster, after running the mkdir command, I get this:

```
sudo mkdir /var/lib/apt/lists/partial
[sudo] password for <USERNAME>: 
mkdir: cannot create directory &#8216;/var/lib/apt/lists/partial&#8217;: Input/output error
```

In fact, I get this when attempting to navigate to the folder:

```
cd /
<USERNAME>@ubuntu:/$ cd /var
<USERNAME>@ubuntu:/var$ cd lib
<USERNAME>@ubuntu:/var/lib$ cd apt
bash: cd: apt: Input/output error
```

I also get the same error after running the command string as "sudo /bin/bash"

The folder exists, and displays under ls when in /var/lib/

---

### Post by slickymaster on 2014-02-28
Those input/output errors while running commands can also be due to bad blocks on the disk. One of the ways you have to scan your hard drive for errors is by creating a file called **forecefsck** on the root of your drive, and reboot. Once your computer is booted, that file will be detected and a fsck will be run during the boot process.
Open the terminal and run:```
sudo touch /forcefsck
sudo reboot
```
Alternatively you have the tool Disk Utility which can be called from the dash by pressing the super key and looking for Disk in the search box.

---

### Post by azulflame on 2014-03-04
I was attempting to work on another hard drive, while using this hard drive to hold the files (booted off of HDD B, files on HDD A. HDD A was giving me problems). My (not not a) friend unplugged the SATA cable for HDD A, and corrupted the drive. I had to format and reinstall, fortunatly with little data lost (backups are important. Do not forget this!). It now works, but I did not find a simple solution to the problem.

---


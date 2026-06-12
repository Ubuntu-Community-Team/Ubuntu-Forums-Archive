---
title: "Scalpel"
date: 2012-09-14
forum: New to Ubuntu
---

### Post by Jackalyn on 2012-09-14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  scalpel
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 33.9 kB of archives.
After this operation, 118 kB of additional disk space will be used.
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/universe scalpel i386 1.60-1build1 [33.9 kB]
Fetched 33.9 kB in 10s (3,131 B/s)                                             
Selecting previously unselected package scalpel.
(Reading database ... 212049 files and directories currently installed.)
Unpacking scalpel (from .../scalpel_1.60-1build1_i386.deb) ...
Processing triggers for man-db ...
Setting up scalpel (1.60-1build1) ...
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
jacky@jacky-Aspire-6930G:~$ scalpel /dev/sda1 -o output
Scalpel version 1.60
Written by Golden G. Richard III, based on Foremost 0.69.

Opening target "/dev/sda1"

ERROR: The configuration file didn't specify any file types to carve.
(If you're using the default configuration file, you'll have to
uncomment some of the file types.)

Please can someone expain. I have no idea what the command line is for apt-get  and will that solve it?

---

### Post by SlugSlug on 2012-09-14
Taken from here [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

> By default, all file types in the database (/etc/scalpel/scalpel.conf)  are commented out.  To specify which filetypes you want to carve, you  need to edit the file and uncomment each line. 

---

### Post by vasa1 on 2012-09-14
> **Jackalyn said:**
> 
Please can someone expain. I have no idea what the command line is for apt-get  and will that solve it?

What command generated the output you posted?

---

### Post by doktorOblivion on 2012-09-14
Like the error message said you may be able to just run:

apt-get update

and the problem may resolve itself.  However, it looks like its asking you to update the configuration file first, uncommenting some file-types that it should recognize, so that the program can start.  Just a thought.

---

### Post by Jackalyn on 2012-09-14
> **doktorOblivion said:**
> Like the error message said you may be able to just run:

apt-get update

and the problem may resolve itself.  However, it looks like its asking you to update the configuration file first, uncommenting some file-types that it should recognize, so that the program can start.  Just a thought.


Oh dear -LOL now I am more confused as I have no idea how to edit it and what to edit it to!

still get E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

Ok back to whatever I did earlier to sort that ....

---

### Post by ajgreeny on 2012-09-14
Just out of interest, why are you installing scalpel, which is normally a forensics application, so far as I can see, and what was the command that gave you those error messages?

---

### Post by SlugSlug on 2012-09-14
to solve all this just 

```
sudo apt-get update
```
```
gksudo gedit /etc/scalpel/scalpel.conf
```un-comment (remove the #'s) the files you want to recover

---

### Post by drmrgd on 2012-09-14
In regard to the scalpel error, SlugSlug's advice is correct.  You have to properly configure the config file first in order to run the program.

In regard to your apt problems, the error you first got suggests issues with your repository sources list.  Would you mind posting the output of the following, using the CODE tags please:

```
cat /etc/apt/sources.list
```

The error suggests you have a duplicate entry in the sources.list, which just needs to be removed.  

Finally, the last error you just got was probably due to you not using sudo to issue the command.  You need to prefix the command with sudo like this:

```
sudo apt-get update
```

---

### Post by vasa1 on 2012-09-14
> **ajgreeny said:**
> Just out of interest, why are you installing scalpel, which is normally a forensics application, so far as I can see, and what was the command that gave you those error messages?

Bit odd! I already asked the second question.

---

### Post by Jackalyn on 2012-09-15
Have fallen and hurt my hand so typing a bit of a no no just now. I lost everything and reinstalled. On another post someone suggested I used it and I thought it was a thing that might get back my lost files. Thankfully I emailed most to myself, but there are a few I hoped I could restore.

OK what exactly is scalpel then? I thought it kind of scraped the partition to tell you what was there. Will reply when can use my hand again!-thankfully probably bruised  not broken!

---

### Post by ajgreeny on 2012-09-16
> **Jackalyn said:**
> Have fallen and hurt my hand so typing a bit of a no no just now. I lost everything and reinstalled. On another post someone suggested I used it and I thought it was a thing that might get back my lost files. Thankfully I emailed most to myself, but there are a few I hoped I could restore.

OK what exactly is scalpel then? I thought it kind of scraped the partition to tell you what was there. Will reply when can use my hand again!-thankfully probably bruised  not broken!
More info on scalpel:-
[http://ubuntuforums.org/showthread.php?p=9814022](http://ubuntuforums.org/showthread.php?p=9814022)
[http://ubuntuforums.org/showthread.php?t=1570963](http://ubuntuforums.org/showthread.php?t=1570963)

Try **testdisk** instead which uses **photorec** to recover files.  The name photorec is historical as it was first used to recover photos from memory cards, but it will work for any filetype.

---


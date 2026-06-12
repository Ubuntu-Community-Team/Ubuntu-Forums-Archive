---
title: "Setting up apache's root as NFS drive (I think)"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by itamaram on 2008-07-29
Hi there everyone! I am new to the magical world of Ubuntu, and in order to make my landing softer I am attempting to make my Ubuntu experience - at least initially - as similar as possible to my previous OS, windows XP.

My current setup involves a brand new HDD, formatted by Ubuntu on installation, and my previous HDD, untouched by Ubuntu, which was formatted by XP on installation about a year back and contains a lot of important information. Getting the computer to recognize its content was easy enough, but now I have a new problem.

I had a website running, hosted from my home machine, using Apache webserver. All source files are now on the 'old' hdd. So the natural thing to do was to install apache on the new (proved to be very easy!) and then set the serverroot to the old server root. It appears this assumption of mine had been wrong.
Quoting from the apache2.conf file a paragraph which I assume is most important and relevant and yet is completely incomprehensible to me:

```

# NOTE! If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.0/mod/mpm_common.html*#lockfile>);
# you will save yourself a lot of trouble.
```

What do I need to do? I want to clarify, just because I know how to run apache does not imply I know how to set it up...
In fact, I know very little about most things, so small words, and code I can copy-paste would be much appreciated.

Also, if anyone has any idea for an alternative, I am open for suggestions...

Thanks,
Itamar

---

### Post by bab1 on 2008-07-29
I can decipher what the quote you have cited means.  

The lock files need to be on the same partition as the O/S. 

From the Apache lockfile discription:> The LockFile directive sets the path to the lockfile used when Apache is used with an AcceptMutex value of either fcntl or flock. [COLOR="Blue"]This directive should normally be left at its default value.[/COLOR] [COLOR="Red"]The main reason for changing it is if the logs directory is NFS mounted,[/COLOR] [COLOR="DarkGreen"]since the lockfile must be stored on a local disk.[/COLOR] The PID of the main server process is automatically appended to the filename.

One sould have no problems with www-root on a NFS share.  But you do not need NFS.  You can mount the other drive via fstab as a local disk.  And yes that can be done easily.  Google "fstab" or search these forums for information on "how do I mount a second hard drive" or a "ntfs partition".

---

### Post by itamaram on 2008-07-31
Thank you, I have now identified my problem, which ended up being something completely different.
I now understand why it is important to password protect my computer. SIGH.

---


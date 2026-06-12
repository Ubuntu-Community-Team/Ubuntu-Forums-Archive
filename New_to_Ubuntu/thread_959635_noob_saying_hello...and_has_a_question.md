---
title: "noob saying hello...and has a question"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by leliphent on 2008-10-26
Hello all.
So the phrase beginner and noob, are both understatements. I am not familiar with Linux at all... but I am working to fix that.
My current situation is this:

I got a kick me down server given to me, and it currently has red hat installed on it, unfortunately I don't have the user name and password so it is useless at this point. 

I downloaded a version of Ubuntu server and would like to install it on this machine. I put the os on a cd, but unfortunately I cant seem to find where I can boot from disk. I did the f2 setup and I cant seem to locate this option... feeling pretty "we todd did"
any help / suggestion?

---

### Post by SunnyRabbiera on 2008-10-26
Hmm, is the burn free of defects?

---

### Post by leliphent on 2008-10-26
yeah should be, is the machine suppose to recognize the cd without telling it to boot from cd?

---

### Post by SunnyRabbiera on 2008-10-26
> **leliphent said:**
> yeah should be, is the machine suppose to recognize the cd without telling it to boot from cd?

It should, but it depends on how the BIOS is set up.
I am not sure on servers, but the principals of a desktop PC and a server are relatively the same

---

### Post by newton93 on 2008-10-26
> **leliphent said:**
> Hello all.
So the phrase beginner and noob, are both understatements. I am not familiar with Linux at all... but I am working to fix that.
My current situation is this:

I got a kick me down server given to me, and it currently has red hat installed on it, unfortunately I don't have the user name and password so it is useless at this point. 

I downloaded a version of Ubuntu server and would like to install it on this machine. I put the os on a cd, but unfortunately I cant seem to find where I can boot from disk. I did the f2 setup and I cant seem to locate this option... feeling pretty "we todd did"
any help / suggestion?

if i dont mis understand u, your computer doesn't recognize your ubuntu cd, did u burned the IMAGE onto the disc?

if not burn the IMAGE onto the disc and try again, Also check your bios settings.

//edit:
(I NEVER WORKED WITH RED HAT!)
I encourage u to use ubuntu, but does red hat not has an recovery thingy like ubuntu?

If so u can try: when starting up that server (if grub ofcourse,) press 'esc'
and try to select an recovery kernel!
if thats possible u will be logged in as root and can change passwords and / or create an user account..

---

### Post by dunkar70 on 2008-10-26
leliphent,

A couple of people have suggested that you check the CD... insert the CD into a working computer (Windows if you're more comfortable) and view the files. If you see one large file with an .iso extension, then the CD is not burned correctly. If this is the case, then you will need to burn the *image* onto a CD. This is different than burning the *.iso file*. By default, Windows will not burn .iso images, only files. If you do not have any software capable of burning an .iso image, then you can download InfraRecorder from [http://portableapps.com/apps/utilities/infrarecorder_portable](http://portableapps.com/apps/utilities/infrarecorder_portable). This is probably the easiest way. You should see a listing similar to the following for version 8.04:

$ ls -la
total 151
dr-xr-xr-x 10 root root   2048 2008-06-30 23:39 .
drwxr-xr-x  6 root root   4096 2008-10-26 18:03 ..
-r-xr-xr-x  1 root root    942 2008-04-22 01:07 cdromupgrade
dr-xr-xr-x  2 root root   2048 2008-06-30 23:38 .disk
dr-xr-xr-x  3 root root   2048 2008-06-30 23:38 dists
dr-xr-xr-x  3 root root   2048 2008-06-30 23:38 doc
dr-xr-xr-x  3 root root   2048 2008-06-30 23:39 install
dr-xr-xr-x  2 root root  12288 2008-06-30 23:39 isolinux
-r--r--r--  1 root root 119942 2008-06-30 23:39 md5sum.txt
dr-xr-xr-x  2 root root   2048 2008-06-30 23:38 pics
dr-xr-xr-x  4 root root   2048 2008-06-30 23:38 pool
dr-xr-xr-x  2 root root   2048 2008-06-30 23:38 preseed
-r--r--r--  1 root root    230 2008-06-30 23:38 README.diskdefines
lr-xr-xr-x  1 root root      1 2008-06-30 23:38 ubuntu -> .

Ok, assuming that you have a working CD, the next step is to determine how to get your computer to boot to the CD. Do you have any information on the computer? Model, serial number, etc? If you do not have a manual, there should be one online that will provide instructions to access the BIOS or at least select the boot options.

---

### Post by leliphent on 2008-10-28
hey all sorry it has taken me a day or two to get back to you all. Im looking over the files I have put on the cd, and I am not sure if it is set up right. 

I downloaded it from the ubuntu website... so I would need to image that download?

I pre-ordered a copy of the cd from them... so I will wait on that as well.

As far as the redhat deal, I am researching a method of getting around the password for that... and I might keep that running, just to learn.

I have another server that is currently running Debian with the same issue no user name or pass... so I will try and install ubuntu on this server.

---


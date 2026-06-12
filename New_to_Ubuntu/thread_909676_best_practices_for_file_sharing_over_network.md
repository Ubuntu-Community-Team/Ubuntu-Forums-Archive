---
title: "best practices for file sharing over network?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-09-03
When i had windows, i was able to right click my secondary hard drive used to store media like pics, movies, and music, and share the entire drive over the network. 

With Ubuntu, i had to add a link to each folder in my secondary drive under my share folder in my home directory, because there is no share options under properties of the hard drive. also, i had to create the link, because when i shared the folders directly, a error came up saying 

```

 'net usershare' returned error 255: net usershare add: cannot share path /media/sdb1/movies as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

```

so what is the best method for sharing an entire drive?  

Thanks.

---

### Post by bodhi.zazen on 2008-09-03
As with Windows, there is no reason to share the entire drive.

In Ubuntu the user must have permissions on the share (mount point) in order to share it, so essentially you are asking to share the entire HD.

If you *must* , use a bind :

```
sudo mount --bind / /home/user_name/share
```

---

### Post by mrsteveman1 on 2008-09-03
In ubuntus gnome you might have to edit the samba config. In kde3 there is a panel to configure samba (but its separate from drive properties).

Also in suse they have their own samba config as well.

You can in fact edit smb.conf though, its easy once you learn the syntax and a functional config is only 10-20 lines.

---

### Post by deathvalleyjoker on 2008-09-03
I already did the suggestion and added the line so that samba can share files that dont have my user permission since most of my stuff was created from my windoes account before i was turned on to ubuntu.

Bod: i agree that it is not nessicary to share the entire drive when it is the drive that has your OS on it, but i have entire secondary drive dedicated to media files that i would like to share with other computer on my network, in which case it is nessicary to share hte entire drive to make it simple and share one point.

just thought of something while typing this: would it be posssible to go into /media and link my media hard drive from there? will let you know how it goes.

EDIT: no it is not possible to link the hard drive folder in /media. the make link option is grey-ed out.

Any other suggestions?

---

### Post by bodhi.zazen on 2008-09-03
you can either change ownership and permissions of the mount point (how to do that depends on the file system) or use mount --bind

```
sudo mount --bind /media/share /home/user/share
```

---

### Post by werries on 2008-09-03
These are all complicated solutions. Why don't we use the classic shares-admin everyone forgot about? 

hit Alt+F2 and type
```
shares-admin
```
This will enable you to properly set up sharing with windows on the network, and you just add the harddrives folder to the list.

---

### Post by deathvalleyjoker on 2008-09-03
> **werries said:**
> These are all complicated solutions. Why don't we use the classic shares-admin everyone forgot about? 

hit Alt+F2 and type
```
shares-admin
```
This will enable you to properly set up sharing with windows on the network, and you just add the harddrives folder to the list.

This is definitely the most easiest way of doing it. The only problem i ran into was when accessing it from a windows computer, it said that i did not have the right permissions to access it. so how can i change the permissions for an entire drive? Thanks!

---

### Post by werries on 2008-09-03
Make sure its the same workgroup, and that it is a WINS server, but i didnt "name" mine. and it works.
And as long as YOU have access to the drive, others should too.

---

### Post by egalvan on 2008-09-03
> **bodhi.zazen said:**
> *As with Windows, there is no reason to share the entire drive.*

In Ubuntu the user must have permissions on the share (mount point) in order to share it, so essentially you are asking to share the entire HD.

If you *must* , use a bind :

```
sudo mount --bind / /home/user_name/share
```

I don't understand; what is wrong with sharing the entire drive?
In my case, EVERYTHING on the drive should be access able over my internal network, to EVERYONE on my network.

OK, it's just me and my six to eight computers scattered around my house, but you get the idea.

On my server, I have three SCSI drives that hold my system, 
and approx ten drives with information (documents, downloads, pictures, music, videos, etc).
The system drives are not shared.
The info drives are all shared.

Every other machine has one (smallish) drive to boot from, then it connects to the network and has all that lovely storage space available.
I can listen to any piece of music I own, or watch any video I own, without having to look for the physical disc. I can read any document/text file I have, and I can log on and surf with the exact same profile from any machine.
An external 120g USB drive lets me take what I need to use with my laptop.

---

### Post by deathvalleyjoker on 2008-09-04
So I think one of the problems is that the owner of the hard drive i am trying to share, and all the files in it are owned by root. can i chown the hard drive to my user? will that fix my problem, or just create more problems latter on? the thing that doesnt make sence is permissions for everyone is rwx. 

```

mikey@mikey-desktop:/media$ cd /media
mikey@mikey-desktop:/media$ ls -la
total 52
drwxr-xr-x  8 root root  4096 2008-09-02 22:26 .
drwxr-xr-x 23 root root  4096 2008-09-02 21:15 ..
lrwxrwxrwx  1 root root     6 2008-06-23 18:35 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-06-23 18:35 cdrom0
drwxr-xr-x  2 root root  4096 2008-06-23 18:35 cdrom1
-rw-r--r--  1 root root     0 2008-09-02 22:26 .hal-mtab
drwxrwxrwx  1 root root  8192 2008-09-02 21:15 sda1
drwxrwxrwx  1 root root 12288 2008-09-02 21:15 sda5
drwxrwxrwx  1 root root 12288 2008-09-03 22:16 sdb1***
drwxr-xr-x  2 root root  4096 2008-07-02 19:34 winshares

```

***sdb1 is the hard drive i want to share.

---

### Post by mrsteveman1 on 2008-09-04
> **deathvalleyjoker said:**
> So I think one of the problems is that the owner of the hard drive i am trying to share, and all the files in it are owned by root. can i chown the hard drive to my user? will that fix my problem, or just create more problems latter on? the thing that doesnt make sence is permissions for everyone is rwx. 

```

mikey@mikey-desktop:/media$ cd /media
mikey@mikey-desktop:/media$ ls -la
total 52
drwxr-xr-x  8 root root  4096 2008-09-02 22:26 .
drwxr-xr-x 23 root root  4096 2008-09-02 21:15 ..
lrwxrwxrwx  1 root root     6 2008-06-23 18:35 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-06-23 18:35 cdrom0
drwxr-xr-x  2 root root  4096 2008-06-23 18:35 cdrom1
-rw-r--r--  1 root root     0 2008-09-02 22:26 .hal-mtab
drwxrwxrwx  1 root root  8192 2008-09-02 21:15 sda1
drwxrwxrwx  1 root root 12288 2008-09-02 21:15 sda5
drwxrwxrwx  1 root root 12288 2008-09-03 22:16 sdb1***
drwxr-xr-x  2 root root  4096 2008-07-02 19:34 winshares

```

***sdb1 is the hard drive i want to share.

hm, i suppose you could chown the mount (use the -R switch if you want the entire filesystem too) and it should work.

---

### Post by bodhi.zazen on 2008-09-05
See my previous post, #5

changing ownership and permissions is dependent on the file system.

---

### Post by anjilslaire on 2008-09-05
Why don't you just create a new folder on the root of the drive, "media" or something, and put everything under that root folder, then share that folder & subfolders?

Easy fix, you're just sharing a folder rather than a whole disk...

---


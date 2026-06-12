---
title: "What does Ubuntu add to root?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by freesitebuilder on 2008-10-12
I last did a clean install for Feisty - at that time, 7Gb was the required space for root, and I allocated 10Gb. I ran upgrades for Gutsy and Hardy. My root partition is now full, and I need to repartition before I upgrade to Intrepid. The current requirements seem to be only 8-10Gb. 

What does Ubuntu add to root during normal use - for example if I install extra software, does that increase the contents of root?

I just want to be sure that I allocate enough - partitioning brings me out in a cold sweat! :)

TIA

---

### Post by schauerlich on 2008-10-12
Basically anything you install that isn't run directly from your /home partition will be installed to / . That means all of your applications (usually somewhere in /usr) and a lot of confuration files (/etc). A lot of applications will also put preference files in ~/.(application name), so you will be able to preserve a lot of your preferences if you back up your /home partition.

---

### Post by jerome1232 on 2008-10-12
That really depends on the partitioning scheme, root contains everything Unless you put it on another partition

/boot is where static boot files are contained
/usr is where executable programs that are installed from the repos go
/etc is where programs system wide configurations go
/sbin is where the bare essentials go
/bin is where alot of useful but not required for a bare metal  installation programs go.
/home is where user files and configurations go
/var is where logs go, and persistent tmp files.
/tmp is where tmp files go, gets cleaned  every boot

that's a basic overview, /var, /usr, and /home tend to be the space eaters.

edit: If you look over that link you'll actually see I had /bin and /sbin a bit wrong.   /sbin is for programs that are essential to admins, /bin is more for programs used by the regular user.

An better overview of the Linux hiearchy can be found here:
[http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/](http://jamesthornton.com/linux/Linux-Filesystem-Hierarchy/)

---

### Post by forger on 2008-10-12
also, make sure that you clean up obsolete packages:
```
sudo apt-get autoclean
```

---

### Post by sisco311 on 2008-10-12
I don't think Interpid uses much more space than Feisty. 

When you install/update a package the .deb file saved in the /var/cache/apt/archives/ directory. 
To free up some disk space you can delete this files(from time to time) by executing:
```
sudo aptitude clean
```from a terminal.

Also check/empty the Trash folder in the /root directory.

---


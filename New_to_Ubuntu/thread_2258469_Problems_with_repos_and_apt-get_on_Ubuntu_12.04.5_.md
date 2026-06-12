---
title: "Problems with repos and apt-get on Ubuntu 12.04.5 CLI"
date: 2014-12-28
forum: New to Ubuntu
---

### Post by Irrationalis on 2014-12-28
Hello, I have installed Ubuntu 12.04.5 (command line only) on my 2006 Intel Core 2 Duo iMac. I am hoping to run a Plex media server from this machine, but I'm running into problems with my fresh install.   

When I run: ```
sudo apt-get update
``` 

      I get this: 

 ```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/sources/Sources Hash Sum mismatch W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources Hash Sum mismatch W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources Hash Sum mismatch W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources Hash Sum mismatch W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages Hash Sum mismatch* W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/binary-i386/Packages Hash Sum mismatch W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/binary-i386/Packages Hash Sum mismatch* W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/binary-i386/Packages Hash Sum mismatch* E: Some index files failed to download. They have been ignored, or old ones used instead. 

```

Any idea what is happening and how to fix it?

---

### Post by Bucky Ball on 2014-12-28
Welcome. Please copy the output from the terminal and then put it in code tags. One long line is a little confusing and hard to diagnose.

The valuable bit of the info is any errors you encounter, which are probably at the end of the output. Thanks. ;)

---

### Post by grahammechanical on 2014-12-28
There is a sum mismatch on a few of the repositories. What happens when you run

```
sudo apt-get upgrade
```

Do you get a list of packages that will be upgraded? Can the upgrade take place. I have found that the message

> E: Some index files failed to download. They have been ignored, or old ones used instead.
does not stop an update - upgrade from completing. I run the development release and I see that particular message all the time because the development release does not have all the usual repositories open.

A "sum mismatch" is another matter. I have never seen that. For how long has this been happening?

[http://ubuntuforums.org/showthread.php?t=2243249](http://ubuntuforums.org/showthread.php?t=2243249)

[http://www.linuxquestions.org/questions/debian-26/apt-hash-sum-mismatch-4175497785/](http://www.linuxquestions.org/questions/debian-26/apt-hash-sum-mismatch-4175497785/)

Regards.

---

### Post by Irrationalis on 2014-12-28
When I run ```
sudo apt-get upgrade
```

I get: 
```
The following packages have been kept back:
linux-headers-generic-its-trusty linux-image-generic-its-trusty
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

This seems normal, because I'm not running trusty, but when I try to run:
```
sudo apt-get install openssh-server
```

I get:
```
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or moved out of Incoming. 
The following packages have unmet dependencies:
openssh-server: Depends libwrap0 (>= 7.6-4~) but it is not installable
Reccomends: ssh-import-id but it is not installable
E: Unable to correct problems, you have held broken packages.
```

This is my second fresh install, this has happened both times from the get-go.

EDIT: This solved my problem:
```
apt-get clean
rm -rf /var/lib/apt/lists/*
rm -rf /var/lib/apt/lists/partial/*
apt-get clean
apt-get update
apt-get upgrade
```

Thanks, Graham!

---

### Post by Bucky Ball on 2014-12-29
After

```
sudo apt-get update
sudo apt-get upgrade
```

run

```
sudo apt-get dist-upgrade
```

---

### Post by waqas_4411 on 2015-02-21
thx slove this my problem

---

### Post by sniegowski on 2015-03-13
[COLOR=#333333][FONT=monospace]This problem would go away if the timestamp on the repository for these two files are changed to a date after [/FONT][/COLOR][COLOR=#333333][FONT=monospace]Jun 23 2014[/FONT][/COLOR][COLOR=#333333][FONT=monospace]
ubuntu/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dists/precise/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]Release[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]ubuntu/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]dists/precise/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]Release.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]gpg
[/FONT][/COLOR][URL="https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1430648"]

https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/1430648[/URL]

---


---
title: "SD Card wont read"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by andrew129 on 2014-07-01
I recently installed Ubuntu 14.04 on an ASUS UL80J. It has a built in Multi Card reader. I installed Ubuntu on this laptop as I did not have a valid WIndows Key and I used Ubuntu briefly in the past and thought I would try it out again. The main thing I am using it for is to store pictures off my Camera and do some minor editing. I run into a problem however when I put the 64gig Sandisk Ultra card into my card reader. I am using a Nikon 9700. Following is the error that pops up:

"Error mounting /dev/sdb1 at /media/atagtmeier/3439-6136: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/atagtmeier/3439-6136"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'"

I do not know a lot about the coding and such, I found a site that said to type a code into something and I loaded up terminal and typed that in. It looked promising at first as it installed something on there but I still ran into thesame problem. below is the results from that.

atagtmeier@atagtmeier-UL80Jt:~$ sudo add-apt-repository ppa:relan/exfat
[sudo] password for atagtmeier: 
 PPA for the free exFAT file system implementation project: [http://code.google.com/p/exfat/](http://code.google.com/p/exfat/)
 More info: [https://launchpad.net/~relan/+archive/exfat](https://launchpad.net/~relan/+archive/exfat)
Press [ENTER] to continue or ctrl-c to cancel adding it


gpg: keyring `/tmp/tmpv8dmr5ed/secring.gpg' created
gpg: keyring `/tmp/tmpv8dmr5ed/pubring.gpg' created
gpg: requesting key A252A784 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpv8dmr5ed/trustdb.gpg: trustdb created
gpg: key A252A784: public key "Launchpad Free exFAT file system implementation" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK

Any help would be greatly appreciated. And keep in mind I am a basic user. I can usually figure it out but the more basic the better.

---

### Post by cariboo on 2014-07-01
You need the next two steps to finish what you started:

```
sudo apt-get update
```

and

```
sudo apt-get install exfat-utils
```

Once you've installed the exfat-utils package, you should be able to access your SD card.

---


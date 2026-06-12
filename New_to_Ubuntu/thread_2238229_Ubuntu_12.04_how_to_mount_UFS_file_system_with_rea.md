---
title: "Ubuntu 12.04 how to mount UFS file system with read and write support"
date: 2014-08-06
forum: New to Ubuntu
---

### Post by simon3 on 2014-08-06
Hello 
Firstly I'm completely new to ubuntu so forgive me if I don't post all details you need first off.

I have a couple of hard drives which are formated UFS2 as they were connected to my panasonic tv to record on. Unfortutately the drives have become unregistered from the TV and only a reformat(losing all the recoded programmes) will enable the TV to recognise them again.  I have managed to mount them to ubuntu 12.04 but only as read only.  There is a small file on each drive which tells the TV it is registered and able to play back the recorded content.  Put simply  I need to mount each drive and copy the file which tells the TV it is registered.  


 After much searching I found out it is possible to mount them as read/write.  I have installed 12.04 to an external hard drive and been trying to use the following [http://blog.drenet.net/enabling-ufs-rw-support-in-ubuntu-12-04-lts/](http://blog.drenet.net/enabling-ufs-rw-support-in-ubuntu-12-04-lts/) in order to acheive this. 

Code as follows

sudo su -
apt-get build-dep --no-install-recommends linux-image-$(uname -r)
mkdir /usr/local/src/ufs_rw
cd /usr/local/src/ufs_rw
apt-get source linux-image-$(uname -r)
_***cd linux***__***-3.x.y-***__***z***_
cp -v /usr/src/_***linux-headers-3.x.y-z***_/Module.symvers .
cp -v /boot/config-3.x.y-z .
make EXTRAVERSION=-4 O=/usr/local/src/ufs_rw  oldconfig
sed -i 's/# CONFIG_UFS_FS_WRITE is not set/CONFIG_UFS_FS_WRITE=y/' /usr/local/src/ufs_rw/.config

I am at a loss with the two items hightlighted/undelined above.  I have managed to get that far but can't for the life of me work out what I need to input.


I've attached pdf of my progress so far.

Any help would be very much appreciated.  

Thanks.

---

### Post by TheFu on 2014-08-06
try **uname -r** to get the numbers.  Using kernels at this specific a level is good for short-term needs, but for long-term needs, you'll want to use the meta-package for the kernel and header sources.

---

### Post by simon3 on 2014-08-07
Thanks TheFu.  

uname - r returns 3.11.0-19-generic.

this

root@HP-EliteBook-8460p:/home/simon/ufs_rw# cd linux-3.11.0-19-generic

returns this

bash: cd: linux-3.11.0-19-generic: No such file or directory

 
The following is what I have from the terminal so far.
 
root@HP-EliteBook-8460p:/home/simon# sudo apt-get build-dep --no-install-recommends linux-image-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Picking ***'linux-lts-saucy'*** as source package instead of ***'linux-image-3.11.0-19-generic***'
NOTICE: 'linux-lts-saucy' packaging is maintained in the 'Git' version control system at:
[http://kernel.ubuntu.com/git-repos/ubuntu/ubuntu-saucy.git](http://kernel.ubuntu.com/git-repos/ubuntu/ubuntu-saucy.git)
Skipping already downloaded file 'linux-lts-saucy_3.11.0-26.45~precise1.dsc'
Skipping already downloaded file 'linux-lts-saucy_3.11.0.orig.tar.gz'
Skipping already downloaded file 'linux-lts-saucy_3.11.0-26.45~precise1.diff.gz'
Need to get 0 B of source archives.
Skipping unpack of already unpacked source in _**linux-lts-saucy-3.11.0**_

I noticed the above highlighted text in the terminal so have substituted 

cd: linux-3.11.0-19-generic 
   for
cd: linux-lts-saucy-3.11.0

which takes me here.
root@HP-EliteBook-8460p:/home/simon/ufs_rw# cd linux-lts-saucy-3.11.0
root@HP-EliteBook-8460p:/home/simon/ufs_rw/linux-lts-saucy-3.11.0# 

the next line i need to suss is
cp -v /usr/src/linux-headers-3.x.y-z/Module.symvers .

I am stuck at the headers and what 3.x.y.z i need to input

Thanks and sorry for the long reply.

---

### Post by TheFu on 2014-08-07
If building a new kernel is too hard (and it isn't easy), perhaps using an OS that natively supports UFS would be a good idea?  
One of the *BSDs?  Those should boot off a flash disk or CD in a "liveRun" mode, then a normal mount command would let you modify files as you like.

 /usr/src/linux-headers-3.x.y-z/Module.symvers  ????
Well, what are the directories under /usr/src/ ?  the one that looks like headers for the same version of the kernel is what you need.  I take it you aren't a C programmer?  ;)

---

### Post by simon3 on 2014-08-08
No definately not a C programmer and this is all completely new to me.   The sum of my knowledge/experience is exactly zero I'm sorry to say :-?

I  am perhaps assuming too much from having found what I thought was a  solution which I could copy to solve the problem I have.  Your  suggestion of using one of the BSDs is not something I'd thought of but  something I'll investigate.   I've seen mention of freeBSD when searching for UFS read write support.  

The use of linux and specifically ubuntu  came from this: 

[http://www.avforums.com/threads/panasonic-viera-tv-usb-hdd-pvr-supported-drives-pc-access-to-recordings.1303759/page-5](http://www.avforums.com/threads/panasonic-viera-tv-usb-hdd-pvr-supported-drives-pc-access-to-recordings.1303759/page-5)    (post no 147)

Thanks again for the help so far.

---

### Post by TheFu on 2014-08-08
Boot any live-CD running a BSD OS should provide RW access to the disk. That is much easier than learning all the programming stuff you are fighting with. 

When I think about explaining how to do this to a non-technical person, I cringe.  The greatness in Linux is the complete flexibility, but nobody ever said that was easier than other options or that it was meant for anyone to jump into.  I've built hundreds of kernels and setup scripts for many different modules - but that was back in the 1990s when we didn't have any other real choice to get things done.  Most of the time, kernel modules just build automatically when the package is installed. RW support for UFS is a very special case and follows the really-old-school method of doing things.

I spent the last 20 minutes looking for a LiveCD version of any BSD.  Only found a CLI option - no GUI.  [http://www.freebsd.org/doc/handbook/using-live-cd.html](http://www.freebsd.org/doc/handbook/using-live-cd.html)  Better than nothing and for the 5 commands you need to type, should be sufficient.

---

### Post by simon3 on 2014-08-08
Thanks again.  I looked at the freebsd site, the livecd link is very helpful.

Will give it a go and report back.

With regard to the original question can anyone clarify what this mean?

'Picking 'linux-lts-saucy' as source package instead of 'linux-image-3.11.0-19-generic'  

uname -r returns 3.11.0-19-generic' 


thank you/

---

### Post by TheFu on 2014-08-08
1 is the exact package only good for 1 specific kernel.
The other is a meta-package - that points to the current kernel for a specific release. APT is smart that way.

---


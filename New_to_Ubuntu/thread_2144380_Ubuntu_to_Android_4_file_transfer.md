---
title: "Ubuntu to Android 4 file transfer"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by Loki*PI on 2013-05-11
**Resolution**:

I haven't resolved this but I did upgrade to 13.04 so the question is no longer relivant.  


**Original Problem:**  It has been a week now since the original post and no suggestions other than to update to 13.4.  No one has any idea how to resolve this?  

I'm running ubuntu 12.10.  I have an Android 4 tablet. I want to be able to pull Android games down on my computer and trasfer them to the tablet.

I did the following from Bilal Akhtar article:

sudo apt-get install golang fuse git-core libmtp-dev libfuse-dev
sudo adduser $USER fuse
mkdir /tmp/go 
GOPATH=/tmp/go go get github.com/hanwen/go-mtpfs
sudo mv /tmp/go/bin/go-mtpfs /usr/bin/
mkdir ~/MyAndroid

then 
go-mtpfs ~/MyAndroid &

I can see the Android table, it comes up as Android but I cannot see the file structure or move files to it.  I've Googled and searched the forum but haven't found anything helpful.

Anyone have an idea what I'm missing or doing wrong???  

Do I need to load gmtp??  

To update - I installed gmtp - it sees the tablet ok but I was not able to transfer an MP3 file. 

Thanks All

---

### Post by MoebusNet on 2013-05-13
If your computer is capable of running 13.04, mounting Android 4  mtpfs should be built-in.

---

### Post by Automat2 on 2013-05-26
MTP support is already built-in in 13.04, however the syncing of files with the PC via USB is rather impossible.

I still have to use Airdroid for that matter.

---

### Post by MoebusNet on 2013-05-26
@Loki*PI - Here is a lengthy discussion of what is going on:

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/903422](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/903422)

If you really need to stay with Ubuntu 12.10, perhaps the easiest thing to do would be to install a virtual machine (I use VirtualBox) and install Ubuntu 13.04 as a guest OS in VirtualBox with 12.10 as the host OS. At any rate, read the bug report and see what you think then.

---

### Post by Loki*PI on 2013-05-27
Thanks I'll read it.

---


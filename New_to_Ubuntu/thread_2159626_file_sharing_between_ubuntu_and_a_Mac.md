---
title: "file sharing between ubuntu and a Mac"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by tlalokman on 2013-07-03
Hello,

I hope you can help me. I'm trying to transfer the last year's photo albums from my Ubuntu machine (12.04 LTS) to an iMac (10.8.4). I don't know how can I do that (it's about 45 GB of pictures that I want to share). What do you suggest? My computer does not have Bluetooth neither CD/DVD drive. I tried to upload the files to a cloud storage server but it is sloooooooooow and it would take years. 

Any ideas?

Thank you in advance for your cooperation.

---

### Post by LukeMorrison on 2013-07-03
Have you looked at BitTorrent Sync?  I have not used it personally, but I have heard good things about it.

[http://labs.bittorrent.com/experiments/sync.html](http://labs.bittorrent.com/experiments/sync.html)

[http://askubuntu.com/questions/284683/how-to-run-bittorrent-sync](http://askubuntu.com/questions/284683/how-to-run-bittorrent-sync)

---

### Post by 3rdalbum on 2013-07-04
If both computers are networked, you can install the Samba server on the Ubuntu machine and access it on the Mac.

The "system-config-samba" package will install Samba and give you a configuration utility to help you set up your shared folder.

When that is done, you can access the shared folder on the Mac by using its network browsing abilities - sorry I can't be more specific, I'm not a Mac user - but it can definitely browse networks and find your Samba server.

If the computers are not on the same wired or wireless network, use a USB hard drive.

---

### Post by cub on 2013-07-04
You could also set up a ftp server on the ubuntu machine and move everything over from the mac.

---

### Post by Morbius1 on 2013-07-04
I got 2 happy customers with this technique - let's see if I can get one more:

On Ubuntu:

[1] Open up a terminal and change directories to the parent folder that contains the Pictures, for example if they are in the Pictures folder of your home directory:
```
cd Pictures
```
[2] Now run the following command:
```
python -m SimpleHTTPServer
```
[3] On the OSX machine open your browser ( I'm talking about your Internet browser not Finder ) and point it to:
```
http://192.168.0.100:8000
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the Ubuntu machine. Note: Since this is a Linux-OSX network you can also use the Avahi/Bonjour naming convention, for example:*[/COLOR]
```
http://ubuntu-host-name.local:8000
```
As long as you don't happen to have an index.html file in that directory in Ubuntu it should simply list the contents of Pictures. Now you can use the browser to download the files to OSX.

After it's done downloading you can stop the temporary http server on Ubuntu by issuing a Ctrl+C.

---

### Post by Lars Noodén on 2013-07-04
> **cub said:**
> You could also set up a ftp server on the ubuntu machine and move everything over from the mac.

You probably meant SFTP instead of [old FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  

SFTP clients are built into both OS X and Ubuntu.  All you need to do is turn on the SSH server on one of the machines.  You can do that in *System Preferences->Sharing->Remote Login* in OS X.  Or you can do it by adding the package 'openssh-server' to your Ubuntu machine.  After that is in place you can connect and transfer the files.  In some ways, it is better to turn on (at least temporarily) sharing from OSX because Ubuntu has better clients.  For example, you can connect from your file manager by pressing ctrl-L and then entering the URI for the server.

---

### Post by Morbius1 on 2013-07-04
Wouldn't you know it I left out a part in my post. THe syntax is:
```
http://192.168.0.100:8000
```
I left out the "http:" part - getting sloppy here, sorry.

I fixed it in my previous post.

---

### Post by BBQdave on 2013-07-04
> **Lars Noodén said:**
> SFTP clients are built into both OS X and Ubuntu.  All you need to do is turn on the SSH server on one of the machines.  You can do that in *System Preferences->Sharing->Remote Login* in OS X.

+1

On my protected home network, I have a legacey eMac set as a FTP file server - the service that is built into osX - activated in osX's *System Settings*. I access the eMac file server from Linux and Windows machines using FileZilla :)

---


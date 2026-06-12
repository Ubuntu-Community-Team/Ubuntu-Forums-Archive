---
title: "Ubuntu as NAS"
date: 2016-10-15
forum: New to Ubuntu
---

### Post by dbchan on 2016-10-15
I did a quick search but couldn't find what I'm looking for. 

I know samba can be used for network sharing in a local network. But I'm looking for solutions for iOS, I like to be able to backup (multiple) iPhone photos/videos to the NAS and be able to browse them on the phone also. Like a personal Cloud.

My desktop has been sitting around doing nothing while my MacBook and iPhones are running out of space. It would be nice if I could turn the desktop into a headless NAS serving as extra storage for the iDevices. 

FreeNAS doesn't seem to offer what I'm looking for. Synology DiskStation maybe the way to go if Ubuntu is a no go.... Thanks in advance.

---

### Post by Morbius1 on 2016-10-15
iOS can do samba. Not natively but through a 3rd party app like File Explorer Free for example. 

That particular app can't browse for servers the way macOS does natively but iOS does speak mDNS so when you specify the server's host name or IP address you would enter something like this:
```
linux-server-host-name.local
```
Anyway, it's something you may want to explore: [https://itunes.apple.com/us/app/fileexplorer-free/id510282524?mt=8](https://itunes.apple.com/us/app/fileexplorer-free/id510282524?mt=8)

There are many apps like these in the App Store so you may find one that is more appropriate for your needs.

---

### Post by kevdog on 2016-10-15
Honestly I have a mixture of Macs and Ubuntu computers.  I suppose I'm running one of my Ubuntu installations as a type of NAS.  It's not headless however it does back up by Ios Machines.  What I did was install AFP on Ubuntu. Here is the guide I originally used:
[https://www.outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/](https://www.outcoldman.com/en/archive/2014/11/09/ubuntu-as-home-server-part-3-afp-server/)
Once the afp server was installed, the computer would automatically show as an afp share which works natively on Apple.  Once an AFP server is in place, it's also possible to set up a Time Machine backup on the server which Apples Time Machine utility can use.  It was pretty simple.  
I've since abandoned this solution however and ended up going with borg backup.  This might not suit your needs, but it's my transition to offsite backups.  I needed an encrypted solution that had versioning similar to Time Machine.

---

### Post by mastablasta on 2016-10-17
> **dbchan said:**
> . 

FreeNAS doesn't seem to offer what I'm looking for. Synology DiskStation maybe the way to go if Ubuntu is a no go.... Thanks in advance.

not sure exactly what you are looking for but FreeNAS does offer anythign NAS might need.

Openmediavault is a nice Linux version of NAS.

if backup is all you need then all you need to do is install ubuntu server, install OpenSSH, generate keys for your devices. then setup a programs that will do automatic backups on devices using sFTP. if oyu plan to backup outside of your home network you will also need to secure the server.

---

### Post by Zero_Bytes on 2016-10-19
Install owncloud on your nas, for the quickest and cleanliest install use docker.  It's very simple:  ```
 sudo apt update; sudo apt install docker;  docker pull owncloud ;  docker run -d -p 80:80 owncloud 
```  now you can access your own storage by going to url on you other device or 127.0.0.1 on the desktop itself

---


---
title: "File sharing with Windows"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by sal55 on 2013-07-01
I now have Ubuntu 12.04 (32-bit) running in Virtual Box under Windows 7 (64-bit).

What's the simplest way of being able to transfer files from one OS to the other?

I've tried doing File Sharing in Ubuntu, but it keeps coming up with excuse after excuse why I cannot share any folders (I've tried it on /home, /home/abc and /home/xyz, after installing 'samba'). And I have little confidence it will work anyway because it's difficult enough to share data between two Windows machines on the same local network, while there is also the oddity of Ubuntu being part of the same network machine it's trying to talk to!

At present I have to use email from one to the other, which is a little ridiculous! And any removable media drives belong to the host.

---

### Post by HermanAB on 2013-07-01
The simplest?  Install FileZilla server on Windows and then use any file browser on Linux to connect to it.

---

### Post by prodigy_ on 2013-07-01
What's wrong with plain Windows shared folders? If your machines see each other, Ubuntu should connect to Windows shares without any problems (assuming stock configuration). No need to install anything.

Samba is a bit trickier because it's best to configure it by directly editing **smb.conf** and that takes some reading and experimenting.

---

### Post by leunam12 on 2013-07-01
Make sure that your smb.conf file is set to be on the same network, then, in ubuntu open nautilus, press Ctrl+L and type smb://(the other computer's IP) and press enter. Don't type the parenthesis, just the other computer's IP.

On a different note, I think that Virtual Box has an option to share folders between the host and the Virtual Machine. Check [this link]("https://forums.virtualbox.org/viewtopic.php?t=15868")

---

### Post by Morbius1 on 2013-07-01
>  What's the simplest way of being able to transfer files from one OS to the other?
If you are talking about transferring files from guest to host then it's "Shared Folders" in VBox: **VirtualBox > Settings > Shared Folders > Add**

[COLOR=#0000cd]*Make sure to enable Auto-mount when you create the shared folder*[/COLOR]

When you reboot ( the guest - not the host ) it's automatically mounted to /media/sf_share-name. All you have to do is make sure you are a member of the vboxsf group. if not add yourself:
```
sudo gpasswd -a your-user-name vboxsf
```
Then logoff ( the guest - not the host ) and login again.
> I've tried doing File Sharing in Ubuntu, but it keeps coming up with  excuse after excuse why I cannot share any folders (I've tried it on  /home, /home/abc and /home/xyz, after installing 'samba'). 
If you are talking about sharing a folder in Linux I'm not familiar with "File Sharing" . Are you talking about "Sharing Options" in Nautilus?

"Sharing Options" ( i.e., Samba Usershares ) allows a regular user to create a Samba share of anything he owns so if he tries to share /home he can't because he doesn't own /home. If he tries to share his own home folder he will get an error massage becase a samba usershare cannot be created with a name matching an existing user name.

The solution to sharing /home is to share it through a root instance of nautilus: **gksu nautilus**

The solution to sharing /home/abc is to name it ( by "it" I mean the share name not the actual folder ) something else.

And remember - you are running this in VirtualBox. By default it uses NAT networking - you can see out but nobody can see in. You need to change it to Bridged networking. This 
does not affect "Shared Folders" but it does affect "Sharing Options".

---

### Post by deadflowr on 2013-07-01
What Morbius1 said, but make sure you have guest additions installed or else you won't have the share option available.

---

### Post by sal55 on 2013-07-01
> **Morbius1 said:**
> If you are talking about transferring files from guest to host then it's "Shared Folders" in VBox: **VirtualBox > Settings > Shared Folders > Add**



That worked perfectly, thanks. (Apart from the mandatory glitches, such as it completely forgetting my video settings on restarting so resorting to the console.)

It probably doesn't matter where the shared folder is, so I'm using one on Windows (the entire C drive in fact), and transfers are both ways anyway.

---


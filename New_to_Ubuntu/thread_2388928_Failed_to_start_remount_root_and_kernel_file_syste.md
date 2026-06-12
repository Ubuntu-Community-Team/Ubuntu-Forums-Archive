---
title: "Failed to start remount root and kernel file systems"
date: 2018-04-09
forum: New to Ubuntu
---

### Post by matevzpetric1 on 2018-04-09
Hello

I'm new to Ubuntu. I've setup a VPN server at work. I was going to make it a backup storage server as well. When i wanted to mount a network drive i followed this procedure: 

[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Specifically these 2 commands: 

```
sudo mkdir /media/windowsshare
```

Then edit your /etc/fstab file (with root privileges) to add this line:
```
//servername/sharename  /media/windowsshare  cifs  guest,uid=1000,iocharset=utf8  0  0
```  (while replacing with server ip and folder name)

However things went wrong (at least i think) with this one:
After you add the entry to /etc/fstab type:
```
sudo mount -a
```

After a reboot i noticed my auto complete in terminal (tab) does not work. It gives me:```
cd /ho-bash: cannot create temp file for here-document: Read-only file system
```,cd /home was my intent. 

On reboot i get this: 

[ATTACH=CONFIG]279227[/ATTACH]

Can someone help me with this?

Cheers Ryan

---


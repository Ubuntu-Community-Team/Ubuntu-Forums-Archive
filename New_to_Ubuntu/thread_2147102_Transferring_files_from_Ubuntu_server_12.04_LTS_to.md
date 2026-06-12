---
title: "Transferring files from Ubuntu server 12.04 LTS to Windows 7"
date: 2013-05-20
forum: New to Ubuntu
---

### Post by CompletelyStumped on 2013-05-20
Hi all!

Well, due to my computer not allowing me (for some reason) to download ubuntu desktop, I was stuck with ubuntu server.

Anyways, I need someone to help with transferring files to windows 7. I have saved a zip file (Backup.zip) in my home directory, and am trying to transfer it to the C: drive on my laptop. Problem is, whenever I look online for a guide, they either screw me over by destroying config files (like destroying the interfaces file, due to them having an older version of ubuntu server), or having complicated setup instructions. 

Can someone help me? I have PuTTy, and the guides about file transferring with FileZilla make no sense. Yesterday alone, I had literally spend about 7 hours cooped up in an office trying to move this file... Help!

---

### Post by steeldriver on 2013-05-20
Hello and welcome to the forum 

If you have an ssh server running on the Ubuntu box, then the easiest way imo is to use a client like WinSCP on the Windows box - you should be able to just drag + drop

If you don't have an ssh server installed yet, you can either use tasksel and check the appropriate box or just

```
sudo apt-get install openssh-server
```

It should install and start a server daemon with the default config, you will just need to type its LAN IP address in the WinSCP connection dialog then enter your login name / password

There should be no need to mess with network configs - unless the box doesn't have a working LAN connection at all

---


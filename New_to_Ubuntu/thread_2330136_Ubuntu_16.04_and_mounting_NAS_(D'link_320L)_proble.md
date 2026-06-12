---
title: "Ubuntu 16.04 and mounting NAS (D'link 320L) problems"
date: 2016-07-08
forum: New to Ubuntu
---

### Post by tr1ggsy on 2016-07-08
[http://ubuntuforums.org/showthread.php?t=2013947]("http://ubuntuforums.org/showthread.php?t=1105264")
[http://ubuntuforums.org/showthread.php?t=1105264](http://ubuntuforums.org/showthread.php?t=1105264)

Hi,

I have moved to Ubuntu as I'm hate windows and this laptop had got really slow, anyway long story short I'm slowly getting my head around it and I'm pretty happy with what I've done so far however I am really struggling with mounting my NAS drive. 

I did a search (see the links above) and found a couple of relevant threads but these don't sort me out. I did manage to create a network drive folder called NAS but it did nothing when I clicked it by folloing this [link]("http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/")... So i clearly did something wrong. 

Can anyone point me in the right direction to a guide how to do this? Sorry for the n00b post asking a question straight out of the box but I really cant work out where I went wrong.

Thanks in advanced,

Tr1ggsy

---

### Post by DuckHook on 2016-07-08
Welcome to the forums, tr1ggsy.

Behind your seemingly simple questions are a world of complexity.

Your first two links point to very old tutorials that are out of date. In any case, they make things far too complicated. Use the following instructions instead. You must first back out any changes you made to your config files from those obsolete tutorials. Then, if you want to piggyback on the Windows protocol (called Samba), follow the instructions here: [https://help.ubuntu.com/community/Samba/SambaClientGuide#Ubuntu_Clients](https://help.ubuntu.com/community/Samba/SambaClientGuide#Ubuntu_Clients)
It really is as simple as opening up Nautilus, searching for your NAS and then connecting to it.

OTOH, if you are completely switching over to Linux, then you may wish to use NFS instead of Samba. NFS is faster and a Google check of your NAS specs shows that NFS is supported. You will have to read your documentation for how to turn on NFS in your NAS if it is not already on by default. Once your server can serve NFS shares, you will need the NFS client on your computers. NFS instructions for installing as client are a little more complicated, but they are here: [https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client](https://help.ubuntu.com/community/SettingUpNFSHowTo#NFS_Client)

I neither recommend nor discourage either protocol. They each have their strengths and weaknesses. However, if you want a "purer" Linux experience, then NFS is the way to go. However, Samba is a perfectly acceptable choice too and especially so if you still have other Windows machines connecting to your NAS, in which case, Samba is a requirement.

---

### Post by tr1ggsy on 2016-07-11
Hi DuckHook,

Thanks for your reply, as you can tell I am a novice to Linux! I will have to use Samba as there are a multitude of other devices running Windows. Thanks for point that link, I will give it a go now.

No doubt I will be posting on here again soon, just hope next time I've learned more about this and will have built up my knowledge base!

---


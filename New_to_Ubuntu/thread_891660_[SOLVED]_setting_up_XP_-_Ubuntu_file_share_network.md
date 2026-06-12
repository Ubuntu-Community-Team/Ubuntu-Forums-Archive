---
title: "[SOLVED] setting up XP - Ubuntu file share network"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by arkein on 2008-08-16
Hello!

In a nutshell: my windows XP system gave me an "unmountable boot volume" error, probably after having been corrupted by a registry cleaner... you try and fix windows and it gets even worse ... typical... 

I can't fix it with the Windows boot disk repair console. But Thank goodness for Ubuntu, I can access the contents of my Hard drive using a Ubuntu live CD. So it seems at first glance that its exclusively a software problem (I'll do a hardware diagnostic once I've managed to backup my files, I don't want to overstress the HD before backing up just in case).

What I'd like to do is setup a wired (routerless) network between ubuntu (running from the CD) on this computer and another computer that runs win XP, so that I can access, run & backup my files on the faulty machine from the second XP machine.

I'm connecting the two computers directly through their ethernet network adapters using normal network cables. Another possibility would be to connect them directly using firewire.

I'm a complete noob at ubuntu and networking. I've given it a stab with no success, and can't find any clear instructions anywhere. Could anyone kindly explain in simple terms, step by step, how to get this up and running? remember I know next to nothing about ubuntu, and not much about windows networking. 

btw, Ubuntu looks amazing and I'm just yearning from the very core of my being to break free from the dark bottomless (cess)pit of windows hell. I'll definitely be running ubuntu once I've got this problem fixed!

Much appreciated! 
Arkein

---

### Post by arkein on 2008-08-16
Ok, I found info on how to set up the network using samba. I've managed to get both computers to see eachother.

I'd like to get the ubuntu side to be the server and the XP as client.

But when I try to share my folders so that I can access them from the XP client, (for example, my windows Documents and Settings) ubuntu gives me this message: net usershare returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied. you do not have permission to create a share.

Can anyone please help me to get around this?

---

### Post by arkein on 2008-08-16
Problems Solved!

I configured the share through the nautilus explorer GUI and it worked.


I have to say I'm pretty dissapointed that nobody bothered to help me though....

---

### Post by arkein on 2008-08-16
just in case someone else might need the info that helped me solve the problem. Here are the sources that helped me get unstuck:

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

[http://ubuntuforums.org/showthread.php?t=885099&highlight=error+255+share](http://ubuntuforums.org/showthread.php?t=885099&highlight=error+255+share)

---


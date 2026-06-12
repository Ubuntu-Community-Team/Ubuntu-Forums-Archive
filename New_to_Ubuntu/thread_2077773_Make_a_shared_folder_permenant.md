---
title: "Make a shared folder permenant"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by graphicsmanx1 on 2012-10-29
I am very new to ubuntu but for the time being I do have a working shared folder.  My issue is after I shut down and boot my PC the shared folder is no longer connected in ubuntu.  My environment is XP with Virtualbox and ubuntu 12.  I do have shared auto-mount and make permanent checked and I did the following in ubuntu

```

sudo mkdir /mnt/windows
sudo mount -t vboxsf shared /mnt/windows
sudo mount -t vboxsf -o uid=1000,gid=1000 shared /mnt/windows

```

suggestions?

---

### Post by Linuxisfast on 2012-10-29
Ubuntu is the champ of setting up samba, no other distro comes close. All you do is right click and set share and then after samba is automatically installed you reboot and set permissions to the folder you shared.

---

### Post by graphicsmanx1 on 2012-10-29
I tried that at home on windows 7 and even made sure I installed Virtualbox's guest editions and it would not share nor add the folder to the network identification that I saw in another tutorial.  I almost think with all the issues Ill just install ubuntu on an old rig and run it straight.  Virtual is proving more issues than its worth.  :(

---


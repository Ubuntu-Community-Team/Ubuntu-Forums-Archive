---
title: "Can't acces Windows shares with samba"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by thomsany on 2008-05-09
Hi!! I installed Samba, but when I go into Nautilus and type smb://192.168.1.200 which is my windows server nothing happens.

It doesn't prompt me for credentials nor connects nor anything.
What might be wrong?

Thanks much in advance,

Teo

---

### Post by FakeOutdoorsman on 2008-05-09
Did you see the Ubuntu Wiki page on [Setting up Samba]("https://help.ubuntu.com/community/SettingUpSamba")?  You may also want to see this thread: [HOWTO: Setup Samba peer-to-peer with Windows]("http://ubuntuforums.org/showthread.php?t=202605").

---

### Post by mlentink on 2008-05-09
Usually, you do not need samba to access windows shares. you need samba to share ***your*** folders to windows users.
So this is odd. have you tried scanning your network by simply clicking
Locations>Network ?

---

### Post by stchman on 2008-05-09
> **thomsany said:**
> Hi!! I installed Samba, but when I go into Nautilus and type smb://192.168.1.200 which is my windows server nothing happens.

It doesn't prompt me for credentials nor connects nor anything.
What might be wrong?

Thanks much in advance,

Teo

It has been my limited experience that Ubuntu (Linux) machines have issues connecting to Windows shares.

If you share a folder on your Linux box using Samba then a Windows machine has no problem connecting to it.

I use NFS for sharing as I am all Linux.

---

### Post by DivineOmega on 2008-05-09
> **thomsany said:**
> Hi!! I installed Samba, but when I go into Nautilus and type smb://192.168.1.200 which is my windows server nothing happens.

It doesn't prompt me for credentials nor connects nor anything.
What might be wrong?

Thanks much in advance,

Teo

If you are running 8.04 LTS and the share you are trying to access is password protected, then this is a known bug which is being worked on.

More information and a manual fix is available on launchpad at [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/207072)

---

### Post by thomsany on 2008-05-09
Great, now I know why it wasn't working..
will wait for the patch to come out..
Regards,

Teo

---


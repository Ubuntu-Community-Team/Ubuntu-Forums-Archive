---
title: "using  ubuntu through a vm player"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by animefan61 on 2008-07-29
I am using windows xp and downloaded vm player to use ubunto. I downloaded ubuntu 840, but I don't know what my user name and password is. Can anyone tell me what the user and password might be? My computer is used and I don't know who had it before me. Thanks in advance for any help you can give me.

---

### Post by LinuxRocks713 on 2008-07-31
> **animefan61 said:**
> I am using windows xp and downloaded vm player to use ubunto. I downloaded ubuntu 840, but I don't know what my user name and password is. Can anyone tell me what the user and password might be? My computer is used and I don't know who had it before me. Thanks in advance for any help you can give me.

Did you download the Ubuntu iso and install it yourself or did you download a preinstalled vm? If you have a preinstalled VM, do the following steps to fix it:

[LIST=1]
[*]Restart in recovery mode
[*]Type in "adduser *yourusername*", you will be prompted for password
[*]Type in "addgroup *yourusername*"
[*]Type in "adduser *yourusername* adm"
[*]Type in "adduser *yourusername* disk"
[*]Type in "adduser *yourusername* dialout"
[*]Type in "adduser *yourusername* cdrom"
[*]Type in "adduser *yourusername* floppy"
[*]Type in "adduser *yourusername* audio"
[*]Type in "adduser *yourusername* dip"
[*]Type in "adduser *yourusername* video"
[*]Type in "adduser *yourusername* plugdev"
[*]Type in "adduser *yourusername* fuse"
[*]Type in "adduser *yourusername* lpadmin"
[*]Type in "adduser *yourusername* admin"
[*]Type in "adduser *yourusername* vboxusers"
[*]Type in "adduser *yourusername* sambashare"
[*]Type in "adduser *yourusername* *yourusername*"
[*]Type in "echo 'export LD_LIBRARY_PATH=/usr/local/lib' >> ~/.profile"
[*]Restart and login!
[/LIST]

---

### Post by Gravidar on 2008-08-16
Not sure if you got that to work but all the vmware appliances for Ubuntu I've seen have a user ID: user & password: user
Worth a shot.

---


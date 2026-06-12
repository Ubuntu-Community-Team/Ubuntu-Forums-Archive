---
title: "how to create share folder?"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by tomzie on 2013-02-08
I wanted to create a shared folder called winxpshare. So far, I have created the same folder name in /media/winxpshare in Ubuntu. When I try to mount is as sudo mount -t vboxsf winxpshare /media/winxpshare, I get mount: unknown filesystem type 'vboxsf'. My Ubuntu environment is inside VirtualBox 4.2.6. When I type in groups, I get the following below. I have my Ubuntu environment as black and command type. I am not sure if that make sense.
 
test adm cdrom sudo dip plugdev sambashare lpadmin.
 
Please help. Thanks.

---

### Post by Morbius1 on 2013-02-08
If you created the shared folder within the VBox application for that Ubuntu guest there is no need to manually mount it. It will automatically mount at boot to:
> /media/sf_winxpshareFrom your output of "groups" however you will not be able to access it so you will need to add yourself to the correct group in the Ubuntu guest:
```
sudo gpassswd -a your-user-name vboxsf
```THen logout and login again for the group membership to take affect.

---


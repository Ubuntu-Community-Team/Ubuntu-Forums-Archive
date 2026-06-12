---
title: "Resolution Problems with old laptop"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by MantinoX on 2008-05-09
Hello I decided to bring back to life an old Dell Latitude C800 Laptop from the dead using Xubuntu 8.04. When installed the screen cuts into three sections and that came be fixed by pressing "FN"+F7  however I can not go pass 800x600. 

I searched the net and found this code
```
sudo dpkg-reconfigure xserver-xorg
```

WHen i do this it dosent give me the options to change the resolution.

Can any one help thanks.

---

### Post by stump138 on 2008-05-09
Try letting xorg reconfigure itself first
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If that doesn't work for you, you can edit your xorg.conf file.  There are examples all over these forums of how you can edit your video settings in xorg.

---

### Post by MantinoX on 2008-05-09
Did that and it says 

Xserver-org is not installed

---

### Post by MantinoX on 2008-05-09
Figured it out thanks for the help

---


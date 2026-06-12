---
title: "How to create a shortcut to Devices"
date: 2015-04-01
forum: New to Ubuntu
---

### Post by houmingc on 2015-04-01
Have a second HDD in ubuntu (/media/SecondDrive)
Want to create a shortcut to Devices on Desktop
Wonder why fail creating softlink (shortcut) on the desktop (/home/ste/Desktop) called Storage123

ln -s target <- linkName

ln -s /media/SecondDrive /home/ste/Desktop/Storage123

Please help, God bless.

---

### Post by kerry_s on 2015-04-01
shouldn't it /dev/something not /media ?

what does "fdisk -l" say in terminal ?

---

### Post by newb85 on 2015-04-01
Is this device already mounted, or are you expecting it to mount when you try to access it through this shortcut?

---

### Post by yancek on 2015-04-01
You could install gnome-panel:

```
sudo apt-get install --no-install-recommends gnome-panel  
```

Then to create a shortcut on the Desktop:

```
gnome-desktop-item-edit /home/user/Desktop --create-new
```

In the window which opens, fill in the boxes.  In this case be sure to select 'Location'.

---

### Post by Bucky Ball on 2015-04-01
As mentioned, the device needs to be mounted for your symlink to work. 

An alternative is to create a launcher if you want it on the desktop. Right click the desktop>create launcher>for the command:

```
<name-of-your-file-manager> /media/SecondDrive
```

... where <name-of-your-file-manager> is just that. For instance:

```
nautilus /media/SecondDrive
```

That will open a Nautilus window at /media/SecondDrive.

BTW, if /SecondDrive is mounted, your original command should work fine if the paths are correct. ;)

---


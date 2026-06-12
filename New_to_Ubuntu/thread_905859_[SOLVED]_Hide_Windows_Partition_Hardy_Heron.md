---
title: "[SOLVED] Hide Windows Partition Hardy Heron"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Glen_Danzig on 2008-08-30
I need help to remove the Windows partition from view on my Hardy Heron install. I have followed the advice in this [previous post]("http://backports.ubuntuforums.com/showthread.php?t=99086&page=2"). It does not matter whether it is mounted or not as it does not show up when I edit /etc/fstab. That partition does appear in the fdisk -l list whether it is mounted or not. Any suggestions how to prevent Gnome from showing that "10.7 GB media" (see attached screen cap) in the drop down and file explorer?

---

### Post by drs305 on 2008-08-30
This is something I used long ago but it may still work. It tells HAL to ignore this drive. Remember what you have done because some day you may want to access it!

The first 2 commands may produce errors - the first if the folder exists and the second if the file does not. Ignore them.
```
mkdir /usr/share/hal/fdi/preprobe/95userpolicy
sudo cp /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi.bak
gksu gedit /usr/share/hal/fdi/preprobe/95userpolicy/10ignore-disks.fdi

```
Add all to an empty file:
Add the bold after **<deviceinfo version="0.2">** if the file exists. Add a section for each device you want hidden. Make sure to use the correct *[COLOR="Red"]/dev/device[/COLOR]* location.
```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
[B]<device>
<match key="block.device" string="/dev/**[COLOR="Red"]sda1[/COLOR]**">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>[/B]	
</deviceinfo>

```
restart hal :  ```
sudo /etc/init.d/dbus restart
```

---

### Post by Glen_Danzig on 2008-08-30
Thank you for that. It worked.

One item of note, I manually created the "10ignore-disks.fdi" file after making this directory: ```
mkdir /usr/share/hal/fdi/preprobe/95userpolicy

```.

Then edited it by inserting ```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
<device>
<match key="block.device" string="/dev/sda1">
<merge key="info.ignore" type="bool">true</merge>
</match>
</device>	
</deviceinfo>
``` followed by restarting the dbus daemon.

---


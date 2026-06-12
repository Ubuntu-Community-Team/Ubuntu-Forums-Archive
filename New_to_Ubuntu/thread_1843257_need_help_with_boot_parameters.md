---
title: "need help with boot parameters"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by mitchell56141 on 2011-09-13
To get lubuntu to boot i need to add acpi=off i need to know how to make this change permanent so i can boot it from the hdd how do i go about making these changes any help would be nice i am a noob so please help me

---

### Post by 2F4U on 2011-09-13
For Grub2 on Ubuntu: 
- Edit the file /etc/default/grub. 
- Add [FONT=Verdana]your boot parameter at[/FONT] the end of the line GRUB_CMDLINE_LINUX_DEFAULT=. 
- Then sudo update-grub

---

### Post by seawolf167 on 2011-09-13
As said above, edit the config file

```
gksu gedit /etc/default/grub
```

add your changes to the line mentioned, save, exit then run

```
sudo update-grub
```

[See here ]("http://ubuntuforums.org/showthread.php?t=1195275")for a guide.

---

### Post by mitchell56141 on 2011-09-13
it won´t let me overwrite the the file it says can´t open file to overwrite what should i do then

---

### Post by seawolf167 on 2011-09-13
You'll need to ensure you open with root privileges - see [here]("https://help.ubuntu.com/community/RootSudo"). (thats what the *gksu* is for)

---


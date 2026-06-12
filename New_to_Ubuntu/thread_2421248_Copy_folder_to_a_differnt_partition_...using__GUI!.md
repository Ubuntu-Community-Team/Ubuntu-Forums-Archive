---
title: "Copy folder to a differnt partition ...using  GUI! - NOT CLI !"
date: 2019-06-18
forum: New to Ubuntu
---

### Post by anneranch on 2019-06-18
OK, there are tons of "how to " using command line interface. 

The "file" app in Ubuntu is GUI and "Copy to.." is a GUI option.

The "problem"  ">>> you do not  have permission to CREATE new folder >>>" in destination.
Using "chown" is hokey, defeats the GUI, and it doesn't do the job anyway. 

**So is using GUI to "Copy to..." no option  option**?

I am not moving the entire /dev.sdx        just want to move a folder 
Any help would be appreciated.

---

### Post by QIII on 2019-06-18
Did you use sudo to change *permissions* not ownership?

You most likely don't want to chown the entire receiving directory.

---

### Post by again? on 2019-06-18
[s]Install nautilus-admin which will give you a right click "Edit as Administrator" and "Open as Administrator" option for files and folders respectively.
```
sudo apt install nautilus-admin
```

Kill nautilus to see in menu.
```
nautilus -q
```[/s]

Scratch that.
Doesn't work anymore in nautilus with copy to.
Works in nemo.

---

### Post by QIII on 2019-06-18
Viable, but GUI as admin stuff is dangerous.

Also, how is the directory mounted?  In fstab?  Have you thought about changing the permissions at mount?

---

### Post by kevdog on 2019-06-20
Could you not use cp or rsync?

---


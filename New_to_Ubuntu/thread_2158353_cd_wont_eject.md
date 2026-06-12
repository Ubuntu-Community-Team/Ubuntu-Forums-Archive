---
title: "cd wont eject"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by ub9876 on 2013-06-28
my cd wont eject unless I restart the computer and hit the button when the little light is on.... what will fix this??

---

### Post by ajgreeny on 2013-06-28
Is some application still using the CD making it impossible to unmount?

What error message, if any, do you get from the command **eject** in terminal?

---

### Post by Kujua on 2013-06-28
> **ub9876 said:**
> my cd wont eject unless I restart the computer and hit the button when the little light is on.... what will fix this??
A new CD drive :)

I might not be of much help here, but just wanted to say that I too had similar issues with my desktop's CD drive long back. It just wouldn't open up. So instead of pressing the button I would run the 'eject' command, which used to work very well for me.

---

### Post by ub9876 on 2013-06-28
mine says something about it being busy on files or something..???

---

### Post by ajgreeny on 2013-06-29
You may find that if you hold in the eject button for several seconds the disk will stop spinning, if it still is, and eject as you want.

---

### Post by buzzingrobot on 2013-06-29
Try "sudo eject -i off". If the tray has been locked for some reason, this will unlock it and allow you to use the device's button to eject the disk.

I run into this a lot using Brasero to blank and burn images.

---


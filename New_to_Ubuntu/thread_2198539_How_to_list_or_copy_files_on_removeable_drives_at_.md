---
title: "How to list or copy files on removeable drives at command line?"
date: 2014-01-09
forum: New to Ubuntu
---

### Post by ruwan2 on 2014-01-09
Hi,
I know GUI file manager can do this work. Sometimes I would like to use command in a terminal to manipulate files on CD or flash drive. How to do that? Thanks,

---

### Post by Impavidus on 2014-01-09
Usually the removable drive will be mounted at /media/label/. Navigate there in the terminal and it works the same way as managing files in your home dir. For my Kingstom usb thumb drive:```
cd /media/KINGSTON
ls
```This is on 12.04. I think on later versions the removable drive will be mounted at /media/username/label/.

---

### Post by jaimeda104 on 2014-01-10
Just adding to Impavidus post. If you are new to file managment terminal commands (copy, paste, move, remove, etc.) this easy link can help you out:

[http://www.howtogeek.com/107808/how-to-manage-files-from-the-linux-terminal-11-commands-you-need-to-know/](http://www.howtogeek.com/107808/how-to-manage-files-from-the-linux-terminal-11-commands-you-need-to-know/)

Also, if for any reason the deivce is not mounting in an automatic way you can use the commands mount and umount in terminal to do so.

---


---
title: "how can i empty trash bin as root"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by malanco on 2008-07-05
hi, i want to know how to empty the trash bin as root because when i want to empty the trash bin some files are kept and i get the message that i dont have the permission, i know i can change the permissions of that files, but i would be easier if i can just know how to empty the trash bin as root, thanks guys. :)

---

### Post by GuitarRocker2562 on 2008-07-05
In terminal

```
sudo rm -rf /home/YOURUSERNAME/.trash
```

---

### Post by malanco on 2008-07-05
hey thanks guitarocker!! :guitar:

---

### Post by ChameleonDave on 2008-07-05
> **GuitarRocker2562 said:**
> In terminal

```
sudo rm -rf /home/YOURUSERNAME/.trash
```

That is for earlier versions.  In Hardy Heron, you need to do this:

```
sudo rm -rf ~/.local/share/Trash
```

You should also empty root's trash, just in case:

```
sudo rm -rf /root/.local/share/Trash
```

In additional, any extra partitions you have mounted will have their own trashcans for each user who has deleted files on that partition.  I, for instance, have to do the following to clear that out:

```
sudo rm -rf ~/Files/.Trash*
```

> **malanco said:**
> hey thanks guitarocker!! :guitar:

To thank him, click on the thank icon on his post.

---

### Post by malanco on 2008-07-05
ok, trash folder is at /.local so my the command looks like this :

sudo rm -rf /home/YOURUSERNAME/.local/share/Trash/files

:)

---

### Post by aysiu on 2008-07-05
Please be **very** careful when entering any of those commands into the terminal. Mess up and you can end up removing a lot more than what's in your trash.

If you decide to use those commands, I highly suggestion you copy and paste instead of retype.

Probably the safest thing to do is ```
sudo chown -R *username* /home/*username*/.local/share/Trash/files
``` and then empty the trash the traditional way.

I suspect people are getting root-owned files in the trash because they're running graphical applications with *sudo* instead of *gksudo*. If you're getting a lot of root-owned files in the trash, read this link: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---


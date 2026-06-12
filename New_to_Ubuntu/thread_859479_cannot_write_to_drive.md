---
title: "cannot write to drive"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by K-D on 2008-07-14
[COLOR="SeaGreen"]I have managed to partition my new drive but it won't let me copy files from an external drive.  I get this error message:

The folder "Kris" cannot be copied because you do not have permissions to create it in the destination[/COLOR]

Any help would super!

Thanks

---

### Post by kk0sse54 on 2008-07-14
You need to change the ownership of the drive. Start nautilus as root by pressing alt+f2 and then typing ```
gksudo nautilus
```. Then navigate to the other drive right click on it and select properties and then go to permission and change the ownership and access rights to the drive to your user name. If you want it done in the terminal use chmod or chown.

---

### Post by K-D on 2008-07-15
Sounds like exactly what i need to do! i will try it tonight when I get n from work.

A stupid question (but I have only been using UBuntu for about 20 hours now)

what difference would it make having it in the terminal?

Cheers

---

### Post by benfindlay on 2008-07-15
In terminal you would type ```
sudo cp /path/of/source/folder/Kris /path/to/destination
```
Hit enter and you will be asked for a password

Also, depending on your view on security, you can create a folder called "Kris" on your main drive using ```
sudo mkdir /path/to/where/you/want/Kris
```

Then you can change ownership of the folder using```
sudo chown -hR [yourusername] /path/to/folder/Kris
```

Hope this helps!

---

### Post by K-D on 2008-07-16
Thanks to both you guys!

This kind of simple help will make Ubuntu really start to become used mainstream!

:guitar:

---

### Post by benfindlay on 2008-07-16
No problems, and welcome to the club! ;)

---

### Post by jimv on 2008-07-16
> **K-D said:**
> Thanks to both you guys!

This kind of simple help will make Ubuntu really start to become used mainstream!

:guitar:

This message board is nothing short of amazing.  You really can't get this kind of help with Windows...not that I've seen.  You post a message here, and a lot of the time have a reply within a few minutes,  Very cool.

---


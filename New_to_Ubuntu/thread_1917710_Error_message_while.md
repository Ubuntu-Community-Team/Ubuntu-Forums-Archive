---
title: "Error message while"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by Peterfc on 2012-01-30
HI
I am trying to setup an online radio station. While trying to follow what it says i get an error message as i try to download and move the download to User/.

The instruction say.

Download the shoutcast server (latest version):

[http://www.shoutcast.com/download/files.phtml](http://www.shoutcast.com/download/files.phtml)

Copy it to the /usr directory and create a folder called shout:

When i try to do this it says Error while moving "sc_serv2_linux_07_31_2011.tar.gz". There was an error moving the file into /. Error moving file: Permission denied

After going into properties and going to permissions i get another error. That i don't have permission, also if i go into share i get another error.

Please click on the thumbnail to view the error messages i am getting.

Thanks for reading my post for help.

---

### Post by drmrgd on 2012-01-30
The problem is that you need root permissions to alter these folders.  If you want to do it by GUI (i.e. Nautilus), then issue:

```
gksudo nautilus
```

into a terminal in order to run Nautilus as root.  Then you should be able to do what you need to do.  

Alternatively, of course, you could do everything you're trying to do by command line by just adding sudo in front of each instruction.

---

### Post by halitech on 2012-01-30
alternatively, just create a folder called bin in your home folder and install shoutcast there then you don't have to mess around with sudo or file permissions

---


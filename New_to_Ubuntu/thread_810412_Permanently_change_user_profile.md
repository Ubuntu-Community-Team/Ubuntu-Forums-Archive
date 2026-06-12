---
title: "Permanently change user profile"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-05-28
Hi,

55 years old, 15 years locked into Windows and only just exploring some form of Linux!!

I'm trying to uncompress a tarball into /opt/xampp/htdocs/ (if I've remembered that correctly), but I cannot!. I can't remember the error message but basically I don't have write permission for that directory.

There is only one user profile (except root) and that's me. How do I change my profile/settings/whatever so that I automatically have such write permissions whenever I log on?

---

### Post by bumanie on 2008-05-28
Firstly to compile a tarball, you have to install build-essential. If yiou have not done that sudo > apt-get install build-essential in terminal. It would be handy if you could cut and paste the error message and post it. To uncompress it you can right click on the tarball and then choose 'extract here'. After that you can compile it. In the extracted file, there should be a text file with instructions on how to compile it.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-05-28
try going to system>preferences>About Me

Check if you can change your accounts name and whatver.

Also, welcome to ubuntu!

---

### Post by wdaniels on 2008-05-28
> **Tim Silver said:**
> There is only one user profile (except root) and that's me. How do I change my profile/settings/whatever so that I automatically have such write permissions whenever I log on?

Ubuntu isn't set up to work that way - you shouldn't write to this part of the filesystem as a normal user. So long as your user is part of the admin group (which it will already be if it's the one created during install) you can gain root privileges using the command "sudo" in a terminal, and providing your user password when prompted.

If you want to write to somewhere with root privileges via the graphical tools you could always just do:

```
sudo nautilus
```

to get get a file browser window running on the root account.

---

### Post by Tim Silver on 2008-05-28
Thanks All,

I don't have my laptop with me at the moment (I'm doing this from my work PC), but I'll certainly have another try tomorrow. Why tomorrow? Bloody BT can't guarantee me even a 1MB broadband connection so I've given-up my land-line in disgust! So it'll have to wait until tomorrow lunchtime - 'cause I want to be able to read your comments on my work monitor. :)

---

### Post by Tim Silver on 2008-05-29
OK chaps,

So I typed```
sudo nautilus
``` into the terminal window and this is what happened -
```
seahorse nautilus module initialized
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net
usershare' returned error 255: net usershare: cannot open usershare
directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

** (nautilus:7518): WARNING **: Unable to add monitor: Not supported
seahorse nautilus module shutdown
```

I've searched help and can find nothing about user sharing! Any suggestions?

As an aside - is it possible to copy & paste from the terminal window?

---


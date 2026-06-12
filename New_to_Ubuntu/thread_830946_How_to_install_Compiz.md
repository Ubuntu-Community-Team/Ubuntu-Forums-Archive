---
title: "How to install Compiz"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Tharakanuwanpro on 2008-06-16
I don't have internet connection for ubuntu hardy . I have downloaded compiz but its a tar.gz file . How can i install without internet

---

### Post by aktiwers on 2008-06-16
It's already there.
Go to: System => Preferences => Appearance
And pick the Visual Effects tab.

If you want to be able to customize it more, plug your computer to the net and type:
```
sudo apt-get install compizconfig-settings-manager
```And run it by:
```
ccsm
```

---

### Post by issih on 2008-06-16
You don't need the tar.gz at all, its already installed with hardy.
Just go to:

System->Preferences->Appearance

Then on the Visual Effects Tab tick normal or extra, either of those enables compiz fusion.

What you may want is to download a deb for compizconfig-settings-manager. As that allows you to change the settings of compiz to use different effects.

---

### Post by Tharakanuwanpro on 2008-06-16
Thank You Very Much . But how can i install packages with tar.gz

---

### Post by Joeb454 on 2008-06-16
Well for this particular package you don't need to. Compiz is already installed in Ubuntu as of version 7.10 :)

---

### Post by aktiwers on 2008-06-16
Usually it has a readme file, but it depends whats inside it.
Extract it first, right-click and pick "extract". Then look whats inside the folder.

If its source code, you need to compile it manually, if its a .bin or another executable you can run it.

Or post link to the tar.gz you downloaded and we can have a look

---

### Post by bobnutfield on 2008-06-16
The basic command is:

> tar xvf <your application>.tar.gz

That will decompress the file and create a directory with the same name as the application.

Then, change to that directory, then run:

> make && make install

You may have to run it as sudo (many apps require this.

But, whenever installing from a tar.gz file READ THE README FILE FIRST.  This will give you specific information that is relevant to the app.

Hope that helps

Bob

---

### Post by Tharakanuwanpro on 2008-06-16
Thank You . I Thanked you all . So Much Info

---

### Post by stoodleysnow on 2008-06-16
If you want Compiz Config Settings Manager (So you can customise compiz with a nice GUI), get yourself to a computer with internet and go to the Ubuntu repository site. There you can download CCSM in .deb format.
Take it by means of USB stick or other handy portable storage back to your Ubuntu PC and open the deb to install.
If you are using Ubuntu 32 bit get the i386 file, or if 64bit get the amd64 file.

---


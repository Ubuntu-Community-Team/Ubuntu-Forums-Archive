---
title: "Installing Webmin"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-09
I tried to run the command line to get an install webmin recieved an error trying to get the app. So i went to webmin website and downloaded the debian version webmin_1.441_all.deb now i have this file sitting on my desktop for ubuntu desktop 8.10. I tried to install using 

sudo dpkg -1 webmin_1.441_all.deb and recieved an error

dpkg: error processing webmin_1.441_all.deb ( -- install ): cannot access archive: no such file  or directory webmin_1.441_all.deb

Now this file webmin_1.441_all.deb is sitting on my desktop. how do i go about installing this?

---

### Post by taurus on 2008-11-09
Are you sure you were in the right directory when you ran that command?

```
cd ~/Desktop
sudo dpkg -**i** webmin_1.441_all.deb
```

---

### Post by shanep-server on 2008-11-09
ok that worked. Ur awesome but can u explain something too me. Im obviously new what does "dpkg -1" mean. I didn't know how to move up lvls to get to desktop and such. Its kind of like the old school dos command cd (file/folder) what would i use to get back down in the tree? Lets say i wanted to back out of /Desktop ? Do you know a good reference that would explain how too move around and command in terminal. I'm not new to computers just linux os.

---

### Post by echovolutionx on 2008-11-09
:confused::(:confused:

---

### Post by shanep-server on 2008-11-09
why are you following me around with confused look LOOOL.

---

### Post by taurus on 2008-11-09
> **shanep-server said:**
> ok that worked. Ur awesome but can u explain something too me. Im obviously new what does "dpkg -1" mean. I didn't know how to move up lvls to get to desktop and such. Its kind of like the old school dos command cd (file/folder) what would i use to get back down in the tree? Lets say i wanted to back out of /Desktop ? Do you know a good reference that would explain how too move around and command in terminal. I'm not new to computers just linux os.

If you want to move up one directory, then you can use the .. such as

```
cd ..
```
Remember, Linux/Unix is case sensitive so Desktop is not the same as desktop.  And the ~ means it's your $HOME directory so when you do

```
cd ~/Desktop
```
it means that move down to Desktop subdirectory from your $HOME.  

And if you want to install a .deb, you have to use the -i option, not -1.  To lean more about dpkg, just read the manpage.

```
man dpkg
```

---


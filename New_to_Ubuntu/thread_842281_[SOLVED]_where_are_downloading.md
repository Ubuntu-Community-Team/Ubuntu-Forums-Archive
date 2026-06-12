---
title: "[SOLVED] where are downloading"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by bengar on 2008-06-27
Hi
I did a download of dedsum, gisomount and isomd5sum, to verify the md5 sum of an iso, but, I don't know where was downloaded, could someone tell where?.
Thanks
bengar

---

### Post by kpkeerthi on 2008-06-27
Run these commands

1. sudo updatedb
2. locate <file-name-to-search>

---

### Post by sharks on 2008-06-27
may be in home folder.

---

### Post by lisati on 2008-06-27
If you downloaded with Firefox, you can click on Tools->Downloads from within Firefox. This will open a download window, which usually tells you at the bottom of the window where it sends the downloads.

---

### Post by manishtech on 2008-06-27
> **bengar said:**
> Hi
I did a download of dedsum, gisomount and isomd5sum, to verify the md5 sum of an iso, but, I don't know where was downloaded, could someone tell where?.
Thanks
bengar
You downloaded and installed it from the repos using apt-get/synaptic?

Or you downloaded it through firefox or any browser as **lisat**i asked?

---

### Post by bengar on 2008-06-28
> **manishtech said:**
> You downloaded and installed it from the repos using apt-get/synaptic?

Or you downloaded it through firefox or any browser as **lisat**i asked?

Yeap using the synaptic. Let me check again and I will tell us if i found something.

---

### Post by bengar on 2008-06-28
> **kpkeerthi said:**
> Run these commands

1. sudo updatedb
2. locate <file-name-to-search>

I used it, but ask me about the root password, I can;t login the terminal display  > Authentication failure Let me resolve this issue first, to see then if it work for me.

---

### Post by manishtech on 2008-06-28
> **bengar said:**
> Yeap using the synaptic. Let me check again and I will tell us if i found something.
If you download download it using Synaptic then it goes to **/var/apt/cache/archives/** all the packages which are downloaded are cached here.

---

### Post by bengar on 2008-06-28
> **manishtech said:**
> If you download download it using Synaptic then it goes to **/var/apt/cache/archives/** all the packages which are downloaded are cached here.

Great, I found it, thank you very much manishtech, I have a lot of applications that I did downloaded and was there. But after reinstall the package and don't see on the applications menu the icon of the application.

---

### Post by oldos2er on 2008-06-28
If these are CLI programs, there will be no menu entry for them. Just type the program name in a terminal.

 When you enter your password in a terminal, nothing is echoed back to the screen. This is normal. Just type it in and hit Enter.

---

### Post by dizee on 2008-06-28
> **bengar said:**
> Hi
I did a download of dedsum, gisomount and isomd5sum, to verify the md5 sum of an iso, but, I don't know where was downloaded, could someone tell where?.
Thanks
bengar
did you know that you can check md5sums through the terminal?
```
md5sum isofile.iso
```

---

### Post by manishtech on 2008-06-30
> **bengar said:**
> Great, I found it, thank you very much manishtech, I have a lot of applications that I did downloaded and was there. But after reinstall the package and don't see on the applications menu the icon of the application.
If you installed these command line programs/apps then use them through Terminal.
If you don't know the exact name, then type some few characters and press Tab button, it will auto-complete. 
If fit doesn't auto-complete, then it means the no of matches are more than one or none. In this case, press Tab button twice in quick succession.
Try to type **isomd** and press tab, the suggestions will be listed,if none, then try twice Tab.

As an example you can try to type **ls** and press tab twice, you can see many suggestions like **ls**,**lspci**,**lsusb** and more

---

### Post by crtlbreak on 2008-06-30
> **bengar said:**
> Great, I found it, thank you very much manishtech, I have a lot of applications that I did downloaded and was there. But after reinstall the package and *don't see on the applications menu *the icon of the application.

Good Day bengar 
I think you are trying to look for some shortcuts in your menu - as in the MS environment.
Most registered programs will  create their own  - although shortcuts in the desktop menu is only recently starting to show in development. The traditional way to start a program in Linux is to type <firefox> or <gaim> at the command prompt to launch it - without the brackets.
You can create your own shortcuts in your menus with
with sudo gedit /usr/share/applications/application_name and save the content within the shortcut as follows

[Desktop Entry]
Encoding=UTF-8
Name=Application_Name
Comment=Application Name Text Label
Exec=application
Icon=/path/to/icon.xpm
StartupNotify=true
Terminal=false
Type=Application
Categories=Applications;Network

Then save the gedit content - Presto - you should have created your own shortcut. Let me know if this helps

---

### Post by bengar on 2008-06-30
Thank you very much to all, now I learned some else about Ubuntu Linux, let me try making the necessary in the terminal to see what happened. I think that all these suggestion will resolved the problem.

---


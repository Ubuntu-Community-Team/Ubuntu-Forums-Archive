---
title: "launching application with desktop shortcut?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by zachbb on 2008-11-13
Hi

A shortcut on my desktop dosent work... I installed a program called ZendStudio, and it is clearly visable in this directory:
/home/zach/Zend/ZendStudioForEclipse-6.0.0/ZendStudio

see:
```
zach@zach-laptop:~/Zend/ZendStudioForEclipse-6.0.0$ pwd
/home/zach/**[COLOR="SeaGreen"]Zend/ZendStudioForEclipse-6.0.0[/COLOR]**

zach@zach-laptop:~/Zend/ZendStudioForEclipse-6.0.0$ ls
about_files    icon.xpm         Uninstall Zend Studio for Eclipse - 6.0.0
about.html     jre              **[COLOR="SeaGreen"]ZendStudio[/COLOR]**
configuration  libcairo-swt.so  ZendStudio.ini
docs           plugins          zend-zendstudioeclipse.desktop
features       toolbars

```

And I have a shortcut on my desktop (which was automatically installed) which points to /home/zach/Zend/ZendStudioForEclipse-6.0.0/ZendStudio

But when I click it, it says:
> 
**There was an error launching the application.**
Details: Failed to change to directory '"/home/zach/Zend/ZendStudioForEclipse-6.0.0"' (No such file or directory)

What's up with that?

---

### Post by dustman on 2008-11-13
How is the laucher on your desktop set? I mean, what's the command it has to run when you double click it?

---

### Post by Tomatz on 2008-11-13
Do this (in a terminal):

```
sudo touch /usr/bin/mylaunch

```
```
sudo gedit /usr/bin/mylaunch
```

add the following to the file:

```
~/Zend/ZendStudioForEclipse-6.0.0
```

save & close

```
sudo chmod a+x /usr/bin/mylaunch
```


Now just set your launcher to launch the command **mylaunch**

---

### Post by zachbb on 2008-11-13
> **dustman said:**
> How is the laucher on your desktop set? I mean, what's the command it has to run when you double click it?


My launcher is set to:
/home/zach/Zend/ZendStudioForEclipse-6.0.0/ZendStudio

Tomatz: that looks a bit complicated for just creating a shortcut.. perhaps this can be fixed?

---

### Post by dustman on 2008-11-13
> **zachbb said:**
> My launcher is set to:
/home/zach/Zend/ZendStudioForEclipse-6.0.0/ZendStudio


at the end of the line, shouldn't there exist the name of a binary file, like there is in Windows: "C:\Path_to_program\program.exe"?

Btw, what Tomatz said is great. You could use that command not only for this launcher, but for any launcher you want, and also you can easily start the program from the command line.

Cheers!

Radu

---

### Post by zachbb on 2008-11-13
The binary file IS ZendStudio:

```
zach@zach-laptop:~/Zend/ZendStudioForEclipse-6.0.0$ ls -la
total 448
drwxrwxr-x 10 zach zach   4096 2008-11-13 11:42 .
drwxrwxr-x  4 zach zach   4096 2008-11-12 20:04 ..
drwxrwxr-x  2 zach zach   4096 2008-11-12 19:28 about_files
-rwxrwxr-x  1 zach zach    577 2008-01-07 11:05 about.html
drwxrwxr-x  7 zach zach   4096 2008-11-12 20:04 configuration
drwxrwxr-x  3 zach zach   4096 2008-11-12 19:28 docs
-rwxrwxr-x  1 zach zach    118 2008-01-07 11:05 .eclipseproduct
drwxrwxr-x 88 zach zach  12288 2008-11-12 19:29 features
-rwxrwxr-x  1 zach zach  52546 2008-01-07 11:05 icon.xpm
drwxrwxr-x  8 zach zach   4096 2006-09-11 17:50 jre
-rwxrwxr-x  1 zach zach 266168 2008-01-07 11:05 libcairo-swt.so
drwxrwxr-x 44 zach zach  45056 2008-11-12 19:29 plugins
drwxrwxr-x  2 zach zach   4096 2008-11-12 19:28 toolbars
drwxrwxr-x  2 zach zach   4096 2008-11-12 20:04 Uninstall Zend Studio for Eclipse - 6.0.0
**[COLOR="SeaGreen"]-rwxrwxr-x  1 zach zach  21118 2008-01-07 11:05 ZendStudio[/COLOR]**
-rwxrwxr-x  1 zach zach    258 2008-11-12 19:29 ZendStudio.ini
-rw-r--r--  1 zach zach    280 2008-11-12 19:28 zend-zendstudioeclipse.desktop
zach@zach-laptop:~/Zend/ZendStudioForEclipse-6.0.0$ 

```

For some reason the shortcut dosent work and it points right to that file!!

---

### Post by dustman on 2008-11-13
> There was an error launching the application.
Details: Failed to change to directory **[COLOR="Blue"]'[/COLOR][COLOR="Red"]"[/COLOR]**/home/zach/Zend/ZendStudioForEclipse-6.0.0**[COLOR="Red"]"[/COLOR][COLOR="Blue"]'[/COLOR]** (No such file or directory) 

Can it be that the problem is from those quotes([COLOR="Blue"]'[/COLOR])/double-quotes([COLOR="Red"]"[/COLOR])?

---

### Post by zachbb on 2008-11-13
I've tried, without quotes, with single quotes '' and with double quotes ""... nothing works...

---

### Post by Tomatz on 2008-11-13
> **zachbb said:**
> 
Tomatz: that looks a bit complicated for just creating a shortcut.. perhaps this can be fixed?



Linux doesnt have a registry so windows style shortcuts are a no go. You can create a symbolic link to the executable by r-clicking on the executable and selecting *"make link"*.

Also, make sure the executable has permissions to be executed. **R-click** on the *"ZendStudio"* executable, select the **permissions** tab then check *"allow executing as a program"* if deselected.

;)

---

### Post by zachbb on 2008-11-13
Thanks for your reply.

I did what you said I made it executable and made a link (right click -> make link), but when I double click on the link it says:
> "[B]There was an error launching the application.
[/B]Details: Failed to change to directory '"/home/zach/Zend/ZendStudioForEclipse-6.0.0"' (No such file or directory)"

The link is right there in the same folder. When I move it to my desktop it dosent work either!!

Another thing that I noticed is that I can't open the program by double clicking in Nautilus. I can only open it by going to the directory in the Terminal and opening it there:
> zach@zach-laptop:~/Zend/ZendStudioForEclipse-6.0.0$ ./ZendStudio


---

### Post by Tomatz on 2008-11-13
> **zachbb said:**
> Thanks for your reply.

I did what you said I made it executable and made a link (right click -> make link), but when I double click on the link it says:


The link is right there in the same folder. When I move it to my desktop it dosent work either!!

Another thing that I noticed is that I can't open the program by double clicking in Nautilus. I can only open it by going to the directory in the Terminal and opening it there:

I think the only way you will be able to launch the app (from a launcher or menu) is like this:

*[COLOR="Red"]Note this is different from my previous post as i can see where you are going wrong now[/COLOR]* ;)

Do this in a terminal **(you can just copy and paste**):

```
sudo touch /usr/bin/mylaunch

```
```
sudo gedit /usr/bin/mylaunch
```

add the following to the file:

```
cd ~/Zend/ZendStudioForEclipse-6.0.0
./ZendStudio
```


save & close

```
sudo chmod a+x /usr/bin/mylaunch
```


Now just set your launcher to launch the command **mylaunch** *or alternativly r-click on the "applications" button (main menu), select edit menus and add an item with the command* **mylaunch**


I have had this happen with "static" (apps that arn't installed) apps before and this was the only way i could get them to launch from a launcher.

---


---
title: "How to install new icons in ubuntu"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by SandyM on 2008-08-15
I downloaded a icon package from Gnome look. Later I tried to copy the extracted package in /usr/share/icons but I am regularly getting message that I don't have permission to do this.

Please tell me how to copy?paste with root priviledges and is there any way to log in with root priviledges.
Also tell me if there is any alternate method to install icon packages

---

### Post by terry123b99 on 2008-08-15
Hi I beleive you need to extract them to /home/.icons

Correct me if am wrong, all I know is the icon folder is hidden

---

### Post by sharks on 2008-08-15
[http://ubuntuforums.org/showthread.php?t=3757](http://ubuntuforums.org/showthread.php?t=3757)

---

### Post by run1206 on 2008-08-15
> **SandyM said:**
> I downloaded a icon package from Gnome look. Later I tried to copy the extracted package in /usr/share/icons but I am regularly getting message that I don't have permission to do this.

Please tell me how to copy?paste with root priviledges and is there any way to log in with root priviledges.
Also tell me if there is any alternate method to install icon packages

(if your file was on the desktop for example...)

open a terminal and type 
```
sudo cp /home/"your username"/Desktop/"icon name" /usr/share/icons
```
it will prompt you for your password. type it in and press enter.  if you check through a file manager, you should see it now.

---

### Post by sharks on 2008-08-15
which theme have u downloaded(name)?

---

### Post by sharks on 2008-08-15
or type gksudo nautilus and type the password when prompted and copy the folder to usr/share/icons

dont forget to close nautilus and terminal after copying.

---

### Post by OldGrey on 2008-08-15
The method I use is to open up appearance and just drag and drop the unextracted package into the window. It is then installed automatically and even asks if you want to use the new icons.

---

### Post by durand on 2008-08-15
> **OldGrey said:**
> The method I use is to open up appearance and just drag and drop the unextracted package into the window. It is then installed automatically and even asks if you want to use the new icons.

Yes, that's the most secure and easiest way of doing this...Don't copy it to /usr/share/icons unless you need to install it system wide...

PS: This method also works with other themes, ie,  GTK and Metacity themes.

---

### Post by SandyM on 2008-08-15
> **sharks said:**
> which theme have u downloaded(name)?
I downloaded 59006-Kamel-alpha-0.3.tar.gz

---

### Post by LeetSpeak on 2008-08-15
Sandy, all you really have to do, is find the unextracted theme you just downloaded, open up system>preferences>appearance drag the theme right in there, it should say it's installing themes, after that it will tell you if you want them applied. Say yes and whoo your done :)

---

### Post by SandyM on 2008-08-15
> **sharks said:**
> or type gksudo nautilus and type the password when prompted and copy the folder to usr/share/icons

dont forget to close nautilus and terminal after copying.
Even after copying There is no option of icons I copied in appearance menu

---

### Post by LeetSpeak on 2008-08-15
> **SandyM said:**
> Even after copying There is no option of icons I copied in appearance menu

That's what happened to me yesturday, try one I just told you, thats how it worked for me, and if it doesn't I have another solution that will work.

---


---
title: "Which editor including ftp??"
date: 2009-05-30
forum: Programming Talk
---

### Post by Terradon2 on 2009-05-30
Hi all,
I am new to Ubuntu and thusfar very satisfied (my laptop starts in 24 seconds instead of 10 minutes with Vista.....)
But....
i am looking for an editor for webdesign. In windows i have used HTML-Kit which had ftp support, so i could easily edit and update my files directly via ftp.

i have tried to search this forum and installed a few editors, but all of them dont do what i want (or i am doing it wrong??)

I have installed:
Bleufish, gPHPEDIT, Quanta Plus en Screem.
In neither of them i just cant find an integrated ftp support??

I am not looking for a seperate ftp and also not for a wysiwyg editor.

Anyone any suggestions??

---

### Post by opticyclic on 2009-05-30
I believe NVU or its unofficial bug fix Kompozer included integrated FTP
Have you tried running HTML-kit under wine?

---

### Post by ruuz on 2009-05-31
I still prefer standalone FTP stuff. Filezilla is nice free program for FTP :)

---

### Post by yoasif on 2009-05-31
you should be able to connect to ftp servers in nautilus and use gio aware programs to edit files on ftp servers.

bluefish and gedit should work if you try this.

---

### Post by Terradon2 on 2009-05-31
Thanks for the answers, but I am still not getting it.

I thought NVU was a wysiwyg editor?

I don't understand what is ment with "HTML-kit under wine"
HTML-Kit had a linux version, but due to a lack of interest its depricated now and development for linux has stopped. Pitty, cause for windows i have a payed for registering (i use it daily, so why not?)

"bluefish and gedit" ?? 
Bluefish is already installed, so i need to install gedit too?

---

### Post by opticyclic on 2009-05-31
Sorry, I thought you were explicitly looking for a WYSIWYG editor!
Wine will let you install and run Windows applications on Linux.
Not everything works perfectly, but its worth a shot if you can't find an equivalent application.
[http://ubuntuforums.org/showthread.php?t=871535](http://ubuntuforums.org/showthread.php?t=871535)

gedit is probably already installed on your system as it comes with the Gnome installation of Ubuntu.
I think what yoasif is saying is that if you connect to your ftp server with nautilus, you can then directly edit the file on the server with most applications, including Bluefish and gedit

geany is another text editor (not quite an IDE) that I used to use for HTML, I'm not sure if it has ftp support though
[http://www.ubuntunews.info/geany-perfect-programming-ide](http://www.ubuntunews.info/geany-perfect-programming-ide)

---

### Post by Terradon2 on 2009-05-31
I have tried to install wine and then html-kit, but it wasn a real succes, not everything worked wel in html-kit and got some errors about violated acces at some points. So this seems no option. 
Wine seems to be a very nice piece of coding, but i changed to Ubuntu. Working with Windows program should not be a logical choice....

next option:
 "nautilus and use gio aware programs"

I can't find nautilus?? and what are gio aware programs??

---

### Post by opticyclic on 2009-05-31
Nautilus is the default file manager in Gnome.
Im not entirely sure what gio aware means, but I'm guessing it refers to being able to edit the file on the server once the file manager has made a connection

---

### Post by Terradon2 on 2009-05-31
I can open a remote php file with bluefish, but after editing i want to save it,
then i get an i/o failure??

---

### Post by Tibuda on 2009-05-31
> **opticyclic said:**
> Nautilus is the default file manager in Gnome.
Im not entirely sure what gio aware means, but I'm guessing it refers to being able to edit the file on the server once the file manager has made a connection

he means Places > Connect to server.

---


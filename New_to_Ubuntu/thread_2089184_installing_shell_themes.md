---
title: "installing shell themes"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by cabz on 2012-11-28
I downloaded a new shell theme from gnomelook.org and I was hopeing that it was as easy to install as regular gtk3 themes . but i found out that it is not . can anyone tell me how to install it?. BTW  I am running 12.10 on a satellite laptop if that matters.

---

### Post by Frogs Hair on 2012-11-28
The same procedure is used to install shell themes if you are placing the folders in .themes or usr/share/themes. Make sure the theme is Gnome 3.6 compatible and report back what exactly is going wrong.

---

### Post by cabz on 2012-11-28
> **Frogs Hair said:**
> The same procedure is used to install shell themes if you are placing the folders in .themes or usr/share/themes. Make sure the theme is Gnome 3.6 compatible and report back what exactly is going wrong. I tried to install the files in usr/share/themes I got an error message that said that i dont have permision to do this ?. do i have to do this in terminal? if so can you tell me how?

---

### Post by audiomick on 2012-11-28
> **cabz said:**
> I tried to install the files in usr/share/themes I got an error message that said that i dont have permision to do this ?. 

/usr belongs to root, so you need to get root privileges to put stuff in their. This can be done via GUI or via the terminal, I expect. How exactly were you trying to put the files in there?

---

### Post by Frogs Hair on 2012-11-28
To make changes in the file system you need to use the following terminal command.```
 gksudo nautilus   
```
Make sure the package is fully extracted and move the folder into usr/share/themes.

---

### Post by cabz on 2012-11-28
> **audiomick said:**
> /usr belongs to root, so you need to get root privileges to put stuff in their. This can be done via GUI or via the terminal, I expect. How exactly were you trying to put the files in there?
i tryed to extract the files to the usr/share/themes folder from the desktop.
I have a themes folder in my /home/cabz/themes  folder where my other stuff is and I put the extracted files there but they didnt show up in the tweak tools menu. thats when i read they have to go into usr/share/themes folder

---

### Post by cabz on 2012-11-28
> **Frogs Hair said:**
> To make changes in the file system you need to use the following terminal command.```
 gksudo nautilus   
```Make sure the package is fully extracted and move the folder into usr/share/themes.
I tryed that and got this

cabz@cabz-Satellite-L355D:~$ gksudo nautilus

(gksudo:11649): Gtk-WARNING **: Unable to locate theme engine in module_path: "smooth",

(gksudo:11649): Gtk-WARNING **: Unable to locate theme engine in module_path: "smooth",

(gksudo:11649): Gtk-WARNING **: Unable to locate theme engine in module_path: "smooth",

(gksudo:11649): Gtk-WARNING **: Unable to locate theme engine in module_path: "smooth",

(gksudo:11649): Gtk-WARNING **: Unable to locate theme engine in module_path: "smooth",

(gksudo:11649): Gtk-WARNING **: Unable to locate theme engine in module_path: "smooth",

(gksudo:11649): Gtk-WARNING **: Unable to locate theme engine in module_path: "smooth",
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

cabz@cabz-Satellite-L355D:~$

---

### Post by audiomick on 2012-11-28
> **cabz said:**
> i tryed to extract the files to the usr/share/themes folder from the desktop.

Yeah, you'd have to have root privileges for that. I have no idea how to do that for "extract to"..

Use Frogs Hair's suggestion for an instance of Nautilus with root privileges to move the files from where they are now into the folder you want them to be in.

---

### Post by cabz on 2012-11-28
> **audiomick said:**
> Yeah, you'd have to have root privileges for that. I have no idea how to do that for "extract to"..

Use Frogs Hair's suggestion for an instance of Nautilus with root privileges to move the files from where they are now into the folder you want them to be in.
well for giggles right clicked the folde i wanted to move and clicked "copy"
I then ran gksudo nautilus and got access to root ( i think) and I copied the folder into usr/share/themes. then i closed the windows and checked , the file was in there but it still does not show up in the lists in the tweak tool. I am gonna try and reboot and seeif it magicaly shows up:)

---

### Post by audiomick on 2012-11-28
Ok. let us know how you go.

---

### Post by Frogs Hair on 2012-11-28
FYI Gnome Shell themes are not applicable in the Unity desktop.

---

### Post by cabz on 2012-11-28
well after a reboot it is still not working, i went into usr/share/themes and my folder is there.
i did some checking and noticed that all the other themes are in a gtk20., gtk3.0 and  metacity
folder mine is in a  gnome shell.does that make a diferance? should it go somewhere else?

---

### Post by cabz on 2012-11-28
> **Frogs Hair said:**
> FWI Gnome Shell themes are not applicable in the Unity desktop.
bingo thats it then , excuse the ignorance but why? i thought gnome /unity are part of each other.

---

### Post by Frogs Hair on 2012-11-28
You can install the shell from the software center if you want to try it. Logout after installation and select Gnome from login list or the right side of the greeter box(icon).

Unity is a shell that runs on top of Gnome 3.xx, like XFCE or LXDE.

---

### Post by audiomick on 2012-11-28
> **Frogs Hair said:**
> 
Unity is a shell that runs on top of Gnome 3.xx, like XFCE or LXDE.

No, wait on. I don't think that is right. Unity is, as far as I know, an add on for Gnome, though I don't know if 2.x or 3.x is what is currently behind it. LXDE and XFCE are desktop environments in their own right that run instead of and not on top of Gnome. Unless I am very much mistaken.

[http://en.wikipedia.org/wiki/Unity_%28user_interface%29]("http://en.wikipedia.org/wiki/Unity_%28user_interface%29")

[http://en.wikipedia.org/wiki/Lxde]("http://en.wikipedia.org/wiki/Lxde")

[http://en.wikipedia.org/wiki/Xfce]("http://en.wikipedia.org/wiki/Xfce")

---

### Post by Frogs Hair on 2012-11-28
I have the XFCE session and Gnome Shell installed along with Unity. The XFCE Session is not the Xubuntu desktop. LXDE has a session as well.

---

### Post by audiomick on 2012-11-28
> **Frogs Hair said:**
> I have the XFCE session and Gnome Shell installed along with Unity.

Yeah, sure. But when you start XFCE, I think you'll find that it starts instead of gnome.

Try this: In the system monitor, I can see a process for "gnome-session". Log in to XFCE and see if there is one of those running in there. I can't try that, because I only have Gnome on this 10.04 install.

---

### Post by Frogs Hair on 2012-11-28
The Gnome system monitor displays the same Gnome sub processes and displays Ubuntu 12.10 on the system description even with XFCE running.

---

### Post by audiomick on 2012-11-28
> **Frogs Hair said:**
> The Gnome system monitor displays the same Gnome sub processes and displays Ubuntu 12.10 on the system description even with XFCE running.
Yes, there are a number of gnome processes running. I must be getting stubborn as I get older. I installed XFCE so I could have a look myself... ;)

In fact, that is a criticism of XFCE-on-Ubuntu that I have read here and there; on Ubuntu too many gnome bits and pieces get dragged in.

Be that as it may, I see an xfce4-session now with xfce started and no gnome-session, which I did see 5 minutes ago when logged into the gnome desktop.

Either way, I could be wrong and we are hi-jacking this thread, which is not polite. :)

---

### Post by cabz on 2012-12-20
Hmmm so is there anyway to change the shell theme in unity?  Just looking for something diffrent. :)

---


---
title: "Untrusted application launcher"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by Norm24 on 2013-03-02
Tried many a times to put a desktop launcher for LibreOffice and I get this error message when I try to launch it from the desktop:

```
The application launcher "libreoffice4.0-startcenter.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.
```

I'm using 12.04 in "gnome classic" mode.

Btw if I drag the LO icon to the panel it launches just fine.

---

### Post by Norm24 on 2013-03-07
Still can't figure this one out.

---

### Post by krustenBrot on 2013-03-07
You could simply do a "chmod +x libreoffice4.0-startcenter.desktop" from a terminal. It should then have the rights to be executed from you and is therefore trusted. I am keeping this short assuming you know how to use a terminal, if not just drop a message and I will clarify it for you ;)

---

### Post by vamp774 on 2013-03-07
I had this problem with my Minecraft icon.  I can't remember exactly what I did to fix it try right clicking the launcher and ticking allow execution as a program.  I know I changed something in the properties for the launcher

---

### Post by Norm24 on 2013-03-11
> **krustenBrot said:**
> You could simply do a "chmod +x libreoffice4.0-startcenter.desktop" from a terminal. It should then have the rights to be executed from you and is therefore trusted. I am keeping this short assuming you know how to use a terminal, if not just drop a message and I will clarify it for you ;)

```
chmod +x libreoffice4.0-startcenter.desktop
```

Got this error message:
```
chmod: cannot access `libreoffice4.0-startcenter.desktop': No such file or directory
```

---

### Post by stinkeye on 2013-03-11
cd to where the libreoffice4.0-startcenter.desktop file is first because your not using the full path.


eg if it's on your desktop it's in your ~/Desktop folder.
```
cd Desktop
```
You can type in **chmod +x libre** and press tab to complete the name of the file.
or 
just paste in the below command
```
 **chmod +x libreoffice4.0-startcenter.desktop**
```

You could also just use the full path.
eg
```
chmod +x **~/Desktop/libreoffice4.0-startcenter.desktop**
```

Achieve the same result by going to the file in nautilus
and right click on the **libreoffice4.0-startcenter.desktop** file
properties > permissions 
and tick the execute box.

---

### Post by Norm24 on 2013-03-11
> **stinkeye said:**
> cd to where the libreoffice4.0-startcenter.desktop file is first because your not using the full path.

eg if it's on your desktop it's in ~/Desktop
```
glen@Quantal:~$ **cd Desktop**
glen@Quantal:~/Desktop$ **chmod +x libreoffice4.0-startcenter.desktop**
```

That's a no go I get this:
```
chmod: changing permissions of `libreoffice4.0-startcenter.desktop': Operation not permitted
```

Still locked out.

---

### Post by stinkeye on 2013-03-11
Right click on the file > properties > permissions
Who owns the file?
How did you create the file?

---

### Post by AlecJ on 2013-03-11
Enter directory: from Places-Computer-File system

/usr/share/app-install/desktop

Find and right-click on "LibreOffice" file, choose "Copy to the desktop".

---

### Post by Norm24 on 2013-03-12
> **stinkeye said:**
> Right click on the file > properties > permissions
Who owns the file?
How did you create the file?

Root owns the file.

I didn't create it I dragged it from the applications menu.It launches from the application menu no problem.If I drag it to the panel it launches no problem.It simply won't launch from the desktop,for some reason this shortcut is locked when on the desktop.

---

### Post by Norm24 on 2013-03-12
> **AlecJ said:**
> Enter directory: from Places-Computer-File system

/usr/share/app-install/desktop

Find and right-click on "LibreOffice" file, choose "Copy to the desktop".

Did that already and get this error message:
```
Details: Failed to execute child process "libreoffice" (No such file or directory)
```

---

### Post by Kopkins on 2013-03-12
List the permissions to show us. From the directory the file is in.
```
ls -l <file>
```

[I]Nevermind
[/I]
You can use sudo to change the permissions.
```
sudo chmod +x <file>
```

Can you post the contents of the file here in  code tags?

It looks like the file you copied from `/usr/share/app-install/desktop' tries to execute libreoffice as the launch command, but you have LO-4.0 right? I think you need the command to be libreoffice4.0 to launch the program. If the file worked except the bad command, you could get the file from /usr/share/app-install/desktop and edit it to launch libreofffice4.0.

---

### Post by stinkeye on 2013-03-12
> **Norm24 said:**
> Root owns the file.

I didn't create it I dragged it from the applications menu.It launches from the application menu no problem.If I drag it to the panel it launches no problem.It simply won't launch from the desktop,for some reason this shortcut is locked when on the desktop.
Yes your right, I just tried in gnome classic and the file is owned by root.
Same in unity just for the libreoffice dash entry.
I think it may be because the .desktop file for libreoffice in /usr/share/applications actually links to 
**/usr/lib/libreoffice/share/xdg/startcenter.desktop**

So I'm not sure how all that works.

Can you drag other applications from the menu to the desktop and make executable?

---

### Post by Norm24 on 2013-03-12
> **Kopkins said:**
> It looks like the file you copied from `/usr/share/app-install/desktop' tries to execute libreoffice as the launch command, but you have LO-4.0 right? I think you need the command to be libreoffice4.0 to launch the program. If the file worked except the bad command, you could get the file from /usr/share/app-install/desktop and edit it to launch libreofffice4.0.

Editing the command to libreoffice4.0 did the trick.

---

### Post by solarghost on 2013-03-12
At first I didn't believe it, but then I tried it for myself, I can't believe Ubuntu makes it so difficult to add icons to the desktop :/

Seems like some applications will work and launch successfully like jEdit, I am able to add to the desktop and launch, but others like Libre Office fails. This is _almost_ unbelivable.

---

### Post by Kopkins on 2013-03-12
> **solarghost said:**
> At first I didn't believe it, but then I tried it for myself, I can't believe Ubuntu makes it so difficult to add icons to the desktop :/

Seems like some applications will work and launch successfully like jEdit, I am able to add to the desktop and launch, but others like Libre Office fails. This is _almost_ unbelivable.

All the more reason for you to use (by force) unity launcher. ;)

---

### Post by arpanaut on 2013-03-12
Not trying to get political here but since Gnome3 the paradigm of what the desktop is and what it is supposed to be has changed.
Nautilus' control of the desktop is going away, and there is an effort to move users away from using the desktop as a catchall for files, folders, launchers etc.  
I'm not sure how it is all going to wash out, but how people are "expected" to use their systems is changing drastically. 
I neither endorse or condemn. I'm along for the ride and try to adapt.
So don't expect the use of the desktop in the old manner to be accommodated easily. 

My 2 cents

---

### Post by solarghost on 2013-03-13
> **Kopkins said:**
> All the more reason for you to use (by force) unity launcher. ;)

Yep, that's what I mainly use, well that and the dash.

---

### Post by basswipe on 2013-08-01
Nevermind.Saw this is solved already.

---

### Post by gene2 on 2013-12-28
Step 1-Right click program. Open and open properties.
Step 2-Under "Permissions" tab,look for "Execute:"
Step 3-Place a check mark in the box,next to "Allow executing file as a program". 

Program should now launch. Had the same problem after creating desktop icons,as soon as I did that the programs launched and worked.

---


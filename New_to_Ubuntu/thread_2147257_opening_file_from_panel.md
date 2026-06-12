---
title: "opening file from panel"
date: 2013-05-21
forum: New to Ubuntu
---

### Post by cmcanulty on 2013-05-21
I am trying to have a shortcut to a file in my panel. All I can get is the directory opened with the file highlighted. here is the command I put in the panel item.

```
file:///home/cmcanulty/Documents/file.txt
```

 I have tried nautilus and nemo. Thunar would actually open the file but now I can't install thunar, see below. I have tried installing the unmet dependencies but it just leads from one that won't install to another in dependency hell. I really like thunar and would like to install it. It ran fine until an update broke it. Nautilus finds no broken packages.


```
cmcanulty@darcytech:~$ sudo apt-get install thunar.
[sudo] password for cmcanulty: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 thunar : Depends: libexo-1-0 (>= 0.9.0) but 0.6.2-4 is to be installed
          Depends: libthunarx-2-0 (>= 1.1.0) but it is not going to be installed
          Depends: libxfce4ui-1-0 (>= 4.9.0) but 4.8.1-1 is to be installed
          Depends: libxfce4util6 (>= 4.9.0) but it is not installable
          Recommends: xfce4-panel (>= 4.9.2) but it is not going to be installed
          Recommends: thunar-volman but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
cmcanulty@darcytech:~$ 


```

---

### Post by ibjsb4 on 2013-05-21
It would be nice to know what desktop your running.  You can't just drag the file to the panel?

---

### Post by Ratscallion on 2013-05-21
If you're just setting up a launcher for a file you probably want something like this:
```
gedit ~/Desktop/file.txt
```
Where gedit is the GNOME Text Editor (installed by default in Ubuntu) and the rest is the absolute location to the file you're looking to open.

---

### Post by ajgreeny on 2013-05-21
You can use the command ```
exo-open *filename*
``` to open any file, and that file will open in whatever default is set  for that file type.  I am not sure if that works in all DEs, or just some of them.  If you happen to be using XFCE you can also use ```
xdg-open *filename*
``` but I believe that is just for XFCE, not the other DEs.

---

### Post by Cheesemill on 2013-05-21
> **ajgreeny said:**
> If you happen to be using XFCE you can also use ```
xdg-open *filename*
``` but I believe that is just for XFCE, not the other DEs.

It's not just for XFCE, it works for any DE which follows the XDG specification (which is all of them AFAIK).

---

### Post by cmcanulty on 2013-05-21
Sorry I am running 12.04 classic Ubuntu. Dragging file to panel does nothing.

---

### Post by ibjsb4 on 2013-05-21
> **cmcanulty said:**
> Sorry I am running 12.04 classic Ubuntu. Dragging file to panel does nothing.

I running classic and can drag a file.  Where are you trying to drag it from?

---

### Post by ajgreeny on 2013-05-22
In 12.04 classic desktop you need Alt+Rt Click to add panel applets, and then add a launcher with the **exo-open /path/to/filename** command.

---

### Post by cmcanulty on 2013-05-22
```
Could not open location 'exo-open /home/cmcanulty/documents/File.txt' operation not supported
```
I substituted the real file name in the actual command

---

### Post by ajgreeny on 2013-05-22
> **cmcanulty said:**
> ```
Could not open location 'exo-open /home/cmcanulty/documents/File.txt' operation not supported
```
I substituted the real file name in the actual command

That is very strange!

What happens if you try that command in terminal?  It works fine in my Xubuntu 12.04, as does the "xdg-open".

---

### Post by cmcanulty on 2013-05-22
this is the terminal result though it does open the home folder. 
```
Error: Error when getting information for file '/home/cmcanulty/documents/File.txt': Not a directory
Please select another viewer and try again.
```

---

### Post by ajgreeny on 2013-05-23
It should work for both files and folders so I am completely stumped.

---

### Post by ubu_dynamite on 2013-05-23
In the first example Documents started with a upper case letter and file.txt lower case in the error output its the other way around.
But seeing he also cant install thunar there are more problems on that system.

---

### Post by cmcanulty on 2013-05-23
OK I corrected the caps and got it to open from terminal but still no go on panel where I need it. Still operation not supported. I am doing it as custom application launcher and as location. Also tried as applic in termainal and applic

---

### Post by ajgreeny on 2013-05-24
There is obviously something very wrong with your setup in some way or other.

When you set up the classic desktop on your 12.04 did you simply install the gnome panel with its dependencies or did you also uninstall some packages that you didn't think were needed, such as the various unity packages?

Also, in view of your letter case problems in some of these posts (Documents vs documents), are you certain you have your filenames correctly spelled in the commands you used?

---

### Post by cmcanulty on 2013-05-24
I didn't uninstall any of the unity things.my system seems fine except for this issue

---

### Post by ibjsb4 on 2013-05-24
> **ajgreeny said:**
> There is obviously something very wrong with your setup in some way or other.

[http://ubuntuforums.org/showthread.php?t=2147684&p=12660063&viewfull=1#post12660063](http://ubuntuforums.org/showthread.php?t=2147684&p=12660063&viewfull=1#post12660063)

---

### Post by jediboaz on 2013-05-24
mmmmm strange indeed. cant you try a alt-f2 put location in and enter.

---

### Post by cmcanulty on 2013-05-24
if I have to type it all I may just as well navigate to it. I can open a directory from the panel just not a file

---


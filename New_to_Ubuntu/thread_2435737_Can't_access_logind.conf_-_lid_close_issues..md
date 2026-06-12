---
title: "Can't access logind.conf - lid close issues."
date: 2020-01-24
forum: New to Ubuntu
---

### Post by nick2learn on 2020-01-24
I'm trying to edit the lid close function to hibernate by following:
[https://www.youtube.com/watch?v=Dl2MHNhpAJ0](https://www.youtube.com/watch?v=Dl2MHNhpAJ0)
but it won't work... 
I get the following:
---------------
nick@MSI:~$ sudo su
root@MSI:/home/nick# gedit /etc/systemd/logind.conf
No protocol specified
Unable to init server: Could not connect: Connection refused


(gedit:6476): Gtk-WARNING **: 14:28:04.750: cannot open display: :0
root@MSI:/home/nick# 
-------------------
I've also tried like this:
---------------
nick@MSI:~$ sudo gedit /etc/systemd/logind.conf
[sudo] password for nick: 
Invalid MIT-MAGIC-COOKIE-1 keyUnable to init server: Could not connect: Connection refused


(gedit:6096): Gtk-WARNING **: 14:22:07.066: cannot open display: :0
nick@MSI:~$ 
---------------
and I tried like this where I can access the file, make changes but not save them becuase it's read only.
-----------------
nick@MSI:~$ gedit /etc/systemd/logind.conf
--------------------

please can anyone help? :-)

P.S. I tried searching forum but I was told "Access forbidden"

---

### Post by TheFu on 2020-01-25
Don't use a GUI editors with root elevated permissions.  The errors are X11 telling you that root doesn't have rights to take control of the display server.

Try:
```
sudo nano  /etc/systemd/logind.conf
```

It is best to never use sudo with any GUI programs as they tend to write config files that are owned by root into the users' HOME.  Next time that user tries to use the GUI program as non-root, he finds all sorts of issues with permissions.

I know you won't listen to me, so you can run some GUI programs with sudo, but you need to use the correct options so root doesn't write to your (the normal userid) HOME.  **sudo -H {whatever GUI program}**
Also, rather than using *sudo su*, perhaps using **sudo -i** or **sudo -s** would be better?  Which just depends on whether you want root's environment or you want to retain the current userid's environment.  Both have risks.

Ok, there is a better answer specifically for editing system files with a GUI.  
```
export EDITOR=gedit
sudoedit /path/to/the/file
```
That will absolutely work on a desktop running a GUI.  It will not work on a server without any GUI.

---

### Post by nick2learn on 2020-01-25
awesome thanks very much!.. that seems to have worked :-)

---


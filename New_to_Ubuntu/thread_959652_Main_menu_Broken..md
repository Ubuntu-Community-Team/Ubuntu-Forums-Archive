---
title: "Main menu Broken."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-26
Hi!

I was trying to move some items on the Applications menu (wanted to move Kate , which is in Other tab, to the programming tab).

The problem is that I cannot access to the main menu. Neither by System->Preferences->Main Menu, nor right click Applications and Edit Menus.

When I click any of those links, nothing happens.

By running the command on terminal 

```
sudo alacarte
```

The Main Menu windows appears. But I cannot do nothing, trying to add items or unselecting items doesn't seem to do nothing. Also, it kinda messes up the applications menu (see screenshot).

I know this behavior is quite odd. Anyone know how to fix it? is Main Menu like any other application that I can uninstall and install again?
It works perfectly on the Ubuntu partition I have on my laptop with exactly same Ubuntu version and packages.

Any help would be appreciated.

Thanks!

---

### Post by SunnyRabbiera on 2008-10-26
its because you are typing in Sudo, you only need sudo when entering administration mode.
try alacarte without typing in sudo :D

---

### Post by fredscripts on 2008-10-26
> **SunnyRabbiera said:**
> its because you are typing in Sudo, you only need sudo when entering administration mode.
try alacarte without typing in sudo :D

```

diffred@fredlab:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/diffred/.config/menus/applications.menu'
diffred@fredlab:~$ 


```

So that may be the reason why all gnome links to Main Menu are broken. Note that using sudo I can actually enter the Main Menu but it doesn't act properly.

---

### Post by fredscripts on 2008-10-27
bump...:(

---

### Post by fredscripts on 2008-10-27
Well I hope Ubuntu 8.10 solve this issue :)

---

### Post by fredscripts on 2008-10-30
> **fredscripts said:**
> Well I hope Ubuntu 8.10 solve this issue :)

NOPE!! It doesn't :(!!! Can't be true!!, I am the only person that cannot run the Main Menu application?!! 

Please help!!!

---

### Post by fredscripts on 2008-10-30
Ok...

I can enter now the Main Menu by going System->Preferences...

after changing some permisions:

```
sudo chown -R username:username /home/username/.config
sudo chmod -R 700 /home/username/.config
```

BUT, once I'm within Main Menu, I cannot unselect some icons nor move to another places nor delete some entries. Nothing works. Just Move Up and Move Down :(

Any ideas?...

---

### Post by fredscripts on 2008-10-31
Well playing with xml files in /home/username/.config menus I've crashed again the Main Menu application lol. So the only way I can think of solve this is reinstalling the Main Menu application, which I hope is like any other application.

I understand that this isn't a common problem, but any help would be much appreciated..:(

---

### Post by Nepherte on 2008-10-31
The problem is that you opened alacarte with sudo permissions. First of all, if you open up a graphical application with root privileges you have to use gksudo. Second, you didn't need those privileges. Now alacarte saved the file with root permissions only, hence not allowing you to access them as a normal user.

Creating a new user will certainly fix the problem, deleting .config perhaps too but you'll certainly lose other application's settings.

---


---
title: "How can i install Pygame in 9.10?"
date: 2010-01-01
forum: Programming Talk
---

### Post by JoeyF on 2010-01-01
I have the tar.gz but i don't know what to do.


Help?

Thanks.

The files on the pygame site are dead (the package link)

---

### Post by wmcbrine on 2010-01-01
Throw out the .tar.gz... pick up the Synaptic or the apt-get.

```
apt-get install python-pygame
```

---

### Post by JoeyF on 2010-01-01
> **wmcbrine said:**
> Throw out the .tar.gz... pick up the Synaptic or the apt-get.

```
apt-get install python-pygame
```



I did that and got:
```
Reading package lists... Done
Building dependency tree        
Reading state information... Done


The following packages were automatically installed and are no longer required:
  python-tagpy libmono-zeroconf1.0-cil podsleuth emacs22-bin-common
  erlang-esdl emacs22-common emacs-snapshot-bin-common emacsen-common
  python-mmkeys python-mutagen python-cddb libtaglib2.0-cil libboo2.0-cil
  emacs-snapshot-common libglademm-2.4-1c2a libnotify0.4-cil
  libboost-python1.38.0
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  python-pygame
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
```

I think i did that earlier also.

I went to the IDLE and typed import pygame and got no pygame found.

---

### Post by snova on 2010-01-02
That command requires root access, and should therefore be run with sudo:

```
sudo apt-get install python-pygame
```

---

### Post by JoeyF on 2010-01-02
I did the above and it seemed to have worked but i still get module not found when i open the IDLE and type import pygame

---

### Post by JoeyF on 2010-01-02
I also tried import python-pygame but got invalid syntax.

---

### Post by Can+~ on 2010-01-02
I'm sure you didn't install it, it wasn't a root access problem (you would've got a "Error 13: Permission Denied"). Seems that you had another thing open (Synaptic, Add/Remove, Appstore)

Run the command again:

```
sudo apt-get install python-pygame
```

Try again, and if not, paste the output from apt-get here.

---

### Post by JoeyF on 2010-01-02
I earlier tried the deb from:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pygame](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=pygame)

and i just tried that command and got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-pygame is already the newest version.
The following packages were automatically installed and are no longer required:
  python-tagpy libmono-zeroconf1.0-cil podsleuth emacs22-bin-common
  erlang-esdl emacs22-common emacs-snapshot-bin-common emacsen-common
  python-mmkeys python-mutagen python-cddb libtaglib2.0-cil libboo2.0-cil
  emacs-snapshot-common libglademm-2.4-1c2a libnotify0.4-cil
  libboost-python1.38.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

And i still can't get it to recognize pygame,

How do i use Pygame with it?

---

### Post by JoeyF on 2010-01-02
i used [http://lorenzod8n.wordpress.com/2007/05/25/pygame-tutorial-1-getting-started/](http://lorenzod8n.wordpress.com/2007/05/25/pygame-tutorial-1-getting-started/) sudo aptitude install python-pygame and it acted like it worked but i don't know how to start using it.

Is it the same as Windows where you have to use import at the IDLE?:confused:

Thanks,

---

### Post by Can+~ on 2010-01-02
Type "python" in the shell, and do "import pygame", it worked for me.

I'll take a wild guess, and say that you downloaded python3 and IDLE for python3, and since pygame isn't available for python 3, that would lead to the error.

---

### Post by JoeyF on 2010-01-02
It worked!

One last thing.
I am following the tut at:
[http://www.youtube.com/watch?v=IG2WidpYUY8](http://www.youtube.com/watch?v=IG2WidpYUY8)

But i don't know where the images folder is.

Thanks.

---

### Post by Can+~ on 2010-01-03
> **JoeyF said:**
> It worked!

One last thing.
I am following the tut at:
[http://www.youtube.com/watch?v=IG2WidpYUY8](http://www.youtube.com/watch?v=IG2WidpYUY8)

But i don't know where the images folder is.

Thanks.

Pygame doesn't include an image folder. I didn't watch the tutorial, but I would guess that the guy who made the tutorial, also provides the images and you should create a folder somewhere with the .py and your own image folder, and do it there.

Btw, you don't even need idle. You can create a .py script, and then run it with "python myscript.py", or install geany.

```
sudo apt-get install geany
```

Geany provides a simple one-click button to execute python scripts.

---


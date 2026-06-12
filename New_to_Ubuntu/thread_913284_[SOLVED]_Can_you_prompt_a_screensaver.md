---
title: "[SOLVED] Can you prompt a screensaver?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by Saul Hudson on 2008-09-07
Simple question. Is there a way to start the screensaver other than waiting for it to start itself? (And if so, how?)

---

### Post by panhandle on 2008-09-07
This topic is covered to some degree in the following thread.


[http://ubuntuforums.org/showthread.php?t=247319](http://ubuntuforums.org/showthread.php?t=247319)


In essence, run the following command at the CLI: 

```
gnome-screensaver-command --activate
```

To make it easy to use (i.e. not typing that lengthy command every time you want to use the screensaver) just create and alias in .bashrc 

Cheers!

---

### Post by Saul Hudson on 2008-09-07
That's embarrassing.... 

...I did search the forums first, naturally, but I couldn't see anything.

Thanks for your help.

---

### Post by ubername on 2008-09-07
> **panhandle said:**
> This topic is covered to some degree in the following thread.


[http://ubuntuforums.org/showthread.php?t=247319](http://ubuntuforums.org/showthread.php?t=247319)


In essence, run the following command at the CLI: 

```
gnome-screensaver-command --activate
```

To make it easy to use (i.e. not typing that lengthy command every time you want to use the screensaver) just create and alias in bash.rc 

Cheers!

Thanks PH 

I would be eager to know how to create an alias in bash.rc

---

### Post by panhandle on 2008-09-07
open .bashrc with your favorite editor. If unfamiliar with editors use gedit.

enter the following code: 

```
gedit .bashrc 
```

locate the commented line entitled

```
# some more ls aliases 
```

Here you'll see the basic format for creating an alias.

create some simple and memorable command for invoking the screensaver, as follows:

```
alias scvr="gnome-screensaver-command --activate" 
```

Then simply type scvr in at the command prompt and it will invoke the screensaver.

---

### Post by lordadi on 2008-09-07
Hi,

To create an alias in bash.rc, follow this [guide]("http://www.finerrecliner.com/?p=32"). I would also suggest that you do what has been put forth in the guide, i.e. create an alias for rm.


Cheers,


Lordadi.
A bit late!

---

### Post by ubername on 2008-09-07
> **panhandle said:**
> open .bashrc with your favorite editor. If unfamiliar with editors use gedit.

enter the following code: 

```
gedit .bashrc 
```

locate the commented line entitled

```
# some more ls aliases 
```

Here you'll see the basic format for creating an alias.

create some simple and memorable command for invoking the screensaver, as follows:

```
alias scvr="gnome-screensaver-command --activate" 
```

Then simply type scvr in at the command prompt and it will invoke the screensaver.
Thanks, that works. I have just realised that system>lock screen does much the same thing, but your info is much more useful for general purposes. Thanks again.

---


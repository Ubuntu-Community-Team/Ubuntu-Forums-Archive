---
title: "How Can I Add Right Click &quot;Edit As Root&quot; to a file?"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by bme on 2008-06-24
In mint there is a right click "edit as Root". How can I add that feature to ubuntu 8.04?

---

### Post by Inxsible on 2008-06-24
> **bme said:**
> In mint there is a right click "edit as Root". How can I add that feature to ubuntu 8.04?
The simplest way would be to use Mint. Its based on Ubuntu, so you wouldn't be losing on anything. 

That said, it is not safe to edit anything as root unless you know what you are doing. and it only takes a simple sudo in front of the command.

Learn to love the command line !

I know it doesn't help you out much but that's just my 2 cents.

---

### Post by dca on 2008-06-24
I don't recommend this but at CLI, type:
 
gksudo nautilus &
 
...from there it will bring up normal nautilus file browsing window (as root, not normal user).  You should be able to right-click/edit a text file in root...

---

### Post by bme on 2008-06-24
Inxsible,
Mint is nice but I like the simplicity of ubuntu as it is. I tried mint but I think mostly it is "eyecandy"....
DCA,
I know about CLI a little and using sudo is a pain if the file you want to edit is buried inside some sub folder....
Thanks all for replying...

---

### Post by superprash2003 on 2008-06-24
hope this is what you wanted [http://prash-babu.blogspot.com/2008/05/how-to-setup-right-click-open-as-root.html](http://prash-babu.blogspot.com/2008/05/how-to-setup-right-click-open-as-root.html)

---

### Post by AOZ on 2008-06-24
> **bme said:**
> I know about CLI a little and using sudo is a pain if the file you want to edit is buried inside some sub folder....
Thanks all for replying...

Not so much once u learn little shortcuts like pressing tab to finish ur filename/path, ls to see the folders, cd'ing into subfolders becomes very easy with the CLI, even easier than clicking. and there u can just do sudo gedit <filename>.

---

### Post by bluepowder7 on 2008-06-24
actually, if you're using xfce / thunar and you're in a directory in which there's a file you wanna edit as root (like fstab, for example), you can right-click and open a terminal that automatically puts you in that directory, and then just "sudo vim fstab" or whatever the file is.

dunno if nautilus has that "open terminal in THIS directory" feature...

---

### Post by oldos2er on 2008-06-24
> **bme said:**
> In mint there is a right click "edit as Root". How can I add that feature to ubuntu 8.04?

 "sudo aptitude install nautilus-gksu"

 Then restart X.

---

### Post by Golem XIV on 2008-06-24
> **oldos2er said:**
> "sudo aptitude install nautilus-gksu"

 Then restart X.

No need to restart X, a simple
```
killall nautilus
```
should do it.

---

### Post by mc4man on 2008-06-24
As long as your aware of the _reduced security_ you can create 2 nautilus actions - open dir. as root (gksudo nautilus) and open file as root (gksudo gedit). Quite easy to do after installing nautilus-actions.
You'd open nautilus actions configuration, click add  and create as in screenshots.
you are free to label and icon to what you want

---

### Post by bodhi.zazen on 2008-06-24
See this thread : [http://ubuntuforums.org/showthread.php?t=47525](http://ubuntuforums.org/showthread.php?t=47525)


command line junkies (you know who you are :twisted: You can :

```
sudo -e file
```

---


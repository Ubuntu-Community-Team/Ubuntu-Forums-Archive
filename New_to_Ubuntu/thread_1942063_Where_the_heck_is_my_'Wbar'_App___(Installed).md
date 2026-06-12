---
title: "Where the heck is my 'Wbar' App ?  (Installed)"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by bipolaric on 2012-03-16
Hello Again people, I have encountered 'another' problem, and I hope someone out there can help me.

I have just installed 'wbar' through 'Synaptic package manager' and everything went well.  Yet alas I could not find wbar anywhere on my desktop or in any application menu ect ect.

I then entered 'wbar' in 'Ubuntu software centre' and it showede as being installed, but gave no 'path name', as it can do with other applications.

I just haven't a clue where it is.

'Anyone have any ideas ?

Thanks - Mark

---

### Post by acimi66 on 2012-03-16
It says it runs in terminal.

try that

---

### Post by bipolaric on 2012-03-16
Hi, thanks for the reply 

Sorry, I still haven't a clue on what to do ???

I'm still a bit of a noob.

Thanks - Mark

---

### Post by ubudog on 2012-03-16
> **bipolaric said:**
> Hi, thanks for the reply 

Sorry, I still haven't a clue on what to do ???

I'm still a bit of a noob.

Thanks - Mark

Assuming you're using Ubuntu 10.10, click on Applications>Accessories>Terminal.

In the terminal, type:
```
wbar
```

Let us know if you have any problems.  ;)

---

### Post by MG&amp;TL on 2012-03-16
You probably don't want to do that all the time, so add it to your startup applications with the same command.

---

### Post by bipolaric on 2012-03-16
I typed wbar into the terminal:

bipolaric@Laptop:~$ wbar
Using /usr/share/wbar/dot.wbar config file.
Using a Super Bar.



But I still can't see a dock bar, am I doing something wrong ?

Thanks Again - Mark

---

### Post by chickenPie4breakfast on 2012-03-17
I got the same problem - I would start it in terminal but nothing would show. If you check running processes you will probably see that it is running but just not showing anything. I didnt find the answer - just uninstalled it.

---

### Post by alphacrucis2 on 2012-03-17
Try this:

```
wbar -pos center -above-desk
``` 

No idea if that will help but read this:

[http://deviceguru.com/adding-wbar-prism-and-gadgets-to-ubuntu/](http://deviceguru.com/adding-wbar-prism-and-gadgets-to-ubuntu/)

The page is rather out of date applying to an obsolete version of ubuntu but may have some useful info.


Tried it myself. Doesn't appear to do anything. I wonder if it is even maintained.

---

### Post by MG&amp;TL on 2012-03-17
I think it might be a unity problem, cairo dock doessn't play too nicely either, for me.

---

### Post by Frogs Hair on 2012-03-17
Login to the fall back session if installed and see if it works there. I have been experimenting with Dockbarx but I can't set it to autostart because I don't want conflicts with Unity or the Gnome shell.

---


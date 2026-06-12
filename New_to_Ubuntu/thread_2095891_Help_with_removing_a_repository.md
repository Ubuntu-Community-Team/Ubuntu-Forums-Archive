---
title: "Help with removing a repository"
date: 2012-12-18
forum: New to Ubuntu
---

### Post by yajnamurti on 2012-12-18
I have added 2 repositories using Synaptic,

deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) unstable/ 
deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) ubuntu/

And now I get this message when I try to open Synaptic:

---

### Post by haqking on 2012-12-18
> **yajnamurti said:**
> I have added 2 repositories using Synaptic,

deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) unstable/ 
deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) ubuntu/

And now I get this message when I try to open Synaptic:

Not familiar with them but there shouldnt be a space after debian/

---

### Post by ibjsb4 on 2012-12-18
You can edit, delete or just uncheck it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

---

### Post by yajnamurti on 2012-12-18
> **haqking said:**
> Not familiar with them but there shouldnt be a space after debian/

My question is, how to remove these 2 repositories that are causing problem using the terminal. Please help!

---

### Post by ibjsb4 on 2012-12-18
```
sudo gedit /etc/apt/sources.list
```

If not there

```
sudo gedit /etc/apt/sources.list.d/*
```

---

### Post by haqking on 2012-12-18
> **yajnamurti said:**
> My question is, how to remove these 2 repositories that are causing problem using the terminal. Please help!

They are causing a problem because you have entered them incorrectly you need to remove the space.

If however you simply dont want the software associated with them then follow instructions above to remove them.

Peace

---

### Post by haqking on 2012-12-18
> **ibjsb4 said:**
> ```
**gk**sudo gedit /etc/apt/sources.list
```If not there

```
**gk**sudo gedit /etc/apt/sources.list.d/*
```

**gksudo f**or graphical apps such as gedit

---

### Post by yajnamurti on 2012-12-18
> **ibjsb4 said:**
> ```
sudo gedit /etc/apt/sources.list
```

If not there

```
sudo gedit /etc/apt/sources.list.d/*
```

Dear haqking,

I deleted the 2 repositories and now the problem is solved, I can run Synaptic and the Software Center.

THANK YOU A LOT!  ):P

---

### Post by audiomick on 2012-12-18
If you specifically want to edit them out of the sources list via the terminal

```
gksudo gedit /etc/apt/sources.list
```

will open the file in the editor. You can comment them out with a # at the start of the line in question, or just remove them. I believe you should then do
```
sudo apt-get update
```
to refresh your package lists.

However, if you installed the repos via synaptic, you can remove them on the same tab in synaptic that you installed them on.

edit: oops, too slow... ;

---

### Post by ibjsb4 on 2012-12-18
> **haqking said:**
> **gksudo f**or graphical apps such as gedit

oops

---


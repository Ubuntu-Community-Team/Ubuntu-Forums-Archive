---
title: "file permission?!"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by dennycraig on 2008-09-30
I am running Hardy Heron. I made a cd file on my MS XP and put the cd into my Ubuntu machine and downloaded the file. It appeared on my screen with an orange bubble attached to it and a white lock in the orange bubble. I can not do anything to the file. I can not take anything out of it. I can not put it in the trash. I can not put it in with my home files. I do not know how the file decided that it was suppose to be locked. It keeps on telling me that I do not have permission to do anything with the file- even though I was the one who made it and who put it in my computer. 

My question is How do I get rid of the file as it is cluttering up my desktop and I do not want such a stubborn file. Any Ideas out there?:confused:

---

### Post by SupaSonic on 2008-09-30
Open up the terminal. If the file is on the desktop, type 
```
cd Desktop
```

if it's somewhere else type 
```
cd <path to file>
```

then type 
```
chmod 777 <filename>
```

or alternatively 

```
chown <your username> <filename>
```

Note that you have to replace anything in <> with actual values according to your system.

---

### Post by YldGuy on 2008-09-30
or alternatively,

go to terminal and type:

sudo nautilus

that will open up nautilus in root mode. go to desktop, right click on file, go to properties, go to permissions and change the owner from root to your username. Click close and close nautilus. Close terminal. Now you have the file ready for your use.

---

### Post by Nepherte on 2008-09-30
> **YldGuy said:**
> or alternatively,

go to terminal and type:

sudo nautilus

that will open up nautilus in root mode. go to desktop, right click on file, go to properties, go to permissions and change the owner from root to your username. Click close and close nautilus. Close terminal. Now you have the file ready for your use.
Please use gksudo for graphical applications. Using sudo can give some nasty side-effects for these applications.

---

### Post by hyper_ch on 2008-09-30
normally, when coyping files off a cd they are read-only. Make it writeable also.

---

### Post by YldGuy on 2008-09-30
> **Nepherte said:**
> Please use gksudo for graphical applications. Using sudo can give some nasty side-effects for these applications.

oh ok.. didnt know that. thanks.

---

### Post by dennycraig on 2008-09-30
Thanks for the help. 

After I did what you suggested I still had to do one more thing. After changing owner on the permission I then had to change the folder access to "create and delete files instead of list files only. that did the trick. :D:KS:guitar: So cool. How do you learn this stuff anyhow? That is besides  having things not work and having to go to the forums?

> **YldGuy said:**
> or alternatively,

go to terminal and type:

sudo nautilus

that will open up nautilus in root mode. go to desktop, right click on file, go to properties, go to permissions and change the owner from root to your username. Click close and close nautilus. Close terminal. Now you have the file ready for your use.

---

### Post by YldGuy on 2008-09-30
> **dennycraig said:**
> Thanks for the help. 

After I did what you suggested I still had to do one more thing. After changing owner on the permission I then had to change the folder access to "create and delete files instead of list files only. that did the trick. :D:KS:guitar: So cool. How do you learn this stuff anyhow? That is besides  having things not work and having to go to the forums?

thats just by digging around in the machine to know what all it can do :). thats how i found the permissions are set there in properties of an object. i saw that "sudo nautilus" somewhere on the internet and that came handy when my folders were locked to root for some reason. I wasnt aware of the chown command then and "sudo nautilus" was a breeze. Although the GUI way of changing permissions is nice and looks easy, the chown is much more powerful than the GUI. I would say learn that command too. you never know...

And as Nepherte said please use gksudo to open up graphical apps.

---

### Post by rybaxs on 2008-10-01
go to properties then emblems/permission thats where the orange bubble and white lock are to be changed.

---


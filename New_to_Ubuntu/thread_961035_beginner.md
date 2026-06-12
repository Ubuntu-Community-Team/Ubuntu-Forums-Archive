---
title: "beginner"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by pvn1220 on 2008-10-27
Hi everyone, I actually just learned about Ubuntu in September.  I've installed the server on my laptop and I'm trying to install the desktop.  I know it's going to take time to learn and research but I'm really excited.  I've seen the demo and it really looks neat.  Eventually, I want to convert to the Ubuntu system.  I appreciate any help.

---

### Post by abeisgreat on 2008-10-27
Why would you install the server off the bat? why not get the desktop version that comes with the gui?

alternatively type
```
apt-get install ubuntu-desktop gdm
```
I think thats it...

---

### Post by spiderbatdad on 2008-10-27
If you are asking how to install a desktop environment to your server install, just run:```
sudo apt-get install ubuntu-desktop gdm
```then reboot.

---

### Post by antmenj on 2008-10-27
Do you want the server install?

The desktop install is what most people would install on a laptop.

---

### Post by pvn1220 on 2008-10-29
Actually, I have a class project and installing the server was our first assignment.  I'm getting acquainted with the command line and am able to view sites.  I am most interested in the desktop, though.  I'm going to install the desktop and see where it takes me from there.
Thanks

---

### Post by pvn1220 on 2008-11-05
hi
i input the command to install the desktop and it asked me if i was root.  (i was root)  i entered "yes" and the screen listed "y's" all the way down.
i left it running all night but nothing happened.  
can someone help me?  i'm trying to find some info to help me.
thx

---

### Post by bodhi.zazen on 2008-11-05
:lolflag:

There is a command in Linux called "yes"

It returns a yes or y until you stop it.

You can stop the command with ctrl-c

---

### Post by hyper_ch on 2008-11-05
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by lepar_m on 2008-11-05
> **pvn1220 said:**
> hi
i input the command to install the desktop and it asked me if i was root.  (i was root)  i entered "yes" and the screen listed "y's" all the way down.
i left it running all night but nothing happened.  
can someone help me?  i'm trying to find some info to help me.
thx

Make sure you use 
sudo apt-get install ubuntu-desktop gdm
rather than just apt-get install ubuntu-desktop gdm

if it asks you if your root just press y

---


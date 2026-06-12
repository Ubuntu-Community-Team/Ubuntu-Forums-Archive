---
title: "Bugs or ??"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by faron45 on 2008-09-28
Okay,nobody seems to be able to answer my posts [Can't get "Suspend" operational] about the missing suspend option under power management preferences...So,how about the missing background properties tab for customizing the panels ? I wonder if I should report these as bugs or,do I just have a corrupted version of Xubuntu ? 
 
According to [http://library.gnome.org/users/user-guide/stable/panel-properties.html.en]("http://library.gnome.org/users/user-guide/stable/panel-properties.html.en") there should be 2 tabs available to us under "customize panel".They are:general properties & background properties.

---

### Post by robert shearer on 2008-09-28
Don"t know that I remember 2 tabs on my Xubuntu- but will look tonight and get back.
Perhaps though you are looking at the Gnome documentation for the Gnome desktop that ships with Ubuntu.
Does the XFCE desktop of Xubuntu environment give these options?(EDIT-NO!)

EDIT. I have checked and Xubuntu does not have two tabs. You are looking for features that apply to the Gnome desktop and do not apply to Xfce desktop that Xubuntu uses.

Links...
[http://www.google.co.nz/search?hl=en&q=xubuntu+documentation+Hardy&btnG=Google+Search&](http://www.google.co.nz/search?hl=en&q=xubuntu+documentation+Hardy&btnG=Google+Search&)
[http://www.xubuntu.org/news/hardy/release](http://www.xubuntu.org/news/hardy/release)

---

### Post by cardinals_fan on 2008-09-28
Xubuntu uses Xfce, not GNOME.

---

### Post by Bölvaður on 2008-09-29
in xfce you can find all the options to change the look in Settings &#8594; Settings Manager

And even download some themes from the internet :)

---

### Post by faron45 on 2008-09-29
Okay,last night I started a thread titled "bugs or ??" I did not get the answers I was looking for & I fell asleep.Here is the link to that thread-[http://ubuntuforums.org/showthread.php?p=5873760#post5873760]("http://ubuntuforums.org/showthread.php?p=5873760#post5873760") 
 
If xubuntu uses xfce [which in fact I already know] then,why under synaptic can I not find _ANY_ instance of an xfce power manager installed but,I CAN find an instance of the gnome power manager as being installed ? Xfce is the desktop environment & gnome is the power manager for that environment,right ?? 
 
And,at this point I have all power mgmnt prefs set to off.And,yet,for some reason,my screen is still going black after a certain period of time & I cannot seem to wake it up without doing a hard reboot.Can anybody explain to me why this may be happening ?

---

### Post by JoshuaRL on 2008-09-29
Probably not a good idea to repost the same issue.  Maybe give your original thread a bump once every 24 hours, and maybe a max of three times.  

One thing to remember is that XFCE, and specifically Xubuntu use some tools and apps from GNOME.  Both are written with the GTK+ toolset and so use some of the same things.  For instance, both use GDM instead of the KDM that KDE (Kubuntu) uses.  But that doesn't mean that all the same apps will transfer over perfectly.  For instance, I installed alacarte, a menu editor.  I has all the options for GNOME, but doesn't recognize that I don't have GNOME installed.  So when I add something, it doesn't always put it where I want it.  More often than not, it adds it to the Other menu.  But that's because it was made for GNOME, not XFCE.

Also, I've found it helpful to remember that Xubuntu is supposed to be lightweight.  It doesn't have all the functionality of GNOME or KDE.  For instance, GNOME has a keyboard shortcut that you can use to lock the screen.  Ctrl+Alt+L will do that.  But Xubuntu doesn't have that, and you can't even get it from the Quit menu.  I've found other options, but I could always try to find the right package to add that functionality.  It just takes some research to find what you need.

So the short answer is that I can't really answer your question exactly.  But you might want to look in another direction.  Often, Suspend is more related to your video driver than any specific app.  What is your video card and when you put the following into your terminal, what does it say your driver is?
```

displayconfig-gtk

```

---

### Post by phidia on 2008-09-29
When the screen goes blank can you get to a commandline by pressing Alt+Ctrl+F1?
If you can get the CLI you can type "dmesg" and/or look at /var/log/syslog & /var/log/messages. 

When you reboot you can see go through the /var/log files to look for some clue to what's causing this.

---

### Post by overdrank on 2008-09-29
Threads merged :)

---

### Post by faron45 on 2008-09-29
Robert-you are correct.
Josh-sorry...what is a bump & how do I do that ? the info I get when I enter that into the term is...I need admin rights to change all screen settings.....& I get a screen & graphics prefs dialog box
phidia-not sure if I can get to the term or not when that happens.Besides,most of what you just said is Greek to me.Heh,heh.Sorry.I'm fairly new to comps.so,that termi stuff is still very confusing to me.

---

### Post by faron45 on 2008-09-29
JoshuaRL-the info that comes up from screen & graphics prefs is...graphics card Intel 810 & for driver it says "none" !

---

### Post by cardinals_fan on 2008-09-29
> **faron45 said:**
> 
If xubuntu uses xfce [which in fact I already know] then,why under synaptic can I not find _ANY_ instance of an xfce power manager installed but,I CAN find an instance of the gnome power manager as being installed ? Xfce is the desktop environment & gnome is the power manager for that environment,right ?? 

Xubuntu is not a pure Xfce distro.  It includes a large amount of GNOME 'contamination'.
> **faron45 said:**
> 
Josh-sorry...what is a bump & how do I do that ?
Bumping is posting a response to one of your threads without adding any new info, merely for the purpose of 'bumping' it up in the thread lists.

---

### Post by JoshuaRL on 2008-09-30
> **faron45 said:**
> JoshuaRL-the info that comes up from screen & graphics prefs is...graphics card Intel 810 & for driver it says "none" !

There's your problem.  You need to probably pick the experimental modesetting driver for Intel (it works great despite the name) and your issue should be fixed.  To do that, put this into the command line:
```

gksu displayconfig-gtk

```
That should give you root access to be able to change that.  That's why the last command I had you launch gave you that warning.  I just wanted to see what it was without changing anything.  So look through the drivers for that one, or through there for what card you have (Intel 810).  Either way should work just fine.

Try that and see if that fixes it.

---


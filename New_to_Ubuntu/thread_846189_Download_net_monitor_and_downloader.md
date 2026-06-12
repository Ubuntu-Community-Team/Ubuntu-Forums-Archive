---
title: "Download net monitor and downloader"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by stevezygote on 2008-07-01
Could someone recommend a good Linux based download net monitor? I'm having some issues with my net and wonder whether I'm actually getting what the IS claims it gives me. In addition, can someone recommend a good Linux based downloader, such that if the download crashes it picks up where it left off? Thanks.

---

### Post by atomkarinca on 2008-07-01
If you're looking for a graph-drawing network monitor, [GKrellM]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html") has a nice one. For a download manager, [Gwget]("http://www.gnome.org/projects/gwget/") and [Downloader for X]("http://www.krasu.ru/soft/chuchelo/") are two great managers. [KGet]("http://kget.sourceforge.net/") is a nice one, too.

---

### Post by alienexplorers on 2008-07-01
If your using firefox in Kubuntu then the addin downthemall works great.

---

### Post by stevezygote on 2008-07-01
> **atomkarinca said:**
> If you're looking for a graph-drawing network monitor, [GKrellM]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html") has a nice one. For a download manager, [Gwget]("http://www.gnome.org/projects/gwget/") and [Downloader for X]("http://www.krasu.ru/soft/chuchelo/") are two great managers. [KGet]("http://kget.sourceforge.net/") is a nice one, too.

I downloaded gkrellm. well actually I installed it from adept. No problem. But then I couldn't find it at all! Wasn't showing up on any of my menus in Kubuntu 8.04. Indeed, ever since the last few updates my system has dramatically slowed...to the point of considering removing it and going back to Windows, but the speed issue is another problem, best handled in another thread I guess. 

Thanks for the tip

---

### Post by aktiwers on 2008-07-01
I use netspeed:
```
sudo apt-get install netspeed
```And then right-click your panel and pick "add to panel" then search for netspeed. ;)

Edit: a good downloader would be wget

---

### Post by saratchandra on 2008-07-01
Use the netmonitor screenlet if nothing else works. I'm using it and its fairly accurate.

---

### Post by stevezygote on 2008-07-01
> **aktiwers said:**
> I use netspeed:
```
sudo apt-get install netspeed
```And then right-click your panel and pick "add to panel" then search for netspeed. ;)

Edit: a good downloader would be wget

Frankly, your solution sounded like an excellent idea. Nice and clean and simple. I just want to see what thruput I'm getting. However, when I followed your instructions, everything seemed to work fine but then I couldn't find netspeed at all. Not on any of the menus. Not as an applet either. Has the fact I'm on Kubuntu got anything to do with it, since netspeed appears to be a gnome app?

---

### Post by aktiwers on 2008-07-01
Oh Im sorry, I didnt see you where a KDE user. Netspeed is for Gnome, but it is still nice though.

You could use Conky to display Netstats of all kinds too.
here is a thread with lots of good tips and inspiration to create a nice Conky:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---


---
title: "is there a &quot;netmeter&quot; for ubuntu?"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by RajaAjmal on 2008-07-11
is there a netmeter for ubuntu?
i've an hsdpa usb modem, model e220, and i can download and upload 2GB of data per month. on windows i'm able to see how much i've been downloaded and uploaded so far, but with ubuntu i don't know how to do so. till now i'm using the system monitor. but the problem with it is that you can know how much u've downloaded and uploaded for the current session only. in windows environment i know we can use netmeter. is there a "netmeter" for ubuntu?

---

### Post by wolfen69 on 2008-07-11
go to system>admin>system monitor>resources it shows how much downloaded and uploaded.

---

### Post by Kevbert on 2008-07-11
Hi. There's a screenlet which will do this for you.  First you need to install the screenlets manager which can be found [[COLOR="Red"]here[/COLOR]]("http://screenlets.org/index.php/Download").  It's probably best to use the deb package.  The screenlet can be found [[COLOR="Red"]here.[/COLOR]]("http://gnome-look.org/content/show.php/Net+Monitor?content=72013")

---

### Post by RajaAjmal on 2008-07-11
thanks for the reply kevbert. i've install the screenlet and the net monitor, and it seemed good. thanks again.

---

### Post by aktiwers on 2008-07-11
```
sudo apt-get install netspeed
```

Right-click on your gnome-pannel, pick "add to panel" and search for: netspeed

I always use that one.

You could also create a Conky for this task
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by vzxa1 on 2008-07-31
Easiest Way: Install "Firestarter" Firewall

---

### Post by aeiah on 2008-07-31
i use a cli program called vnstat

it can show me daily, average, weekly, monthly, estimated for this week, estimated for this month blah blah. all that sorta stuff.

i dont need to check much because im on an unlimited package, but if i did id probably make it display its results in conky, where i keep track of kb/s, cpu and ram usage etc anyway.

---

### Post by ingeon on 2009-11-01
[http://ubuntuforums.org/showthread.php?p=8212617#post8212617](http://ubuntuforums.org/showthread.php?p=8212617#post8212617)

---


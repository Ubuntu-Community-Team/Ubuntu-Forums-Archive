---
title: "Any way to turn on the firewall?"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by TAspr on 2012-01-17
I know there is an option to turn on/or off the firewall.  Anyway to do this?

---

### Post by BlinkinCat on 2012-01-17
Here is a complete guide - :)

[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by Lars Noodén on 2012-01-17
There is also a graphical front end available for UFW:

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by Johnny3 on 2012-01-17
I use this nice person's site.
[http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)

I just have to change the ports to whatever Thunderbird uses. Mine e mail doesn't us port 25.
Good Luck and God Bless Johnny3 65+++

---

### Post by TAspr on 2012-01-17
Where do you bring the terminal up?

---

### Post by TAspr on 2012-01-17
How do you bring up the terminal?  There is no option for it?

---

### Post by androssofer on 2012-01-17
> **TAspr said:**
> Where do you bring the terminal up?

click the ubuntu logo on the top left of your screen and search for 'terminal'

---

### Post by Johnny3 on 2012-01-17
> **androssofer said:**
> click the ubuntu logo on the top left of your screen and search for 'terminal'

Also called the Dash home.
Thanks and God Bless Johnny3 65++

---

### Post by androssofer on 2012-01-17
i'd also like to point out that on Linux, unlike some other OSes, the firewall is part of the system itself. So it is always on.

All the tools and utilities for it simply allow you to enable access to certain ports, services, ip address etc...

---

### Post by oldos2er on 2012-01-17
> **TAspr said:**
> How do you bring up the terminal?  There is no option for it?

Ctrl-Alt-t

```
sudo ufw enable
``` will turn on the firewall. Please read [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177) also.

---

### Post by TAspr on 2012-01-17
Where is the picture viewer, that used to be able to take pictures and send screen shots?

---

### Post by Johnny3 on 2012-01-17
> **TAspr said:**
> Where is the picture viewer, that used to be able to take pictures and send screen shots?

Under Dash home screenshot.
Thanks and God Bless Johnny3 65++

---

### Post by oklokl on 2012-01-17
ufw bug 
Unprotected exposure

[COLOR=#000000][FONT=Monaco][FONT=Gulim][FONT=Gulim]sudo ufw enable[/FONT][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][FONT=Gulim]sudo update-rc.d -f ufw defaults [/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=Monaco][FONT=Gulim]sudo ufw logging on
sudo ufw logging low[/FONT][/FONT][/COLOR]
sudo apt-get update && sudo apt-get install gufw

GUI  -> Windows Button ->gufw 
option > reSetting >turn on

---


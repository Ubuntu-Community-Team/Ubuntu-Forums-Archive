---
title: "[SOLVED] computer name change"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by adamogardner on 2008-06-01
I misspelled my computers name.  It as supposed to be spelled CRONUS with a "U"  Not a second letter "O."  I've been looking around for a place to edit but my eyes easily miss the obvious (hence the mispelling) so. is there a way to change this?  I really feel like a dummy until I do.

---

### Post by dave-5B on 2008-06-01
System > administration > network > general > hostname

:)

---

### Post by Joeb454 on 2008-06-01
Click System > Administration > Network

Then unlock it (if using 8.04) and choose the general tab. You can change it from there.

You may need to restart your system afterwards though

---

### Post by bobnutfield on 2008-06-01
> **adamogardner said:**
> I misspelled my computers name.  It as supposed to be spelled CRONUS with a "U"  Not a second letter "O."  I've been looking around for a place to edit but my eyes easily miss the obvious (hence the mispelling) so. is there a way to change this?  I really feel like a dummy until I do.

You can change you hostname in /etc/hostname.  Type:

```
sudo gedit /etc/hostname
```


You will see the name you have assigned.  You can correct the spelling just by changing it.  But keep in mind that you also have to change the name in
/etc/hosts as they must match.

Bob

---

### Post by Joeb454 on 2008-06-01
Which is why the GUI method may be easier ;)

Also you should use ```
gksudo gedit /etc/hostname
``` as Gedit is a graphical application :)

---

### Post by adamogardner on 2008-06-01
thankyou.  I went the terminal route and restarted my computer.  worked great.  SOLVED.

---

### Post by Joeb454 on 2008-06-01
Great :D And you can mark the thread as solved by clicking thread tools at the top of this page :)

---

### Post by Nythain on 2008-06-01
> **Joeb454 said:**
> Which is why the GUI method may be easier ;)
Only assuming the GUI is gnome... the mentioned gui method is useless to us *box, xfce or kde users :P

---

### Post by Joeb454 on 2008-06-01
That's what the prefixes are for ;)

---


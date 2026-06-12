---
title: "Deleting various things."
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Obero on 2008-11-17
My speed is pretty decent right now, but what I want to do still is remove some software that I already know is useless. For example, Rhythmbox. Amarok is a much better alternative, and I'd like to use that. Also, Firefox. Opera is better in my opinion. How do I go about removing these things, other than Synaptic which takes a bit longer?

Also, is there anything that I could remove that would be negative (as in, *bad*) for the computer system? Like, some kind of essential program I need? Also, will deleting mass software = faster computer? Probably not, though, but just asking. I still want to get rid of some useless softwares.

---

### Post by Crafty Kisses on 2008-11-17
You can technically remove packages from Add/Remove and the terminal:
```
sudo apt-get remove package name
```

---

### Post by jenkinbr on 2008-11-17
> **Obero said:**
> My speed is pretty decent right now, but what I want to do still is remove some software that I already know is useless. For example, Rhythmbox. Amarok is a much better alternative, and I'd like to use that. Also, Firefox. Opera is better in my opinion. How do I go about removing these things, other than Synaptic which takes a bit longer?

Also, is there anything that I could remove that would be negative (as in, *bad*) for the computer system? Like, some kind of essential program I need? Also, will deleting mass software = faster computer? Probably not, though, but just asking. I still want to get rid of some useless softwares.
```
sudo apt-get remove rhythmbox firefox
```
should work for removeing Rhythmbox and firefox, when typed into a terminal.

---

### Post by aysiu on 2008-11-17
Codename's right. If you want a method that's faster than Synaptic for removing Synaptic, typing ```
sudo apt-get remove firefox rhythmbox
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) will do it.

That said, if you're worried about possibly accidentally removing essential software, you should use Synaptic, as with each mark for removal you do you'll be warned about exactly what other packages will be removed as well.

And, no, deleting software won't speed up your computer. It will, however, free up hard drive space. So if you have a 4 GB hard drive (as I do on my Eee PC), removing unwanted programs is necessary. But if you have a 250 GB hard drive, then it's completely unnecessary.

There are other things you can do to speed up your computer, though: [list][*]Go to System > Administration > Services and turn off services you don't need. [*]Switch to KDE instead of Gnome, since you favor AmaroK and Opera (both are QT-based programs; loading both QT and GTK libraries takes extra resources). [*]Actually ditch desktop environments altogether and go for a lightweight window manager like [IceWM](http://www.psychocats.net/ubuntu/icewm) (or Fluxbox or Openbox or Enlightenment).[/list]

---

### Post by Obero on 2008-11-17
Thanks, there's this program called *Bulk Rename*. Anyway to get rid of that, yo?

---

### Post by Obero on 2008-11-17
> **aysiu said:**
> Codename's right. If you want a method that's faster than Synaptic for removing Synaptic, typing ```
sudo apt-get remove firefox rhythmbox
``` in [the terminal](http://www.psychocats.net/ubuntu/terminal) will do it.

That said, if you're worried about possibly accidentally removing essential software, you should use Synaptic, as with each mark for removal you do you'll be warned about exactly what other packages will be removed as well.

And, no, deleting software won't speed up your computer. It will, however, free up hard drive space. So if you have a 4 GB hard drive (as I do on my Eee PC), removing unwanted programs is necessary. But if you have a 250 GB hard drive, then it's completely unnecessary.

There are other things you can do to speed up your computer, though: [list][*]Go to System > Administration > Services and turn off services you don't need. [*]Switch to KDE instead of Gnome, since you favor AmaroK and Opera (both are QT-based programs; loading both QT and GTK libraries takes extra resources). [*]Actually ditch desktop environments altogether and go for a lightweight window manager like [IceWM](http://www.psychocats.net/ubuntu/icewm) (or Fluxbox or Openbox or Enlightenment).[/list]

Which one of those window managers are the best?

---

### Post by Obero on 2008-11-17
Also, how do I get rid of the *Games* all together? Pretty sure I'm not going to use any of them. Also, there's this thing called *Terminal Emulator*. Should I/can I get rid of that? It doesn't seem that useful, as opposed to the actual *Terminal*.

---

### Post by aysiu on 2008-11-17
> **Obero said:**
> Thanks, there's this program called *Bulk Rename*. Anyway to get rid of that, yo? I don't know the exact name of the package, but that's why Synaptic can be handy. If you do a search by name and description for the word *rename*, I'm sure you'll be able to find it and remove it.

> **Obero said:**
> Which one of those window managers are the best? Are you looking to start a war? "Best" is obviously a matter of opinion. I do think IceWM, while others may not think it "the best," is a good place to start, as it operates the closest to a normal desktop environment out of all the window managers. After you feel comfortable with the lightweight part of IceWM, you might want to explore some other ones. Fluxbox is very popular.

---

### Post by jenkinbr on 2008-11-17
> **Obero said:**
> Also, how do I get rid of the *Games* all together? Pretty sure I'm not going to use any of them. Also, there's this thing called *Terminal Emulator*. Should I/can I get rid of that? It doesn't seem that useful, as opposed to the actual *Terminal*.

games:

sudo apt-get remove gnome-games

---

### Post by Obero on 2008-11-22
> **Obero said:**
> Also, how do I get rid of the *Games* all together? Pretty sure I'm not going to use any of them. Also, there's this thing called *Terminal Emulator*. Should I/can I get rid of that? It doesn't seem that useful, as opposed to the actual *Terminal*.

It's been four days and the latter of the questions hasn't been answered, but anyway. The one to get rid of games worked, but when I tried to search for rename to get rid of Bulk Rename, there was nothing that showed that could be uninstalled. Also, the latter of the questions above has to be answered.

---


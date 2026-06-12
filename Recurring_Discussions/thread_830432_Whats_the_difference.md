---
title: "Whats the difference?"
date: 2008-06-15
forum: Recurring Discussions
---

### Post by XTR0RDiNAiRE on 2008-06-15
what is the difference between

ubuntu
kubuntu
xuntu

and others?

i have ubuntu right now
just wonderin which is better

---

### Post by akiratheoni on 2008-06-15
The only difference are the default desktop environmen (gnome, kde, xfce, for ubuntu, kubuntu, xubuntu respectively) and their default applications.

If you're on Ubuntu, you can install Kubuntu by going to Applications -> Accessories -> Terminal and typing:
```
sudo apt-get install kubuntu-desktop
```

If you want Xubuntu, type instead:
```
sudo apt-get install xubuntu-desktop
```

---

### Post by rainwalker on 2008-06-15
Ubuntu - The most popular flavor, uses the Gnome desktop environment which focuses more on simplicity and ease-of-use rather than features and customization
Kubuntu - Uses KDE instead of Gnome, which focuses more on features and customization and may not work very well on older hardware
Xubuntu - Uses XFCE instead of Gnome or KDE, and is the lightweight flavor usually used on older or less powerful hardware

There's not a "best" one, it's all personal preference.

---

### Post by EtniesBMX on 2008-06-15
That's a good question. Each includes a different desktop environment. Ubuntu and Kubuntu give you the same thing, just in slightly different ways (different menus and defaults and stuff), and Xubuntu is really minimalistic, no frills, and a bit faster.

You can try U/K/Xubuntu at the same time without messing up your system too.

Read more here: [http://www.psychocats.net/ubuntu/whichbuntu](http://www.psychocats.net/ubuntu/whichbuntu)

---

### Post by knavarathna92 on 2008-06-15
Ubuntu uses the GNOME desktop environment which is intended to be simple and functional with room for lots of customization.  Kubuntu uses the KDE desktop environment which is more feature heavy but not that customizable.  Xubuntu uses the XFCE interface, which is lightweight on resources and is recommended for older computers.

---

### Post by akiratheoni on 2008-06-15
> **knavarathna92 said:**
> Ubuntu uses the GNOME desktop environment which is intended to be simple and functional with room for lots of customization.  Kubuntu uses the KDE desktop environment which is more feature heavy but not that customizable.  Xubuntu uses the XFCE interface, which is lightweight on resources and is recommended for older computers.

Eh, I wouldn't quite say KDE is less customizable...

---

### Post by JoshuaRL on 2008-06-15
> **akiratheoni said:**
> The only difference are the default desktop environmen (gnome, kde, xfce, for ubuntu, kubuntu, xubuntu respectively) and their default applications.

If you're on Ubuntu, you can install Kubuntu by going to Applications -> Accessories -> Terminal and typing:
```
sudo apt-get install kubuntu-desktop
```

If you want Xubuntu, type instead:
```
sudo apt-get install xubuntu-desktop
```

Actually, it's better to not use APT for metapackages like the desktops.  Instead, use Aptitude:
```

sudo aptitude install kubuntu-desktop

```
and if you want to delete it:
```

sudo aptitude remove kubuntu-desktop

```
The reason is that with APT, it doesn't keep track of all the packages in a metapackage.  It just deletes the empty container, so to speak.  Aptitude can keep track of that, and so can delete the whole metapackage.

And FYI, get ready to spend 30-45 minutes for Xubuntu and about 1-1.5 hours for Kubuntu.  Those are pretty big.

If you are looking for a lightweight Desktop Environment, you might check out Enlightenment.  It's what I use and its quite speedy.

[http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

---

### Post by JoshuaRL on 2008-06-15
> **akiratheoni said:**
> Eh, I wouldn't quite say KDE is less customizable...

I'd agree.  While seeming more comfortable with users coming from Windows, KDE is much more customizable.  Really powerful.

---

### Post by Joeb454 on 2008-06-15
Flux is lightweight too :) I used Flux for a custom VM I made :)

---

### Post by JoshuaRL on 2008-06-15
Yeah, but isn't Flux (like all the other ones based off of Blackbox) really a Window Manager instead of a full Desktop Environment?

---

### Post by Joeb454 on 2008-06-15
I'm not sure, I think it is yes :)

Though I installed Firefox and amarok, and they worked just fine from what I recall :)

---

### Post by cariboo on 2008-06-15
I would like to throw in Linux Mint, another light weight distribution based on ubuntu. It works really well on my older HP laptop.

Jim

---

### Post by Joeb454 on 2008-06-15
I thought Mint was Gnome based :confused: In which case it's no lighter than the standard Ubuntu :)

---

### Post by powerpleb on 2008-06-15
I'd say it's a little heavier than a standard Ubuntu install because it has all the codecs installed plus other tweaks such as the mintmenu etc.

---

### Post by JoshuaRL on 2008-06-15
Agreed.  Although, there are XFCE and Fluxbox based Community Editions to Linux Mint though.

---

### Post by cariboo on 2008-06-16
I forgot to mention I installed the light version of Linux Mint and it runs faster then Ubuntu. I haven't used it much as I find the keyboard is a pain to use, I use a MS ergonomic split keyboard for everyday usage.

JIm

---


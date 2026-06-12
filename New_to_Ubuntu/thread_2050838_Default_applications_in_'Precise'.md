---
title: "Default applications in 'Precise'"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by Raphicerus on 2012-08-31
For the most part, I've been happy to use the default applications. I've never got anywhere with Thunderbird, but that's just me, I think. Whatever I finally pick for email, it can't possibly be worse than Outlook. ;)

Today, though, I had to copy an audio CD, and Brasero just wouldn't do it.  Fair play, at least it didn't spoil my blank CDs  while it was throwing up "unknown error" and ejecting.

After a bit of googling I tried **k3b**, and it worked like a dream.

This is pure curiosity, but why does 12.04 have Brasero as its default? It gets a *terrible* feedback in the repository, while k3b does very well.

Is this something to do with wide hardware compatibility, or backward compatibility? I'm just guessing now...

---

### Post by Paddy Landau on 2012-08-31
Because k3b is based on KDE, not Gnome, and Ubuntu is based on Gnome, not KDE. You would have noticed that the user-interface for k3b is somewhat different from the standard applications in Ubuntu.

Brasero may be the best of a bad lot that is Gnome-based.

You can use Gnome applications on KDE systems, and vice-versa.

When you install k3b on Ubuntu, it has to also install the relevant KDE libraries for k3b. That is not a problem, of course, except on the installation disk.

The Ubuntu family also includes — among others — Kubuntu, which uses KDE; Xubuntu, which uses XFCE; and Lubuntu, which uses LXDE.

---

### Post by tartalo on 2012-08-31
Because Ubuntu has always been based in Gnome and therefore chooses programs that use the GTK framework. 

K3B uses the QT framework, the one used by KDE, that means that you have now both sets of libraries installed.

There's nothing wrong with that, it's very common in real world installations, but distros tend to stick to only one framework in their default software selection.

They do that to save storage space and to create an uniform experience (Gnome apps tend to give priority to simplicity and KDE apps to feature richness).

EDIT: Paddy Landau was faster :)

---

### Post by Raphicerus on 2012-08-31
> Because k3b is based on KDE, not Gnome, and Ubuntu is based on Gnome,  not KDE. You would have noticed that the user-interface for k3b is  somewhat different from the standard applications in Ubuntu.  

Aahhhh! I had no idea that these schisms existed. I didn't even notice the differences in user interface.  k3b did the job, so it will receive good feedback that doesn't mention Brasero.

The libraries would explain why it was such a large download.

> They do that to save storage space and to create an uniform experience  (Gnome apps tend to give priority to simplicity and KDE apps to feature  richness).

Thanks - I'm beginning to understand the Linux world.

Today I finally and accidentally got terminal into full screen mode, and enjoyed the timeless experience of a real character-based interface. Is there a command-line CD copier?

---

### Post by tartalo on 2012-09-01
> **Raphicerus said:**
> Is there a command-line CD copier?

Yes, for example:
[https://help.ubuntu.com/community/cdrdao](https://help.ubuntu.com/community/cdrdao)

---

### Post by Paddy Landau on 2012-09-01
> **Raphicerus said:**
> I had no idea that these schisms existed.
They aren't schisms. They are simply alternatives, when people have developed something else to satisfy their own personal preferences. That's the wonderful thing about Linux — unlike commercial companies, people are perfectly happy for you to leave one distro and go to another, or even to leave Linux and go to another OS.

That's also why KDE, Gnome, LXDE, etc. applications can so happily co-exist. Each one's creators are not trying to prevent you from switching.

> **Raphicerus said:**
> The libraries would explain why it was such a large download.
Correct. Next time you install a KDE-based application, the download won't be as large.

> **Raphicerus said:**
> Is there a command-line CD copier?
There is a command-line interface (CLI) to most things: creating DVDs, playing music, displaying and modifying pictures, and more.

---

### Post by Raphicerus on 2012-09-01
Thanks, Paddy and tartalo. 

Linux CLI is going to suit me.

It seems k3b installed cdrdao behind the scenes, so I've got it already! Time for some experimenting.
I'll mark this thread as solved.

---


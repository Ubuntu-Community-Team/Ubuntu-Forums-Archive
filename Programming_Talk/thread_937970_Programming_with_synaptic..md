---
title: "Programming with synaptic."
date: 2008-10-04
forum: Programming Talk
---

### Post by davbren on 2008-10-04
Hey Im looking to make a program that accesses the repos to install software. Could anyone enlighten me as to how I would do that...

---

### Post by eragon100 on 2008-10-04
Why would you do that? We have synaptic and apt-get already! :confused:

---

### Post by davbren on 2008-10-04
It seems silly I know. Its for beginners when they first install ubuntu. If they can decide what they want in their system for when they first install it then it'll be great. I know everything is available through apt or synaptic but to attract new users I think this will be ideal.

It will also give them the opportunity to see software that they wouldn't necessarily know of. 

I spose its of the same mould as Automatix but in a more "introductory" way.

---

### Post by CptPicard on 2008-10-04
There already are apps like tasksel, and on KDE there's Adept Installer... I am sure that on GNOME there is something similar.

On the other hand I am sure you can just check out the source to some existing applications to see how they do this.

---

### Post by yaknowwat on 2008-10-04
The most simplistic, safe and efficient way to do this might be through apt-get and its commands. Just have your GUI cover it up for the most part.

Also what he's doing is good if something like this is done polished enough it can be useful to new users. Pretty much the ability to make an easy or more recognizable way for installation of things like codecs, java, to an auto customize firefox button and so on.

You should look into Ubuntu Tweak if you want to see something of similar value.

---

### Post by nvteighen on 2008-10-04
> **CptPicard said:**
> There already are apps like tasksel, and on KDE there's Adept Installer... I am sure that on GNOME there is something similar.


GNOME has Add/Remove (Applications->Accesories).

Anyway, in a Debian system, you'd need to develop using the APT library, which seems a bit complex to me, as it is available divided into a higher-level and a lower-level library.

Install the "libapt-front-dev" (which is the high-level library, but depends on the lower "libapt-pkg-dev") and "libapt-pkg-doc" (docs) packages. Be warned that the documentation is really bad; maybe even worse than ncurses'!

---

### Post by pmasiar on 2008-10-04
I am not sure how you can make something easier than synaptic. All what beginner needs to know is what to search for, rest is trivial - dead squirrel can do that.

---

### Post by yaknowwat on 2008-10-05
> **pmasiar said:**
> I am not sure how you can make something easier than synaptic. All what beginner needs to know is what to search for, rest is trivial - dead squirrel can do that.

By putting the most commonly wanted things right in front of a user in a UI that is very minimal with big buttons and easy to understand well written descriptions.

Along with the ability to remove them easily .  Most of they easy installers are just that they install the item but don't make it just as easy to remove them.

---


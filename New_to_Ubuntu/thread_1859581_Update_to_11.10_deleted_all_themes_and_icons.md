---
title: "Update to 11.10 deleted all themes and icons"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by MadPoet on 2011-10-14
Hey there. I had a weird problem when I updated to Ocelot last night: all the themes and icons I had installed just disappeared, into thin air. Also, I don't know if this is what is supposed to happen with the upgrade, but in the system settings there is no way to add or edit themes. Some themes I even installed simply by dragging the tar file to the system settings, but that is not working anymore either. Can some one point me in the right direction? :) Much appreciated.

---

### Post by sadaruwan12 on 2011-10-14
That tends to happen after a upgrade so tell us do you get errors when you try to install your themes or just nothing happens.

---

### Post by CatKiller on 2011-10-14
As I understand it, Oneiric uses Gnome 3, which means your Gnome 2 themes will no longer work.

---

### Post by MadPoet on 2011-10-14
It's only my second upgrade so I had no idea this could happen, it caught me by surprise... :( I have different problems for the icons and the theme. For icons I use the Faenza pack, which installs without problem. However, the icons are placed at home/.icons; shouldn't it install at usr/share/icons? Anyway, I just don't see where can I change the icons in the Appearance settings; I only have option to change the wallpaper and the theme.

The theme I just don't know how to install. I use the [Not Mac theme]("http://blog.sudobits.com/2011/05/07/mac-os-x-theme-for-ubuntu-11-04/") which doesn't have an installer; it was as simples as drag and drop into the old theme menu (and as far as I can remember I did the same for pretty much every theme I ever downloaded). Any idea if it's possible to install them like this?

EDIT: Just saw the reply from CatKiller, that's a shame. :( And I guess that's why it just vanished after the upgrade... Could the same have happened to the icons set? If so, does anyone know any website with themes / icons for Gnome 3?

---

### Post by CatKiller on 2011-10-14
There's no difference between ~/.icons and /usr/share/icons except that icons in your Home folder are only available to your user.

Again, this is my understanding although I haven't yet used Gnome 3, but AIUI the theming mechanism for Gnome 3 is still in flux so there aren't many third-party themes at the moment. Which may or may not be why the Appearance tool doesn't do anything.

KDE had to go through a similar shake-up with the transition to KDE 4. It'll work out over time. Ubuntu's got extra trouble because they're trying to make Unity work at the same time.

---

### Post by MadPoet on 2011-10-14
Thanks mate, really appreciate the explanation. I've been using Ubuntu for just 3 months now so I still get confused with some basic stuff from time to time. :x

In the meantime, I googled a bit and came upon the Gnome-Tweak app, that allowed me to see that the Faenza icons were, indeed, properly installed. I changed to them without a problem. It really strikes me as odd that the OS comes without options as basic as this and you have to install an app to change them. Same thing about the Unity dock... For me it's odd that such options aren't included by default.

Anyways, thanks a bunch for the help mate, once again, I really appreciate it. ;)

---

### Post by CatKiller on 2011-10-14
Gnome 3 (and KDE 4 for that matter) is essentially a complete re-write. It's not that the customisation tools have been taken out, just that they haven't been written yet. The same thing happened when they re-did the networking framework. There are still some things that the old tools did well that the new ones don't do at all, even though the new one is better in lots of other ways. It'll get there in time.

---

### Post by grahammechanical on 2011-10-14
I have been testing 11.10 since alpha 2 and there have only been four themes. I think that the intention is for the Ubuntu community to develop themes that work with Gnome 3 and Unity and them submit them for inclusion. The Ubuntu developers have been working very hard on other things.

Regards.

---

### Post by michele.bartolettistella on 2011-10-16
Dear users,

I encountered the same problems... I've just advanced to Ocelot and all my preferred appearances (icons, themes...) disappeared. It's bad, because (see .png attached) all the icons are identical: directories, text files...

And the Aspect Panel is quite rudimental; on Natty I could mix different icons, themes and wallpapers.

How can I modify the icons?

Thank you,

Michele

---

### Post by mcduck on 2011-10-16
> **michele.bartolettistella said:**
> Dear users,

I encountered the same problems... I've just advanced to Ocelot and all my preferred appearances (icons, themes...) disappeared. It's bad, because (see .png attached) all the icons are identical: directories, text files...

And the Aspect Panel is quite rudimental; on Natty I could mix different icons, themes and wallpapers.

How can I modify the icons?

Thank you,

Michele

Install the [gnome-tweak-tool]("apt:gnome-tweak-tool"), it will allow you to select the icon, window border and application themes you want to use. And it gives you some other settings missing from the default options as well, like the ability to choose which fonts to use etc.

However based on your screenshot you have a bit of a different problem, it's not a question of having a boring theme but instead theme not applying at all. Some people have had that problem after upgrading from 11.04 (as opposed to making a fresh install).

There are several threads about that in the forums, so searching for one might give you a solution. However it could be simply because it's now trying to use the theme you were using before doing the upgrade, which doesn't actually work in 11.10 (as 11.10 uses GTK3 themes while previous Ubuntu versions used GTK2). In that case simply selecting some working themes with the gnome-tweak-tool migh be enough to get things working again...

---


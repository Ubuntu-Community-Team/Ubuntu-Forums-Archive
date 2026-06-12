---
title: "color for theme in 11.10/12.04"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by beelzebufo on 2012-04-13
I have seen similar threads, but the only answers given were that I had to change my theme, I don't want to change the theme, I just want the orange to be blue.. that's it, everything else is great, I just want the orange to be blue, you used to be able to customize the current theme and I can't figure out how to do it now.  I am using gnome 3 with ubuntu 12.04 now, but I had the same problem on 11.10.  Any help would be greatly appreciated

thanks 
beelzebufo

---

### Post by pqwoerituytrueiwoq on 2012-04-13
i think your best bet it to edit the theme
it seems to me each release has less and less options
luckily the themes are written in css which is a easy language to learn i just wish i could use firebug on the system
i think the files you want are look at are in here
/usr/share/themes/Ambiance/gtk-3.0/
if you edit them and the theme updates there goes your mod

---

### Post by anejo on 2012-04-13
What you want is the 'Ambiance-Blue' theme and the 'Humanity-Colors-Dark-Blue' icons (for example) from the RAVEfinity guys.

The ppa info or downloads at:
[https://launchpad.net/~ravefinity-project/+archive/ppa]("https://launchpad.net/%7Eravefinity-project/+archive/ppa")

---

### Post by Frogs Hair on 2012-04-13
> **beelzebufo said:**
> I have seen similar threads, but the only answers given were that I had to change my theme, I don't want to change the theme, I just want the orange to be blue.. that's it, everything else is great, I just want the orange to be blue, you used to be able to customize the current theme and I can't figure out how to do it now.  I am using gnome 3 with ubuntu 12.04 now, but I had the same problem on 11.10.  Any help would be greatly appreciated

thanks 
beelzebufo

Gnome 3 no longer includes the customize option in appearance preferences. There is an Ambiance Blue theme at the link, but has not been updated for the Gnome Shell 3.4 yet and may not work right in the shell . I know this because I have the happy/themes PPA.

Theme:[http://gnome-look.org/content/show.php/?content=133676](http://gnome-look.org/content/show.php/?content=133676)

PPA: [https://launchpad.net/~satyajit-happy/+archive/themes](https://launchpad.net/~satyajit-happy/+archive/themes)

---

### Post by beelzebufo on 2012-04-13
so why in God's name are they taking customization out of ubuntu? sort of negates what ubuntu is doesn't it? if I wanted to use an operating system that looks and feels the way someone else wanted it to feel.. I would use Windows.. anyway, thanks for the responses, I will check out that ambiance blue theme

---

### Post by Frogs Hair on 2012-04-13
> **beelzebufo said:**
> so why in God's name are they taking customization out of ubuntu? sort of negates what ubuntu is doesn't it? if I wanted to use an operating system that looks and feels the way someone else wanted it to feel.. I would use Windows.. anyway, thanks for the responses, I will check out that ambiance blue theme

Gnome removed the option and they no longer support Gnome 2.

---

### Post by grahammechanical on 2012-04-13
>  sort of negates what ubuntu is doesn't it?

That is not how I see Ubuntu. A lot of people are happy about what they get as default. I am. Too much choice can be a bad thing. Leads in some cases to people messing up their systems and then blaming Ubuntu.

And then there is community involvement. What community involvement would there be if Canonical provided everything? So, there now is an opportunity for anyone to create themes, and icon sets, app indicators, scopes, lenses, and all that other stuff.

People are invited to develop for Ubuntu.

[http://developer.ubuntu.com/]("http://developer.ubuntu.com/")

Regards.

---

### Post by beelzebufo on 2012-04-14
people that don't want choice or free will should use windows or mac.  Ubuntu has never been a platform for mindless sheep.  I don't understand why they would take away the ability to customize, I like the defaults too, I just don't like orange, I like blue.

---

### Post by beelzebufo on 2012-04-15
I like the defaults too, but what I love about ubuntu is the ability to customize.  What I am saying is that the more they take away my ability to have a choice, the less I like ubuntu, but I have strayed from the topic.  Is there an easy way to simply change things from being orange to being blue?

---

### Post by zombifier25 on 2012-04-15
Use the ppa from anejo's posts above. Then use a tool like Ubuntu Tweak or GNOME Tweak Tool to apply the theme..
However, keep in mind that the themes will only work with 11.10 (with GNOME 3.2) They won't display correctly on 12.04 (GNOME 3.4) If you want them to work on 12.04, wait for the developers to update the theme.

---

### Post by mcduck on 2012-04-15
> **Frogs Hair said:**
> Gnome 3 no longer includes the customize option in appearance preferences. There is an Ambiance Blue theme at the link, but has not been updated for the Gnome Shell 3.4 yet and may not work right in the shell . I know this because I have the happy/themes PPA.

Theme:[http://gnome-look.org/content/show.php/?content=133676](http://gnome-look.org/content/show.php/?content=133676)

PPA: [https://launchpad.net/~satyajit-happy/+archive/themes](https://launchpad.net/~satyajit-happy/+archive/themes)

More appropriate than "no longer" would be to say that Gnome 3 doesn't yet support the color customization. ;)

Even though the theme might look roughly the same to the end user, the underlaying theme engine is completely new one, and it took almost 10 years for people to develop the option for changing color in Gnome2/GTK2. Nobody has had time to build the same feature for Gnome3/GTK3 yet.

So it's not that they had removed a working feature we used to have, but that there has never been such feature for the theme engine we are using now. The developers are not removing things just to annoy you, actually they are doing quite an amazing job considering the new theme engine looks and feels so close to the old one that people are able to make such misconceptions about features having been removed... ;)

Anyway, to actually answer the question of the thread,  the easiest option is to install a theme that has already made the color chnage for you. And the harder option is to edit the GTK3 theme files by hand and change the color codes to whatever you want, it's not too complicated of a task if you are familiar with CSS syntax and aren't afraid of editing text-based config files by hand.

---

### Post by 3rdalbum on 2012-04-15
No Gnome 3-based distro has fine-tunable options for theming. This is because the controls for this have been taken out of Gnome by the Gnome developers.

In other words, stop blaming Ubuntu.

In fact, Gnome 3 originally had no way of changing the theme at all. The Ubuntu developers patched the "wallpaper" program to allow changing the theme.

---


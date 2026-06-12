---
title: "Change Theme Colors?"
date: 2011-07-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moore.bryan on 2011-07-18
Any chance of being able to change theme colors in Oneiric?

---

### Post by lucazade on 2011-07-18
> **moore.bryan said:**
> Any chance of being able to change theme colors in Oneiric?

You could change themes via GUI using gnome-tweak-tool or via CLI using gsettings/dconf-editor but all these tools doesn't allow to change theme colors.
You can change colors easily via css files at the moment.

---

### Post by moore.bryan on 2011-07-18
> **lucazade said:**
> You could change themes via GUI using gnome-tweak-tool or via CLI using gsettings/dconf-editor but all these tools doesn't allow to change theme colors.
You can change colors easily via css files at the moment.
Thanks for the quick reply... I find it interesting we can install other themes easily, but can't select them easily.

Which CSS files do you suggest I look for?

Hmm... an interesting problem. Any changes I make in gnome-tweak-tool are kept, but do not change **anything** in my session, even after logging-out and restarting. So, there seems to be no way to make **any** changes. Am I missing something?

---

### Post by lucazade on 2011-07-18
> **moore.bryan said:**
> Thanks for the quick reply... I find it interesting we can install other themes easily, but can't select them easily.

Which CSS files do you suggest I look for?

yes, strange.

you can change colors here:
gksu gedit /usr/share/themes/Ambiance/gtk-3.0/gtk.css

and in this one
gksu gedit /usr/share/themes/Ambiance/gtk-3.0/settings.ini

then you need to logout/login to see new colors because gnome-tweak-tool doesn't see changes, same for dconf.

---

### Post by moore.bryan on 2011-07-18
> **lucazade said:**
> gnome-tweak-tool doesn't see changes, same for dconf.

Er, then, what's the use of it?

---

### Post by mc4man on 2011-07-18
> **lucazade said:**
> yes, strange.

you can change colors here:
gksu gedit /usr/share/themes/Ambiance/gtk-3.0/gtk.css

and in this one
gksu gedit /usr/share/themes/Ambiance/gtk-3.0/settings.ini

then you need to logout/login to see new colors because gnome-tweak-tool doesn't see changes, same for dconf.
For _some_ windows in unity session atm you may also need to edit in 
/usr/share/themes/Ambiance/gtk-2.0/gtkrc
ex. I like to get rid of the orange, so in addition to the above 2 files need to change the nselected_bg_color: in the gtkrc to change in all windows (firefox, synaptic, update manager, ccsm,  ect.

---

### Post by moore.bryan on 2011-07-18
Yeah, I've done that too. The only thing I think I can't seem to change is the orange "close" button. I didn't think that was a jpg... I thought it was CSS'd.

---

### Post by lucazade on 2011-07-19
> **moore.bryan said:**
> Er, then, what's the use of it?

ahah, good question! I'd like to know as well why doesn't see changes in css files.
Yesterday, working on Ambiance, I believe I've done 100/200 login-logout :)

if anyone know how to avoid this I'd be grateful, this didn't happen with gnome2, maybe gnome-settings-daemon related.

ps you can use thewidgetfactory gtk3 to test theme but doesn't have all widgets.

---

### Post by lucazade on 2011-07-19
at least I have found a workaround to reload new theme changes without logout.
it is enough to rename theme folder before opening tweak-tool to switch theme, this way the system cannot find old theme in cache and have to load and apply new one.

---

### Post by moore.bryan on 2011-07-19
> **lucazade said:**
> ahah, good question! I'd like to know as well why doesn't see changes in css files.
Yesterday, working on Ambiance, I believe I've done 100/200 login-logout :)
Well, at least you can feel better knowing you're not alone!

> **lucazade said:**
> at least I have found a workaround to reload new theme changes without logout.
it is enough to rename theme folder before opening tweak-tool to switch theme, this way the system cannot find old theme in cache and have to load and apply new one.
An intriguing, genius solution... can I assume, as with most of my "solutions," serendipity?

EDIT
For no apparent reason, this morning gnome-tweak-tool is *actually* working and reflecting changes *immediately*. What's strange is this is after not upgrading anything. Oh, well...

---

### Post by mc4man on 2011-07-19
> The only thing I think I can't seem to change is the orange "close" button
That I've no idea, though on one install if I switch from nvidia to nouveau the button changes to blue

---

### Post by moore.bryan on 2011-07-19
Well, it turns-out the buttons actually *are* images (png's, to be exact). Interestingly, when I try and replace them with blue ones (from the [Ambiance Blue theme on gnome-look.org]("gnome-look.org/content/show.php/Ambiance+Blue?content=133676")), the whole theme goes to hell and won't work.

---

### Post by mc4man on 2011-07-19
I've not a clue to what nouveau is doing - as far as I know there is no blue close icon on this install

---

### Post by moore.bryan on 2011-07-19
I have an integrated Intel chipset, so I don't worry about the nouveau stuff, but I can't figure how changing the files should mess anything up if they're all named the same--which they are.

---

### Post by kolinab on 2011-10-12
Thanks for sharing this exchange here.

I hate the orange and find it a little baffling why the option was removed to easily change it via GUI. I had to edit the three following files to change the orange to something a little nicer. 

/usr/share/themes/Ambiance/gtk-3.0/gtk.css
/usr/share/themes/Ambiance/gtk-3.0/settings.ini
/usr/share/themes/Ambiance/gtk-2.0/gtkrc

---


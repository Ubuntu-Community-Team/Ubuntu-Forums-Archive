---
title: "Missing User Data"
date: 2010-09-04
forum: Programming Talk
---

### Post by KdotJ on 2010-09-04
I am writing a program which will store the user's data in a directory inside the hidden .config folder in that user's home directory. Now I read on this forum a while back that it is not best practise to create these files on the program install (via a script in the .deb for example) but rather create them upon the program's first execution. 
My program does this, when it is run for the first time the user is presented with a new setup dialog which gathers the required information and creates the files. My program does this upon execution by checking to see if the directory exists, along with the files in it. If the directory and/or files do not exist, the setup dialog is displayed and they are created accoringly.

However, on future runs of my program, if this data or the directory somehow has been deleted or the program can't find it.. the program will present the user with the "new setup" dialog again. This will be somewhat confusing to the user as they will think *"I've already done this before, and it isn't the first time I've used this program"*

So what is the elegant solution? My only real idea is to have some text on the setup dialog along the lines of "Click here if this is not the first time you have used this program" and when clicked, will show a message dialog explaining that the data cannot be found and must be re-created etc etc. This obviosuly is a bit of a somewhat lazy solution... so is there a better way?

I know that it is unlikely that the data will be deleted unless the user deletes it themselves or something bad happens, but
the problem still needs to be trapped in case such situation does arise.

Thanks in advance

---

### Post by worksofcraft on 2010-09-04
Interesting thoughts... I'm kind of working on configuration stuff myself atm.

My feeling is that whenever it finds no configuration file it simply says: "Configuration file is missing. Setting up now!" or something like that.

BTW is ~/.config a kind of established standard place to store user configuration options for all packages?

p.s. on my computer there are loads of packages who just make their config in my home directory and I don't like the clutter even if they are hidden:
```


.		.gconf		 .java		      .recently-used.xbel
..		.gconfd		 .kde		      .ssh
.adobe		.gegl-0.0	 .lmmsrc.xml	      .sudo_as_admin_successful
.audacity-data	.gimp-2.6	 .local		      .themes
.bash_history	.gksu.lock	 .loki		      .thumbnails
.cache		.gnome		 .macromedia	      .update-notifier
.compiz		.gnome2		 .mission-control     .VirtualBox
.config		.gnome2_private  .mozilla	      .windows-serial
.dbus		.googleearth	 .nautilus	      .wine
.dmrc		.gstreamer-0.10  .nvidia-settings-rc  .xchat2
.dvdcss		.gtk-bookmarks	 .openoffice.org      .xinput.d
.esd_auth	.gvfs		 .pki		      .xsession-errors
.evolution	.ICEauthority	 .pulse		      .xsession-errors.old
.fontconfig	.icons		 .pulse-cookie

```

just look at that mess :/
and I don't even have "evolution" on my computer!

---

### Post by KdotJ on 2010-09-05
Yeah that kind of idea seems the simplest. I can't even have a file which says it's been set up previously, as if the directory gets deleted it will still appear as if it has been run yet. And the thing is I don't really want to have "data missing" come up even though it's the first time run of the program, as even though the statement is true, it doesn't look very good and a bit confusing to the user who has just installed this program and it says data is missing already lol. But I guess you're right, just have some way to tell the user the what's happening and why

> **worksofcraft said:**
> 
BTW is ~/.config a kind of established standard place to store user configuration options for all packages?


I'm pretty sure I remember reading this, in this forum in fact. Mine is littered too just like yours, and even my home folder is filled with a lot hidden bits and pieces. I think .config is a newer standard? As I still have configs for some packages just dumped in my home folder. Not too sure though...

---

### Post by Bachstelze on 2010-09-05
> **worksofcraft said:**
> 
BTW is ~/.config a kind of established standard place to store user configuration options for all packages?


Yes and no. There's a number of programs that use it (programs using the QSettings framework provided by Qt for example), but it's by no means an "official" standard.

---

### Post by Barrucadu on 2010-09-05
~/.config is part of the XDG basedir spec. $XDG_CONFIG_HOME contains the name of the directory which should be used to store user configuration which, if empty, should default to ~/.config.

Regarding the topic of the thread; I think the cleanest way would simply to treat it like the first run if the directory is missing. Is someone really going to be deleting their configuration files so frequently that it'd be irritating for it to do that?

---

### Post by KdotJ on 2010-09-05
> **Barrucadu said:**
> 
Regarding the topic of the thread; I think the cleanest way would simply to treat it like the first run if the directory is missing. Is someone really going to be deleting their configuration files so frequently that it'd be irritating for it to do that?

No you're quite right. I know that this would be unlikely to happen unless the user explicitly did it anyway. I'll just go with the plan,

thanks guys for your help

---


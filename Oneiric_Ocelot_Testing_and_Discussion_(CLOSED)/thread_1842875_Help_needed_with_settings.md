---
title: "Help needed with settings"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-09-12
I am trying to write a script to customize and set up the desktop exactly as I want.

Firstly, I am trying to customize the launcher with

```

gsettings set desktop.unity.launcher favorites '['nautilus-home.desktop', 'chromium-browser.desktop', 'thunderbird.desktop', 'pidgin.desktop', 'filezilla.desktop']' 

```

But I just get a "no such schema" error.

I am also looking for a bash command line script to set the launcher the icon size and autohide for the 3D desktop but cannot find how you edit compiz settings in this way.

---

### Post by mc4man on 2011-09-12
the command would be 
gsettings set com.canonical.Unity.Launcher favorites "[...]"

Also in this case you'd use " instead of ' at beginning & end (type as values
man gsettings should prove helpful

As far as the other - those settings are still in gconf so you'd need to construct a gconftool command
the icon size is in 
/apps/compiz-1/plugins/unityshell/screen0/options/icon_size
To get you going there

```
gconftool-2 -s --type=integer  /apps/compiz-1/plugins/unityshell/screen0/options/icon_size 40
```

---

### Post by sonicb00m on 2011-09-12
Thanks!

The compiz one didnt work but I noticed that the Unity plugin in the settings manager seems to have disappeared.

How do you figure out the key paths for the compiz settings?

---

### Post by mc4man on 2011-09-12
> **sonicb00m said:**
> Thanks!

The compiz one didnt work but I noticed that the Unity plugin in the settings manager seems to have disappeared.

How do you figure out the key paths for the compiz settings?
The gconf command works here fine, not sure why you don't see unity plugin in ccsm?

Anyway, -  for gconftools this provides some info 
gconftool --help-all

Then an easy way to get path, key  and value type that is somewhat redundant - I open gconf-editor, find the key and copy the path from screen
(so in other words, as far as setting changes I could just do there, but a good way for getting a proper command
Ex. the prev. posted one
screen 1 - I'm coping the the key path which shows after highlighting it
screen 2 - d. checking the value type by clicking edit on the key, in this case integer. (most are either integer, boolean, or list

There is a get commannd for gconf, and some others so this can be done solely from the cli, though in most  cases I take the easiest way above

Ex. here from cli
 ```
gconftool-2 --get /apps/compiz-1/general/screen0/options/active_plugins

```
This produces a list of current active plugins, to set a new one I'd do (also example of the list type which is a bit tricky to do right
```
gconftool-2 -s --type=list --list-type=string /apps/compiz-1/general/screen0/options/active_plugins  [core,composite,opengl,decor,vpswitch,resize,place,cube,gnomecompat,move,regex,rotate,scale,scaleaddon,animation,expo,unityshell]

```

---


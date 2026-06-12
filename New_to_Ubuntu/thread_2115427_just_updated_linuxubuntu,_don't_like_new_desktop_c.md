---
title: "just updated linux/ubuntu, don't like new desktop configuration"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by Jonathan47 on 2013-02-12
I just updated (without knowing much about what I was doing)  linux,    and ubuntu from 10.04 to 12.10 (I think).
 I now have a working extended desktop, which was my original problem, but I have a new desktop configuration that I do not like. I have a series of icons, which get in the way,  down the left side of my main monitor, and nothing in the top bar. With the old configuration, I had a few drop down menus along the top, which I much prefer, as there were some useful things (can't remember what they were called) that I don't seem to have any more. Does anyone know what I'm talking about, and can you tell me how to go back to my old config?
I had GNOME before, I think. Don't know what if anything I have now

Thanks

---

### Post by ibjsb4 on 2013-02-12
If you upgraded from 10o4 I think you now have 12o4 and you can add the Gnome Classic desktop to your install.

```
sudo apt-get install gnome-session-fallback
```And choose which desktop you want at boot (login).

Also, heres some tweaks to make you feel more at home  :)

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

---

### Post by stinkeye on 2013-02-12
Spend some time with it and learn how to use it.
You may find you like it.
The launcher to the left can be hidden.
You can add indicators to the top panel.
[**_[COLOR="DarkRed"]indicators-collection-for-ubuntu[/COLOR]_**]("http://www.noobslab.com/2012/11/indicators-collection-for-ubuntu.html")

Press the Super(windows) key and type in "help".

You can install **unity-tweak-tool** to change
unity, window manager, appearance and system settings.
```
sudo add-apt-repository ppa:freyja-dev/unity-tweak-tool-daily
sudo apt-get update && sudo apt-get install unity-tweak-tool
```

---

### Post by JiuJitsu500 on 2013-02-12
Yeah bro, get used to it. Ever since 11.04 the new config you speak of is the standard. It's Gnome-based and called Unity.

I hated it at first, and only liked it on my old netbook until recently. I've learned to like it a lot. gnome-session-fallback (look for it in the software center) gives a lot of the old functionality back.

Cinnamon, KDE, XFCE, LXDE, MATE, GNOME 3 (gnome shell), and Unity are your major players - the old Gnome is gone, but I think cinnamon is the one closest to it. Google how to install it (it's a ppa and simple to do). Then, google how to fully remove Unity if you like.

I have one laptop with gnome fallback as my only environment because it's pretty close to the old style I loved.

I removed unity once and had 12.04 with gnome-shell only (and some leftovers from unity dependencies the system needed) which worked very well until I screwed it up. Fool around with new environments man, it took me a while, but I learned to move on as the new releases did.

You don't really have a choice, actually.

---


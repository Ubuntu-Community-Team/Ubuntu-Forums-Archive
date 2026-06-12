---
title: "Downloaded a sound theme and placed it in the right directory but can switch to it"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by HunterDX77M on 2011-12-24
I just downloaded a sound theme and placed it in /usr/share/sounds, but it looks like there is no way to switch to it in the audio settings. There used to be a way to do this via GUI in Natty, right?

---

### Post by HunterDX77M on 2012-01-02
Thread bump.

---

### Post by HunterDX77M on 2012-01-25
bump

---

### Post by HunterDX77M on 2012-01-30
bump

---

### Post by HunterDX77M on 2012-02-19
And two weeks later . . .

bump

---

### Post by stinkeye on 2012-02-19
In the terminal run...
```
gsettings set org.gnome.desktop.sound theme-name '[COLOR="Magenta"]Name of Theme[/COLOR]'
```
[COLOR="magenta"]Use your sound theme name[/COLOR]

eg I installed a theme called **Fresh and Clean**
So the command to change to this sound theme is
```
gsettings set org.gnome.desktop.sound theme-name 'Fresh and Clean'
```


To revert back to default
```
gsettings reset org.gnome.desktop.sound theme-name
```

---


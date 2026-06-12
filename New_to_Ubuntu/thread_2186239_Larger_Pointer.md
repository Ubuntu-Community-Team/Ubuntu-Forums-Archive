---
title: "Larger Pointer"
date: 2013-11-06
forum: New to Ubuntu
---

### Post by Cycledoc on 2013-11-06
On Ubuntu 13.10.  One of my frustrations with Ubuntu is the difficulty one has in having a larger mouse pointer.  I've seen a number of tutorials and suggestions on the internet most applying to older distributions but can't seem to find simple, easy directions (a few clicks) to get a more visibile pointer....I have some visual issues.

I'd appreciate directions to help me with this.  I've tried the system settings larger pointer route and it only works on application screens, not on the desktop.  Similarly, the deconf editor fix has the same effect.  

Many thanks.

---

### Post by stinkeye on 2013-11-06
You need to do 2 things....

**1) _Change the dconf setting**_ (this is what the various tweak tools do)
```
gsettings set org.gnome.desktop.interface cursor-size [COLOR="#EE82EE"]**xx**[/COLOR]
```

**2) _Create/edit ~/.Xresources**_
```
gedit ~/.Xresources
```
and edit/add the line with the same value you used in dconf....
```
Xcursor.size:[COLOR="#EE82EE"]**xx**[/COLOR]
```


For [COLOR="#EE82EE"]**xx**[/COLOR] use [COLOR="#EE82EE"]24[/COLOR], [COLOR="#EE82EE"]32[/COLOR] or [COLOR="#EE82EE"]48[/COLOR]
[COLOR="#EE82EE"]24[/COLOR] is the default size.

Log out/in.

This works with the default DMZ themes as they are made with scalable formats of 24, 32 and 48.

---

### Post by Cycledoc on 2013-11-06
Bingo.  Thanks for the clear concise instructions!

---


---
title: "Manually change colors of text, highlight etc?"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by Niemil on 2013-11-23
I don't know how and why. But for some reason it seems like many things have changed since I have kind of changed gnome theme or something else, not sure what have changed the things.

I am using Ubuntu 13.10 with Gnome 3.8 (I think it is).

When I first installed Ubuntu here, the highlights in webbrowser (firefox and chrome, that I am using, mostly chrome though) were orange color.
Now I have noticed that the highlight color are blue.

Also I now when writing this post, I notice the font aren't the same as it used to be I think.


I just wonder how I can change those stuffs, the default highlight colors, fonts, color of fonts etc, if that is possible?
I just went on tweak tool and checking, but I seem only be able to change the font type in the OS/gnome shell, but not this text that I'm typing on this post.
Nor I seem to be able to change the font color or anything else.

---

### Post by stinkeye on 2013-11-23
Try GTK Theme Preferences for some colour customization.
```
sudo add-apt-repository ppa:shimmerproject/ppa
sudo apt-get update
sudo apt-get install gtk-theme-config
```

******No saucy package. In my **saucy** install I just downloaded and installed the latest raring deb
[https://launchpad.net/~shimmerproject/+archive/ppa/+sourcepub/3354264/+listing-archive-extra](https://launchpad.net/~shimmerproject/+archive/ppa/+sourcepub/3354264/+listing-archive-extra)

---

### Post by vasa1 on 2013-11-23
Another light solution is "lxappearance".

---


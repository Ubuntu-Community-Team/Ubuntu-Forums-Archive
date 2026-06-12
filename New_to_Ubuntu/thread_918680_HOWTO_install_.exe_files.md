---
title: "HOWTO install *.exe files"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Dadsgé on 2008-09-13
hellow,

I tried to install my DivX player I usually use on my windows system
but it looks like ubuntu doesn't recognize *.exe files

how can I solve my problem?

mvg
Dadsgé

---

### Post by ajmorris on 2008-09-13
> **Dadsgé said:**
> hellow,

I tried to install my DivX player I usually use on my windows system
but it looks like ubuntu doesn't recognize *.exe files

how can I solve my problem?

mvg
Dadsgé

to install that, you can use a program called 'wine' which can be installed from your synaptic package manager from the menus (System --> Administration --> Synaptic package manager (or something like that))

However, you dont need this for a multimedia application. You might like to try out VLC (there are many more that you can use), go to synaptic, and install vlc, you will also need some codecs, but vlc should come up and alert you that you need them, if you try to play a movie/music that needs them :)

AJ

---

### Post by RuleMaker on 2008-09-13
You have to install "wine".
In terminal type:
```
sudo aptitude install wine
```

---

### Post by iaculallad on 2008-09-13
> **Dadsgé said:**
> hellow,

I tried to install my DivX player I usually use on my windows system
but it looks like ubuntu doesn't recognize *.exe files

how can I solve my problem?

mvg
Dadsgé

You could install it using WinE but it seems that [DivX player]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=2289") just won't run on emulator in Ubuntu. Better yet, try installing the restricted codecs if it would support divx format.

---

### Post by Dadsgé on 2008-09-13
i think I ll just try to use that vlc where ajmorris was talking about, cause i already seem to have some problems where to install
so if i just install the vlc with synaptic it should be ok?

---

### Post by 3rdalbum on 2008-09-13
Linux doesn't run Windows applications, just as Windows doesn't run Linux applications.

If you haven't already, you can enable DivX playback in Linux video playing software (like Totem, VLC and Mplayer) by installing the package "ubuntu-restricted-extras" from the Synaptic Package Manager.

---

### Post by insane_alien on 2008-09-13
totem has no trouble playing divX movies when the appropriate codecs are installed(and it will install them for you assuming you have the extra repositories enabled.

---

### Post by ajmorris on 2008-09-13
> **Dadsgé said:**
> i think I ll just try to use that vlc where ajmorris was talking about, cause i already seem to have some problems where to install
so if i just install the vlc with synaptic it should be ok?

It will work fine to play your divX movies, and should pop up with a box with what codecs it wants to install when you try to play the movie, but if it doenst, and it just says you need codecs, try this guide:
[https://wiki.ubuntu.com/RestrictedCodecs](https://wiki.ubuntu.com/RestrictedCodecs)

AJ

---

### Post by Dadsgé on 2008-09-13
thnx everyone, 
i think im just gonna run vlc
just because i dont really understand the language used in the terminal
maby ill try to install divX later ;)

---

### Post by ooobuntooo on 2008-09-13
> **3rdalbum said:**
> Linux doesn't run Windows applications, just as Windows doesn't run Linux applications.

If you haven't already, you can enable DivX playback in Linux video playing software (like Totem, VLC and Mplayer) by installing the package "ubuntu-restricted-extras" from the Synaptic Package Manager.

Linux does run Windows applications with WINE.

---

### Post by Nepherte on 2008-09-13
True, though it is better to use alternatives that do work in linux. If people would only use wine to run their exe files, I think they're better off with windows. Again, it's possible with wine but I'd only use it as a last resort.

---


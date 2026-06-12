---
title: "[SOLVED] Xine media Codecs"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Syndacate on 2008-07-01
Hey,

I just installed Hardy (fresh formatted from Gutsy) and was trying to get all the media codecs installed - I thought I did but then I realized some files didn't play, played glitchy, or played with no sound.  

I followed a link after a google search and thought I had every codec I need, I use Kaffeine (and have the KDE Xine backing w/ all the libraries), like 95% of my stuff plays, some stuff doesn't, but works fine on windows and mac.  I think I'm missing a codec some place, can anybody link me to a site that lists all the ones you need to pretty much play anything?  It all worked fine in gutsy, and I thought I had 'em all installed :confused:.

---

### Post by sayakb on 2008-07-01
Try out VLC:
```
sudo apt-get install vlc
```
Also, install xine extras for kaffeine.

---

### Post by Syndacate on 2008-07-01
> **LinuxIsInnovation said:**
> Try out VLC:
```
sudo apt-get install vlc
```
Also, install xine extras for kaffeine.

I have VLC already and tried it - it's the one I was referring to that was giving me the video but no sound.

Xine extras isn't a package name  per-se, and I did try "xine-extras" and "xine" but neither worked - but I did some searching around based on that.

removed unneeded packages:

```
sudo apt-get autoremove
```

Then installed Ubuntu and Kubuntu extras (I use both libs as I use a lot of KDE apps on Ubuntu)

```
sudo apt-get install ubuntu-restricted-extras
```

and

```
sudo apt-get install kubuntu-restricted-extras
```

Somewhere between the two new packages and removing the unneeded ones (it could have been a codec conflict) it worked fine with what it wasn't working with before.

Thanks for the help.

---


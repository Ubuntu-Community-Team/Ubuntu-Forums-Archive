---
title: "Playing ogg file"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by vhadiant on 2008-06-12
Hi,

New here. I'm having problem playing Ogg files, at least I *think* they are encoded on Ogg. How do I find out for sure? I have some other Ogg files and they play OK while others have only sound output.

I've installed the restricted package, which from what I understand should install the Ogg codec.

Also Totem seems to be having a hard time playing some of my other video files. Is there a better media player that most people use here?

Cheers,

---

### Post by Vivaldi Gloria on 2008-06-12
> **vhadiant said:**
> Is there a better media player that most people use here?

vlc, gnome-mplayer, gxine are much better.

> **vhadiant said:**
> I *think* they are encoded on Ogg. How do I find out for sure? 

To get more info about your.video.file try the followings in the terminal:

```
ffmpeg -i /location.of.the.file/your.video.file
```

or 

```
file /location.of.the.file/your.video.file
```

---

### Post by Grishka on 2008-06-12
VLC seems to work best, and it uses it's own codecs, but if you want to use Totem or alike, installing ubuntu-restricted-extras will put necessary, restricted codecs on your system.

---

### Post by kdcoetzee on 2008-06-12
Exaile and Amarok

I prefer Amarok because the equalizer is better. but Amarok is KDE.
and Exaile is a gnome but the equalizer does not match Amarok's.

---

### Post by Grishka on 2008-06-12
> **Juggernaut_KDC said:**
> Exaile and Amarok

I prefer Amarok because the equalizer is better. but Amarok is KDE.
and Exaile is a gnome but the equalizer does not match Amarok's.

man, he's talking about movies. ;)

---

### Post by kdcoetzee on 2008-06-12
> **Grishka said:**
> man, he's talking about movies. ;)

Sorry My Mistake...
Then i would use mplayer.

---

### Post by billgoldberg on 2008-06-12
Totem (movie player) shouldn't have problems playing ogg files.

Click on "media" in my signature to install the medibuntu repo.

Then install the following packages

ubuntu-restricted-extras

non-free-codecs

libdvdcss2

you could replace the last two packages by installing vlc (after adding the medibuntu repo) but remember that you'll need some of those to play divx files on the internet, and other formats as well.

---

### Post by vhadiant on 2008-06-12
OK. VLC seems to play all my Ogg files. Odd that Totem can't do it.

I followed your instruction here:

[http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/](http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/)

But it fails while installing xmms-wma. It says:
The following packages have unmet dependencies.
  xmms-wma: Depends: xmms (>= 1.2.10+20070501) but it is not installable
E: Broken packages

When I tried to install xmms on its own:
Package xmms is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xmms has no installation candidate

---


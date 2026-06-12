---
title: "my totem doesn't play DVD"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by superwoman.t.squared on 2008-04-30
it says no proper plugins, and then I tried download some codex. but still doesn't work
please help

---

### Post by FleetAdmiral74 on 2008-04-30
From what I remember, VLC handles DVD's nicely out of the box. 

That being said, you *should* be able to do the same in Totem, with the right codecs.

---

### Post by Tatty on 2008-04-30
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This guide will set you up to play almost any type of multimedia you might encounter.

---

### Post by piratesmack on 2008-04-30
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by superwoman.t.squared on 2008-04-30
I used to use VLC for windows but I don't know how to install for ubuntu

---

### Post by AndThenWhat on 2008-04-30
this is a really straightforward tutorial that should help you:

[http://www.vimeo.com/372538]("http://www.vimeo.com/372538")

---

### Post by Tatty on 2008-04-30
To install VLC, open a terminal then:

```
sudo apt-get install vlc
```

or if you want to do it the GUI way then Applications->Add/Remove

---

### Post by piratesmack on 2008-04-30
> **FleetAdmiral74 said:**
> From what I remember, VLC handles DVD's nicely out of the box. 

That being said, you *should* be able to do the same in Totem, with the right codecs.


VLC won't play dvd's in Linux unless you install libdvdcss with this tutorial:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

The steps for Gutsy work on Hardy as well

---

### Post by SunnyRabbiera on 2008-04-30
as for installing extra apps in ubuntu read this:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by superwoman.t.squared on 2008-04-30
thanks. my flash player doesn't work either so I can't really see the tutorial. but i suppose I can jsut copy and past the codes?

---

### Post by superwoman.t.squared on 2008-04-30
will i be able to search libdvdcss from package manager?

---

### Post by piratesmack on 2008-04-30
> **superwoman.t.squared said:**
> will i be able to search libdvdcss from package manager?

No, to install it
 
-Go to Applications>Accessories>Terminal
-Then copy and paste this:
```

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

```
-Press enter and type in your password
-After that has finished, copy and paste this
```

sudo /usr/share/doc/libdvdread3/install-css.sh

```

After that, dvds should play fine

---

### Post by superwoman.t.squared on 2008-04-30
oh it worked! 
thank you so much
but I don't think Totem can play DVD from playlist

---

### Post by superwoman.t.squared on 2008-04-30
> **piratesmack said:**
> No, to install it
 
-Go to Applications>Accessories>Terminal
-Then copy and paste this:
```

sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot

```
-Press enter and type in your password
-After that has finished, copy and paste this
```

sudo /usr/share/doc/libdvdread3/install-css.sh

```

After that, dvds should play fine

thanks thanks!!

---

### Post by piratesmack on 2008-04-30
> **superwoman.t.squared said:**
> oh it worked! 
thank you so much
but I don't think Totem can play DVD from playlist

yeah I'm not sure, I usually use VLC

---


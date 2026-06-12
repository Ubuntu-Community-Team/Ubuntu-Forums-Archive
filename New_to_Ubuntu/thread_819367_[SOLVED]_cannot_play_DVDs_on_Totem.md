---
title: "[SOLVED] cannot play DVDs on Totem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by al.adab on 2008-06-05
hello,

I've just switched to Hardy Heron 8.04 and I'm really impressed. It works very well. Excellent job!

One minor trouble: I can't play DVDs (original copies) on Totem Media Player. Totem opens automatically when I insert a DVD, and if I click on Movie>Play Disk, all I get is the "Warning: License for private home viewing only...etc". If I go to Go>DVD menu, nothing happens. It used to work on Gutsy 7.10...

I can play DVDs with VLC Media Player, though, and that's fine. I'm wondering what I should do to have them work on Totem as well...or to have VLC start automatically if I insert a DVD...

Thanks.

---

### Post by freduardo on 2008-06-05
I'm not sure what to do about the totem issue. But maybe someone else does.

In the mean time, if you want vlc to play DVD's automatically you'll need to edit the /etc/gnome/defaults.list as root.

So fire up a terminal and issue:
```
gksudo gedit /etc/gnome/defaults.list
```

Then replace this line:
```
x-content/video-dvd=totem.desktop
```

With:
```
x-content/video-dvd=vlc.desktop
```

Save and exit.

That should do it.

---

### Post by Raval on 2008-06-05
> **al.adab said:**
> hello,

I've just switched to Hardy Heron 8.04 and I'm really impressed. It works very well. Excellent job!

One minor trouble: I can't play DVDs (original copies) on Totem Media Player. Totem opens automatically when I insert a DVD, and if I click on Movie>Play Disk, all I get is the "Warning: License for private home viewing only...etc". If I go to Go>DVD menu, nothing happens. It used to work on Gutsy 7.10...

I can play DVDs with VLC Media Player, though, and that's fine. I'm wondering what I should do to have them work on Totem as well...or to have VLC start automatically if I insert a DVD...

Thanks.

The issue is the codecs. See, Ubuntu and Linux are pro-open source software and thus support open media formats.

You can play home made DVDs as is but to play commerical DVDs you'll have to d/l the codecs for it. 

go to add/remove and search for the Ubuntu restricted extras and install it. It also contains the codec for MP3s.

---

### Post by Otto-C on 2008-06-05
Go here

[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)

In item 2 use this line

    sudo apt-get install ubuntu-restricted-extras

and continue with your choices.

hth
otto-c

---

### Post by billgoldberg on 2008-06-05
> **Otto-C said:**
> Go here

[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)

In item 2 use this line

    sudo apt-get install ubuntu-restricted-extras

and continue with your choices.

hth
otto-c

restricted extras won't play most commercial dvds

take a look at the "media and ubuntu" link in my sig

---

### Post by wolfen69 on 2008-06-05
> **al.adab said:**
> hello,

I've just switched to Hardy Heron 8.04 and I'm really impressed. It works very well. Excellent job!

One minor trouble: I can't play DVDs (original copies) on Totem Media Player. Totem opens automatically when I insert a DVD, and if I click on Movie>Play Disk, all I get is the "Warning: License for private home viewing only...etc". If I go to Go>DVD menu, nothing happens. It used to work on Gutsy 7.10...

I can play DVDs with VLC Media Player, though, and that's fine. I'm wondering what I should do to have them work on Totem as well...or to have VLC start automatically if I insert a DVD...

Thanks.

just one of the few reasons i uninstall totem first thing after a fresh install.

---

### Post by kaibob on 2008-06-05
> **al.adab said:**
> <snip>I can play DVDs with VLC Media Player, though, and that's fine. I'm wondering what I should do to have them work on Totem as well...<snip>

I am by no means an expert on this, but after a clean install of Hardy I installed Totem xine and libdvdcss2 from the Medibuntu repo's, and commercial movies play just fine. I did look at the more inclusive codec packages, but I didn't want to install a bunch of stuff I never use.

---

### Post by al.adab on 2008-06-06
thanks freduardo I'm now happily using VLC. All video formats work (possibly this means that I've downloaded all the required codecs, etc?). Totem won't play any format though (?). SOLVED?

---

### Post by billgoldberg on 2008-06-06
> **al.adab said:**
> thanks freduardo I'm now happily using VLC. All video formats work (possibly this means that I've downloaded all the required codecs, etc?). Totem won't play any format though (?). SOLVED?

In the link from my signature "media and ubuntu"

after installing the medibuntu repo give this command:

```
sudo apt-get install -y ubuntu-restricted-extras non-free-codecs livdvdcss
```

that should make totem play the dvd's

That being said, vlc is better.

---

### Post by Raval on 2008-06-07
> **wolfen69 said:**
> just one of the few reasons i uninstall totem first thing after a fresh install.

Every time I do a fresh install one of the first things I do is use the remove standard Totem and use the mplayer backend.

---


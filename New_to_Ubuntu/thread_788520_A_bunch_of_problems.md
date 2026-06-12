---
title: "A bunch of problems"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by LemanRuss on 2008-05-09
No Sound on flash plugins:
I have no sound on youtube, myspace etc. Anything using flash. I have the shockwave flash plugin for firefox.

No adobe acrobat.
I updated my repositories and ran:
sudo apt-get install acroread mozilla-acroread acroread-plugins

but it just gives me the error:
The following packages have unmet dependencies:
  acroread: Depends: libldap2 but it is not installable
E: Broken packages

Problems with dvd and .vobs:
I followed directions here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
And now I can watch dvds, however I can't go through the menus and what not, so seeing special features or putting on subtitles is impossible. When I put in the dvd it just plays the movie.

.vob files don't work at all, they are all garbled and terrible looking, as if I was trying to watch a dvd that was all scratched. In windows I could open a .vob with the default dvd player app and it would treat the .vob just like a dvd. Is there any way to do that?

---

### Post by HotShotDJ on 2008-05-09
[LIST=1]
[*]Install flashplugin-nonfree -- if you've already done that, I'm not sure what the problem might be
[*]You need to use the medibuntu repository. Follow the howto at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[*]Install vlc.  For some reason, totem doesn't seem to like DVD Menus
[*]See #3
[/LIST]

---

### Post by LemanRuss on 2008-05-09
> **HotShotDJ said:**
> [LIST=1]
[*]Install flashplugin-nonfree -- if you've already done that, I'm not sure what the problem might be
[*]You need to use the medibuntu repository. Follow the howto at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[*]Install vlc.  For some reason, totem doesn't seem to like DVD Menus
[*]See #3
[/LIST]

I already activated the medibuntu repository. I still get that error.

I already tried to install vlc, it doesn't show up anywhere though so I don't know how to start it. Could I get a terminal command or something in order to access it? And as a more general question where do all of the apps I install go. Is there an equivelent of c/my programs in ubuntu?

also installing flashplugin-non free gets: flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by HotShotDJ on 2008-05-09
> **LemanRuss said:**
> I already activated the medibuntu repository. I still get that error.Thats odd.  On my system, simply installing acroread (and associated plugins) using Synaptic got it up and running with no errors or fuss.  I can't imagine why your getting that error.  Hopefully somebody will happen upon this thread that has some insight into this problem.
> **LemanRuss said:**
> I already tried to install vlc, it doesn't show up anywhere though so I don't know how to start it. Could I get a terminal command or something in order to access it? And as a more general question where do all of the apps I install go. Is there an equivelent of c/my programs in ubuntu?vlc should be under Applications --> Sound & Video --> VLC media player.  If not, you can open a terminal (Applications --> Accessories -- Terminal) and type "vlc" (without the quotes, of course).  I don't know what you mean by c/my programs.  HotShotDJ is to Windows as LemanRuss is to Linux:)

> **LemanRuss said:**
> also installing flashplugin-non free gets: flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.My guess is a problem in your sound subsystem.  However, I don't have any clue what that problem might be.  Again, perhaps somebody with some insight into this problem will happen upon this thread.

I'm sorry that I wasn't as helpful as I thought I would be when I first answered you.

---

### Post by asrai on 2008-05-09
Have you installed libflashsupport? If you don't have this installed on Hardy then you will likely have problems with sound in flash.

There is an excellent and comprehensive how-to here: [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683") that should help you. Go through from the beginning and you should be able to get everything working perfectly, post back if not.

---

### Post by JoshuaRL on 2008-05-09
> **LemanRuss said:**
> No Sound on flash plugins:
I have no sound on youtube, myspace etc. Anything using flash. I have the shockwave flash plugin for firefox.

No adobe acrobat.
I updated my repositories and ran:
sudo apt-get install acroread mozilla-acroread acroread-plugins

but it just gives me the error:
The following packages have unmet dependencies:
  acroread: Depends: libldap2 but it is not installable
E: Broken packages

Problems with dvd and .vobs:
I followed directions here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
And now I can watch dvds, however I can't go through the menus and what not, so seeing special features or putting on subtitles is impossible. When I put in the dvd it just plays the movie.

.vob files don't work at all, they are all garbled and terrible looking, as if I was trying to watch a dvd that was all scratched. In windows I could open a .vob with the default dvd player app and it would treat the .vob just like a dvd. Is there any way to do that?


I think that most of your problems come from the "E:  Broken packages" issue.  Try the following commands from the terminal, they should fix any broken packages and dependencies:
```

sudo dpkg --configure -a
sudo apt-get clean --fix

```

---

### Post by LemanRuss on 2008-05-10
That seems to have worked pretty well, thanks.

---

### Post by billgoldberg on 2008-05-10
> **LemanRuss said:**
> No Sound on flash plugins:
I have no sound on youtube, myspace etc. Anything using flash. I have the shockwave flash plugin for firefox.

No adobe acrobat.
I updated my repositories and ran:
sudo apt-get install acroread mozilla-acroread acroread-plugins

but it just gives me the error:
The following packages have unmet dependencies:
  acroread: Depends: libldap2 but it is not installable
E: Broken packages

Problems with dvd and .vobs:
I followed directions here: [http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)
And now I can watch dvds, however I can't go through the menus and what not, so seeing special features or putting on subtitles is impossible. When I put in the dvd it just plays the movie.

.vob files don't work at all, they are all garbled and terrible looking, as if I was trying to watch a dvd that was all scratched. In windows I could open a .vob with the default dvd player app and it would treat the .vob just like a dvd. Is there any way to do that?

1. install libflashsupport".
2. acroread is in the medibuntu repos. Click [here]("http://linuxowns.wordpress.com/2008/02/11/media-and-ubuntu/") to see how to install it.

3. After you installed the medibuntu repo, install vlc. Subtitles won't be a prob, nor would opening .vob files.

---


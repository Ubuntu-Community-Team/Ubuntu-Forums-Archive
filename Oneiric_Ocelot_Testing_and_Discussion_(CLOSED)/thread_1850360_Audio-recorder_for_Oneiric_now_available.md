---
title: "Audio-recorder for Oneiric now available"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by moma on 2011-09-26
Hello,
I just want to inform you that "audio-recorder" has now been ported to GTK+3 libraries.

[[img]http://bildr.no/thumb/984014.jpeg[/img]](http://bildr.no/view/984014)

Audio-recorder v0.6 is available for Oneiric from
[https://launchpad.net/~osmoma/+archive/audio-recorder](https://launchpad.net/~osmoma/+archive/audio-recorder)

Notice: This [GTK+3]("http://developer.gnome.org/gtk3/stable/") based version is only available for Oneiric. There are no 0.6 package for Natty or Maverick.

Of course, I need to monitor all changes that go to Oneiric before its final release. Especially I want to get rid of "libgconf2-dev" package. The "libgnome-media-profiles-3.0" package sees to depend on gconf-2.0 even this latter is not installed automatically.
Ref: [https://bugs.launchpad.net/ubuntu/+source/libgnome-media-profiles/+bug/856508](https://bugs.launchpad.net/ubuntu/+source/libgnome-media-profiles/+bug/856508)

Audio-recorder uses now GSettings (and dconf) instead of the older GConf2.
Start dconf-editor to see the settings in /apps/audio-recorder/.

Really cool features in [GTK 3.2]("http://www.h-online.com/open/news/item/GTK-3-2-with-support-for-Wayland-and-HTML5-1350113.html").

---

### Post by arm-c on 2011-09-28
I realize I should have posted here.

So far, I have not installed your software, although it is high on my list and a feature I have been looking forward to.

I am thinking that it would be nice if your application were to be grafted into the Sound Menu of Ubuntu.  I think it makes a perfect fit and reduces the number of icons in the AppIndicator tray while simultaneously being in a logical location for access.

Just some thoughts.

Warm regards,
ARM-C

---

### Post by moma on 2011-10-02
Hello,
The sound menu integration needs some development work so completing this idea may take time. Anyway it would be cool to get this audio-recorder (and even GNOME's own  
[gnome-sound-recorder]("http://www.bomahy.nl/hylke/blog/gnome-voice-recorder/") :o) to the sound menu. Very good idea Arm-c.

Please read also the responses to this on askubuntu.com:
[http://askubuntu.com/questions/63705/can-i-add-audio-recorder-to-the-sound-menu](http://askubuntu.com/questions/63705/can-i-add-audio-recorder-to-the-sound-menu)

---


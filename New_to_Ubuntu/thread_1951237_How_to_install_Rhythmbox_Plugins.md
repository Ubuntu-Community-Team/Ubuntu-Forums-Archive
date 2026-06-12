---
title: "How to install Rhythmbox Plugins"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by cbennett926 on 2012-04-02
Hello,

I have tried and tried and cannot find a way to add plugins to Rhythmbox. I added them to the .gnome2/Rhytmbox/plugins, and still they will not show up. I went through multiple tutorials and no dice, can someone please help me with a step by step solution? 

This is one of the plugins:
[http://cornerofseven.com/blog/2009/04/rhythmbox-eq/](http://cornerofseven.com/blog/2009/04/rhythmbox-eq/)

and here is the other:
[http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html#comment-140743484](http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html#comment-140743484)

---

### Post by santosh83 on 2012-04-02
> **cbennett926 said:**
> Hello,

I have tried and tried and cannot find a way to add plugins to Rhythmbox. I added them to the .gnome2/Rhytmbox/plugins, and still they will not show up. I went through multiple tutorials and no dice, can someone please help me with a step by step solution? 

This is one of the plugins:
[http://cornerofseven.com/blog/2009/04/rhythmbox-eq/](http://cornerofseven.com/blog/2009/04/rhythmbox-eq/)

and here is the other:
[http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html#comment-140743484](http://www.webupd8.org/2011/01/pandora-plugin-for-rhythmbox.html#comment-140743484)

Did you look at these two threads?
[http://ubuntuforums.org/showthread.php?t=1219423](http://ubuntuforums.org/showthread.php?t=1219423)
[http://ubuntuforums.org/showthread.php?t=1482936](http://ubuntuforums.org/showthread.php?t=1482936)

---

### Post by cbennett926 on 2012-04-02
Indeed I have, and I have done both of those, to no such luck :(

---

### Post by santosh83 on 2012-04-02
> **cbennett926 said:**
> Indeed I have, and I have done both of those, to no such luck :(

Since I don't use Rhythmbox, I don't know what else to suggest to you! Did you have a look at this page as well, especially the section titled 'What makes up a plugin.' The developers give a list of directories where Rhythmbox searches for the plugin apparently, and $HOME/.local/share/rhythmbox/plugins is different from .gnome/...

here's the link [https://live.gnome.org/RhythmboxPlugins/WritingGuide](https://live.gnome.org/RhythmboxPlugins/WritingGuide)

---

### Post by cbennett926 on 2012-04-02
Yes I did :/ looks like it's time to go back to banshee till 12.04 haha

---

### Post by Frogs Hair on 2012-04-02
Both links in the first post are outdated . The first is for Gnome 2 and the second is for Rhythmbox 0.13.2 and the current version 2.90 .1 . 

If you would like a system wide EQ you can try the following . 

Source: [http://www.ubuntuupdates.org/package/webupd8/oneiric/main/base/pulseaudio-equalizer](http://www.ubuntuupdates.org/package/webupd8/oneiric/main/base/pulseaudio-equalizer)

---

### Post by cbennett926 on 2012-04-02
> **Frogs Hair said:**
> Both links in the first post are outdated . The first is for Gnome 2 and the second is for Rhythmbox 0.13.2 and the current version 2.90 .1 . 

If you would like a system wide EQ you can try the following . 

Source: [http://www.ubuntuupdates.org/package/webupd8/oneiric/main/base/pulseaudio-equalizer](http://www.ubuntuupdates.org/package/webupd8/oneiric/main/base/pulseaudio-equalizer)


Oh wow! Thank you, however I forgot how awesome Banshee is haha

---

### Post by Frogs Hair on 2012-04-02
> **cbennett926 said:**
> Oh wow! Thank you, however I forgot how awesome Banshee is haha

The equalizer will work regardless of media player because it is system wide .

---

### Post by Nikola.srb on 2012-04-16
I would still like to get some neat plugins for Rhythmbox that I had in version 0.13, like Desktop Art, Jump to file, and such.

Is there a way to import and enable these plugins in new version of Rhythmbox (2.95) on Gnome3?
And when did Rhythmbox jumped to such high version, years have passed on 0.12-0.13 it seams, and now it's almost v3? :D

---

### Post by BoogeyOfTheMan on 2012-07-12
I am also interested in this. I just upgraded to 12.04 from 11.04 and am just trying to get the functionality I used to have back.

While the system wide EQ is cool, I use Rhythmbox for music, Clementine for audiobooks, and Totem for video. The main reason I started using Clementine for audiobooks is because I got tired of resetting the EQ in Rhythmbox every time i switched from music to books.

---

### Post by davidmohammed on 2012-07-16
this thread seems to be jumping between different versions of rhythmbox...

However for the immediate reply above - there is an equalizer plugin for rhythmbox 2.9x you can install from [github]("https://github.com/luqmana/rhythmbox-plugins")

Alternatively if you are using 12.04 - I've packaged this in my [PPA]("https://launchpad.net/~fossfreedom/+archive/rhythmbox-plugins").  I've also written this up in a [Q&A format]("http://askubuntu.com/questions/147942/how-do-i-install-third-party-rhythmbox-plugins") if you want a guide to install.

Hope this helps.

---

### Post by BoogeyOfTheMan on 2012-07-16
Thank you sir, thats exactly what I was looking for :)

---


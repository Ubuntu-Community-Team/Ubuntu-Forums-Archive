---
title: "Fonts Almost Exactly Like Mac"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by Danny_Michel on 2013-10-22
I've got my fonts almost looking/rendering exactly how they do on my Mac, but the fonts on Mac are just ever so slightly vertically taller. Is there some way I can achieve this on Ubuntu?

---

### Post by Baldrick_NZ on 2013-10-22
> **Danny_Michel said:**
> I've got my fonts almost looking/rendering exactly how they do on my Mac, but the fonts on Mac are just ever so slightly vertically taller. Is there some way I can achieve this on Ubuntu?

Sure. Let MacBuntu be your friend...
[http://www.noobslab.com/2013/05/mac-os-x-theme-for-ubuntu-1304-raring.html](http://www.noobslab.com/2013/05/mac-os-x-theme-for-ubuntu-1304-raring.html)

...depending on which version (and DE) of Ubuntu you're using.

Have fun!

---

### Post by Danny_Michel on 2013-10-22
But i dont want a mac theme. I'm interested in emulating the OS X font rendering.

---

### Post by czgirb on 2013-10-22
> **Danny_Michel said:**
> But i dont want a mac theme. I'm interested in emulating the OS X font rendering.

Please try this [http://www.webupd8.org/2010/06/how-to-install-apple-mac-osx-fonts-in.html](http://www.webupd8.org/2010/06/how-to-install-apple-mac-osx-fonts-in.html)
Or you can try g**gling for ... **Ubuntu Mac Default Font**

---

### Post by Danny_Michel on 2013-10-22
Thanks, but those are just the actual fonts to install. What I'm referring to is the rendering of all fonts rather than how to get Mac specific fonts.

---

### Post by coffeecat on 2013-10-22
@Danny_Michel, I've not tried this myself but this may be what you want:

[http://www.webupd8.org/2013/06/better-font-rendering-in-linux-with.html](http://www.webupd8.org/2013/06/better-font-rendering-in-linux-with.html)

I see there's a setting to emulate OSX font rendering.

---

### Post by buzzingrobot on 2013-10-22
> **coffeecat said:**
> @Danny_Michel, I've not tried this myself but this may be what you want:

[http://www.webupd8.org/2013/06/better-font-rendering-in-linux-with.html](http://www.webupd8.org/2013/06/better-font-rendering-in-linux-with.html)

I see there's a setting to emulate OSX font rendering.

This is a link to a good tutorial on installing and configuring, and backing out, the Infinality toolset.  It's worth a try.

Infinality consists of freetype patches and a very configurable fontconfig system, originally developed for Fedora.  Some, but not all, of the patches have been incorporated in freetype.

Infinality *will* change the appearance of fonts, and a knowledgable person can tweak things in a very finen-grained manner.  

Whether or not you like the results is up to you. Its approach is different than the Ubuntu approach.  I'd say the results are equally good, just different.

NOTE: The settings to emulate OS X, etc., require the presence of the fonts from that OS. It isn't about making, say, Droid Sans on Linux look like Helvetica on a Mac.

---

### Post by Danny_Michel on 2013-10-22
I tried that, and i used the os x and os x2 settings. Wasnt as good as what i've done manually myself. I'll try it again in-case there was something i missed.

[IMG]http://i.imgur.com/beM2Cbx.png[/IMG]

[LIST]
[*]What ive done manually was delete all the files name 'alias' in /etc/fonts/ configurations.
[*]Import all my fonts from Mac OS X and Windows
[*]Set my fonts to grayscale and no hinting.
[*]Include the following in mt ~/.fonts.conf [https://gist.github.com/dannymichel/7103077](https://gist.github.com/dannymichel/7103077)
[/LIST]

It's close, but I've noticed fonts like Helvetica on Linux are vertically shorter. I'm trying to fix that. Infinality's OS X setting wasn't close to what i've done manually.
Anybody use Infinality know how to configure it to actually look like OS X other than using 
'[COLOR=#000000][FONT=UbuntuBeta Mono]sudo bash /etc/fonts/infinality/infctl.sh setstyle' > OSX
and [/FONT][/COLOR][COLOR=#555555][FONT=Arial]USE_STYLE="DEFAULT"OSX?[/FONT][/COLOR]

---

### Post by buzzingrobot on 2013-10-22
You need to tweak the settings in /etc/profile.d/infinality-settings.sh, or create your own.  The options enabled by infctl.sh are approximations created by the developer, so they are going to vary in appearance from system to system.

The Arch wiki, I think, has info on Infinality.

---

### Post by Danny_Michel on 2013-10-22
Is there some place i can configure manually instead of with[COLOR=#000000] Infinality to make the fonts slightly taller without using hinting?[/COLOR]

---

### Post by Danny_Michel on 2013-10-23
My fontconfig setting are pretty much perfect at this point. The one and only issue is that the fonts are vertically shorter than they appear on both Mac and Windows. if i could stretch the fonts vertically every so slightly, it would be an exact match for Mac. Any ideas?

---

### Post by Danny_Michel on 2013-10-24
I've been fiddling with the Infinality setting for quite some time.
No matter what I do, the fonts render square.
Can I please pay someone to make Helvetica look exactly like this?
[IMG]http://i.imgur.com/u44Nk5Q.png[/IMG]

---

### Post by a8j8i8t8 on 2014-01-16
Hi,
Please let me know if you got this working.
Thanks.

---


---
title: "Android Development"
date: 2011-03-29
forum: Programming Talk
---

### Post by samalex on 2011-03-29
Anyone doing Android development on Ubuntu?  Last night I downloaded the Android SDK and plugins for Eclipse 3.5, but it got too late to hack out a Hello, World app.  Just curious, anyone doing Android development on Linux? Also do you guys know of any open source apps for Android I could peak into?

Thanks --

---

### Post by sanderj on 2011-03-29
Yes, a little.

First did some mini-programs in Eclipse. Then I 'downgraded' to appinventor.

FYI: the Android emulator is memory hungry. My 1GB laptop gets filled and slow when running the emulator. So: more memory recommended.

---

### Post by leg on 2011-03-29
I have been looking into Android development and using my laptop (Linux) to do so. I have 3gb RAM and this makes the emulator reasonably acceptable. Connecting a device is ten times easier than with Windows though which I haven't managed to do yet. Download the samples from within Android manager if you want to look around a working app.

---

### Post by SevenMachines on 2011-03-29
Eclipse + Android plugin is decent, but as mentioned, is memory hungry
In addition, you might want to look at running android on virtualbox (or similar). see [www.android-x86.org](www.android-x86.org), version 2.2 certainly runs fine on virtualbox here

---

### Post by samalex on 2011-03-30
> **leg said:**
> I have been looking into Android development and using my laptop (Linux) to do so. 

Looks like we're in about the same boat, except my Linux laptop has 4 Gigs of ram which should hopefully help.  The Android emulator though still took a minute or so to load, but maybe it was just that with the first boot .. not sure.

> **SevenMachines said:**
> Eclipse + Android plugin is decent, but as mentioned, is memory hungry
In addition, you might want to look at running android on virtualbox (or similar). see [www.android-x86.org](www.android-x86.org), version 2.2 certainly runs fine on virtualbox here

I didn't realize there was a port of Android that could be ran in VirtualBox, which I do use extensively.  I'll check it out..

Sam

---

### Post by forrestcupp on 2011-03-30
> **samalex said:**
> The Android emulator though still took a minute or so to load, but maybe it was just that with the first boot .. not sure.

Yeah, every time you load up the emulator, it takes forever to boot. At first, I didn't think anything was happening and I thought it didn't work at all. Then finally, I just let it sit for a long time, and the app finally appeared in the emulator. It's best to just leave the emulator window open the whole time you're working so it doesn't have to boot every time you want to test something.

The boot time is a pain, as well as not being able to test multitouch or accelerometer features in the emulator.

The one thing I hate about Android vs. iPhone is that about every Android phone has a different size screen with a different resolution.

---

### Post by shawnhcorey on 2011-03-30
> **forrestcupp said:**
> The one thing I hate about Android vs. iPhone is that about every Android phone has a different size screen with a different resolution.

Guess you're going to have to design your apps with fluid layout (aka liquid layout).

---

### Post by forrestcupp on 2011-03-30
> **shawnhcorey said:**
> Guess you're going to have to design your apps with fluid layout (aka liquid layout).

I'm not in it far enough yet to have figured that out yet. Is it hard to have a fluid layout with a full screen background image? Do they make it easy to fit an image to any size screen?

I know about all of the different view layouts in the SDK that make that stuff easy, but it seems that none of those are suitable for a game.

---

### Post by shawnhcorey on 2011-03-30
A fluid layout means the elements on the screen adjust to fit.  Each block would have a minimum width, maximum width, minimum height.  The bottom of the block would float up or down to accommodated what it contains.

It's would be hard to do a game in fluid layout unless it's a word game.  The worst ones would be those with a grid or tiles.

---

### Post by forrestcupp on 2011-03-30
> **shawnhcorey said:**
> 
It's would be hard to do a game in fluid layout unless it's a word game.  The worst ones would be those with a grid or tiles.

I know they make fluid layouts easy with all of their various types of layouts, views, and widgets. That's good for productivity apps, but I was thinking along the lines of graphic games. That's where the various screen sizes becomes a pain.

I'm sure when I get deeper into it, I'll learn the methods of dealing with that. Like, I wonder if you can just dynamically stretch your graphics to fit, or if you just have to compile a hundred different versions of your game.

---

### Post by shawnhcorey on 2011-03-30
> **forrestcupp said:**
> That's where the various screen sizes becomes a pain.

Agreed.  Since most of them are at 90 to 100 dpi, all your artworks needs to be drawn (or at least tweaked) by hand.  I would use different icons for different sets of screen sizes.  For example, I would have a set for screens from 100x100 to 124x124, one for 125x125 to 149x149 screens, etc.  Take way I can have a reasonable small set of images to manage.

---

### Post by myrtle1908 on 2011-03-30
> **shawnhcorey said:**
> Agreed.  Since most of them are at 90 to 100 dpi, all your artworks needs to be drawn (or at least tweaked) by hand.  I would use different icons for different sets of screen sizes.  For example, I would have a set for screens from 100x100 to 124x124, one for 125x125 to 149x149 screens, etc.  Take way I can have a reasonable small set of images to manage.

It's a shame SVG is not supported in the 2.2 platform.  Would be ideal here.  SVG is available in Honeycomb though ... [http://googlesystem.blogspot.com/2011/02/android-honeycombs-browser-supports-svg.html](http://googlesystem.blogspot.com/2011/02/android-honeycombs-browser-supports-svg.html)

---


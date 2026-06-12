---
title: "Installing a Linux-based SNES emulator?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by ChaosMuffins on 2008-09-30
I'm not sure if we're allowed to ask questions about emulators on this forum, but I supposed it best to in the least try. I'm attempting to install either SNES9x or ZSNES, which both have linux versions, on my computer, but the install instructions make very little sense to me. It's probably just because I've never had to do anything more than "download, extract, voila-it-works-have-fun!"

I have wine, but the windows-based emulators have laggy graphics and choppy sound, so I'm guessing that I either need to figure out the linux ones or tweak the windows ones appropriately.

Does anyone have any advice or way to make all this seem simple for someone who was *raised* using windows and has only had linux for about a week and a half? :confused::confused::confused:

Thanks in advance!

---

### Post by bumanie on 2008-09-30
Both those are available in the repositories. Go to synaptic package manager and type snes in th search window and you you will find snes and zsens in the list that appears. Mark for installation. Click apply and they should download and install.

---

### Post by ChaosMuffins on 2008-09-30
> **bumanie said:**
> Both those are available in the repositories. Go to synaptic package manager and type snes in th search window and you you will find snes and zsens in the list that appears. Mark for installation. Click apply and they should download and install.

Thank-you very much; I'll give that a try. At least I'm having fun learning everything with this. :3

---

### Post by dfreer on 2008-09-30
Nothing wrong with asking about emulators, just be aware ROM requests or links to ROM sharing sites is not allowed. Have fun with your SNES emulator!

---

### Post by ChaosMuffins on 2008-09-30
ZSNES is up and running, but...er...it has no sound. Is that normal?

---

### Post by wilsong on 2008-09-30
Some emulators might need a little adjusting settings for different sound setups, if one emulator doesnt produce sound, try another it may automatically detect what sound system your using.  Try ALSA its very typical sound driving in ubuntu. Also try running the program straight from boot, without using other audio programs and see if its working then, ive seen sometimes using one program with sound might not work well when using it with another.

---

### Post by ChaosMuffins on 2008-09-30
Multiple tries, checked to see if I have ALSA (I do), and still no sound. I think I'll give it a shot tomorrow morning and see if I'm less dead on ideas (It's six AM down here in Oklahoma... =_= )

---

### Post by dfreer on 2008-09-30
> **ChaosMuffins said:**
> ZSNES is up and running, but...er...it has no sound. Is that normal?

[http://ubuntuforums.org/showthread.php?t=851396](http://ubuntuforums.org/showthread.php?t=851396)
[http://board.zsnes.com/phpBB2/viewtopic.php?t=12091](http://board.zsnes.com/phpBB2/viewtopic.php?t=12091)
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11510](http://board.zsnes.com/phpBB2/viewtopic.php?t=11510)
[http://board.zsnes.com/phpBB2/viewtopic.php?p=168959](http://board.zsnes.com/phpBB2/viewtopic.php?p=168959)

Basically, either use a new patched version of ZSNES, or try using zsnes with -ad sdl output.

---


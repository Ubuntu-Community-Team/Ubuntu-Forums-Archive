---
title: "MIcrophone too quiet. While using headphones"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Johnnie_Walker on 2008-06-22
When I first tried to use the mic and talk via Skype I realised that the level of my headphone's microphone is too quiet and the other side barely hears me.

As you can see the Headphones are missing from the picker in the preferences. Any help will be appreciated!

---

### Post by Johnnie_Walker on 2008-06-22
In addition I will say that I tested the sound with other devices and it is still quiet. However, the same hardware works fine with Winbuzz. I hope that I will get some advice on how to set up the sound properly, because I couldn't do it the standard way.

---

### Post by Johnnie_Walker on 2008-06-24
Seems to be major problem or bug with the OS, if no one is able to help :(

---

### Post by Methuselah on 2008-06-24
I've had this problem too but I don't know if the cause is exactly teh same for you. I'll share my resolution, it shouldn't hurt.

Skype has an options to adjust your mixer levels under the options->audio menu. I'd disable that.

If that doesn't help.

In add remove applications search for pulseaudio and install all the pulseaudio tools. Go to the sound and video menu and launch the pulseaudio device chooser. Click it in the upper right panel and select volume control. On the input tab ensure it isn't muted and turn it up to the max.

Hope it helps.

---


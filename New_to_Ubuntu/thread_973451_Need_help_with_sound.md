---
title: "Need help with sound"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by bhendry on 2008-11-06
I am really at my wit's end.  I'm new to linux.  I installed ubuntu recently, went to the forums and asked what's the "best" Linux replacement for Winamp.  Amarok was highly recommended - so I installed it.  But I can't even get a peep out of it. I like it's look and feel - but as far as sound goes: nada, nichts, kein sound.

All of my files play ok in RhythmBox (lousy look though) i.e. .mp3, .wav and .pls.  

I am using the Gnome desktop under ubuntu, and my motherboard has the NVidia chipset with built-in sound card.  I've been to System -> Prefeerences -> Sound and have the proper devices selected (NVidia CK804) selected; i hear a tone when I click on 'Test'.  Also, music plays without a hitch using Totem Movie Player and RhythmBox.  Just nothing in Amarok.  

Can anyooe here H-E-L-P??  I would be in your debt . . .

Cheers!

Bob Hendry

---

### Post by Daveth on 2008-11-06
when you open Amarok, and go to Settings/Configure amarok/engine what does it say? Mine has xine as the sound system, with the output plugin on "autodetect" which seems to work best for me; putting it on pulseaudio gives me no sound. I must say the whole of the pulseaudio thing is a dark art to me.

---

### Post by GepettoBR on 2008-11-06
Just install the kubuntu-restricted-extras package and restart Amarok. Since Amarok uses the Xine backend (KDE), the codecs you installed for Gstreamer (GNOME) can't be used by it. Installing the Xine codecs will fix your problem. There is also no need to remove the ones you already have; they can coexist peacefully.

---

### Post by bhendry on 2008-11-07
Ok, OK.  I have SOUND through Amarok!

I downloaded kbuntu-kde4-desktop and installed it.  Evidently, some codecs or other needed drivers (???) were not present on my system.  The desktop is still the gnome desk top - but I haven't rebooted yet.  don't know if that will change when I reboot or not.  Don't really much care . . .

Thanks for y'all's help.  Cheers!

Bob Hendry
Clan MacNaughton

---

### Post by GepettoBR on 2008-11-07
Installing the KDE desktop may improve some functionality of Amarok, but unless there's been some change in the package recently, you'll still need the kubuntu-restricted-extras. I didn't install the kde desktop, only the extras and everything works here. But as long as your problem is solved, nothing else matters :)

---


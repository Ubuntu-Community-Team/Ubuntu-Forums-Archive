---
title: "No sound Ubuntu Intrepid ALC880"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by foxh8er on 2008-11-09
I am just beginning with ubuntu- I installed my first full copy today.
A major problem I am having is that there is absolutely no sound coming out of the headphone jack at all- it does not work with speakers, headphones, ect.
I am running a desktop without internal speakers, and I cannot find anything in the forums with a situation similar to mine.

Thanks in advance.

P.S- I am running the ALC880 controller, which worked perfectly with windows.

---

### Post by roger_1960 on 2008-11-09
Hi

Go to a terminal

applications-accesories-terminal

then type:

 alsamixer

In the GUI which appears, check that master vol and others are not set to zero.  Use the left/right arrows to move around and set volumes.  Sometimes new installs set everything to silent.

---

### Post by WelshChris on 2008-11-09
Sometimes you need to select the card that alsamixer is working with.
So try
alsamixer -c0
or alsamixer -c1

---

### Post by 73ckn797 on 2008-11-09
Double click on the speaker icon and set volume levels. Enable all options for settings in preferences once you are in volume control window. This accomplishes the same as using terminal.

---

### Post by foxh8er on 2008-11-10
Thanks for the suggestion, but I have done that already with no avail.

I am still confused, however, on the devices on that panel- should I change from the default at all?

---

### Post by JKBurton on 2008-11-10
No doing it from Gnome's volume control isn't the same right now, as there's a known bug where some sound devices don't get shown there.

The way I solved it:
sudo apt-get install gnome-alsamixer

Start playing a music file in Rhythmbox. Make sure Rhythmbox's volume isn't down or muted.

Run Applications/Sound & Video/Gnome ALSA Mixer

Checked every vertical slider, cranking them all up (the horizontal ones are L/R balance). Verify no "mute" boxes are checked. Go to the bottom section of checkboxes turning off any checkboxes that say "External Amplifier" or "Headphone". Repeat on each tab. At some point, hopefully there shall be sound.

You can do the same thing in the text-based alsamixer, but since it doesn't have tabs, it's pretty inconvenient.

Best of luck,
Keith

---

### Post by foxh8er on 2008-11-11
Thanks for the fast service:)

Unfortunately there is still no sound, even though I unmuted everything.

I feel like tearing my hair out:(:(:(

BTW-I have tried different distros on the same pc, and none of them have sound at all-they are Sabayon, PClinuxOS, and Puppy.

I hope that gives someone a clue on what is going on.

---


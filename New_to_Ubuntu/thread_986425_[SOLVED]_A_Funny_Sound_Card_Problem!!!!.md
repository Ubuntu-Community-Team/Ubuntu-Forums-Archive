---
title: "[SOLVED] A Funny Sound Card Problem!!!!"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-18
Ok so I have an intel hda880 soud card (i have heard of many problems with this sound card but none like mine)

Interestingly enough Everything works accept...

**My front inputs for mic and headphones are inverted. **

I have to plug the headphone into the mic jack to listen and the mic into the headphone jack to record.

Not That this is a huge issue. I mean I could work with this but I would like to have this switched back to normal.

Any Ideas on how to do this?

---

### Post by cwsnyder on 2008-11-18
That sounds like a hardware rather than a software problem.  The connections to the motherboard going to the front connectors are either (if it is a single connector) turned around or swapped.

---

### Post by nakama85 on 2008-11-18
> **cwsnyder said:**
> That sounds like a hardware rather than a software problem.  The connections to the motherboard going to the front connectors are either (if it is a single connector) turned around or swapped.

thats what you would think but everything works correctly in windows!
Also I just checked the connections and everything is fine.

---

### Post by cwsnyder on 2008-11-18
Okay, the input and output are not switched in Windows.  What that tells me is something in the driver for the sound system is not initializing the sound card properly.  Somehow something in the Windows driver is setting up the connections to the card differently from the way it works with the Linux driver.  Sounds like it is time to submit a bug report to [http://bugs.launchpad.net](http://bugs.launchpad.net).

---

### Post by nakama85 on 2008-11-18
> **cwsnyder said:**
> Okay, the input and output are not switched in Windows.  What that tells me is something in the driver for the sound system is not initializing the sound card properly.  Somehow something in the Windows driver is setting up the connections to the card differently from the way it works with the Linux driver.  Sounds like it is time to submit a bug report to [http://bugs.launchpad.net](http://bugs.launchpad.net).

I will do that. Do you think there is some config file that can be edited to switch the input output,?

---

### Post by nakama85 on 2008-11-18
bump

---

### Post by cwsnyder on 2008-11-19
> **nakama85 said:**
> bump
I am sorry, but I don't have a clue.  Anyone else?

---

### Post by mutesyndrome on 2008-11-20
I have the same sound card, with the same problem.
The quality comming out of the mic jack is awful compared to when I use the front headphone jack in windows.
Lol, this is the only problem I've ever experienced using ubuntu, and that's very minor.
Hopefully some has an idea of how to fix it! (Tried with OSS and same problem.)
Thanks

---

### Post by nakama85 on 2008-11-25
does anyone have a solution for this?

---

### Post by nakama85 on 2008-11-25
so i figured it out

I entered the following code into terminal
```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

and at the bottom of the page that opens I added this line
> options snd-hda-intel model=6stack

Clicked Save and then I rebooted.

The correct jack works now.

The only Problem I am having now is that when I plug in My headphones it does not automatically shut off my speakers. But it's not all that inconvenient to reach 1 1/2 feet to turn them off.

---

### Post by cwsnyder on 2008-11-26
Glad to see you solved your own problem!

---


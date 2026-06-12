---
title: "Today updates breaks OO installation (31 May)"
date: 2011-05-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by lucazade on 2011-05-31
I bet it is due to new gcc-4.6 4.6.0-10ubuntu2
Boot up ends in a BusyBox shell!

---

### Post by kansasnoob on 2011-05-31
Ditto :p

You beat me to the punch.

Things had been a bit disagreeable with me anyway since gnome-panel-3 came into the mix, so I'm just going to wait for the iso-testing build and reinstall.

---

### Post by coffeecat on 2011-05-31
Thanks for the warning! It's the end of the month and I was going to use up as much of my unused download allowance as possible. I think I'll defer. :)

---

### Post by lucazade on 2011-05-31
> **kansasnoob said:**
> Ditto :p

You beat me to the punch.

Things had been a bit disagreeable with me anyway since gnome-panel-3 came into the mix, so I'm just going to wait for the iso-testing build and reinstall.

:D

My guess was wrong it was not due to new gcc..

I've restored a previous snapshot of OO installation inside Vbox and updated again avoiding gcc stuff.. same results.. busybox!

My new bet is new udev!

---

### Post by portis on 2011-05-31
Indeed, downgrading udev brings my desktop back.

> **lucazade said:**
> :D

My guess was wrong it was not due to new gcc..

I've restored a previous snapshot of OO installation inside Vbox and updated again avoiding gcc stuff.. same results.. busybox!

My new bet is new udev!

---

### Post by PilotPaul on 2011-05-31
Just type "return" when you get the "(initramfs)" prompt and the boot will continue normally....

PP

---

### Post by novatillasku on 2011-05-31
Me too, when start open initramfs and i write "reboot" and select other kernel and start well ;-)

---

### Post by coffeecat on 2011-05-31
I managed to update after all by omitting the offered udev, but now when I get to the desktop, Nautilus opens with no buttons on the window and no global menu, Firefox has the global menu but no buttons and terminal has the old-style window bar menu - and no max-min-close buttons. :)

---

### Post by MacUntu on 2011-05-31
Udev has been trouble here since the beginning: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/787610](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/787610)

---

### Post by Quackers on 2011-05-31
I haven't rebooted yet but I have symptoms.
My mouse wil scroll down, but not up. I cannot click on some items at all - eg the close screen buttons, the cairo-dock. It's as if it doesn't realise that the pointer is there :-) That's not good!

---

### Post by coffeecat on 2011-05-31
> **Quackers said:**
> I cannot click on some items at all - eg the close screen buttons

But at least you've got close buttons, even if you can't click on them. Be grateful for small mercies. :p

---

### Post by Quackers on 2011-05-31
It got worse :-(
It became unusable, so I rebooted.
I now get 2 seconds of disc activity then nothing, then one second of disc activity then absolutely nothing. Just a black screen. No Busybox prompt. It's not getting that far :-)
But at least the run/udev error has gone :-)  along with everything else though :-(  That was my gnome-shell system. I'm now on my OO unity system, which still has dodgy rendering on the top bar, but it's working :-)

---

### Post by matt_symes on 2011-05-31
I am getting the same issue. 

However typing exit at the busybox prompt is booting into the new kernel and initramfs i installed :confused:

Also, having a look at the messages by removing quiet and splash from the kernel command line was not very informative either. It's failing after finding the hard drive (that was the last message shown) but no specific error message.

Tried rebuilding initramfs but that made no difference. It's almost like it's being told to stop at one of the scripts (although i am pretty sure that is not the issue).

---

### Post by Quackers on 2011-05-31
If it helps anyone, I just updated my OO/unity system but did not run the 
libgudev
udev
updates. I rebooted and all is well, so they do seem to be the cause.

---

### Post by Squonk07 on 2011-05-31
Wow. Dodged a bullet here. I was just about to install all those shiny, tempting, non-partial upgrade-encumbered updates, thinking, "What's the worst that could happen?"

This, apparently. I'm not sure if I'm going to just selectively update without the udev stuff, or else wait until all this blows over. I'm leaning toward the latter, unless it takes ages.

EDIT: On second thought, I'm not testing for nothing. Full steam ahead! I'll report back what happens.

---

### Post by matt_symes on 2011-05-31
> **Quackers said:**
> If it helps anyone, I just updated my OO/unity system but did not run the 
libgudev
udev
updates. I rebooted and all is well, so they do seem to be the cause.

I think you might be right about udev Quackers. I have just booted using the debug option for initramfs to get the extended error messages and it bailed out with this error message

> + echo ALERT!  /dev/disk/by-uuid/de64035e-65c8-4d1e-93eb-e46321158bdc does not exist.  Dropping to a shell!
ALERT!  /dev/disk/by-uuid/de64035e-65c8-4d1e-93eb-e46321158bdc does not exist.  Dropping to a shell!
+ REASON=ALERT!  /dev/disk/by-uuid/de64035e-65c8-4d1e-93eb-e46321158bdc does not exist.  Dropping to a shell! PS1=(initramfs)  /bin/sh -i

The ID's are correct as blkid at the busybox prompt shows them.

```

<snip>
/dev/sda13: LABEL="11.10 x32" UUID="de64035e-65c8-4d1e-93eb-e46321158bdc" TYPE="ext4" 
<snip>
```

I will do some more research on this. Maybe udev is not creating the device nodes correctly (or promptly) ?

---

### Post by Quackers on 2011-05-31
Or it's just taking no notice of them :-)

---

### Post by Squonk07 on 2011-05-31
> **PilotPaul said:**
> Just type "return" when you get the "(initramfs)" prompt and the boot will continue normally....

PP

This worked fine for me.

> **coffeecat said:**
> I managed to update after all by omitting the offered udev, but now when I get to the desktop, Nautilus opens with no buttons on the window and no global menu, Firefox has the global menu but no buttons and terminal has the old-style window bar menu - and no max-min-close buttons. :)

I have these same symptoms. In fact, I had them before this morning's batch of updates. It seems like something that was introduced in the last batch I installed, sometime either earlier this morning or late last night (of course these relative terms mean nothing on an international forum! :P).

I'll just keep updating and see if it sorts out. The first alpha is in two days; I would hope all this will be straightened out by then.

EDIT: Anyone else's Update Manager telling them that they might not be able to check for or download new updates? Networking is working (Firefox can connect to non-cached sites and it was doing this even before I downloaded and installed the latest batch of updates). Kind of nitpicky given the level of breakage at present, but I just want to see if I'm not the only one.

---

### Post by Quackers on 2011-05-31
This happened to me recently too, and it's still the same. I have to right-click and choose close for anything other than FF windows.

---

### Post by wojox on 2011-05-31
If I double click my window's top bar, it maximizes and the buttons come back.

---

### Post by Squonk07 on 2011-05-31
> **wojox said:**
> If I double click my window's top bar, it maximizes and the buttons come back.

Same here. It's amazing I didn't think to do that.

---

### Post by Quackers on 2011-05-31
Yes, once it's maximised they come back.

---

### Post by paul_in_london on 2011-05-31
I was also bitten earlier by this boot problem, but the latest **udev** updates have fixed it.

---

### Post by Quackers on 2011-05-31
Ah I see that udev 171-0ubuntu2 has appeared, and a new libgudev too :-)
I'll try them now. See if they fix my gnome-shell system too!

---

### Post by Quackers on 2011-05-31
Ok, I've run the updates in my Unity system and all went well.
The run/udev error is still there at boot but it boots up fine eventually.
Problem solved.........
except for the system refuses to shutdown now!
It closes as far as Plymouth and scrolls all the text about plugins etc etc and then sits there - no HD activity.
REISUB was my only answer.
It did the same thing on the next boot too.
Very odd.

My Gnome3 system is fixed with these updates though :-)
And that one shuts down ok.

---

### Post by paul_in_london on 2011-05-31
> **Quackers said:**
> Ok, I've run the updates in my Unity system and all went well.
The run/udev error is still there at boot but it boots up fine eventually.
Problem solved.........
except for the system refuses to shutdown now!
It closes as far as Plymouth and scrolls all the text about plugins etc etc and then sits there - no HD activity.
REISUB was my only answer.
It did the same thing on the next boot too.
Very odd.

My Gnome3 system is fixed with these updates though :-)
And that one shuts down ok.

I prefer just to use a base install with a minimal(ish) set of Gnome3 packages on top. No Unity for me. Today's boot glitch aside, breakage has been pretty negligible on my boxes so far.

---

### Post by Quackers on 2011-05-31
It's early yet :-)

---

### Post by paul_in_london on 2011-05-31
> **Quackers said:**
> It's early yet :-)

Very true. Less to go wrong with a minimal setup, although having said that I'm using the Ricotz ppa as well as the main Gnome3 ppa and the xorg-edgers ppa...

---


---
title: "Power Gremlins"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by BinaryHulledIon on 2012-09-13
I've recently settled on Kubuntu after purchasing a used laptop. It runs great, with the exception of two very small but occasionally annoying bugs.
 
Laptop: HP Pavilion DV6500 (Core2 Duo 1.5 GHz, 2GB RAM)
OS: Ubuntu 12.04.1 LTS (precise), KDE 4.8.4
 
Problem 1: The battery status indicator (a KDE widget) isn't working correctly. The only time it says that it's running on battery power is if it booted that way, and once it's plugged in it switches correctly but doesn't recognize any further connection or disconnection of the AC adapter. However, the power management system does dim the screen if the adapter is disconnected, and /proc/acpi/ac_adapter/ACAD/state is showing the correct status.
 
Problem 2: This is going to be sort of convoluted to explain. There's a popping sound coming from the speakers along with the mute indicator on the keyboard flashing on (amber) and off (blue). This only happens after the computer has booted on battery power only and then only after Chrome or Firefox has been opened (it may do this for other programs as well). Any sounds or music being played temporarily stops this from happening, but once the sound is done it goes right back to doing it again. However, once the ac adapter has been plugged in, it stops altogether. Removing the AC adapter afterwards doesn't make it start happening again, and if it's booted from AC power, it never does it. I'd be willing to accept that it's a driver issue but with both of these problems being related to how the laptop is being powered, I think at least part of the problem might be there.

---

### Post by BinaryHulledIon on 2012-09-15
Giving this a bump... Hopefully there's an answer available.

---

### Post by Epodx64 on 2012-09-15
For the battery indicator just try adding a different widget i'm pretty sure there's several that monitor battery life one's bound to work for you especially if you can get under /proc and it shows it's running correctly 

As for the sound it seems like it has something to do with Kubuntu selecting the wrong driver this is kind of an older tutorial but should apply to you [http://iamyouruser.blogspot.com/2009/07/ubuntu-sound-pops-glitches.html](http://iamyouruser.blogspot.com/2009/07/ubuntu-sound-pops-glitches.html)

---

### Post by BinaryHulledIon on 2012-09-17
I'm afraid I'm not getting anywhere on both accounts. I looked for additional battery widgets and only found one, really, called "Enhanced Battery Widget" which is more of a better status indicator, and still throws the false indicator. However, it did give an interesting indicator: it displayed information for Battery 1 and Battery 4, giving "Unknown" for 2 & 3. yet /proc/acpi/battery only has "BAT0," so I have no idea where this widget is getting its information from.

As for sound drivers, I only have the one output available. "Built-in Audio Analog Stereo." As it stands, that little oddity only happens while the laptop has booted from the battery, has remained only on battery power, and is looking at Gmail while in Chrome. I'm going to reinstall Firefox and maybe Konqueror to see if it stays there as well.

---

### Post by quirks on 2012-10-12
Hi BinaryHulledIon,

I hope my answer is not coming too late. I have a Pavilion DV6700 and I suffer from the exact same issues.

At least for the clicking noise from the speakers I might be able to help you: the noise is caused by switching off the power of the sound card for energy saving. Whenever the LED turns amber, the sound card is switched off. This causes a clicking noise. The sound card is switched off after a certain amount of inactivity (e.g., a couple of seconds after listening to a song/watching a video on YouTube). The solution is to disable power saving for the sound card. This can be accomplished fairly easily with the following command:

```
sudo sh -c 'echo 0 > /sys/module/snd_hda_intel/parameters/power_save'
```

If it was already switched off, when the command was issued, you need to play a sound to wake it up. After this, it will not be switched off automatically anymore.

To make this change permanent, open the file /etc/rc.local:

```
sudo nano /etc/rc.local
```

Put the following line at the end of the file (but before the **exit 0**, if there is one!):

```
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
```

After the next reboot, the sound card should never be switched off again.

Also, I will let you know, when I have found a solution to the faulty battery indicator, which is really annoying. I actually noticed, that when you hover with the mouse over the icon, the popup mostly displays the right information. It is only the icon, which is wrong (mostly, not always).

---

### Post by BinaryHulledIon on 2012-10-12
Is it totally weird that disabling the power saving on the sound card fixed the power indicator? Of course, now it still stays lit in blue even when the sound is muted (which, from what you're telling me, that light just watches the power state of the sound card, so I guess I should expect that).

However, it still does its thing, but only when Chrome (and no other browser, *not even Chromium*) has Gmail open. I suspect it has something to do with  the chat feature.

I guess the sound card was somehow getting in the way of the environment in recognizing the battery state, but disabling the power saving on it fixed that. The other issue of the power card cycling on and off looks like it may be a Chrome issue. 

Thank you for the help! Marking as solved.

---


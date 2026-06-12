---
title: "Making sense out of the battery indication"
date: 2014-02-10
forum: New to Ubuntu
---

### Post by Oinos on 2014-02-10
I'm having trouble what does battery indication at the top right of the screen exactly show. I've made it to show both the time and the percentage in the menu bar.

When the battery is fully charged, it shows no time and (0%), which makes little sense - maybe it shows how much it's exhausted?
However, when it's charging, it shows percentage close to 100, e.g. 95% and some random numbers, such as 5:38, 11:20, 7:52, which on top of that change every half to one minute, up to every 10 seconds, but this is somewhat rare. I don't know if it shows how much time remains until it's charged or how much time it'd last. I don't even know if it shows hours:minutes or minutes:seconds.
The situation when the laptop is on battery is similar.
Even stranger, when it charged completely, the indicator just remained on 98% even though under closer inspection in the battery menu it said everywhere it was charged. 

Could you shed some light?

I'm using ubuntu 13.10

---

### Post by varunendra on 2014-02-11
I am on 12.04, and this is how it behaves on my laptop -
> **Oinos said:**
> When the battery is fully charged, it shows no time and (0%), which makes little sense - maybe it shows how much it's exhausted?
When fully charged, it shows only the indicator (with electric bolt sign in it, indicating that I'm on AC power). If I click on the icon, it shows "Battery (charged)".

> However, when it's charging, it shows percentage close to 100, e.g. 95% and some random numbers, such as 5:38, 11:20, 7:52, which on top of that change every half to one minute, up to every 10 seconds, but this is somewhat rare. I don't know if it shows how much time remains until it's charged or how much time it'd last. I don't even know if it shows hours:minutes or minutes:seconds.
The numbers keep fluctuating due to the power consumed by the running processes keeps changing. If you are running very stable processes (not opening/closing programs or browser tabs, not loading/refreshing browser tabs, not doing anything that involves much hard disk activity etc.), then the numbers will decrease constantly as well.

They show how much time is remaining for the battery to get fully charged. If the laptop is idle, battery charges faster as more power is available for it - so the time appears to be lesser. If the laptop is busy and doing a lot of work, battery charges slower and this time appears to be longer.

The time is in Hr:Min.

When discharging, it again shows the time that is left until the battery is fully drained. This time is again in Hr:Min.

I'm not sure why it shows 98% when fully charged. Maybe it is because it 'Reserves' 2% for safe shutdown/suspend/hibernation, or maybe the battery practically never reaches the peak that it 'Reports' to be achievable. Just guessing, because I'm on 12.04 and haven't experienced any such behaviour.

PS:
By the way, you can also use "acpi -i" command to show detailed information (as available) about the battery and its state. You may have to install the program first (sudo apt-get install acpi).

---


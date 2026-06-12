---
title: "Power statistics not refreshing."
date: 2013-12-08
forum: New to Ubuntu
---

### Post by nargor34 on 2013-12-08
My problem is the following, when i check the battery status in Power Statistics (gnome-power-statistics in terminal), it shows that my battery status is being refreshed every 20 seconds or so...
The thing is, that it doesn't refresh the AC Adapter, and so it shows that the adapter is disconnected all the time.

When i use acpi -V on terminal i get:
```

tw@potatOS:~$ acpi -V
Battery 0: Discharging, 96%, 06:14:38 remaining
Battery 0: design capacity 6100 mAh, last full capacity 6400 mAh = 100%
Adapter 0: on-line
Thermal 0: ok, 29.8 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 106.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 95.0 degrees C
Thermal 1: active, 56.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 106.0 degrees C
Thermal 1: trip point 1 switches to mode active at temperature 87.0 degrees C
Thermal 1: trip point 2 switches to mode active at temperature 55.0 degrees C
Cooling 0: LCD 0 of 100
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Fan 1 of 1
Cooling 6: Fan 1 of 1
Cooling 7: Fan 1 of 1
Cooling 8: Fan 1 of 1
Cooling 9: Fan 0 of 1

```

When it is connected, and now, without the AC Adapter conected, it shows:

```

tw@potatOS:~$ acpi -V
Battery 0: Discharging, 96%, 04:23:30 remaining
Battery 0: design capacity 6100 mAh, last full capacity 6400 mAh = 100%
Adapter 0: off-line
Thermal 0: ok, 29.8 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 106.0 degrees C
Thermal 0: trip point 1 switches to mode passive at temperature 95.0 degrees C
Thermal 1: ok, 54.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 106.0 degrees C
Thermal 1: trip point 1 switches to mode active at temperature 87.0 degrees C
Thermal 1: trip point 2 switches to mode active at temperature 55.0 degrees C
Cooling 0: LCD 0 of 100
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10
Cooling 5: Fan 1 of 1
Cooling 6: Fan 1 of 1
Cooling 7: Fan 1 of 1
Cooling 8: Fan 1 of 1
Cooling 9: Fan 0 of 1

```

So, acpi does take notice of when the adapter is connected, but fails to recognize that the battery is being charged, and power statistics don't refresh the status.

Any ideas on how to solve this?

Edit: The refresh on the battery side seems to be dependent (among other things) of the battery status. For example, (i restarted with the ac adapter plugged in, so it knows it is plugged, but not refreshing) when my battery got fully charged, as it doesn't recognize when the AC adapter gets unplugged, and so, it doesn't need to refresh the battery status (if it isn't losing any battery charge, because the AC adapter has been plugged all the time, why refresh it?).

---

### Post by nargor34 on 2013-12-09
i don't know if people will hate me for this, but i think i will bump this thread. if it is inappropriate, tell me so i don't do it again ;)

---

### Post by nargor34 on 2013-12-10
Is there a more appropriate forum or subforum to ask this question?
So I can start a thread there, or maybe some mod can move this thread there :)

---


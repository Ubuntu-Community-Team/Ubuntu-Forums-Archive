---
title: "Fujitsu-Siemens AMILO 7440 Throttling Final Solution"
date: 2006-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Daniel Lewandowski on 2006-09-06
If you have FSAM 7440 (and probably others too) than you have a problem with the fans. They started working when cpu temperature raises. But very often they don't stop working and there is a little jet in front of you ](*,).

Solution is very simple. FSAM 7440 has probably broken bios and on start linux kernel disables a polling of the temperatures. To enable it add this line to /etc/rc.local:

echo -n "5" > /proc/acpi/thermal_zone/THRM/polling_frequency

This makes linux to poll the temperatures for every 5 seconds. Now fans start working and stop working.

But if you think that the fans starts too often than you can change the acpi trip points by adding this line:

echo -n "105:0:85:70:63" > /proc/acpi/thermal_zone/THRM/trip_points

Now fans starts rarely but cpu is much more hotter. I don't know if long time work with this setting can make any harm to the cpu or any other component. I have worked with this trip points setting and my amilo is still in good health.

I don't take any responsibility if you burn cpu! 

Changing polling frequency is completely safe :)

---


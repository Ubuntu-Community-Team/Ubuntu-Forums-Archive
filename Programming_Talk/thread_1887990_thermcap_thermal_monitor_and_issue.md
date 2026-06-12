---
title: "thermcap thermal monitor and issue"
date: 2011-11-28
forum: Programming Talk
---

### Post by GiovanniS on 2011-11-28
Hi,
I've developed a CPU thermal data collector with the feature to produce SVG files with the graph of the temperature.
It's an alpha version so there is much to do but it basically works.

You can look at the simple code here (and test too if you want): [http://code.google.com/p/thermcap/](http://code.google.com/p/thermcap/)

A result may be this
[IMG]http://thermcap.googlecode.com/svn/trunk/samples/MonNov281438552011_raster.jpg[/IMG]

Now (do not joke on my cpu temperature :lolflag: I'm working also to find the problem -already cleaned the fan-) here comes the issue.

I take my temperature data from the /proc file 
/proc/acpi/thermal_zone/CPUZ/temperature
but I'm an amd athlon x2 ql-66 dual core and I've not reached some proc files that tells me the temperature of each core on my Ubuntu 10.10.
So I ask your help to find a way (if there is one) to take CPU1 to N temperature with the proc filesystem or if there is another way to take these data.

Thanks for the attention.
Regards
  Giovanni

):P

---


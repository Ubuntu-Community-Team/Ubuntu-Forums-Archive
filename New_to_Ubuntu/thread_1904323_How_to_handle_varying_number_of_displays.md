---
title: "How to handle varying number of displays?"
date: 2012-01-04
forum: New to Ubuntu
---

### Post by javafanboy on 2012-01-04
Hi!

I got a laptop where I have installed 11.10. When on the road I only have the built in dispaly to use. When at home I have one external display and would like to use both the internal and the external one. At my work I have two external screen (my laptop can only drive two screens) and I would then like to use only the external screens and not the internal one.

My laptop has a fairly recent NVidia grapgic board and I use the latest manufacturer driver.

How can I manually (or even better automatically) select the right configuration depending on how many screen that are attached? 

When I used Windows 7 it was easy to have the machine pick the right profile and I hope it is doable with Linux as well since it is so much nicer in many other ways :D

/Javafanboy

---

### Post by audiomick on 2012-01-04
I don't think you should have a problem with this. My laptop (nVidia card) and my netbook both behave well in this respect. In fact, the netbook works better in Ubuntu than it does in Win7. ;)

Have you already tried this? What happened when you did?

I should mention, this will not happen automatically, at least not going from one monitor to many. If you shutdown, unplug the external and restart, I think it should come back only wanting to use the in-built monitor.
To get the external turned on, you will likely have to open the nVidia Settings application, but that is not hard.

---

### Post by javafanboy on 2012-01-04
Thanks for the quick reply!

By using manual config I have had some success. When disabling the built in display and later booting with no external monitors at all attached I did run into some problems to get my system working again though (would probably have been ok if I had enabled it again before shuting down).

I was hoping there where some way to have multiple profiles and automatically have the system use the right one based on how many screens that is detected (one to three) but perhaps that is not doable?

/Javafanboy

---

### Post by audiomick on 2012-01-04
> **javafanboy said:**
> ...(would probably have been ok if I had enabled it again before shuting down)....

Yes, this is probably a good idea.

I don't think there is anything along the lines of profiles, or any way of automating this. At least, I can't recall having seen anything on the subject, and I do have a bit of an eye open for it.

---

### Post by javafanboy on 2012-01-04
In some other forum thread I found a snippet that went something like this 

NR_OF_MONITORS=$(xrandr -d :0 -q | grep ' connected' | wc -l)
if [ $NR_OF_MONITORS = "2" ]; then
xrandr --output VGA1 --primary
fi

but I am not sure where I would put something like this? It must run before the screen is initialized I supose...

/Javafanboy

---

### Post by audiomick on 2012-01-05
Yeah, I don't know where that stuff would go, either. The thing is, there is a configuration file called xorg.conf, and then there is a thing called xrandr. Putting things very very simply, using the xorg.conf file is the "old way" of controlling monitors and xrandr is the "new system". That bit of code refers to xrandr. As far as I know, the nVidia drivers still refer to the xorg.conf file. I don't really know how much influence xrandr has when using nVidia drivers. Sorry I am not better informed.

---


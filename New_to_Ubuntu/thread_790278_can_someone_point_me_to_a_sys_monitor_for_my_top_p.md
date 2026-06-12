---
title: "can someone point me to a sys monitor for my top panel?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by srossnz on 2008-05-11
in my ubuntu gnome top bar I would like a little readout of cpu, hdisk space and even temps.  is there such a thing?  I see a few things available but prefer to have the readouts live in the bar itself so I do not need to click to see any information.. I tried using screenlets but it is very buggy, I setup items and even told it to load these items at startup but often i reboot and none of it loads, then i have to reload it and set it up again so got sick of trying to get screenlets working.


Thanks!

---

### Post by sujoy on 2008-05-11
you could try conky, it wont display on the gnome panel but its sweet.

---

### Post by prcm311 on 2008-05-11
There certainly is something like that.

I would run the following.

```
sudo apt-get install sensors-applet lm-sensors
```

Then you will have to configure this install by running

```
sudo sensors-detect
```

Make sure you pay attention to what the install is asking, most of the default settings will work for you, but near the end you are asked if you want to write the changes to a configuration file.  The default response is "no".  If you agree to that you will have to edit the file yourself.  I would let the install write the file, this is much easier.

---

### Post by SunnyRabbiera on 2008-05-11
you can also use the built in system monitor too.
right click on your top panel and select "add to panel"
and go down to "system monitor"
and add it to your panel, you can even drag and drop it if you wish.
after its added right click it and you can edit what it displays by going to "preferences"

The processor is loaded by default, and you can add the others by clicking the little boxes next to the monitors you want.
I recommend the "swap" and "memory" boxes as they will give you the gist of what you need.
You can resize it too if needed, I find it too big by default so I usually set it to the lowest possible (10 pixels)

also when you are done make sure to right click it again and slect "lock to panel" :D

---

### Post by srossnz on 2008-05-12
> **prcm311 said:**
> There certainly is something like that.

I would run the following.

```
sudo apt-get install sensors-applet lm-sensors
```

Then you will have to configure this install by running

```
sudo sensors-detect
```

Make sure you pay attention to what the install is asking, most of the default settings will work for you, but near the end you are asked if you want to write the changes to a configuration file.  The default response is "no".  If you agree to that you will have to edit the file yourself.  I would let the install write the file, this is much easier.

I did all this but do not see how to run the applet?

---


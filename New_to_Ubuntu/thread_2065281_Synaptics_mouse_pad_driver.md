---
title: "Synaptics mouse pad driver"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by gertcher on 2012-10-01
I have used Ubuntu before on a desktop as a dual boot, now I want to install it on my new laptop as the only operating system.

This is my 3rd laptop, the 1st with Ubuntu. What I really like about the other laptops is the version of SYNAPTIC I use. It allows me to program the movements as if it were a track ball, and more.

I looked on the [SYNAPTICS ]("http://www.synaptics.com/resources/drivers")website, they don't list a Linux driver. Is there anything else for Linux that will do the same, preferably 64 bit?

Thanks  Greg

---

### Post by sandyd on 2012-10-01
What movements are you specifically talking about?

---

### Post by ajgreeny on 2012-10-01
You don't say what actions you want or need, but it could be worth your while investigating synclient, a terminal utility which can give you masses of configuration options for synaptics pads.

Run ```
synclient -l
``` in terminal to see all the options and the current values/settings for your system, and then play around with the values for some of them to see if you can get what you are looking for.

To change any current value you need the command ```
synclient <option>=<value>
``` where **<option>** is one of the options listed in the first command I showed and **<value>** is a value shown in that first command. For example ```
synclient MaxTapTime=0
``` would turn of completely "tap-to-click". The zero in that configuration is milliseconds, hence that value is "Off"; higher values, up to 300 in my experience will turn it on with suitable sensitivity, but find your own values by trial and error.

---

### Post by gertcher on 2012-10-01
> **sandyd said:**
> What movements are you specifically talking about? Scrolling up/down/left/right,and flicking - this when you flick hard across the pad and the pointer travels to the edge and bounces off. Flicking gently the pointer travels less. Adjust the sensitivity of the pad to stop accidental movements. Program the corners to tap and perform an action.

They are the actions I use on a regular basis, the software has loads of other features

---

### Post by gertcher on 2012-10-01
> **ajgreeny said:**
> You don't say what actions you want or need, but it could be worth your while investigating synclient, a terminal utility which can give you masses of configuration options for synaptics pads.Although I have used Ubuntu before I have enough trouble finding how to run a command line, let alone adding code. Adding an app is going to be my best option, thanks.

---

### Post by gertcher on 2012-10-17
I found an app that replicates most of what Synaptic does.

Synaptiks can be installed via the Unbuntu Software Centre. The only thing I have used in windows was the ability to bounce the pointer off the edges of the window, cannot do that with Ubuntu.

I am happy with what I have, maybe Synaptiks will add more features later

---


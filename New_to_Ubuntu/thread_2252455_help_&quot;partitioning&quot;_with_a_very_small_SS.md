---
title: "help &quot;partitioning&quot; with a very small SSD (chromebook)"
date: 2014-11-12
forum: New to Ubuntu
---

### Post by sand_bird on 2014-11-12
This is not so much a technical question as a request for advice.

**Scenario:**
I'm running crouton on a Toshiba Chromebook 2 (16GB non-expandable SSD). The ChromeOS install takes up about 5GB, plus (ideally) a couple more in temp files and caching that will accumulate over time, so Ubuntu has 9-11 GB of total space to work with. My current setup is showing 5.2 GB remaining on the SSD, but I haven't yet installed any of the IDEs or libraries I'll need to use the machine for coding (so far I have xfce, Chromium, Steam, and the software center, as far as heavy hitters go). I've never used Linux before, let alone developed on it, so I have no idea how much space I can expect this all to take.

I also have a 64GB SD card to use as "primary" storage -- ie, my Home directory and whatever else is necessary to keep there. I realize this is somewhat risky, but my main concern is the poor read/write speeds I'll get from the card and card reader.

**Now the question(s):** *how much of my Ubuntu install, including software, can I get away with leaving on the SSD,* as opposed to the card? Will ~5 GB be enough for all the productivity software I still need? Would it actually be better for performance just to thow everything on the card but the kitchen sink (I mean, the OS) and allocate the rest of the SSD to swap? Specifically, which directories would you recommend housing on the SD card given the space constraints I described?

I really appreciate your input. Thank you!

---

### Post by mastablasta on 2014-11-12
ridiculous setup. also Chromebook was not ment for that and you get what you pay.

Ubuntu install will take between 6 or 7 GB. depends on what kind of libraries and what kind of things you will load this will increase. only you know what you plan to load. we can't read your mind. to keep it around 7GB you need to do regular cleaning and maintenance of old kernels and stuff. and to not install much. using SD card is doable but slow as you noted. USB stick or USB external drive might be better. if the notebook has USB port.

ok so what I have on 8GB virtual disk is: Xubutnu+LAMP= around 6.5GB, then a added a few other programs and installed some opencart, classOS and a few other web services I was testing and I still have about 1 GB left. I fi dont' clean kernels they would clog it up.

a better option is to install ubutnu minimal then add XFCE - it will install less programs (if you don't need them there is no reason for them to be installed). 

also why od you need steam?

---


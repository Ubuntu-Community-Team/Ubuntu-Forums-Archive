---
title: "Why is my PC suddenly shutting down and restarting???????????"
date: 2017-06-01
forum: New to Ubuntu
---

### Post by jstar1 on 2017-06-01
Argh. I'm still using Ubuntu - I like it - but wth - every few hours it shuts down and restarts. What gives? TIA

---

### Post by ian-weisser on 2017-06-01
Ubuntu does not have a 'poweroff and restart without warning' feature.
Turns out nobody wanted it. And nobody wanted to write it.

Read your /var/log/syslog in the seconds before a shutdown to learn what gives.
If there is no warning in the log, then you have a hardware failure.

---

### Post by poorguy on 2017-06-01
It could very well be a hardware failure depending on the age of the computer.

If it is a desktop then pull the case cover and give it a good dusting with an air hose. 

Then take a flashlight and start checking for swollen / bloated capacitors on the motherboard.

It may also be a power supply or graphics card starting to fail also check that all cooling fans spin freely and are clear of dust.

---

### Post by jstar1 on 2017-06-01
How do I access the log?

---

### Post by RobGoss on 2017-06-01
Hello and welcome to the forum, I do not believe this is a hardware problem I have two of these machines, it has to do with configuration for the BIOS

I had this issue on one of my machines, this YouTube video should help
[https://youtu.be/3BlhdH_DmY4](https://youtu.be/3BlhdH_DmY4)

If for some reason you have trouble with accessing the BIOS password you can also remove the lithium battery that's on the motherboard and it with bypass the BIOS password

---

### Post by jstar1 on 2017-06-01
Oh cool. Thank you so much. 
Will have a see and try to make the repair and report the outcome. If you don't mind me asking, how have you been liking these Optiplexes? I was just in awe of its massiveness but it seems like a good enough PC and then some :)

---

### Post by RobGoss on 2017-06-01
> **jstar1 said:**
> Oh cool. Thank you so much. 
Will have a see and try to make the repair and report the outcome. If you don't mind me asking, how have you been liking these Optiplexes? I was just in awe of its massiveness but it seems like a good enough PC and then some :)

Well I picked up two for dirt cheap and they seems to run ok, except for that problem rebooting it self

One of the I have Fedora 25, on it and the other Manjaro so far so good

I try sticking with Dell because it plays well with Linux

---

### Post by poorguy on 2017-06-01
What Dell Optiplex do you have?

I just bought six of them for $5.00 each without hard drives all powered up and I could get into bios.
All Dell Optiplex 380 and all have Intel Core2 duo E7500 processors and Intel integrated graphics and 3.0gb ddr3 memory.

They will make excellent Linux boxes and for what I paid for them I don't think it was a bad buy.

---


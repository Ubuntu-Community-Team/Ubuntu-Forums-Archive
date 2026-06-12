---
title: "System under 8.04 grinds to a halt"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by carusoswi on 2008-08-08
Running 8.04 on my 3gHz system, 2gb ram, plenty of HD space.
Last evening, ubuntu just ground to a halt.  Gradually, all input/output just slowed down to a crawl.

Terminal command iwconfig only reported back no extensions for my lo and eth0 (neither connected).  Wlan0 wasn't reported at all.  Further, no additional input possible in the terminal at that point, just a black blinking cursor.  I could exit the terminal and restart it to type in the iwconfig command and receive the same result.

Everything else on my machine just slowed to a snail's pace.

Very, very strange.

Eventually, the machine froze.

It's as if something took over all the resources.

Reboot solved the problem, but this bothers me.

I've never experienced that sort of system expiration in Ubuntu before.

Anyone have suggestions as to what might have caused it?

Caruso

---

### Post by darrenn on 2008-08-08
Turn off visual effects if you have it turned on. I was having problems with my system until I turned it off.

---

### Post by spiderbatdad on 2008-08-08
sounds like maybe an indexing program took over? You might like the program htop from synaptic...a little more graphically informative about running processes. Next time that happens, you can try to launch it...was your disk spinning like there was a lot of activity?

htop is accessible under Applications>>System Tools

---

### Post by Crafty Kisses on 2008-08-08
Run the following command:
```
top
```
Post the results.

---

### Post by carusoswi on 2008-08-09
> **Codename said:**
> Run the following command:
```
top
```
Post the results.

So, I ran that top command.  How do I capture and post the results (not certain what good the results might be now, as the system has been rebooted multiple times and is running ok.

OTOH, I would like to go ahead and post what's there if you could be so kind as to explain how I go about capturing it.

Thanks.

Caruso

---

### Post by Crafty Kisses on 2008-08-09
> **carusoswi said:**
> So, I ran that top command.  How do I capture and post the results (not certain what good the results might be now, as the system has been rebooted multiple times and is running ok.

OTOH, I would like to go ahead and post what's there if you could be so kind as to explain how I go about capturing it.

Thanks.

Caruso

You can technically just copy and paste it here on the forums.

---

### Post by carusoswi on 2008-08-09
> **spiderbatdad said:**
> sounds like maybe an indexing program took over? You might like the program htop from synaptic...a little more graphically informative about running processes. Next time that happens, you can try to launch it...was your disk spinning like there was a lot of activity?

htop is accessible under Applications>>System Tools

No, my disk was not spinning.
What was very interesting was that even a simple terminal command like: 

iwconfig

would not return proper results.  Because of another quirk in my system, I often have to run iwconfig to reset the association between my router and my adapter, so I know what to expect from that command.

When this mysterious sluggishness began, that command would show the lo and  ethos states, the wlan0 state would not even appear, so I knew something was really messed up.  I was online at the time, so my adapter had to have been functioning.

It was not long after that when my machine totally locked up and I had to reboot.

After reboot, it was back to its normal, fully functioning state.

Problem has not re occurred since, and I run this system some 8 - 10 hours a day.

I appreciate all the replies.  Any further suggestions welcome.

Hopefully, this problem will not resurface.

Caruso

---


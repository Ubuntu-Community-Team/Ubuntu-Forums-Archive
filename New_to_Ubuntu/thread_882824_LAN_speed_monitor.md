---
title: "LAN speed monitor?"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-08-07
I just replaced a few pieces of network equipment here to boost up to gigabit LAN. Other than relying on what it says in the marketing materials, is there a way to get a readout of the actual connection speed? Something like one of the speedtests you can find on the net to check your **Inter**net connection, but for the **intra**net connection. 

I'd really like to find out the average speeds *between* machines – from the Linux file server, through the router, then to a Mac OSX or a WinXP box (and the reverse). 

Thanks, 

Rhythm

---

### Post by NoFearDJB on 2008-08-07
Bump.

I like gnome-applet "System Monitor" but unfotunately the network graph give no bandwidth data like Rhythmdvl is looking for as well. Anyone know of something that would give out actual bytes/bits per second?

---

### Post by hyper_ch on 2008-08-07
make a webserver on one machine, put there a huge file and then

```

wget IP:/path/to/huge_file

```

wget shows the download speed

---

### Post by Mi11z on 2010-12-10
You may like this, i don't use panels at the moment though myself, but this is close to what your after.

```
http://www.howtoforge.com/keeping-an-eye-on-your-internet-speed-with-netspeed-gnome-ubuntu-8.04
```

---

### Post by randumnumber on 2010-12-10
This post is old and i dont know why it was zombied but since it has not been i will give it a good shotgun to the head and answer the question.

```

sudo apt-get install iftop

```it is exactly what the original poster 2 years ago needs. it will tell you which ip is connected to which both lan and wan. and the transfter rate between the two over 3 increments of time.

---

### Post by Rhythmdvl on 2010-12-13
Awesome, thanks!

---


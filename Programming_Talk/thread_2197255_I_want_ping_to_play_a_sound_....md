---
title: "I want ping to play a sound ..."
date: 2014-01-02
forum: Programming Talk
---

### Post by vasa1 on 2014-01-02
Sometimes my net goes down in such a way that I see my regular "network connected" icon in the panel but I can't go anywhere beyond my ISP. At such times, if I ping [www.google.com](www.google.com), nothing happens. All I see is:```
PING www.google.com (74.125.236.116) 56(84) bytes of data.
```Then, when whatever was wrong gets fixed, I get the regular output that ping generates when everything is fine.
```
[09:26 AM] ~ $ ping www.google.com
PING www.google.com (74.125.236.147) 56(84) bytes of data.
**64 bytes** from bom03s02-in-f19.1e100.net (74.125.236.147): icmp_seq=1 ttl=57 time=9.59 ms
64 bytes from bom03s02-in-f19.1e100.net (74.125.236.147): icmp_seq=2 ttl=57 time=8.80 ms
64 bytes from bom03s02-in-f19.1e100.net (74.125.236.147): icmp_seq=3 ttl=57 time=8.71 ms
64 bytes from bom03s02-in-f19.1e100.net (74.125.236.147): icmp_seq=4 ttl=57 time=8.72 ms
...
```

My question is this: I want to get a sound using **mplayer -really-quiet /home/vasa1/Dropbox/short.ogg** when ping starts generating regular output (= when I can start using the internet).

If I have a script that will let me do that, I don't need to keep looking at the terminal (or at my Dropbox icon in the panel) to know that all is now well.

In other words, the script should be able to see that "**64 bytes from**" has been output and then play the sound.

---

### Post by blackout2 on 2014-01-03
I'm just guessing here, but I would go into your Ping program, find the part where it prints out the successful connection, and add in your code to be played. I'm sure someone has a better, easier, and more *safe* version.

---

### Post by vasa1 on 2014-01-03
Okay, I don't need a script, just:```
ping -c3 www.google.com && mplayer -really-quiet /home/vasa1/Dropbox/short.ogg
```

---

### Post by blackout2 on 2014-01-04
That works.
You may want to create an alias if you just want to test if your internet is up.
Find your bash profile script.
Put this in on the bottom.

```


alias netUp="[COLOR=#000000][FONT=Ubuntu Mono]ping -c3 www.google.com && mplayer -really-quiet /home/vasa1/Dropbox/short.ogg"

```
Close the terminal, open it again, type in "netUp"(or whatever you want to name it), and there you go.[/FONT][/COLOR]

---


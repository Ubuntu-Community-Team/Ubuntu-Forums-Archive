---
title: "[SOLVED] Dual CPU running at 100%"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by scotcella on 2008-07-27
Hi,

Is it bad my CPU is running at 100%?  I have an intel duo core and both spike up to 100% every couple seconds..  

Not sure what I should do to make it go down? I only have one firefox tab open. 

:confused::confused::confused:

---

### Post by Vivaldi Gloria on 2008-07-27
> **scotcella said:**
> Hi,

Is it bad my CPU is running at 100%?  I have an intel duo core and both spike up to 100% every couple seconds..  

Not sure what I should do to make it go down? I only have one firefox tab open. 

:confused::confused::confused:

Open a terminal and start

```
top
```

to find out which app is causing it.

---

### Post by mikewhatever on 2008-07-27
Take a look in System Monitor > Processes, what's using the CPU most.

---

### Post by adobrakic on 2008-07-27
I heard that the system monitor gives a false reading of your CPU usage, so that might be it.

---

### Post by scotcella on 2008-07-27
top output says that the cairo dock is using my cpu at 100% YIKES.. i installed it last night and had a poke around..

not good..

what do i do now?

---

### Post by tuxxy on 2008-07-27
In terminal;

Killall <appname> , so

```
killall cairodock
```

ALso **conky** is a good tool for monitoring CPU usage also

---

### Post by insane_alien on 2008-07-27
unless it is sustained at 100% then there is probably nothing to worry about.

even then, i've been running a quad core at 100%(technically 123% as it is over clocked a fair bit) for a few months now and nothing bad has happened. although, i know why it is running at full utilization and thats cause its doing what i told it to do.

---

### Post by scotcella on 2008-07-27
> **insane_alien said:**
> unless it is sustained at 100% then there is probably nothing to worry about.

even then, i've been running a quad core at 100%(technically 123% as it is over clocked a fair bit) for a few months now and nothing bad has happened. although, i know why it is running at full utilization and thats cause its doing what i told it to do.

one goes up and down..   and the other stays at 100%...

the top output sustains at 100%..  been looking at the top output for more than a minute and it stays out 100% while the other processes goes up and down between 1-4%

---

### Post by scotcella on 2008-07-27
> **tuxxy said:**
> In terminal;

Killall <appname> , so

```
killall cairodock
```



this is what I get back after putting in the command you just gave me
```

cairodock: no process killed
```

---

### Post by seagullplayer77 on 2008-07-27
You might have better luck if you try killing Cairo-Dock with the process ID instead. I believe it shows you the PID when you run "top," and while top is running just press "k" and it'll give you a kill dialog. Punch in the PID and keep pressing enter until it dies. Although, I'm not quite sure why Cairo-Dock is using so much CPU power. I've used Cairo-Dock for six months and it's been a resource hog. I just checked, and mine is listed as using 1% of the total CPU power, and I have an AMD64 dual core running as well. Maybe something other than Cairo-Dock is the culprit??

---

### Post by scotcella on 2008-07-27
> **seagullplayer77 said:**
> You might have better luck if you try killing Cairo-Dock with the process ID instead. I believe it shows you the PID when you run "top," and while top is running just press "k" and it'll give you a kill dialog. Punch in the PID and keep pressing enter until it dies. Although, I'm not quite sure why Cairo-Dock is using so much CPU power. I've used Cairo-Dock for six months and it's been a resource hog. I just checked, and mine is listed as using 1% of the total CPU power, and I have an AMD64 dual core running as well. Maybe something other than Cairo-Dock is the culprit??

Thank you!! your explaination was a bit clearer how to kill it.. now i know how do kill processes doing it this way..  thank you..

It's definately Cairo-dock.. the CPU activity levels has died down right after cairo dock was killed off...   down to a safe 4-11% for both processors.

I also have compiz running as well..   but doesn't take up much resource- barely 1%. 

I now find the cairo dock a bit annoying anyway..  looks nice but bugs me a little so it's not for me..  but I LOVE compiz though!

---

### Post by adobrakic on 2008-07-27
You might want to uninstall cairodock now as well. You can do it through synaptic and then run

```

sudo apt-get autoremove

```

---

### Post by seagullplayer77 on 2008-07-27
Glad I could help :-). I'm miffed as to why Cairo-Dock was being such a resource hog, but whatever. Anyway, it wouldn't be a bad idea to go into the "Thread Tools" menu at the top of your post and mark it as "Solved."

---


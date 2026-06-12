---
title: "gathering and plotting system info (temp, voltages etc)"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-08-03
Is there a simple program that gathers and plots system voltages, temperatures etc from lm-sensors? 

I have the sensors running well on my computer and there seem to be various daemons like sensord, hddtemp etc that log some info but I've spent all day trying to plot the round-robin database that sensord creates.. to no avail. It seems so complicated and needs installation of apache, mysql, cacti etc etc .. 

Isnt' there a simple utility to plot what the temperature has been doing recently?

---

### Post by tamoneya on 2008-08-03
look into conky.  There are many threads in this forum about it.

---

### Post by K2712 on 2008-08-03
From the guys at Gentoo:

[http://gentoo-wiki.com/Lm_sensors/Script](http://gentoo-wiki.com/Lm_sensors/Script)

---

### Post by ingrid_ozikem on 2008-08-04
@tamoneya -- I think you misunderstood my question (or I underestimate conky). I want to LOG all details like voltage, temps. and plot their HISTORY. Conky can make pretty graphs but basically of the last 10 mins.. not the entire last year.

@K2712 -- that's for that script! Does look like what I want, if only for core temps.. hopefully I can modify it to work for any sensor. A spreadsheet sounds far more friendly than these Round-Robin databases that all other such programs seem to create! 

Impossible to simply open and view!

---

### Post by tamoneya on 2008-08-04
just use cron and a small script that parse "sensors"

---

### Post by ingrid_ozikem on 2008-08-04
That's what is has come to now.. only I also want to get the CPU load (on a Q6600) -- that's one load for each core.

Do you know of a simple way to do this? I worry that doing it naively will cause the script to be heavy on the system..  is a script that parses 'sensors' light enough to be an elegant solution to this?

Also, how about a sleep command in the script instead of cron? 

Sorry, I'm new and just not sure if these are ridiculous ugly solutions or if they are acceptable loads on a system.. that's why I was hoping programs already exist that do this since I'm sure many people want this.

---

### Post by tamoneya on 2008-08-04
i think cron would be better than sleep because then you dont have to have the process running 24/7 (i see this being run every 5 minutes).  cron will launch it when necessary.  For the CPU load use top and just parse through the first line to a section that looks like this:```
load average: 0.37, 0.37, 0.37
```
Take the first number as your CPU average.  Note that your computer given that it is quad core will have numbers in a range of 0-4.  If you want percents just multiply by 25.

---

### Post by ingrid_ozikem on 2008-08-04
Thanks! I am writing a script to parse sensors for system voltages but meanwhile I found a very useful simple program that collects the rest of the data in a textfile. It is called,

dstat

and it basically puts together programs like vmstat,iostat etc and prints a long line of numbers reporting cpu usage, memory usage, disk usage, eth0 etc.. 

looks like i still need to parse sensors for temperatures and voltages but that's OK.

What annoys me is that I have gkrellm running which displays all this info.. and now I must have another script running to write down the same info. A bit of a waste.. if only gkrellm or conky could write down the info.. oh well.

---

### Post by tamoneya on 2008-08-04
in conky you could use execi to call dstat to write to a file.

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by cariboo on 2008-08-04
This may be a little bit more than your are looking for, but have a look at Cacti here:

[http://www.cacti.net/](http://www.cacti.net/)

Cact is available in the repositories.

Jim

---

### Post by tamoneya on 2008-08-04
cacti looks really nice but mysql, php and apache seems like overkill for me. I may eventually add it to my network to monitor servers as I add some more.

---

### Post by ingrid_ozikem on 2008-08-05
Yeah, I got half way into installing cacti when I realized what a dinosaur it was.. along with apache and mysql. 

On the other hand,I've spent more than a day now write scripts and still am learning up on gnuplot to make plots of my data..

(new to perl)

---


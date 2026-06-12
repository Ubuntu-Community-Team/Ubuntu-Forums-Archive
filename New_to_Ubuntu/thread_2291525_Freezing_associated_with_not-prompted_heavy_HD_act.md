---
title: "Freezing associated with not-prompted heavy HD activity (swap problem?)"
date: 2015-08-20
forum: New to Ubuntu
---

### Post by marco112 on 2015-08-20
Hello!

My system is very unstable. It becomes unresponsive, very slow and subsequently completely frozen while I can hear the HD being accessed/operated.
Usually the actions that prompt the freeze are not related to I/O of large files on the HD, it is mostly stuff that I would correlate to RAM activity.
For instance switching tabs on my browser, or opening a program (even the command shell), or moving from a program to another (e.g. checking a pdf file while on a skype conversation). 
It doesn't always happen, I can work for one hour without any problem and than have multiple freezes one after the other in few minutes.

Once frozen I can't do anything, sometimes the cursor still moves very slowly, usually it is frozen, while I can hear the HD running. Few times the system starts working again (around 5-10 minutes wait), usually there is nothing to do but a hard physical reset.
I noticed that the system boot time has been increasing too.

I searched online and found that it could have been a problem related to swapping. I tried to change swappiness to 10 but the problem persists. 

I have Ubuntu 15.04, installed after changing internal HD so it sounds unlikely to be an hardware problem (or not?).

Thanks!

---

### Post by TheFu on 2015-08-20
Sounds like swapping, then running out of swap, so it crashes.
How much RAM do you have?
How much swap?
What processes are running and how much ram are the top 10 using?

---

### Post by marco112 on 2015-08-26
I have 4 GB of RAM and 500 MB of swap.

The top RAM using process is Firefox with ~500 MB, then I have a few (like compiz and mathematica) using up to ~100 MB.

---

### Post by v3.xx on 2015-08-26
You could try running a different window manager (desktop).  "Flashback" using Metacity WM.
```
sudo apt-get install gnome-panel
```
And choose at login by clicking on the icon in top right of screen.

Also, what graphic card and driver are you using?

Will monitoring the load
```
free -m 
```
tell you anything?

---

### Post by TheFu on 2015-08-26
> **marco112 said:**
> I have 4 GB of RAM and 500 MB of swap.

The top RAM using process is Firefox with ~500 MB, then I have a few (like compiz and mathematica) using up to ~100 MB.

Minimal swap for a desktop is normally 4G thanks to modern browsers easily sucking up 2G of RAM over time. Beyond 4G, swap is generally counter productive.  For a netbook with 2G of RAM and 2G of swap, the system crashes. At 4G of swap, the crashes never happen - it has been 8 crash-free months.

When a system runs out of RAM+swap, it crashes. Remember that.

---

### Post by sandyd on 2015-08-26
Open a terminal, run the following to install a lovely command line cpu/ram monitor named htop
```

sudo apt-get install htop

```

After the install, make a bit of room on your screen, a place that won't be covered by any other window. Drag the terminal there, and run
```

sudo htop

```

The terminal should now show something like the below:
[IMG]http://i.imgur.com/kH3cUTk.png[/IMG]

The first two bars on the left (1/2) represents CPU usage (htop does not discriminate against HT cores, and shows them all the same)
The bar after that is for memory, and the bar after that is the swap, and the stuff on the right includes the load average, uptime, and number of processes.

When the computer freezes now, you should be able to see exact RAM usage, and if that is the issue.

Side Note:
Ignore the rediculously low resource usage in the screenshot, that server doesn't have a gui

---

### Post by marco112 on 2015-08-28
Thanks all.

So I tried htop and the last time my system froze I had SWAP completely full but RAM only half full (around 1.8 GB of the 4 GB total). The CPU load was less than 30%. 
Shall I try to modify the partition and make the SWAP memory larger?

My graphic card is a ATI [Radeon HD 6630M/6650M/6750M/7670M/7690M]. The drivers are the fglrx-updates ones, if it makes sense.

---

### Post by sandyd on 2015-08-28
Something is using ridiculous amounts of memory it seems like, possibly memory leaking that Ubuntu is trying to stuff into the swap.

Press F6 with HTOP opened, choose MEM, and see what is using the most memory when everything crashes.

---

### Post by TheFu on 2015-08-28
Post #5 works. Why wait?

---

### Post by tgalati4 on 2015-08-29
Make your swap 4.1 GB.  See how it runs for a while.

---

### Post by marco112 on 2015-09-02
I tried to change the size of my SWAP partition but I wasn't able. 
I used a live CD and gparted, I start thinking that I have some problem with partitions in general, this what I see
[ATTACH=CONFIG]264176[/ATTACH]

---

### Post by TheFu on 2015-09-02
There isn't any room for a larger swap - you'll have to make some room first.  

I've never seen anything like that layout before. Was there a specific reason for it?  

Reduce SDA6 - I'd make it much smaller and leave some room for other, unknown stuff.  Then just make a new swap inside the extended partition and hook that up. You don't have to delete SDA1 or even remove it - if you don't want, but I would to have swap all in 1 group on the physical disk. Should be quicker than having swap on opposite sides of the disk.

---


---
title: "Please help"
date: 2016-03-07
forum: New to Ubuntu
---

### Post by NewYorkGiant on 2016-03-07
I am new to Linux and recently installed Ubuntu 15.10 on a legacy HP ProLiant DL360 G4 server with dual Xeon 3.4GHz processors and 2GB RAM. The OS isn't running fluidly whatsoever. Are 2GB RAM enough? Is this the completely wrong OS? Could it be that the kernel wasn't written over properly? Thanks for any input.

---

### Post by 1clue on 2016-03-07
2G should be enough to run, but I'm not sure whether multi-socket systems take more memory.

IMO 2G is very marginal for a desktop system and extremely marginal for anything I would expect to use a dual socket system on.

I have observations:
[LIST=1]
[*]If you are budget-constrained and NEED this hardware to work, then by all means continue.
[*]If you are bored and looking for something to do, then by all means continue.
[*]If you're just looking for something to learn Linux on, then I advise you to create a virtual machine on whatever you're using now, or get different hardware.
[*]If you heard somewhere that Linux is great at making old hardware new again, then see #3.
[*]Current smart phones have this much RAM. You could max the memory out, but it's ecc memory which is more expensive.
[*]This hardware is 9 years old. Most large businesses I've dealt with replace server hardware at around 5 years age.
[*]I would expect a modern i7 to outperform this box while drawing a fraction of the power, making almost no noise and lasting much longer.
[/LIST]

The big problems with old hardware:
[LIST=1]
[*]It tends to burn much more electricity and create much more heat and noise than the equivalent modern hardware would.
[*]It tends to become available either right after hardware failures have begun, or just before they are likely to begin.
[*]Old server hardware may have limited driver support.
[/LIST]

Let me be clear:  I've been in most of these situations before. If you're desperate for hardware of a certain class and this is what you can get, then I don't mean to discourage you at all. Statistically speaking this thing is about to fail, but for all anyone knows this one could last another 20 years. It's up to you.

---

### Post by sandyd on 2016-03-07
> **NewYorkGiant said:**
> I am new to Linux and recently installed Ubuntu 15.10 on a legacy HP ProLiant DL360 G4 server with dual Xeon 3.4GHz processors and 2GB RAM. The OS isn't running fluidly whatsoever. Are 2GB RAM enough? Is this the completely wrong OS? Could it be that the kernel wasn't written over properly? Thanks for any input.

Hi, I noticed that you said this is Ubuntu 15.10, and not Ubuntu 15.10 Server (which has no GUI).

If this is Ubuntu 15.10 (with GUI), it may be that your video card is not powerful enough. Most server video cards are mainly meant to provide basic video support and are pretty much useless for running desktops as heavy as Unity.

You may want to try something lighter such as Lubuntu in this case.

---

### Post by mörgæs on 2016-03-08
1clue, your statements are of a very general nature and only in part useful for troubleshooting a particular problem.

Rule of thumb is that old hardware is less power greedy than new if one compares server with server, for example. Changing the type of hardware, for example swapping an old server for a new Raspberry of course saves power. 
[http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html](http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html)
Don't discard old stuff until you have measured the power consumption. Seeing the label on the back is not enough.

Statistics is useful for predicting when a group of hardware is going to fail, not the individual computer. 

2 GB is fine if you choose the right operative system.

---

### Post by mastablasta on 2016-03-08
also, we need to know other system specs to give a better advice. see this thread for more info: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

you likely need a better GPU, or you can use a lighter desktop as suggested.

---

### Post by sudodus on 2016-03-08
Welcome to the Ubuntu Forums :-)

I 'inherited' an HP xw8400 workstation with similar processors to yours, 4 GB RAM and I bought a new graphics card some years ago. It works well for me. With Lubuntu (and the ultra-light desktop environment LXDE) I can play HD videos (1920x1080 50p) without problems. Most other tasks work well with more demanding desktop environments too. The computer is a good number crunching machine, for example to convert video clips from my video camera, where ffmpeg can use all 2x2 cores in an efficient way.

I suggest that you listen to the advice of sandyd, mörgæs and mastablasta. I think 2 GB RAM will not be a bottleneck with Lubuntu. It might be a good idea to get a graphics card (nothing fancy, maybe a used 'second-hand' card) if you want better performance with a (graphical) desktop environment. If you use your computer as a server in text mode, I don't think you need better graphics.

Good luck :-)

---

### Post by HermanAB on 2016-03-08
Howdy,

The problem is the low performance GPU.

On that sort of hardware you should use either the Server version (best), Lubuntu or Xubuntu.

---

### Post by NewYorkGiant on 2016-03-08
Thank you all for your prompt responses.

 I was recently given a stack of machines. 10 HP ProLiant DL360 G4 dual 3.4GHz Xeon CPUs, 2GB, 800fsb rack servers; an HP ProLiant ML570 G2 rack server with 4 Xeon MP 2.5GHz CPUs 8GB RAM with 3 600w (redundant) psu with a spare 2.5GHz CPU; a Compaq ProLiant ML570 G2 rack server with 4 Xeon MP 2.0GHz cpus and 3 600w (redundant) psu; and more...

I would like to "repurpose" these machines and I kind of wanted to see if I could run the "best" one as a desktop for possible gaming or as a media center.

---

### Post by 1clue on 2016-03-08
> **mörgæs said:**
> 1clue, your statements are of a very general nature and only in part useful for troubleshooting a particular problem.


I did not mean to be disrespectful or distracting.

> 
Rule of thumb is that old hardware is less power greedy than new if one compares server with server, for example. Changing the type of hardware, for example swapping an old server for a new Raspberry of course saves power. 
[http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html](http://www.complang.tuwien.ac.at/anton/computer-power-consumption.html)
Don't discard old stuff until you have measured the power consumption. Seeing the label on the back is not enough.


My comment was oriented toward getting the same performance out of the hardware, MIPS per MIPS, approximately.  For example, I have an i7 920 (first-gen i7, 24g RAM) I'm using as a desktop, and a new c2758 atom (16g RAM).  The i7 is packed full and using most of the capacity of the 600w power supply, the c2758 has a 20w power supply, the motherboard uses 11w full load. Both systems are equipped with an SSD and some number of spinners. The atom is faster at compression, network transfers, encryption and a few other things. The i7 compiles almost 2x faster.  The key here is the i7 was at the time of purchase a higher-end workstation and the c2758 box is a router.

I have observed the same sort of scenario over and over again, desktop/laptop hardware and server hardware. Each generation of hardware expands performance markedly, which means a lower class of new hardware can perform the same tasks as the older higher class. Within reason.
> 
Statistics is useful for predicting when a group of hardware is going to fail, not the individual computer. 


Which is exactly what I said.
This is an approximate example of service life:  As you can see in the following link, the E5-2400 v2 series was released first quarter 2014.  [http://ark.intel.com/products/family/78582/Intel-Xeon-Processor-E5-v2-Family#@Server](http://ark.intel.com/products/family/78582/Intel-Xeon-Processor-E5-v2-Family#@Server)

Here is the EOL announcement for Cisco gear with this processor: [http://www.cisco.com/c/en/us/products/collateral/servers-unified-computing/ucs-b-series-blade-servers/eos-eol-notice-c51-733775.html](http://www.cisco.com/c/en/us/products/collateral/servers-unified-computing/ucs-b-series-blade-servers/eos-eol-notice-c51-733775.html)  So Cisco will stop supporting this processor 6 years after its launch date.  Again, this box is 9 years old. Surely this matters in anyone's analysis of potential return on investment?

> **NewYorkGiant said:**
> Thank you all for your prompt responses.

 I was recently given a stack of machines. 10 HP ProLiant DL360 G4 dual 3.4GHz Xeon CPUs, 2GB, 800fsb rack servers; an HP ProLiant ML570 G2 rack server with 4 Xeon MP 2.5GHz CPUs 8GB RAM with 3 600w (redundant) psu with a spare 2.5GHz CPU; a Compaq ProLiant ML570 G2 rack server with 4 Xeon MP 2.0GHz cpus and 3 600w (redundant) psu; and more...

I would like to "repurpose" these machines and I kind of wanted to see if I could run the "best" one as a desktop for possible gaming or as a media center.

The way you worded this post, it seems that "return on investment" is not so important. Doing something to see if you can make it work, that's what learning is all about and in this case a very inexpensive hobby.

Good luck and have fun.

---

### Post by mastablasta on 2016-03-09
> **NewYorkGiant said:**
> Thank you all for your prompt responses.

 I was recently given a stack of machines. 10 HP ProLiant DL360 G4 dual 3.4GHz Xeon CPUs, 2GB, 800fsb rack servers; an HP ProLiant ML570 G2 rack server with 4 Xeon MP 2.5GHz CPUs 8GB RAM with 3 600w (redundant) psu with a spare 2.5GHz CPU; a Compaq ProLiant ML570 G2 rack server with 4 Xeon MP 2.0GHz cpus and 3 600w (redundant) psu; and more...



wow so someone is giving descent server hardware away?!?!?! 

> 
I would like to "repurpose" these machines and I kind of wanted to see if I could run the "best" one as a desktop for possible gaming or as a media center.
you can but you need a good GPU for gaming. For media center a descent one (can be a cheapest low profile card) would do. remember that Raspberry Pi B with it's puny CPU and descent GPU runs well as media center. media center is usually always on which is where the low power usage of RPi plays it's part well.

for these servers and so many of them you could probably build some game servers.

still can't believe... so many and all free...

---

### Post by mörgæs on 2016-03-09
We need more specific information. Too much guessing.

For the server on which you want to work please run ```
sudo lshw -C video
``` and post the results in CODE tags. You can do it from a live boot or an installed operative system.

---

### Post by Edward_Fish on 2016-03-09
Just in case you wanted another opinion:
1. The above command (sudo lshw -C video) is safe to run.
2. I got an... eh, below average, but definitely usable Unity desktop on a REALLY old machine. I used Ubuntu 14.04, and it had 1GB RAM and I think about 1.2 GHz processor speed. I don't know the number of cores. It was preinstalled with Vista, which was COMPLETELY unusable. You could click the start button and wait 10 secs for the menu to appear, with no open applications and just Dropbox in the background.
3. I currently have a machine with 2GB of RAM. It runs Unity fine, although some applications are slow to start. (LibreOffice Writer takes 10 secs; Firefox takes 10-15 secs.)

---

### Post by NewYorkGiant on 2016-03-11
I've yet to find an OS that can run these machines fluidly other than MS (XXXX) SERVER...(which works amazing well on both) I HAVE TO BE DOING SOMETHING WRONG. Ubuntu 15.1 was the only OS that got me anywhere (other than SERVER XXXX). How is that? There are some major differences between the HP DL360 dual cpu(x64) and the ML570 quad cpu(x86?) which I think I understand. Architecture<---spelling was the reason for EDIT) I've tried "Haiku"...i've tried "Lubuntu"...i've tried "Xubuntu". I can be more device specific as to which OS i've tried on which but somehow I believe that there's a "kernel" issue involved. These embedded GPU's could be a major issue I understand...but should at least be capable fluid operation with the most basic drivers...idk. STUMPED

---

### Post by sudodus on 2016-03-11
I suggest that you run for example Lubuntu in text mode: Use the boot option **text**

[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)
[HR][/HR]

and in text mode, run the command

```
sudo bash -c 'lshw -sanitize | gzip -c > lshw.txt.gz'
```

and attach the file **lshw.txt.gz** to a reply (Press the orange-red button [COLOR="#cc3c00"]**Go Advanced**[/COLOR], Manage Attachments ...)

***Edit:*** This will tell us about your hardware and help understand if there are problems with for example your graphics cards/chips in the servers.

---


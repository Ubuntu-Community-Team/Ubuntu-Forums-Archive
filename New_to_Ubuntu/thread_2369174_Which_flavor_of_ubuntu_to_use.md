---
title: "Which flavor of ubuntu to use?"
date: 2017-08-19
forum: New to Ubuntu
---

### Post by atulmohan007 on 2017-08-19
Hello All, 

I use linux as my default OS. I switched from Ubuntu 14.04 to Ubuntu Gnome 17.04, because of performance and Overheating issues. 

However, Ubuntu Gnome works even slower and is resource heavy. 
Ex: If I open PyCharm, Document Viewer and Chrome at the same time, it takes over a minute to switch tabs and system is unresponsive and many times the system freezes. 

I mostly work with such editors and normal computations on my Laptop. 

Please suggest me which flavor of Ubuntu Family should I use. Below are the specs of my Laptop. 

[ATTACH=CONFIG]276452[/ATTACH]

Edit 1 : Output of inxi -F 

[ATTACH=CONFIG]276457[/ATTACH]

---

### Post by vasa1 on 2017-08-19
Please install *inxi* and post the output of *inxi -F* so that people have a better idea of your system.

---

### Post by vocx on 2017-08-19
> **atulmohan007 said:**
> Hello All, 

I use linux as my default OS. I switched from Ubuntu 14.04 to Ubuntu Gnome 17.04, because of performance and Overheating issues. 

However, Ubuntu Gnome works even slower and is resource heavy. 
Ex: If I open PyCharm, Document Viewer and Chrome at the same time, it takes over a minute to switch tabs and system is unresponsive and many times the system freezes. 

I mostly work with such editors and normal computations on my Laptop. 

Please suggest me which flavor of Ubuntu Family should I use. Below are the specs of my Laptop. 

If you are using a Core i3 and an integrated Ivybridge Mobile graphics card, I think your computer is a low-end machine.

Therefore, I think it is probably "normal" that you experience a bit of lag when using a relatively heavy desktop environment such as Gnome, KDE, or Unity.

My recommendation would be to try a lighter desktop environment such as MATE, XFCE, or LXQT. These environments can be installed in your current system, or they also come preloaded in the installation media for Ubuntu MATE, Xubuntu and Lubuntu.

---

### Post by Autodave on 2017-08-19
Would like to know how much RAM is in there. I woulde suggest at least going with Xubuntu. And then, I would go with Xubuntu 16.04.

  	 	 	 	   Every 2 years, a long term service release is made. These LTSs have a service life of 5 years: security and software updates are available for 5 years after the release.  The last LTS was 16.04. 16 stands for the year of the release, 04 stands for the month (April). The next LTS will be 18.04. Releases in the interim will be 6 month releases and only supported until the next release.

I stick with only the LTSs and even then I usually wait a month after their release before installing them. Further, I do not upgrade to them but completely install the new release after copying all files that I need to save to an external HD.

---

### Post by atulmohan007 on 2017-08-19
Edit1: Output of the command inxi -F 

[ATTACH=CONFIG]276456[/ATTACH]

---

### Post by atulmohan007 on 2017-08-19
Thanks of the suggestion. :) 
My Laptop has 4 gb of RAM , However it shows 3.7 GB of internal memory. 
I have posted the full spec of the hardware above in the post. 
Please have a look and suggest.

---

### Post by Autodave on 2017-08-19
Go with Xubunu 16.04. At least give it a try. You have nothing to lose but a little time.

---

### Post by vocx on 2017-08-19
> **atulmohan007 said:**
> Edit1: Output of the command inxi -F 


Never post pictures of terminal output. Why? It's annoying. If it's only text, you can copy and paste it in this forum inside CODE tags so it will use a monospace font and preserve the spaces.

Posting code in this way makes it easy for other users to see, copy and search text easily, which is not possible with images. I mean, you cannot select the text inside an image, but you can if it's plain text.
```

CPU:       Dual core Intel Core i5-5200U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2700 MHz 1: 2294 MHz 2: 2460 MHz 3: 2455 MHz 4: 2282 MHz
Graphics:  Card-1: Intel Broadwell-U Integrated Graphics
           Card-2: NVIDIA GM108M [GeForce 940M]
           Display Server: X.Org 1.18.4 driver: nvidia Resolution: 1920x1080@60.02hz, 1920x1080@60.00hz
           GLX Renderer: GeForce 940M/PCIe/SSE2 GLX Version: 4.5.0 NVIDIA 375.66
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller driver: snd_hda_intel
           Card-2 Intel Broadwell-U Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-92-generic
Network:   Card-1: Intel Ethernet Connection (3) I218-V driver: e1000e
           IF: enp0s25 state: down mac: 50:50:9d:2c:90:90
           Card-2: Intel Wireless 7265 driver: iwlwifi
           IF: wlp3s0 state: up mac: 4c:4c:88:52:f7:f7
Drives:    HDD Total Size: 1016.2GB (22.6% used) ID-1: /dev/sda model: TOSHIBA_MQ01ABD1 size: 1000.2GB
           ID-2: /dev/sdb model: SanDisk_SSD_U110 size: 16.0GB
Partition: ID-1: / size: 19G used: 15G (82%) fs: ext4 dev: /dev/sda5
           ID-2: /home size: 94G used: 71G (80%) fs: ext4 dev: /dev/sda8
           ID-3: swap-1 size: 15.36GB used: 0.00GB (0%) fs: swap dev: /dev/sda6
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 58.5C mobo: N/A gpu: 48C
           Fan Speeds (in rpm): cpu: 3722
Info:      Processes: 261 Uptime: 1 day Memory: 3199.5/7683.6MB Client: Shell (bash) inxi: 2.2.35 

```

---

### Post by ClickXT on 2017-08-19
I have really been enjoying Xubuntu with it's XFCE desktop environment.

---

### Post by vasa1 on 2017-08-19
Please follow the advice of vocx and always post terminal output as text using code tags. Use your mouse to select all the text you need, *preferably including the command you ran to generate the output*, right-click and copy it and then paste it here.

FYI,
When you start a new thread or make a post in an existing thread using "Reply With Quote" or "Adv Reply", you'll see an icon that looks like **#** above the posting area's text box. Single-click on it. Automatically, you'll see [noparse]```

```[/noparse] appear in the text area where the insertion cursor is located. Simply paste your content from the terminal between the opening [noparse]```
[/noparse] and closing [noparse]
```[/noparse] tags.

In case you use the "Reply to Thread" or "Quick Reply" options, the **#** icon will not appear: these options provide a minimal set of icons. In that case you can carefully type in the tags yourself or click on "Go Advanced" below the posting area's text box to make the **#** icon (and other icons) appear.

Your image showed a CPU temperature of 61 degrees Celsius. Unless you were doing something really CPU intensive, that's bad.

Have you cleaned your laptop recently?

Anyway, if you go for a change in flavor, I suggest doing a clean install after backing up your data. I don't like adding a new desktop environment and logging into that even if it's easier.

I also suggest you stay on 16.04 and use the first release so that you'll be on an older kernel channel. Newer kernels are for newer hardware. In this context see wiki.ubuntu.com/Kernel/LTSEnablementStack.

You may have to search for the first release of 16.04.0 for your flavor. 
Some links: 
[http://old-releases.ubuntu.com/releases/16.04.0/](http://old-releases.ubuntu.com/releases/16.04.0/)
[http://cdimage.ubuntu.com/kubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/16.04/release/)

---

### Post by atulmohan007 on 2017-08-20
Ahh My Bad. 
Thanks a lot for the suggestion :)

---

### Post by atulmohan007 on 2017-08-20
> **vasa1 said:**
> Please follow the advice of vocx and always post terminal output as text using code tags. Use your mouse to select all the text you need, *preferably including the command you ran to generate the output*, right-click and copy it and then paste it here.

FYI,
When you start a new thread or make a post in an existing thread using "Reply With Quote" or "Adv Reply", you'll see an icon that looks like **#** above the posting area's text box. Single-click on it. Automatically, you'll see [noparse]```

```[/noparse] appear in the text area where the insertion cursor is located. Simply paste your content from the terminal between the opening [noparse]```
[/noparse] and closing [noparse]
```[/noparse] tags.

In case you use the "Reply to Thread" or "Quick Reply" options, the **#** icon will not appear: these options provide a minimal set of icons. In that case you can carefully type in the tags yourself or click on "Go Advanced" below the posting area's text box to make the **#** icon (and other icons) appear.

Your image showed a CPU temperature of 61 degrees Celsius. Unless you were doing something really CPU intensive, that's bad.

Have you cleaned your laptop recently?

Anyway, if you go for a change in flavor, I suggest doing a clean install after backing up your data. I don't like adding a new desktop environment and logging into that even if it's easier.

I also suggest you stay on 16.04 and use the first release so that you'll be on an older kernel channel. Newer kernels are for newer hardware. In this context see wiki.ubuntu.com/Kernel/LTSEnablementStack.

You may have to search for the first release of 16.04.0 for your flavor. 
Some links: 
[http://old-releases.ubuntu.com/releases/16.04.0/](http://old-releases.ubuntu.com/releases/16.04.0/)
[http://cdimage.ubuntu.com/kubuntu/releases/16.04/release/](http://cdimage.ubuntu.com/kubuntu/releases/16.04/release/)

Thanks  lot for the help :)

I had just Chrome, Foxit Reader and Video(application) running at that moment. My Laptop heats a lot and the fan is running almost all the time. (Please suggest any remedy for it :( )
I did not perform any Hardware or software cleanup recently. Should I do that ? 

Do u mean Xubuntu 16.04 ?

---

### Post by vasa1 on 2017-08-20
Look under your laptop. Is there a lot of dust on the air-vents? Is your laptop placed on a hard surface with good air-flow?

16.04 of any sort. Xubuntu may not be a bad idea.

---

### Post by sp40140 on 2017-08-20
Your issues stem from poorly designed hardware (along with old age). If the heat can't get out easily, it will constantly make cpu throttle. 
Fans run constantly as the temp runs high.
You should open it up and clean up any / all dust (carefully). Also, at least clean up air vents. 
I suggest you always keep your laptop on hard surface like table (and not mattress or pillows or even laps which can suffocate the airflow). 
Also as trial, buy a laptop cooling pad. They are cheap. They come with fans so help a lot with heat management. It's not very convenient, but gives you best chance of fixing the problems.
And you manage the heat better, you will see performance jump as cpu doesn't have to choke performance because of heat.

Also, use xubuntu, lubuntu or Elementry OS as they are not as resource hungry. Changing the distro will help a little, but it will be moot if you can't fix the heat issue.

That's why I always suggest people to get better designed laptops. They cost more but worth it.

---

### Post by gordintoronto on 2017-08-20
sp40140 +1

The CPU fan is probably half-clogged with dust.

I'm about to do the same thing with my 7-year-old HP G64. I found detailed instructions online.

---

### Post by Cpyles07 on 2017-08-21
I have bought and been given so many "broken" laptops and desktops that are just clogged up with dust. The one im on now was so bad it would shut off 10 seconds after powering on. So definitely check the vents and fan.

---


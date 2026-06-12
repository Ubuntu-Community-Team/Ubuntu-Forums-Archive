---
title: "Will Ubuntu 12.10 work on my netbook"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by kamehamehack on 2013-03-25
Will ubuntu 12.10 work on my hp mini 110 please help and how can wifi work on it

---

### Post by carl4926 on 2013-03-25
You can try it live
It works on my eeepc
But xubuntu is better

wifi works OOTB for me but I don't know what hardware your HP has

---

### Post by Adi Krishnan on 2013-03-25
With Mint Julia, I had issues connecting to WiFi. Apparently, I had to install the WiFi driver using a wired connection before I could use WiFi. I'm not sure if this is the case with yours but if it helps, then great.

Good Luck!

---

### Post by kamehamehack on 2013-03-26
here are my specs in the screen below 

  [SIZE=6][ATTACH=CONFIG]240572[/ATTACH] [SIZE=2]will it work on these specs and will it work on 1024x600 resolution READ UPDATE HERE[/SIZE][/SIZE]

---

### Post by carl4926 on 2013-03-26
Here are mine:

```
Machine:   System: ASUSTeK product: 1015PEM version: x.x           Mobo: ASUSTeK model: 1015PE version: x.xx Bios: American Megatrends version: 0904 date: 11/16/2010
CPU:       Dual core Intel Atom CPU N550 (-HT-MCP-) cache: 512 KB flags: (lm nx sse sse2 sse3 ssse3) 
           Clock Speeds: 1: 1000.00 MHz 2: 1000.00 MHz 3: 1000.00 MHz 4: 1000.00 MHz
Graphics:  Card: Intel Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller 
           X.Org: 1.13.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1024x600@60.0hz 
           GLX Renderer: Mesa DRI Intel IGD GLX Version: 1.4 Mesa 9.0.2
Audio:     Card: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel Sound: ALSA ver: 1.0.25
Network:   Card-1: Atheros AR8132 Fast Ethernet driver: atl1c 
           IF: eth0 state: down mac: bc:ae:c5:63:3d:82
           Card-2: Ralink RT3090 Wireless 802.11n 1T/1R PCIe driver: rt2800pci 
           IF: wlan0 state: up mac: 48:5d:60:41:41:7d
Drives:    HDD Total Size: 250.1GB (7.7% used) 1: id: /dev/sda model: ST9250315AS size: 250.1GB 
Partition: ID: / size: 21G used: 4.9G (25%) fs: ext4 ID: /home size: 68G used: 14G (21%) fs: ext4 
           ID: swap-1 size: 4.33GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 67.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 155 Uptime: 20:34 Memory: 625.4/1993.6MB Client: Shell inxi: 1.8.4 



```

I suggest you use Xubuntu

---

### Post by kamehamehack on 2013-03-26
what is xubuntu and READ UPDATE ABOUT SPECS

[COLOR=#000000][INDENT]here are my specs in the screen below 

[SIZE=6][[IMG]http://ubuntuforums.org/attachment.php?attachmentid=240572&d=1364277172&thumb=1[/IMG]]("http://ubuntuforums.org/attachment.php?attachmentid=240572&d=1364277172") [SIZE=2]will it work on these specs and will it work on 1024x600 resolution[/SIZE][/SIZE][/INDENT]
[/COLOR]

---

### Post by carl4926 on 2013-03-26
Yes it will work
Xubuntu is Ubuntu but it uses a lighter desktop called XFCE
[http://xubuntu.org/](http://xubuntu.org/)

I also use a Ubuntu derivative call **Mint**, the MATE desktop version works very well.
[http://blog.linuxmint.com/?p=2216](http://blog.linuxmint.com/?p=2216)

---

### Post by kamehamehack on 2013-03-26
but how to make wifi work cause it doesn't have a lan cable socket or something like that

---

### Post by carl4926 on 2013-03-26
> **kamehamehack said:**
> but how to make wifi work cause it doesn't have a lan cable socket or something like that

Have you booted a live USB of Xubuntu? or any Linux distro? Did your wireless not work?

I have no idea what wireless device you have

---

### Post by kamehamehack on 2013-03-26
UPDATE my wifi card it is broadcom 802.11 wireless lan adapter

---

### Post by kamehamehack on 2013-03-26
wifi is broadcom 802.11 wireless lan adaptor

---

### Post by carl4926 on 2013-03-26
> **kamehamehack said:**
> wifi is broadcom 802.11 wireless lan adaptor

I figured you'd come back with some pretty useless info

No offence, but windows doesn't provide the kind of info we need.

But I can tell you, it will probably work.

What you could do is:

1. Make a bootable USB of Xubuntu

2. When it's up and running (if the wireless isn't working, and it probably won't) open a terminal and paste in this:

```
lspci -nnk | grep -iA2 net
```
You will have to save it to a file to get it to us here. So it will require some ingenuity on your part.

See what happens though when you boot Xubuntu, because IIRC it had some broadcom drivers in the live system.

---

### Post by kamehamehack on 2013-03-26
but does that command work in ubuntu 12.10

---

### Post by carl4926 on 2013-03-26
> **kamehamehack said:**
> but does that command work in ubuntu 12.10
Assuming it's a built in wireless and not a dongle?

---

### Post by nonedrinkwater on 2013-03-26
> **carl4926 said:**
> Here are mine:

```
Machine:   System: ASUSTeK product: 1015PEM version: x.x           Mobo: ASUSTeK model: 1015PE version: x.xx Bios: American Megatrends version: 0904 date: 11/16/2010
CPU:       Dual core Intel Atom CPU N550 (-HT-MCP-) cache: 512 KB flags: (lm nx sse sse2 sse3 ssse3) 
           Clock Speeds: 1: 1000.00 MHz 2: 1000.00 MHz 3: 1000.00 MHz 4: 1000.00 MHz
Graphics:  Card: Intel Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller 
           X.Org: 1.13.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1024x600@60.0hz 
           GLX Renderer: Mesa DRI Intel IGD GLX Version: 1.4 Mesa 9.0.2
Audio:     Card: Intel NM10/ICH7 Family High Definition Audio Controller driver: snd_hda_intel Sound: ALSA ver: 1.0.25
Network:   Card-1: Atheros AR8132 Fast Ethernet driver: atl1c 
           IF: eth0 state: down mac: bc:ae:c5:63:3d:82
           Card-2: Ralink RT3090 Wireless 802.11n 1T/1R PCIe driver: rt2800pci 
           IF: wlan0 state: up mac: 48:5d:60:41:41:7d
Drives:    HDD Total Size: 250.1GB (7.7% used) 1: id: /dev/sda model: ST9250315AS size: 250.1GB 
Partition: ID: / size: 21G used: 4.9G (25%) fs: ext4 ID: /home size: 68G used: 14G (21%) fs: ext4 
           ID: swap-1 size: 4.33GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present
Sensors:   System Temperatures: cpu: 67.0C mobo: N/A 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes: 155 Uptime: 20:34 Memory: 625.4/1993.6MB Client: Shell inxi: 1.8.4 



```

I suggest you use Xubuntu

how did you get the output look that? was it done in linux?

---

### Post by AndyOpie150 on 2013-03-26
Read this: [https://www.linuxdistrocommunity.com/forums/showthread.php?tid=524](https://www.linuxdistrocommunity.com/forums/showthread.php?tid=524)
Explains how to get Xubuntu, Mint, Snowlinux, Peppermint, Puppy Slacko, etc, on to flash drive and make them bootable.

You will need a wired connection to get wireless working, except on Puppy Slacko which has a repostory of wireless drivers.

Ubuntu, Kubuntu, and most of the other CPU/GUI intensive Distros shouldwork on the newer netbooks with a 4GB or better of RAM. Assuming the graphics card is decent. 

If it where me, I would install Xubuntu, Mint, Snowlinux, or Peppermint. Then put Puppy Slacko on the USB full time.

---

### Post by carl4926 on 2013-03-26
> **nonedrinkwater said:**
> how did you get the output look that? was it done in linux?

Install inxi

then

```
inxi -F
```

---

### Post by kamehamehack on 2013-03-26
oh WHAT 4GB OF RAM mine is 1gb is it okay

---

### Post by kamehamehack on 2013-03-26
> **carl4926 said:**
> Assuming it's a built in wireless and not a dongle? and btw it is built in

---

### Post by carl4926 on 2013-03-27
> **kamehamehack said:**
> oh WHAT 4GB OF RAM mine is 1gb is it okay

2GB actually
It came with 1GB and worked
Originally it shipped with win7 and was a dog with 1GB

I wiped the HD and split it up for daily use and sandboxing
Currently the HD looks like this
[[img]http://storage9.static.itmages.ru/i/13/0327/s_1364360674_3889663_9eb50ba0dc.png[/img]](http://itmages.ru/image/view/956976/9eb50ba0)

---

### Post by c24ck32 on 2013-03-27
> **kamehamehack said:**
> UPDATE my wifi card it is broadcom 802.11 wireless lan adapter

It should work, have you try the live cd?

I have to agree with the others that go with xubuntu, it is designed to run on machine with low specs.

---

### Post by anandu on 2013-03-27
mine is also Broadcom BCM4313 802.11b/g/n Wireless LAN Controller 
driver: brcmsmac 

But am using linux mint 13 (based on ubuntu 12.04) xfce edition.great performance in my asus eee pc 1015cx.

HP is also using same configuration like asus.

Go for mint.it comes with mp3 codecs as well.u dont need to download it.in built vlc player etc


[www.**linuxmint**]("http://www.linuxmint.com/rel_maya_xfce_whatsnew.php")[.com/rel_maya_[URL="http://www.linuxmint.com/rel_maya_xfce_whatsnew.php"]**xfce**]("http://www.linuxmint.com/rel_maya_xfce_whatsnew.php")_whatsnew[/URL][.php]("http://www.linuxmint.com/rel_maya_xfce_whatsnew.php")


hope this helps

Anandu

[www.ananduvr.com](www.ananduvr.com)

---

### Post by musicmanbiker on 2013-03-27
Following this thread because I have the same machine and already have 12.10 on it. Of course the wireless doesn't work and I'm old and a newbie to this. Can I overwrite the ubuntu with xubuntu? And how? Or is there a fix for ubuntu that someone could "guide" me through? Thanks John

---

### Post by mastablasta on 2013-03-27
> **musicmanbiker said:**
>  Can I overwrite the ubuntu with xubuntu? And how? Or is there a fix for ubuntu that someone could "guide" me through? Thanks John
Yes you can ovewrite the OS or simply search for xubutnu-desktop in software center install it and then on loging in select xubuntu. you can later remove gnome if you wish to keep xubuntu.

---

### Post by musicmanbiker on 2013-03-27
Thanks masta, very quick. Can you or someone tell me how to overwrite it?

---

### Post by carl4926 on 2013-03-27
> **musicmanbiker said:**
> Thanks masta, very quick. Can you or someone tell me how to overwrite it?

Just go this route
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

And point to your existing partition
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)
You likely only have root (/)
So you should backup your files

---


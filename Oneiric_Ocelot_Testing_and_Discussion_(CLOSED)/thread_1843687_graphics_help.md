---
title: "graphics help"
date: 2011-09-13
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by raja.genupula on 2011-09-13
Hi Friends i am using Ubuntu 11.10 .
configuration of my PC is 
RAM-2GB
Dual core processor with 3Ghz 

while i am using any application , if i minimize it then i am finding some lines on the screen , i tried to capture them but when i did it they automatically gone . i found temporary solution is if we click , right click as dragging(moving cursor by holding right click) . i am thinking that this must be a graphical issue , so please help me guys to solve it .

---

### Post by cariboo on 2011-09-13
What graphics device and driver is your system using? The amount of ram and cpu aren't important in this case.

---

### Post by raja.genupula on 2011-09-14
Intel graphics i think

---

### Post by 2F4U on 2011-09-14
What desktop environment are you using? I have kind of a similar effect in Xubuntu when I am using Thunderbird. I have a Intel 950 graphics card. In my case, this effect occurs only in Thunderbird, so I don't care much about it.

---

### Post by raja.genupula on 2011-09-14
i am getting it in the ubuntu 11.10  only .

---

### Post by raja.genupula on 2011-09-14
here  i am attatching my system info text file  and done with 
```
sudo dmidecode
```
command

thanks in advance

---

### Post by lucazade on 2011-09-14
This text file doesn't tell too much about your system.
Paste the output of this to know what graphic card you have:

```
sudo lshw -C video

```

then tell us what DE are you using (gnome,xfce,kde..) and what shell on top of it (Unity, unity-2d, gnome-shell).
Was this issue present in old ubuntu release?
Can you make a screenshot of the graphic glitch (also with a cam if needed)?

---

### Post by cariboo on 2011-09-14
That file really doesn't tell us what we want to know. Can you paste the output of:

```
lspi | grep VGA 
```

or

```
sudo lshw -C display
```

in your next post.

---

### Post by raja.genupula on 2011-09-14
> **lucazade said:**
> This text file doesn't tell too much about your system.
Paste the output of this to know what graphic card you have:

```
sudo lshw -C video

```

then tell us what DE are you using (gnome,xfce,kde..) and what shell on top of it (Unity, unity-2d, gnome-shell).
Was this issue present in old ubuntu release?
Can you make a screenshot of the graphic glitch (also with a cam if needed)?

this is the output of ```
sudo lshw -C video

``` 

```
assassin@raju-xubuntu:~$ sudo lshw -C video
[sudo] password for assassin: 
  *-display:0             
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fd800000-fdbfffff memory:d0000000-dfffffff ioport:ff00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:fde00000-fdefffff
assassin@raju-xubuntu:~$ 


```
i am using Ubuntu-desktop installed xubuntu 11.10 , with unity .
i am facing this issue first time and that too in 11.10 . so i am thinking that i have to install graphic driver .

---

### Post by raja.genupula on 2011-09-14
> **cariboo907 said:**
> That file really doesn't tell us what we want to know. Can you paste the output of:

```
lspi | grep VGA 
```

or

```
sudo lshw -C display
```

in your next post.

```
assassin@raju-xubuntu:~$ lspi | grep VGA
No command 'lspi' found, did you mean:
 Command 'lspci' from package 'pciutils' (main)
lspi: command not found

```



```
assassin@raju-xubuntu:~$ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:fd800000-fdbfffff memory:d0000000-dfffffff ioport:ff00(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:fde00000-fdefffff

```

sudo lshw -C display  & sudo lshw -C video both are giving the same  output  , i think

---

### Post by realzippy on 2011-09-14
```
configuration: driver=i915
```
..means,the intel driver for your intel graphics is working.
There is no driver you can install...

---

### Post by raja.genupula on 2011-09-14
> **realzippy said:**
> ```
configuration: driver=i915
```
..means,the intel driver for your intel graphics is working.
There is no driver you can install...
Hi 
   but why i am getting the shades on desktop , read post one

---

### Post by lucazade on 2011-09-14
as realzippy stated you already have drivers installed..
i suggest you to open a bug report against unity and explain the issue attaching a screenshot

```
ubuntu-bug unity
```

from terminal

---

### Post by raja.genupula on 2011-09-14
> **lucazade said:**
> as realzippy stated you already have drivers installed..
i suggest you to open a bug report against unity and explain the issue attaching a screenshot

```
ubuntu-bug unity
```

from terminal

i couldnt able to  make a shot , because when i press at any application to open which is minimized or  print screen key on the keyboard , those shades are clearing  . actually while making the first post only i had tried to make a screen shot .  i will use my friends mobile to capture the area , how is it sounds ?

---

### Post by RomeReactor on 2011-09-14
This might be the relevant bug report:

[minimizing a maximized window leaves artifacts on the screen]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/835994")

I get that frequently when minimizing Firefox.

---

### Post by raja.genupula on 2011-09-14
> **RomeReactor said:**
> This might be the relevant bug report:

[minimizing a maximized window leaves artifacts on the screen]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/835994")

I get that frequently when minimizing Firefox.

yes , same issue .

---

### Post by raja.genupula on 2011-09-14
i have seen that bug reported in launchpad , same issue . i also notified that, it effects my system  also.

thanks to all for spending your great time . 
i am closing this .

---


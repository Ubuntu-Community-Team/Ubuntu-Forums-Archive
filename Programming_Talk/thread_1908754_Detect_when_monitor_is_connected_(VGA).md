---
title: "Detect when monitor is connected (VGA)"
date: 2012-01-14
forum: Programming Talk
---

### Post by xzased on 2012-01-14
Hi guys. Im trying to find a way to detect when a monitor is connected to the vga port in my laptop (also, if possible, if it is turned on). I've read some blogs and articles on the net, and they point to check /sys/class/drm/cardX, but looking at my installation there is no drm folder under /sys/class. Any pointers are appreciated.

---

### Post by xzased on 2012-01-16
just one bump :P

---

### Post by craigp84 on 2012-01-16
Hi,

Try:
```
xrandr | grep VGA | grep "connected"
```

---

### Post by xzased on 2012-01-16
This is my xrandr output, I have a nvidia card, the monitor is setup in twinview mode:


```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 3286 x 1080, maximum 3286 x 1080
default connected 3286x1080+0+0 0mm x 0mm
   1366x768       50.0     51.0    107.0  
   1360x768       52.0  
   1024x768       53.0     54.0     55.0  
   960x540        56.0  
   840x525        57.0     58.0  
   832x624        59.0  
   800x600        60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   720x400        67.0  
   700x525        68.0     69.0  
   680x384        70.0     71.0  
   640x512        72.0     73.0  
   640x480        74.0     75.0     76.0     77.0     78.0     79.0  
   640x400        80.0  
   640x350        81.0  
   576x432        82.0     83.0     84.0     85.0     86.0     87.0     88.0  
   512x384        89.0     90.0     91.0     92.0     93.0  
   416x312        94.0  
   400x300        95.0     96.0     97.0     98.0     99.0  
   360x200       100.0  
   320x240       101.0    102.0    103.0    104.0  
   320x200       105.0  
   320x175       106.0  
   3286x1080     107.0     51.0* 
```


If I disable twinview and disconnect the monitor then plug it back in, the output is:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 1366 x 768, maximum 3286 x 1080
default connected 1366x768+0+0 0mm x 0mm
   1366x768       50.0*    51.0    107.0  
   1360x768       52.0  
   1024x768       53.0     54.0     55.0  
   960x540        56.0  
   840x525        57.0     58.0  
   832x624        59.0  
   800x600        60.0     61.0     62.0     63.0     64.0  
   800x512        65.0  
   720x450        66.0  
   720x400        67.0  
   700x525        68.0     69.0  
   680x384        70.0     71.0  
   640x512        72.0     73.0  
   640x480        74.0     75.0     76.0     77.0     78.0     79.0  
   640x400        80.0  
   640x350        81.0  
   576x432        82.0     83.0     84.0     85.0     86.0     87.0     88.0  
   512x384        89.0     90.0     91.0     92.0     93.0  
   416x312        94.0  
   400x300        95.0     96.0     97.0     98.0     99.0  
   360x200       100.0  
   320x240       101.0    102.0    103.0    104.0  
   320x200       105.0  
   320x175       106.0  
   3286x1080     107.0     51.0  
```

---

### Post by WasMeHere on 2012-01-16
Hi xzased,

You can log in to your Ubuntu computer via ssh (remote login) without any monitor attached. And then you can run (almost) any program you want interactively. But I guess you want the computer to detect automatically, if a monitor is connected (not only during boot).

I use a KVM switch to connect one single desktop (monitor, keyboard, mouse and loadspeakers) to several computers. If I start a computer when another computer is connected via the KVM switch, Ubuntu defaults to low graphics; obviously it does not see the monitor. So I would be interested in an automatic way for the computer to see a monitor (and set the graphics according to the current monitor).

Maybe one way to find out is to log in via ssh and try interactively, and then make some script (cron job?) from that.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by WasMeHere on 2012-01-16
We were posting at the same time. Thanks,*craigp84*, I think we can use xrandr in some automatic script to check if and how a monitor is connected :-)

---

### Post by xzased on 2012-01-16
Actually, what Im trying to do is write a python service that monitors when the monitor is plugged in, if it does find one it will ask you to do whatever changes you want to your X config and save them as an alternative xorg.conf file, that way, when you connect the monitor again in the future it will apply those same settings automatically, makes it easy for me since I have different monitor setups at home and at work.

---

### Post by WasMeHere on 2012-01-16
> **xzased said:**
> Actually, what Im trying to do is write a python service that monitors when the monitor is plugged in, if it does find one it will ask you to do whatever changes you want to your X config and save them as an alternative xorg.conf file, that way, when you connect the monitor again in the future it will apply those same settings automatically, makes it easy for me since I have different monitor setups at home and at work.

That is a great idea, and it would be nice if you can shared it at the Ubuntu Forums :-)

---


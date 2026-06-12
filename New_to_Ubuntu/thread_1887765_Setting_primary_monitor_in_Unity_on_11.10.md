---
title: "Setting primary monitor in Unity on 11.10"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by marenum on 2011-11-27
Since I upgraded to 11.10, attempting to run in twinview has been a bit of a headache. While switching to twinview upon startup, I always have to first set the monitors as clones, and then set one left and one right. If I don't do it in that order I usually have to restart because the screen stays blank. I don't really mind doing this, but it causes every window to open on my right monitor which is actually my HDTV. I've been going insane trying to set my left monitor as the primary, but nothing seems to work. Most of the tutorials are before Unity, and the rest of them just haven't solved the issue. Has anyone had the same issue, or could help me resolve it?

---

### Post by FatFrog on 2011-11-27
I have been having a slightly similar issue to yours in my streaming content, when made fullscreen seemed to always default to my VGA connected screen and not my DVI. I am still looking for the best work around for my solution, but the one described in this post may help you with your issue.
[http://ubuntuforums.org/showthread.php?t=1309247](http://ubuntuforums.org/showthread.php?t=1309247)


Good luck. keep us posted.

---

### Post by marenum on 2011-11-28
Thank you for your reply. I've experimented with using xrandr to set the primary monitor. My output from "xrandr --prop" is:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 175, current 3600 x 1080, maximum 3600 x 1080
default connected 3600x1080+0+0 0mm x 0mm
   1680x1050      50.0     51.0    148.0  
   1600x1024      52.0  
   1440x900       53.0  
   1400x1050      54.0     55.0     56.0  
   1360x768       57.0     58.0  
   1280x1024      59.0     60.0     61.0  
   1280x960       62.0     63.0  
   1152x864       64.0     65.0     66.0     67.0     68.0     69.0     70.0  
   1024x768       71.0     72.0     73.0     74.0     75.0     76.0  
   960x720        77.0     78.0  
   960x600        79.0  
   960x540        80.0  
   928x696        81.0     82.0  
   896x672        83.0     84.0  
   840x525        85.0     86.0     87.0     88.0     89.0  
   832x624        90.0  
   800x600        91.0     92.0     93.0     94.0     95.0     96.0     97.0     98.0     99.0    100.0  
   800x512       101.0  
   720x450       102.0  
   720x400       103.0  
   700x525       104.0    105.0    106.0    107.0  
   680x384       108.0    109.0  
   640x512       110.0    111.0    112.0  
   640x480       113.0    114.0    115.0    116.0    117.0    118.0    119.0  
   640x400       120.0  
   640x350       121.0    122.0  
   576x432       123.0    124.0    125.0    126.0    127.0    128.0    129.0  
   512x384       130.0    131.0    132.0    133.0    134.0  
   416x312       135.0  
   400x300       136.0    137.0    138.0    139.0    140.0  
   360x200       141.0  
   320x240       142.0    143.0    144.0    145.0  
   320x200       146.0  
   320x175       147.0  
   1920x1080     148.0  
   3600x1080      50.0* 

```
I'm not sure if I'm missing something, but I don't think the displays are being listed properly here so I can't use the command to change them.

---

### Post by FatFrog on 2011-11-28
What's your video card situation? I know ATI drivers are kind buggy with the 11.10 release.

---


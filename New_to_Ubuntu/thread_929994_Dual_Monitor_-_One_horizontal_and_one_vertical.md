---
title: "Dual Monitor - One horizontal and one vertical?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by cefs99 on 2008-09-25
Hi All,

I did some search here but cannot find similar questions.

I am currently use a Thinkpad T61 laptop with a ThinkVision 20" monitor. With xrandr,I configure both as one virtual monitor and things work great.


Now I think by turning my 20" monitor to a vertical setting can make my work more efficiently. But seems the menu System=>preference=>screen resolution cannot help. It successfully display my two monitor. When I try to select "right" from drop down menu of "Rotation" and click Apply, it simply doesn't work.


li@li-laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 3120 x 1050, maximum 3120 x 1050
VGA connected 1680x1050+1440+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0 +   74.9*    60.0  
   1280x1024      75.0     71.9     59.9  
   1440x900       75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     65.4     60.0  
   720x400        70.1  
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1440x900       60.0*+   50.0  
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0     59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)


Is it because by turning my 20" monitor vertically it will break the current configuration of the extended desktop which is 3120(laptop: 1440+VGA 1680)x1050(VGA 1050 exceed the laptop 900)? is it necessary to add a new mode which is 2490 (laptop 1440+VGA 1050) x 1680 (VGA 1680 exceed the laptop 900)?


Thanks,

L

---


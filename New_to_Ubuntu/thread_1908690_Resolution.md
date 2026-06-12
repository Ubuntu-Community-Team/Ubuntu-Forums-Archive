---
title: "Resolution"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by matt0076 on 2012-01-13
I own a Sony laptop capable of 1600x900 resolution, however upon downloading ubuntu and splitting my hard drive I'm operating on a 800x600. When I go to System>Preferences>Monitors it only lets me switch between 800x600 and 640x480. I've looked online and cannot seem to resolve this by myself.


xrandr:

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  
  1600x900_60.00 (0x11d)  118.0MHz
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock   55.9KHz
        v: height  900 start  903 end  908 total  934           clock   59.8Hz



Help?

---

### Post by Gone fishing on 2012-01-14
I'd first check if you need to install a driver for the video open the additional drivers application, is there any drver that needs activating?

---

### Post by matt0076 on 2012-01-14
> **Gone fishing said:**
> I'd first check if you need to install a driver for the video open the additional drivers application, is there any drver that needs activating?

Nope.


I should also add I'm using 10.04

---

### Post by matt0076 on 2012-01-14
double post

---

### Post by Gone fishing on 2012-01-14
What laptop are you using what vdeo deos it use?

---

### Post by Mark Phelps on 2012-01-15
Open a terminal and enter "lspci".  Look for the line containing "VGA" -- and post the results here.  That will tell us the make and model of your video chipset.

---

### Post by Fernhill Linux Project on 2012-01-15
:o)

---


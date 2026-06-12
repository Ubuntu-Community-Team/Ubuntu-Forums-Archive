---
title: "black and white lines"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by prestoaa on 2008-08-02
Tried to install Ubuntu. It seemed to be working OK and the orange line got to the end of the bar. Then as the Ubuntu logo disappeared all that appeared were black and white lines.

Is this likely to be the video card a Nvidia or could it be the monitor - a Sony TV with a PC input.

Whichever, what is the solution.

---

### Post by phidia on 2008-08-02
The nvidia card is pretty well supported/recognized in linux although it would be nice to know what model card you have. > lspci | grep VGA in a terminal will provide that. 
I suspect the TV as a monitor is the problem but what model TV is the Sony and what is the specific connection type?

---

### Post by phidia on 2008-08-02
I forgot to mention make sure you have the nvidia driver enabled. 
When you first installed (do you have hardy 8.04?) did you get a hardware driver icon on your top panel? 
For most nvidia cards you just want to install nvidia-glx. There is also a nvtv package that might help in your situation. 

Fpr more info on multimedia you can look at [this]("http://ubuntuforums.org/showthread.php?t=766683").
The Ubuntu video wiki is [here]("https://help.ubuntu.com/community/Video").

---


---
title: "Cannot boot to GUI display"
date: 2017-01-08
forum: New to Ubuntu
---

### Post by daniel852 on 2017-01-08
Hello all,

_The setup_

Ubuntu 16.04
Dell Inspiron 7559, GTX960m running bumblebee

_The problem_

When I switch on the machine I get one of two outcomes: either a completely blank screen (no usual Ubuntu graphical loading animation) or a message saying "/dev/sda2: clean XXXXfiles, XXXXblocks".

I can get into command line using shortcuts and can access the filesystem and am connected to the web so can perform installations/updates.

I thought the problem could be as simple as the brightness settings (I had the brightness turned very low before switching off yesterday, and previously on another machine fixed using brightness shortcuts, however, the FN + F12 shortcut does not work on this machine because of the dual graphics card setup. When I installed and tried to use xbacklight I get an error message "RANDR Query version returned error -1"

I also don't seem to be able to enter Grub at startup.

Up until I powered off the machine yesterday I had no issues.

I did not carry out an update immediately prior to the problem occurring.

I've had a look at other similar questions and solutions on here, but cannot seem to find a solution.

Any help would be HUGELY appreciated. If you need any further specific information or want me to run any tests please let me know. Very much a beginner.

Many thanks,

---

### Post by daniel852 on 2017-01-08
Apologies, I discovered the problem and it's fixed.

I had followed these [instructions]("http://askubuntu.com/questions/766725/annoying-flickering-in-16-04-lts-chrome") yesterday to edit the usr/share/X11/xorg.conf.d/20-intel.conf file to stop screen tearing in Chrome. I deleted the additions to the configuration file, rebooted, and have reached the lightdm login screen with no problem.

---


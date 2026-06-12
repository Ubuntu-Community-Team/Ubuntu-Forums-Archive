---
title: "Resolution issue with older of two same model monitors"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Odyssey1942 on 2008-08-15
I have been using Ubuntu 7.04 on a 1 to 1-1/2 year old 19" Sceptre lcd monitor for some time and want to move that computer to another location and use it alongside a Windoze machine with a KVM also with an (older) Sceptre 19" lcd monitor allowing me to switch between the two. It works OK except for one thing.

The natural resolution for each screen is 1024 x 768. Ubuntu comes up just fine in that resolution on the newer monitor I had been using. But it only comes up in 800 x 600 on the older monitor in the new setup using the KVM. I went to the System/Preference/Screen Resolution, but it only offers a lower resolution (640 X 480), not the 1024 x 768 that I want and need.

Is this likely because the monitor that I want to use is older than the one that works correctly or because of the KVM?

Any ideas welcome. TIA

---

### Post by rossjman1 on 2008-08-15
Go to the terminal and type
```
sudo dpkg-reconfigure xserver-xorg
```
Let it autodetect everything (just keep pressing enter to keep your settings). At one point it will ask you what resolutions you want to enable. Scroll down the list with the arrow keys and to enable a selected res press the spacebar. When you are done press enter. You will need to restart x by pressing ctrl-alt-backspace after you are done.

---

### Post by Odyssey1942 on 2008-08-15
Thanks for that. Tried it and "entered" through 2 screens and got to a screen:

"&#9474; Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000 
(....more....)

with an OK at the bottom of the screen. No amount of <enters> or clicking on the <OK> progresses to the next screen. I'm stuck :confused:

P.S. I'm awed that you know this.

---

### Post by Odyssey1942 on 2008-08-16
Anyone else?  TIA

---

### Post by Odyssey1942 on 2008-08-18
Solution found: 

The following articles are helpful: 

1.  [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

and

2. [HOWTO: YES! There IS an easy, safe way of reloading Xorg.conf without shutting down X - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=679059)

A combination of the two results in a changed xorg.conf file and when a second session is started, the screen still comes up in the lower resolution.

However, clicking on System/Preferences/Screen Resolution shows that the desired resolution choice is now available. Choosing the desired resolution implements properly.

Thanks for your help.

---


---
title: "No Sound, Network and Keyboard repeating"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by poscomp on 2008-09-01
Please help. I almossst haave it. I haave  sound  wwith Visstaa but  no  sssoundd in 8.04. 8.04 sees my netwwork  but not drivess or printers attached to Vistaa ccomputer. Andd, as yoou  cccaan  ssee  my keyboard repeaatss unccontrollibly.  Thaanksss.

---

### Post by drs305 on 2008-09-01
You will probably have to be more specific. Let's start with the basics:

Sound: 
Double click the speaker icon in the panel and check the volume sliders levels, especially the Master and PCM one. You can also run "alsamixer" and check the volume levels there. Use the arrow keys to select the column and volume levels.

Have you gone to System, Preferences, Sound, Devices and tried the Test button to check if you can hear anything? Try changing to any device available - ALSA, PulseAudio, etc, and hitting the Test button again.

Printer:
System, Administration, Printing. What happens when you select New Printer? And what kind of printer do you have? Since it is on a network you are going to have to get that working first.
Samba is the normal way, but not only way, to connect to a windows machine. There is plenty of documentation on how to set up SAMBA.

Keyboard:
Have you gone to System, Preferences, Keyboard, Layouts and tried a different keyboard? Also in the General tab there is a slider for the delay for key press repeats. You might be able to solve your problem by changing the value there.  Moving the Delay keys slider toward 'Long' will probably fix this problem.

---

### Post by poscomp on 2008-09-01
Keyboard problem solved. Now all I need is to attach to my network. It sees the workgroup and it sees the computer name, I know the connection is gook as this notebook sees the drives and printers when in Vista. Ideas, anyone?

---


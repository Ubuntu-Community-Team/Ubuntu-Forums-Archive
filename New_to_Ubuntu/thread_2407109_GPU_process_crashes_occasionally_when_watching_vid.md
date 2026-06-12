---
title: "GPU process crashes occasionally when watching videos"
date: 2018-11-29
forum: New to Ubuntu
---

### Post by endershadow on 2018-11-29
I'm not really sure what the solution to this problem is. Here's the relevant part from the log files.

```
Nov 29 17:20:41 matthew-ubuntu org.gnome.Shell.desktop[2603]: [10622:10622:1129/172041.872664:ERROR:gles2_cmd_decoder.cc(4583)]   GLES2DecoderImpl: Context reset detected after MakeCurrent.
Nov 29 17:20:41 matthew-ubuntu org.gnome.Shell.desktop[2603]: [10622:10622:1129/172041.872683:ERROR:gpu_channel_manager.cc(213)] Exiting GPU process because some drivers cannot recover from problems.
Nov 29 17:20:41 matthew-ubuntu org.gnome.Shell.desktop[2603]: [10622:10622:1129/172041.873130:ERROR:gpu_channel_manager.cc(213)] Exiting GPU process because some drivers cannot recover from problems.
```

My computer has a GTX 1080 Founders Edition and no integrated graphics. When the GPU process crashes audio still plays, but the keyboard and mouse lockup. The only way I've found to get back into the computer without restarting it is to kill gnome-shell.

---

### Post by wildmanne39 on 2018-11-29
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by Autodave on 2018-11-30
What, if any, driver did you install for the Nvidia card?  Where did you get it from?

---

### Post by endershadow on 2018-11-30
I've installed the proprietary nvidia driver. I'm currently using the latest which is 415

---

### Post by Autodave on 2018-11-30
I am assuming that you d-led that driver from the repositories?  If not, that could be the problem.  Again I am assuming that you have the eight pin power cable hooked up?  That card takes a good deal of power to run and you could be experiencing low power failures.  How about ventilation/cooling?  All fans working properly?  You can always remove the cover of the PC and try it that way to see if additional cooling will cure the problem.

---

### Post by endershadow on 2018-11-30
I did download the drivers from the repository, the eight pin power cable is hooked up, and my PSU shouldn't be getting overdrawn. All fans are working too.

---

### Post by Autodave on 2018-11-30
Do you happen to know the power rating of your power supply?

---

### Post by endershadow on 2018-11-30
It's rated for 750W continuously and pcpartpicker says my build only uses 450W. When using outervision's power supply calculator it says My load wattage is 650W which is still below 750W.

---

### Post by Autodave on 2018-12-01
I would try removing the PC access panel to let more cool air in.  I would also make sure that the cooling fins on the CPU are clogged with debris.

---

### Post by endershadow on 2018-12-01
Alright. I'll test that out and report back. Another interesting thing I've noticed about the issue though. I have 2 monitors, one plugged into a DVI port and another into a DisplayPort. The issue hasn't occurred since I started playing videos on the DVI monitor.

---


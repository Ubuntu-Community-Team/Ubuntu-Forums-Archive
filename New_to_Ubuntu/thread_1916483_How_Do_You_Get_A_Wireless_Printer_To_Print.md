---
title: "How Do You Get A Wireless Printer To Print?"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by TAspr on 2012-01-28
I have a wireless HP3050 that is networked to print.  All I want to do is print to it Wirelesly.

---

### Post by shakabra on 2012-01-28
YES! finally get to help some else do this.

Make sure the printer is connected to the same network as your computer.

Run this.
```
hp-setup -i
```

Profit.

---

### Post by ajgreeny on 2012-01-28
Make sure you also have the **hplip** package along with **hplip-gui**, either from the repos, or if that version is not up to date enough for your 3050 printer, go to the hplip website and download the newest version (3.11.12) which get you a file called hplip-3.11.12.run which you can simply run in terminal with command ```
./hplip-3.11.12.run
``` from the folder where you have the .run file.

---

### Post by TAspr on 2012-01-28
Ok, how do you get to load this in your browser?

---

### Post by mastablasta on 2012-01-28
not in browser. in terminal. or i think you can right click the file and tell it to run.

---

### Post by ajgreeny on 2012-01-29
Run it as I told you.

Open a terminal and navigate to the folder where the hplip-3.11.12.run is sitting and use command ```
./hplip-3.11.12.run
```
If you asked your browser to open the file when you clicked on the download button on the hplip web-site, this time ask to save it instead.

---

### Post by 3rdalbum on 2012-01-29
I don't know how new the 3050 is.

If the printer is supported by the version of HPLIP (HP Linux Imaging and Printing driver) that's on Ubuntu, then it's really easy to set up and requires no command-line at all.

Make sure the printer is turned on and connected to the wireless network but NOT via USB to your computer. Go to the cog menu at the top-right of your screen. Come down to Printers. Click on Add, then click on the little triangle to the side of "Network Printers". Wait a few seconds and the printer will appear in the list on the left. Click it and follow the prompts, put in the information it asks for, and then you're done.

Try that first BEFORE attempting to install a newer version of HPLIP.

---

### Post by wisdomlight on 2012-03-04
I have a HP wireless b 109(z-n) it is detected by the ubuntu 11.10 when connected with cable but not when the cable is detached.

The thread talks about adding a code.
I am not familiar with coding. 
Any help on this?

Thank you

---


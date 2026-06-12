---
title: "[SOLVED] Sending ESC Sequences to Hp Printers"
date: 2007-12-10
forum: Programming Talk
---

### Post by cmnorton on 2007-12-10
I am having trouble sending this command

[ESC] ( s 1 6 H

27 40 115 49 54 72 	16.66 cpi (132 columns in portrait, 160 landscape)

to an HP printer

My reference for this is [http://www.dragon-it.co.uk/links/hp_pcl_codes.htm](http://www.dragon-it.co.uk/links/hp_pcl_codes.htm)

I have a C program that will correctly turn a terminal emulator's VT102 port on and off, but I cannot get these esc sequences to change the HP printer's width.

I know it can be done, but cannot find the source code for a program called laserlp, which I believe is a SCO utility.

The context for this is I support an application that tried to issue all reports directly to an attached printer, so that having the reports manually queued by DP staff could be eliminated. 

The reports are formatted by Informix 4GL, and are wider than portrait mode. The laserlp utility on SCO not only sends these reports to the attached printer, but it also sends internal commands to the HP printer, so it will accommodate the wider-than-portrait report and print it within the bounds of a portrait-sized document.

Any thoughts, directions, or comments would be appreciated.

tnx
cmn

P.S. I've found the <ESC>(16H is printed rather than being interpreted. If I could figure out why this is being printed and not interpreted, that might help solve the problem.

P.P.S After further testing, I was able to get the HP printer to accept the <ESC>(s16H and go into a narrower mode.

---

### Post by gladwyn.lewis on 2010-06-01
Hi cmn,

We are trying to build an internal kiosk application with a ticket printer from Custom Engineering using the printer KPM300H, using ESC/POS Emulation to send formatting codes, etc to the printer.

I am having a bit of difficulty in figuring out how to do this, considering that our application is developed completely in Adobe AIR 2 RC 1. If you could share your experiences in more detail, especially how you were able to get this to work, it would be much appreciated.

Cheers,

Gladwyn

---


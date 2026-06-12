---
title: "Monitor calibration failed, internal error ?"
date: 2018-05-28
forum: New to Ubuntu
---

### Post by colinpt0357 on 2018-05-28
Greetings All.
After many years dabbling with linux I have now moved over completely, away from the dreaded W10!
My knowledge is limited at the moment, but I've manged to use command lines (where appropriate) to achieve a nice working system. I'm using 18.04. 
As a photographer, I am used to a managed colour work flow. I have used an i1 Display Pro for monitor calibration for some time - but on Windows. 
I have tried to use the i1 with ubuntu, which is a supported device. I follow the process to the point where I am asked to place the measuring device on the screen. When I click next to start the calibration a dialogue box pops up saying 'Internal error, Calibration failed' and I can't continue any further.
I've looked on the forums but can't get a lead as to why this is happening / the cause. Any thoughts would be appreciated.

Regards

Colin

---

### Post by Holger_Gehrke on 2018-05-28
Try to start the calibration process from the command line. Most programs on Linux send lots of diagnostic messages to the standard output (which gets either lost or stuffed into some log when a program gets started without a terminal involved). Check the manual-page ('man programname' on the command line) for the program for possible options / switches.

Holger

---

### Post by colinpt0357 on 2018-05-29
Thank you for replying Holger. I will try this and let you know !
Regards, Colin

---


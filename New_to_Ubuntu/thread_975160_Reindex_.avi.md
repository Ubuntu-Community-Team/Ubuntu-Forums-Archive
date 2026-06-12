---
title: "Reindex .avi"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by expatCM on 2008-11-08
I have an .avi which does not play.  Not quite sure why not but I thought I would rebuild the index using the following command

mencoder start.avi -o final.avi -forceidx -ovc copy -oac copy

The command does create the file final.avi but it only runs for 5 seconds.  The final file plays.  The start file does not play at all.  How do I get the command to run to process the whole file and not just the first five seconds?

---

### Post by dracayr on 2008-11-08
try using the lavc video encoder (instead of copy). Also use the -lavcopts option

dracayr

---

### Post by expatCM on 2008-11-09
Tried that ....  more or less the same thing happens but I do get some information .......

VDec: vo config request - 720 x 400 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.80:1 - prescaling to correct movie aspect.
videocodec: libavcodec (720x400 fourcc=34504d46 [FMP4])
Writing header...1f ( 0%)  0.00fps Trem:   0min   0mb  A-V:0.000 [0:0]
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

---


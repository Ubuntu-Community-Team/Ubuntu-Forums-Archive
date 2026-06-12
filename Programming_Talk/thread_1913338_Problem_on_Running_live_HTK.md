---
title: "Problem on Running live HTK"
date: 2012-01-22
forum: Programming Talk
---

### Post by beji on 2012-01-22
Hi there!
I've got the following problem: I can't run live  recogniser under Ubuntu. Got config from htkbook and HVite returns  this:
C:\htk\tutorial>HVite -H hmm15/macros -H hmm15/hmmdefs -C  config2 -w wdnet -p 0.
0 -s 5.0 dict tiedlist

READY[1]>
   ERROR [+6320]  OpenAsChannel: IOConfig tgt not a parameter kind
   ERROR [+6316]  OpenBuffer: OpenAsChannel failed
  ERROR [+3250]   ProcessFile: Config parameters invalid
 FATAL ERROR - Terminating  program HVite


i do not any change to ;y config file . 

 # Waveform capture
SOURCERATE=625.0
SOURCEKIND=HAUDIO
SOURCEFORMAT=HTK
ENORMALISE=F
USESILDET=T
MEASURESIL=F
OUTSILWARN=T

please help me m it is urgent

---

### Post by Zugzwang on 2012-01-22
Obviously, you copied most of the problem description from here: [http://www.voxforge.org/home/dev/acousticmodels/linux/create/htkjulius/tutorial/triphones/step-10/comments/running-live-htk](http://www.voxforge.org/home/dev/acousticmodels/linux/create/htkjulius/tutorial/triphones/step-10/comments/running-live-htk), including the Windows prompt, and only changed "Windows" to "Ubuntu".

There is actually a potential solution in that thread (the last post - the line ending note). Did you try it?

---

### Post by beji on 2012-01-23
I think that this solution is not appropriate to my situation , because i dont try to run live HTK under Windows but  under ubuntu and also i create all my files under linux 
so what i can do in order to solve this problem

---

### Post by Zugzwang on 2012-01-24
> **beji said:**
> I think that this solution is not appropriate to my situation , because i dont try to run live HTK under Windows but  under ubuntu and also i create all my files under linux 
so what i can do in order to solve this problem

Did you nevertheless double-check that the configuration file has the correct line-endings? The error message "IOConfig tgt not a parameter kind" could root in such a problem.

---

### Post by caba11 on 2012-02-20
hi.
i have a same problem.
If you solve it let me know please.
btw i compiled and runs HTK under windows...

thanks

---


---
title: "xpdf keep crashing"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-05-19
as soon as i open the program and try to open a pdf file it crashes. adobe and document viewer still work fine. also i uninstalled (completely deleted and removed config files) with spm. then reinstalled. problem still persists

---

### Post by billyseth on 2012-05-19
try running it from the command line and posting any errors that it outputs during the crash

---

### Post by rburkartjo on 2012-05-20
here is output


THIS IS A LINUX COMPUTER HAVE FUN
ray@ray-GC660AA-ABA-SR5123WM:~$ xpdf &
[1] 9901
ray@ray-GC660AA-ABA-SR5123WM:~$ ***** MediaBox = ll:0,0 ur:720,573
***** CropBox = ll:0,0 ur:720,573
***** Rotate = 0
gs /GS1
  gfx state dict: << /Type /ExtGState /SA false /SM 0.02 /OP false /op false /OPM 1 /BG2 /Default /UCR2 /Default /TR2 /Default >>
q
cm 720.24 0 0 573.12 0 0
Do /Im1
Q
***** page 1 *****
***** MediaBox = ll:0,0 ur:720,573
***** CropBox = ll:0,0 ur:720,573
***** Rotate = 0
gs /GS1
  gfx state dict: << /Type /ExtGState /SA false /SM 0.02 /OP false /op false /OPM 1 /BG2 /Default /UCR2 /Default /TR2 /Default >>
q
cm 720.24 0 0 573.12 0 0
Do /Im1
Q
Segmentation fault

---

### Post by Toz on 2012-05-20
It looks like a bug with libpoppler. Have a look here for the bug report and a work around: [https://bugs.launchpad.net/ubuntu/+source/xpdf/+bug/943195]("https://bugs.launchpad.net/ubuntu/+source/xpdf/+bug/943195"). Note that this bug report is an extension of the original bug report: [https://bugs.launchpad.net/ubuntu/+source/xpdf/+bug/669211]("https://bugs.launchpad.net/ubuntu/+source/xpdf/+bug/669211").

---

### Post by rburkartjo on 2012-05-20
tks toz i googled also and found a bug report dating back to 2011 but thought it was fixed by now. my bad

---

### Post by rburkartjo on 2012-05-20
going to mark as solved. if i try to install fix it will also remove my desktop not worth it.

---


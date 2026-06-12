---
title: "Compiling a program from source code for Windows"
date: 2006-07-19
forum: Programming Talk
---

### Post by sawjew on 2006-07-19
I have a very limited knowledge of programming with only a small amount of Visual Basic and Matlab/Maple experience.  I am an engineer and I need to use the modelling package SWMM (Storm Water Management Model).  Currently this is only available for Windows but the source code is also available on the US EPA website ([http://www.epa.gov/ednnrmrl/models/swmm/index.htm#Downloads]("http://www.epa.gov/ednnrmrl/models/swmm/index.htm#Downloads")).
Can anyone tell me if it is possible to compile this program to run on Linux from this source code?  I have the program working on wine but it is not entirely successful.

Any information will be appreciated.

---

### Post by x64Jimbo on 2006-07-19
The windows source will most likely not work under Linux unless it's written in a cross-platform language, but I doubt that it is since it's only published for Windows. You could try running the Windows binary version of it under Wine. Wine frequently runs Windows programs just the way they should work, especially if they don't do anything special like interact with external hardware.

---

### Post by toojays on 2006-07-19
I took a look at the download link, and the readme file for the computational engine mentions makefiles for GCC on GNU/Linux, so if you only need the engine, that should be fine. 

The the GUI part is written in Delphi, so that's Windows only.

---

### Post by wmcbrine on 2006-07-20
> **toojays said:**
> The the GUI part is written in Delphi, so that's Windows only.There's always Kylix for that, or perhaps Free Pascal (maybe with winelib?).

---


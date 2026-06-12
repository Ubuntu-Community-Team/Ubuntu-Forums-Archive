---
title: "Configuring custom components in GHDL"
date: 2008-02-01
forum: Programming Talk
---

### Post by raptir on 2008-02-01
I'm using GHDL to compile and simulate my VHDL programs. For the first time, I've had to write one in Structural mode. I defined two custom components in Behavioral mode, and tried to connect them using some Structural code. However, when I try to run ghdl -e on the test bench, it gives me this error:
```
 disp_cnt.vhd:24:9:warning: component instance "l1" is not bound
disp_cnt.vhd:10:14:warning: (in default configuration of disp_cnt(structural))
```

I googled the problem, and came up with a few results that implied I should add this line:
```
 for all : lcddcd use entity work.lcddcd;
```
However, since the lcddcd is a custom component, the compiler fails to recognize it. Is there a way to refer to the component just by virtue of it being in the proper directory, or do I need to somehow redefine the "work" library for my code? Thanks in advance for any help.

---


---
title: "ships with ubuntu?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by mrstimpson on 2008-09-21
Hi,

question: if this is true and the dell studio 1535 ships with ubuntu, where are all the drivers? Im finding it impossible toget the graphics card and wireless drivers installed properly - thanks sam



"[ubuntu] Dell studio 1535 Video issue [x3100 > me]
I recently purchased a dell studio 1535 from a store (staples) and immediately went to install 8.04 on it. I would have ordered it directly through dell since they now ship the laptop with ubuntu, but the wait time is backed up for weeks." 

source - [http://ubuntu.linuxguru.co.uk/ubuntu-dell-studio-1535-video-issue-x3100-me-2/152/](http://ubuntu.linuxguru.co.uk/ubuntu-dell-studio-1535-video-issue-x3100-me-2/152/)

---

### Post by mikewhatever on 2008-09-21
The drivers are usually on the Ubuntu installation cd you download from a mirror. There shouldn't be any problem with Intel's X3100, and if anything is wrong with that, specify what is, and meanwhile, check the CD for errors. It may also be a good idea to reburn the iso at slow speed using a good quality CD.
Wireless can be trickier, since Dell uses different hardware for Vista and Ubuntu. If the wireless card is Intel's 3945 or similar, it should be detected and working, but if it's a Dell 1390 or something, you have a broadcom stinker to deal with. You can check what it is with <sudo lshw -C network>.

---

### Post by MegaJim on 2008-09-21
The Dell laptop you are talking about doesn't contain the exact same hardware as the linux version.  The Linux laptops are designated with an N at the end, e.g. 1525N as opposed to pure 1525 which ships with windows and has slightly different (inferior) hardware without native linux support.  The drivers for the N laptops work mostly 100% in 8.04, but there are sometimes problems which you can research on the dell linux wiki page: [http://linux.dell.com/wiki/index.php/Wiki_Main_Page](http://linux.dell.com/wiki/index.php/Wiki_Main_Page)

In short if you want to guarantee 100% native hardware support you need to buy the linux version.

However the x3100 is very well supported on linux; I have a 1525 with an x3100 which works great/very smooth with compiz

---


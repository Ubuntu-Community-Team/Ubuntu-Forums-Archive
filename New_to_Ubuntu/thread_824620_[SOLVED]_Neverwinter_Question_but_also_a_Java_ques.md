---
title: "[SOLVED] Neverwinter Question but also a Java question"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by jasontu on 2008-06-10
Okay.  I have installed the linux client for Neverwinter Nights, and it seems that everything has gone fine until I get to this when I try to run the program via ./nwn

#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7ba3450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

I searched around the forums and found a posting in the bug forum:

[https://bugs.launchpad.net/xorg-server/+bug/185311](https://bugs.launchpad.net/xorg-server/+bug/185311)

This suggests this command:
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so

but the terminal found no such command, and I could not find any jvm or any directory starting with J in the /usr/lib/ directory.

Do I need to install Java JRE, if so, how is that done?

Any help would be appreciated.

Thank you!

---

### Post by the_doc on 2008-06-10
What is the output of the following command?

java -version

---

### Post by CameO73 on 2008-06-10
Search for **sun-java** in Synaptic. It looks like you only need **sun-java6-jre**. This will install in /usr/lib/jvm/java-6-sun-1.6.0.0**6**/, so change your command accordingly.

---

### Post by jasontu on 2008-06-10
Installed Java6, the command that wouldn't work before worked but I still get this error when trying to run the ./nwn command:

#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

---

### Post by jasontu on 2008-06-11
Ha... while it was probably good that I got the Java thing sorted out, the ultimate solution was a lot simpler than I thought it would be.

I removed the "./lib:" in the script and the command was routed properly to where Hardy keeps this code.

---

### Post by aktiwers on 2008-06-11
Yes I did the same thing in neverwintersnight..

Open the nwn file in text editor and remove the ./lib from this line, so it looks like this:
> export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@

---

### Post by jasontu on 2008-06-18
After installing Java JRE, I did a Windows install using Wine, and used the latest downloadable patch executable to update the program also in Wine.  Then I just slapped the Linux binaries downloaded from Bioware's site, and *bingo* it was worked just fine.

---


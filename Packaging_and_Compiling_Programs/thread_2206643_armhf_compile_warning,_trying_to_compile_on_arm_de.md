---
title: "armhf compile warning, trying to compile on arm device"
date: 2014-02-20
forum: Packaging and Compiling Programs
---

### Post by damian5 on 2014-02-20
Noob here, so apologies in advance :p

Currently running 12.04 LTS on an udoo board (arm-based quad-core board: [http://www.udoo.org/](http://www.udoo.org/)). I have some source files and binaries which utilise the FlyCapture SDK ([http://ww2.ptgrey.com/sdk/flycap](http://ww2.ptgrey.com/sdk/flycap)) and when I try to compile them (either my own code, or supplied examples which came with the SDK) I get the following error:

warning: ld-linux-armhf.so.3 , needed by ../../lib/libflycapture.so, not found (try using –rpath or –rpath-link)

If I attempt to run the resulting binaries, there is no error message, the terminal just brings up a new line awaiting another command. My own code and the supplied examples compile and run fine when I use Ubuntu 11.10, however the flycapture SDK in this case is a 'soft float' version (hard float only for 12.04). Google suggests that other people get this error when they are trying to cross-compile for an arm device, but I am trying to compile directly on the device itself (the code is very small and only takes few seconds). If anyone can give some pointers it would be very much appreciated as I would like to run the latest version if possible.

I have:
-searched the device for the *armhf.so.3 file, it is not present
-used apt-get to check that all required dependencies mentioned by SDK documentation are installed (including, among others, libc6)
-re-imaged the device and clean install of dependencies and SDK as per documentation (from point grey - flycapture)

Thank you :-)

---

### Post by damian5 on 2014-02-20
Hmm, always the way. Literally minutes after making the post I discover that the udoo 12.04 distro does not support hard float. Pretty much explains it!

---


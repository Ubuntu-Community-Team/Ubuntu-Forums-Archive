---
title: "Razer Abyssus driver issue."
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Gnawnsense on 2012-10-18
Hello all!

After just switching to Linux, I realized my mouse sensitivity was absolutely driving me crazy. I am currently using a Razer Abyssus, realized there were no Linux drivers, and immediately searched for an alternative.

I came across this: [http://bues.ch/cms/hacking/razercfg.html](http://bues.ch/cms/hacking/razercfg.html)

Installation instructions seemed easy enough. I downloaded all the dependencies, then the package itself. The next step for me would be to CMake/Make the makefiles and binaries. This is where I am getting stuck at.

Once I enter in the CMake command, I get this error:

[php]CMake Error at CMakeLists.txt:18 (message):
  Could not find library "libusb-1.0" with header libusb.h
Call Stack (most recent call first):
  CMakeLists.txt:23 (check_lib)


-- Configuring incomplete, errors occurred![/php]

So, the next thing I did was check with my limited abilities that libusb properly downloaded and installed. So I tried installing the package again, and was told it was completely up to date.

I've only had about 2-3 hours experience with terminal so far, and this is day #2 with Ubuntu. When it comes to most issues, I'll tinker around until I can figure it out, but messing blindly (in my case) with mouse or graphics drivers and Ubuntu absolutely terrify me, haha.

I don't know if it's something obvious I'm missing or not. I searched a few other threads and found similar issues, but am not knowledgeable enough to gather if their symptoms are caused by the same issue as mine. It wouldn't appear so, because the threads I were reading had people CMaking the files fine.

Any assistance or guidance would be very much appreciated! Thanks everyone! :)

---


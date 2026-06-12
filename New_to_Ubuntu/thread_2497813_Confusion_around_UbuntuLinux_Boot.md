---
title: "Confusion around Ubuntu/Linux Boot"
date: 2024-05-18
forum: New to Ubuntu
---

### Post by vskaggs12651 on 2024-05-18
Hello, I am completely new to Ubuntu and was having a lot of issues surrounding it. This problem occurs when I try to start up the computer. When I was downloading Ubuntu from my USB Drive, I was able to access the desktop and everything just fine. The issue comes after when I restart or turn the computer off and then back on. When I boot the computer, I can access my BIOS just fine, but the screen after the loading will go black and then the display will turn off. There is no login, there is no main screen. I have also tried this on Kubuntu. I'm just really confused.

---

### Post by TheFu on 2024-05-18
The exact release you are using (we need the YY.MM) and the exact hardware being used matter.  To provide the hardware, we need a report.  There are lots of ways to provide that, but they all require booting from a flash drive with the Try Ubuntu ISO (aka the installation flash drive), downloading or installing a tool, then running it.  [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info) is one that will get everything about the install and hardware for some gurus to look over.

There used to be a blank screen troubleshooter wiki/help page.  This happens most often with older Nvidia GPUs - usually when the linux drivers for it has lost support from nvidia.  I think the general, 1st thing to try is, booting the kernel with a **nomodeset** option.  I found lots of how-to guides for doing this, but all of them were from 2012 or older.  I don't know that this has changed since then, but it probably has.  [https://askubuntu.com/questions/1511762/black-screen-on-boot-can-i-use-24-04-without-permanent-nomodeset](https://askubuntu.com/questions/1511762/black-screen-on-boot-can-i-use-24-04-without-permanent-nomodeset) is probably right.   It won't do any harm besides making the GPU a little slower.

Also, be certain you read the Release Notes for both 24.04 Ubuntu and the specific DE flavor you use (KDE).

With Intel or AMD GPUs, things tend to just work on any system from 2015 on.

---

### Post by MAFoElffen on 2024-05-19
+1 on running the 'system-info' Script and posting the URL of where it uploads to.

In the Wiki? Like this? [X/Troubleshooting/BlankScreen]("https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen")

Also the "Graphics Resolution" Sticky in my signature line... Yes I originally wrote it in 2011, but most of it still applies to current Linux. It's still good reference. I was asked to rewrite it and put it into the Wiki, but heck, that's a lot of work I didn't have time for at that time.

---


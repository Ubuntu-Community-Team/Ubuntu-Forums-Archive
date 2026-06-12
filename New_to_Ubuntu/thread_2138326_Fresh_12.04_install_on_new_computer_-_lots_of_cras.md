---
title: "Fresh 12.04 install on new computer - lots of crashes - bad processor?"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by ScooterBoogles on 2013-04-23
Hello,

I'm getting tons of crashes on my brand new 12.04 Wubi installation -- and on the 12.10 that I just deleted previous to this one.

I suspect that I may have a bad processor (because of my communications with the vendor). I would appreciate some guidance on how to test the CPU.

Thanks!

---

### Post by MoebusNet on 2013-04-23
Maybe someone else can help you with testing your CPU, but if you boot Ubuntu from Live-CD/DVD or Live-USB, there is an option to test your RAM from the Live-session. I am under the impression that poorly-seated RAM or defective RAM is more common than a defective CPU. Free to check, anyway! Easiest way I've found to do the RAM test is to start it just before bed-time, leave it running all night, then check it in the morning.

[https://help.ubuntu.com/community/LiveCD#Using_your_LiveCD](https://help.ubuntu.com/community/LiveCD#Using_your_LiveCD)

---

### Post by ScooterBoogles on 2013-04-23
Cool, I'll try booting from a USB and doing that. I flipped back over to Windows and ran their memory diagnostic and it said there were no problems, FWIW. Thanks for your reply.

I probably should have specified that I got lots of system crashes on the 12.10 and lots of browser crashes on 12.04. This is the Firefox crash message:

> Notes: OpenGL: Intel Open Source Technology Center -- Mesa DRI Intel(R) Sandybridge Desktop  -- 3.0 Mesa 9.0.3 -- texture_from_pixmap


ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 2258
StartupTime: 1366749468
Theme: classic/1.0
Throttleable: 1
URL: [http://seattletimes.com/html/home/index.html](http://seattletimes.com/html/home/index.html)
Vendor: Mozilla
Version: 20.0


This report also contains technical information about the state of the application when it crashed.


---

### Post by MoebusNet on 2013-04-23
One other fairly common source of problems can be a corrupted download of the .iso file. You can confirm the integrity of the downloaded image by checking the MD5SUM:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You can also boot from Live-CD/DVD or Live-USB and choose the 'Check CD' option.

---

### Post by Choragos on 2013-04-23
How to test the CPU is likely going to be brand-dependent.  For example, Intel has their Processor Diagnostic Tool [[http://www.intel.com/support/processors/sb/CS-031726.htm](http://www.intel.com/support/processors/sb/CS-031726.htm)].  Maybe there's something in your Bios too that you could use?  

Another memory checking tool is Memtest86--it's my bread and butter.

---

### Post by ScooterBoogles on 2013-04-23
@Choragos, thanks! I ran that diagnostic and my CPU is in perfect condition according to its tests. It was also funny to watch it rotate my screen. Appreciate it!

---

### Post by ScooterBoogles on 2013-04-23
@MoebusNet -- is there an equivalent test that I can run from within Wubi, right now?

---

### Post by MoebusNet on 2013-04-24
I've never bothered with Wubi because I don't run Windows for anything, but my guess would be "no". Keep in mind that booting from the Ubuntu Live-CD/DVD or Live-USB is not going to make any changes to your HDD unless you try to install Ubuntu, which you don't need to do. You'll be using the same .iso image you used to install Wubi in Windows but booting from it rather than your HDD. If you don't want to boot from anything but Windows, I guess you'll need to attempt to diagnose any hardware problems with a Windows program.

---

### Post by Mark Phelps on 2013-04-24
You say you have a Wubi install -- so that means you have Windows, as well.  If Windows is not crashing, that means it's not a bad processor.

---

### Post by ScooterBoogles on 2013-04-24
Thanks for your help guys! At this point my problem is basically that my web browsers keep crashing for no particular reason. So I'll close this thread, try booting from a USB, and keep on sniffing.

---

### Post by deadflowr on 2013-04-24
> **ScooterBoogles said:**
> Thanks for your help guys! At this point my problem is basically that my web browsers keep crashing for no particular reason. So I'll close this thread, try booting from a USB, and keep on sniffing.

I find crashes happen for some reason or another.
Whenever that happens, I try launching the program from a terminal, to get a basic idea (possibly) of what's going on.
After that, I go looking around log files. Starting with the hidden file .xsession-errors. Then move on over to the /var/log directory.
Typically, though, I don't have to look any further than the output generated from the terminal.

---


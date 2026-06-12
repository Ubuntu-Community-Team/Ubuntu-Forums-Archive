---
title: "Unable to install Ubuntu 12.10"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by Dozo23 on 2013-01-03
I am new to linux and ubuntu. i was looking to get a new os system and being a windows user thought of windows 8 but i am not a fan. so i looked around and being a computer science major, heard about linux. 
 
i have a laptop. asus g51j. that runs on windows 7. 
 
so i look around and i have decided to try out ubuntu. i went to the website and saw that i could try ubuntu out without installing by placing it on a usb flash drive or a dvd. i downloaded ubuntu 12.10 64bit version and put it on a dvd just like i read. 
 
i restart the computer and i am given a option of operating systems. i pick ubuntu and i chose the demo. it starts to work but then it seems to just stop. it says failed idle channel 2 and 3. then the screen changes to one with purple, black and white and then i like freezes. i restart the computer.
 
i tryed to do it on a usb and pretty much the same thing happens. 
 
i also tryed to run the dvd and chose help me. it then starts to download but ends up failing. it says there is a file missing or something. 
 
before all of this i also tryed to install ubuntu as a dual boot but when installing it seems to just freeze. the computer doesnt freeze just the installation. i allowed it to install for like 10 hours but there was no progress. 
 
so i tryed a different linux system and it just worked fine on the first try. 
 
 
thank you for your help.

---

### Post by Calinou on 2013-01-03
How did you put the ISO on the DVD/USB drive? For USB drives, use Unetbootin: [http://unetbootin.sf.net](http://unetbootin.sf.net)

---

### Post by CodyPy1 on 2013-01-03
Jeeez and you study computer science and you aren't even using linux yet? -_-

Install it on the usb from unetbootin. Works perfect. Shouldn't have any problems at all. 
Make sure your iso file isn't damaged or anything either. 

So just download a new image. Or let unetbootin do it for you. Try out 12.04 before you switch to 12.10. 

I always find LTS version to be better.

---

### Post by RottNKorpse on 2013-01-03
unetbootin for the USB drive install but you will probably not be able to dual boot into Windows 7 as it sounds like you have already tried the "Install in Windows" method which basically uses Windows as a stepping stone into Ubuntu. This is outstanding especially to start but if you didn't install it properly that way then that could explain why the dvd install is not working.

Are you trying to dual boot or are you trying to just jump to Ubuntu?

The reason I ask is because dual booting may not be an option if you already tried the "install in windows" thing because that will make a lot of adjustments to your drives and partitions.

This may be the cause of the dvd install messing up but I don't know for sure.

If you are wanting to install Ubuntu by itself then you will need to format the harddrive with the live usb that you made with unetbootin. (*Warning - this will delete EVERYTHING)

-----

> **CodyPy1 said:**
> Try out 12.04 before you switch to 12.10. 

I always find LTS version to be better.

I disagree with that sentiment. I am currently running 12.04 (regardless of that stupid crap on the left says...I can't edit it on this forum, wtf) but 12.10 is great and has a bit more polish (though of course uninstall the amazon crap) - LTS is for people who care mostly about stability and support.

---

### Post by Dozo23 on 2013-01-03
I have used unetbootin and the one mentioned in the instructions on ubunutu.com. what I am trying to do is just try it out first. Then if I like make a dual boot.

I was able to try another linux operating system that was not ubuntu and the live USB worked fine. I was able to try it out without installing and it was ok. I have been told that ubuntu is better. 

I just switched my major to computer science and all I have learned so far is basic c++.

---

### Post by tlhIngan on 2013-01-03
If the installer freezes, try the alternate installer.
Worked for me.

---

### Post by Dozo23 on 2013-01-03
i just used unetbootin to put ubuntu 12.10 on a usb and then i restarted the computer. i try to try out the os first but it doesnt work. 
 
so then once windows restarted i tryed to run the usb. and there was an option to help me. i installed it but right before the ubuntu cd boot helper finished an error occurred.
 
it says
 
could not retrieve the required installation files
 
for more information, please see the log file:
wubi-12.10-rev273 in my users\appdata\local\temp.
 
but then i try to do the same thing on another laptop i have that is about 5 years old and it was very simple and worked fine. 
 
is there something missing on my newer laptop because there is nothing wrong with the download file.

---

### Post by scottmcon on 2013-01-04
Outside of your possible preference not to use it -- the WUBI Windows Installer worked perfectly on a larger PC with Windows XP.  Problem though is the slower graphics transition of the VIRTUAL DISK approach when using this UBUNTI and 12.10.  Whether design or energy savings, the applications do not pop into place - they slowly fade in as a window.

---

### Post by DuckHook on 2013-01-04
In your case, the major differences between 12.10 and 12.04 are as follows:

1. 12.10 has dropped support for non-PAE CPUs. This means that older laptops in particular (using old Pentium M processors) cannot load the new kernel.
2. 12.10 doesn't work out of the box with some video cards. Often, this is not the fault of Ubuntu. On such occasions, the included video drivers are proprietary, and the manufacturer has written a buggy driver that the community can't change because the source code isn't available. This requires a workaround at boot time.
3. 12.10 no longer works with certain wireless chipsets.

Granted, none of these constraints would seem to apply to you--your notebook is a powerful little beast that is very new, but kernel incompatibilities are notoriously hard to pin down and the problem may not be how old your system is, but the fact that drivers are actually too new (and therefore unstable).

Re: 12.04LTS

The advantage of 12.04 is not only the long term support and stability, but compatibility. Because it is more conservative, and based on a more conservative kernel, it plays nice with a broader range of equipment. I always recommend LTS versions for new users simply because there tend to be less issues. Therefore:

I strongly suggest that you try installing 12.04 in lieu of 12.10. This may solve your installation problems without any further frustrations. If not, please post back to this forum and we'll see where we can go from there.

Steps:

1. Burn CD or USB with 12.04LTS
2. Run as LiveCD first. Do not install until test-driven. Only if everything works, then install.
3. It is perfectly possible to install as dual boot so that you save your current Win7 installation. Instructions are [here]("https://help.ubuntu.com/community/WindowsDualBoot").
4. If the LiveCD doesn't work, then carefully note at what stage of the install process it dies. Especially note any error messages (you will need to be precise and detailed) that crop up over the course of the install. Post back here.

---


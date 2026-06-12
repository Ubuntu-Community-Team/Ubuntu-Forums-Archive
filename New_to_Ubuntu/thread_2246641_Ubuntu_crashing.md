---
title: "Ubuntu crashing"
date: 2014-10-02
forum: New to Ubuntu
---

### Post by gleb5 on 2014-10-02
Dear Ubuntu users!

I've just installed recent Ubuntu on my Lenovo lat top, install  340 nvidia drivers and made dist-update. Unfortunately my system periodically take a cruches especially in the internet sessions (less in Chrome than Firefox) what updates should I do to prevent it?

Gleb :guitar:

---

### Post by Vladlenin5000 on 2014-10-02
Define "crush", please...

---

### Post by gleb5 on 2014-10-02
the system is don't respond to any commands :) and after 30 sec of such lag is been rebooted automatically

---

### Post by Vladlenin5000 on 2014-10-02
Now is a good time to post yours hardware specs and the Ubuntu version you-re running...

---

### Post by gleb5 on 2014-10-02
lenovo t420 lop-top
with Ubuntu 14.04.1 LTS
you can also give me any commands which should I pass to terminal and send back you its result

---

### Post by mastablasta on 2014-10-02
read this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

then give at least the basic specs and exact Graphics chip.

otherwise this info should be available in gui as well - for example if you install "hardinfo": [http://apt.ubuntu.com/p/hardinfo](http://apt.ubuntu.com/p/hardinfo)

or sysinfo... have a look at this article: [http://www.webupd8.org/2011/07/how-to-get-hardware-information-in.html](http://www.webupd8.org/2011/07/how-to-get-hardware-information-in.html)

---

### Post by Vladlenin5000 on 2014-10-02
The aforementioned request notwithstanding - please do post the complete info -, one thing is already clear: Hybrid graphics.
You may need this: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by gleb5 on 2014-10-02
Thank you very much for the suggestions!

So the main problem is due to the presence of hybrid GPU on my note-book isn't it ? Is it possible just to turn off non nvidia gpu (I'm using alot of graphics software and in all cases its normally recognize nvidia card? Alternatively what options of Bumblebee might be useful for me? Will it works with the existing nvidia driver or here I should to remove all gpu drivers and install Bumblebee  with its native ndivia gpu driver ?


Thanks for help,

Gleb

---

### Post by mastablasta on 2014-10-03
check the link provided by Vladlenin5000. it does what you want. you then use the intel GPU and only turn on NVidia (with a simple command) when you plan to play a game or do some task that needs more power...

---

### Post by gleb5 on 2014-10-03
Thanks!

btw I noticed that the crushes might be associated with the call of some flash modules in internet browser. Where solutions here might be exist?  Btw is it possible to check some log after each crash to obtain its real source?

Gleb

---

### Post by Vladlenin5000 on 2014-10-03
You can also disable one of the graphics at BIOS/UEFI but it isn't really needed.
Hybrid graphics were always a PITA in Linux due to some manufacturers' unwillingness to help the open source community. In spite of that we've gone a long way since the troubled beginnings. Later reports from users indicate it's working almost as good as in Windows and also almost as practical with the addition of the "prime indicator" or something, a GUI switch.

Adobe Flash is another PITA... Abode stopped supporting Linux for Flash some time ago: Latest version is 11.2 and, with the exception of security updates, it's frozen. Google Chrome, thanks to the agreement between Adobe and Google, comes OOTB with a newer, *au pair* with Windows, Flash version. Currently Chrome is the only browser with such feature by default; it can also be added to Chromium.
That said, here's my suggestion: Avoid Flash as much as you can. Among other things prefer HTML5 for Youtube. If you can't avoid it try Google Chrome in order to test if it makes a difference with the latest Flash version.
Also to keep in mind is the close interaction between Flash and the graphical drivers which makes everything even harder to troubleshoot. There are a few logs that can be analyzed for sure but I'm not an expert in those and I can't remember what they are or how to get them in a human readable form. I'm sure someone will give better support for those if needed.

---

### Post by gleb5 on 2014-10-03
thanks for suggestion!

yes, i've noticed that using chrome i've reduced number of crashes. Could you tell me how it possible to switch off all Chrome's dangerous plugin's including Flash etc?

Gleb

---

### Post by gleb5 on 2014-10-06
Still can't allocate the source of the crashes: sometimes computer does not response to any command and rebooted with the message that some system conflict are detected. How it would be possible to detect the source of the issue from any log file? Mostly the system got a crush when the internet is open ( I use Chrome)- last time it was crashed during updating of the page with this forum :) What should I turn off in chrome settings to prevent it? I used debian many years but never faced with this problem. 

Gleb

---

### Post by gleb5 on 2014-10-09
one thing that I've noticed is that when the system is stop to respond to any command I still able to switch to the terminal  by means of alt+ cntrl + f1 from which I could restart X by means of 'lightdm restart'. Does it means that the problem in my GPU driver?  I still notice both GPUs in use

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: Lenovo Device 21d0
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [Quadro NVS 4200M] (rev a1)
	Subsystem: Lenovo Device 21d0
	Kernel driver in use: nvidia

how it possible to disable the first?  what logs should I check after crush to allocate its source ?

---


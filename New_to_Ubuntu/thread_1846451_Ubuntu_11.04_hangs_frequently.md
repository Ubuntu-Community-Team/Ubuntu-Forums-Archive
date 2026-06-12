---
title: "Ubuntu 11.04 hangs frequently"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by technosysind on 2011-09-19
I'm using Ubuntu 11.04. It hangs quite frequently and there is no specific application that hangs the whole OS. Sometimes its when I'm using firefox, sometimes it hangs when I'm using the terminal, sometimes it hangs when my laptop is running the screensaver....
Any idea what could be the problem??

---

### Post by uncontrolable™ on 2011-09-19
Are you using ubuntu 32 or 64 bit? What is your system's specs, ie. CPU, RAM?

---

### Post by technosysind on 2011-09-19
Thanx for the quick response. I'm using ubuntu 32-bit.
I'm using a Samsung R480. Its an Intel(R) Core(TM) i3 CPU M 330  @ 2.13GHz+4GB Ram+Nvidia Card with experimental 3D drivers(not proprietary drivers)

---

### Post by swapnilps on 2011-09-19
Even I am having the same issue..:(
Especially when I am accessing Internet.. Initially I thought, Its a problem with firefox (as I was facing same issue with previous version of Ubuntu Studio 10.04) That time updating firefox helped me.. Now when I check with Chromium or Firefox n my Ubuntu Studio 11.04, No clues.. why this is happening!:confused:
just for the info: I was using Studio 10.04 as mentioned earlier, then I updated it to 10.10 using update manager; then again I updated it to Studio 11.04.
Here I am attaching three screenshots which might be to the help.

Please please please Advice!!!

---

### Post by wildmanne39 on 2011-09-19
Hi, you can look at your log files.
```
sudo tail -n100 /var/log/syslog
```
```
tail -n100 /var/log/kern.log
```
```
dmesg | less
```
Also you can use log file viewer to review all these logs, I recommend using it to look at the x.org logs.

You want too run these commands right after your recovery from your next freeze.
Thank you

---

### Post by technosysind on 2011-09-20
Please someone try to help me out with this problem as it is becoming difficult for me to use Ubuntu. It really hangs frequently

---

### Post by pierreyy on 2011-09-20
the nividea graphics card might be you problem ( since its experimental and all) do you have the proper driver installed on ubuntu?

---

### Post by psrdotcom on 2011-09-20
Try to install the graphic card drivers ..

(Guess)
as per your 2nd screenshot .. and with little bit of knowledge ..  browser is trying to download some plugin .. or some add-on is trying to play some media file through the plug-in ..

Please install the adobe-flash player and then let me know the status ..

---

### Post by technosysind on 2011-09-20
Same problem with Nvidia propriety drivers also:(. What to do now?

---

### Post by mörgæs on 2011-09-20
> **technosysind said:**
> What to do now?

You could follow the suggestion given by Wildmanne.

---

### Post by technosysind on 2011-09-20
I did try but I could not figure that out. Can someone atleast tell me what to do when my laptop hangs? I want to avoid hard boot everytime.

---

### Post by mörgæs on 2011-09-20
> **technosysind said:**
> Can someone atleast tell me what to do when my laptop hangs?

Probably not, since there could be a lot of very different reasons for this. Investigation is needed, and you need to be the active part here.

---

### Post by wildmanne39 on 2011-09-20
Hi, here is a safe method to shut down your system even when it is frozen.
That is - hold down Alt+PrintScreen, and then press R-E-I-S-U-B slowly allow 5 seconds between pressing another button, one after the other. On some keyboards/systems, you need to use the AltGr key. 
Thank you

---

### Post by uncontrolable™ on 2011-09-21
> **wildmanne39 said:**
> Hi, you can look at your log files.
```
sudo tail -n100 /var/log/syslog
``````
tail -n100 /var/log/kern.log
``````
dmesg | less
```Also you can use log file viewer to review all these logs, I recommend using it to look at the x.org logs.

You want too run these commands right after your recovery from your next freeze.
Thank you

> **technosysind said:**
> I did try but I could not figure that out. Can someone atleast tell me what to do when my laptop hangs? I want to avoid hard boot everytime.
You should post the log outputs here, so they can be analyzed. Then someone may be able to offer more advice.

---

### Post by pierreyy on 2011-09-21
Maybe Ctrl+Alt+Backspace will do the trick?

---

### Post by technosysind on 2011-09-26
I have finally solved this problem by installing some packages using synaptic. AWK & DPKG

---

### Post by wildmanne39 on 2011-09-26
Hi, I am happy to hear you have it fixed, would please tell us what you installed so other people can benefit from your experience?
Thank you

---

### Post by technosysind on 2011-09-26
I already mentioned in thread number 15. Please see it.  Thanx.

---


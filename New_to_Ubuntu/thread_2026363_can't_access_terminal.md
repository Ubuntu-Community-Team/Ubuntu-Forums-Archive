---
title: "can't access terminal"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by barrykgerdes on 2012-07-15
Ubuntu 11.04 appears to be working OK however I cannot access the ternminal to get a download.

Opening the terminal tells me that dpkg is broken and needs to be fixed by sudo dpkg --configure -a

I run this and it tries to down load what appears to be fonts but seems to get locked into some sort of a loop mainly looking for "aarnet.dl.sourceforge.net|32.1.3.136|:80..." after about a minute it gives up connects to some other places then gets back to that line again and starts the whole step again. Although I am not certain if it is actually trying to do the same steps each time.

This has been going on for about 2 hrs but not getting anywhere.

The only clue I can give is that I started an update two days ago and I think the computer crashed before the update was finished downloading in an unattended situation. 

Barry

---

### Post by Shadius on 2012-07-15
You can probably try:
```
sudo apt-get install -f
```
Maybe that'll fix the broken packages.

---

### Post by barrykgerdes on 2012-07-15
I can't stop the process to enter that command without crashing the program. Is that OK

Barry

---

### Post by barrykgerdes on 2012-07-15
I closed the program and tried sudo apt-get install -fhowever it just told me to run. 

sudo dpkg --configure -a

Barry

---

### Post by Shadius on 2012-07-15
Hmm...I'm not sure what to try from here. The only thing I can think of is using Synaptic Package Manager to look for broken packages and then fixing those broken packages.

---

### Post by lolpenguin on 2012-07-15
Could you post the output of
```
sudo dpkg --configure -a
```

---

### Post by barrykgerdes on 2012-07-15
The output from that command is still running it appears to be progressing slowly. I can't post the response. It must be well over 1000 lines now.

The prpogram is trying to access and down load files but it only gets a few successful results and keeps trying to get them and the rest. I will leave it to run for a few more hours it may eventually finish.

---

### Post by barrykgerdes on 2012-07-15
I think it has finished I have the command ptompt back after almost 5 hrs

Yes it is OK now

Barry

---

### Post by Shadius on 2012-07-15
> **barrykgerdes said:**
> I think it has finished I have the command ptompt back after almost 5 hrs

Yes it is OK now

Barry

Maybe it just took that long to configure the packages? :-s

---


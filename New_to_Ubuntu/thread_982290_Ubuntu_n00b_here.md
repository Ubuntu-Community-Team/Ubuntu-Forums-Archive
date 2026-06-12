---
title: "Ubuntu n00b here"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by tberli on 2008-11-14
Could someone please try to answer this thread? And possibly some easy digestible link concerning the subject.

I am wondering why can't I open any of my downloaded files? I tried downloading AVG anti-virus, and when clicking the downloaded file I get an error message: "An error occurred while loading the archive." Is there something I need to do to be allowed to execute my downloads?

---

### Post by Idefix82 on 2008-11-14
You don't need an antivirus under Linux. There are no serious viruses under linux. It will only help you to find windows viruses but it will also report lots of false positives and give you more headache than you need.

Next time, please help people help you and choose a descriptive thread title. "noob here" doesn't tell anybody whether they can be of any help and I only clicked on it by pure chance.

---

### Post by mitsos_ on 2008-11-14
What is the kind file is the AVG. Is it compressed? 
But why AVG?

---

### Post by SuperSonic4 on 2008-11-14
Virus protection is useful if you dual boot to protect from windows viruses. I suspected you downloaded the linux version of AVG.

What is the filetype and error code when you try run (copy and paste)

---

### Post by mitsos_ on 2008-11-14
Why AVG? If you want an AV under Linux you can use the free AV clamav from the synaptic manager which is free.

---

### Post by newbuntuxx on 2008-11-14
You do not need an Anti-virus for linux. Please be more specific and let us know what the file extensions are? Are they .zip? .rar?

---

### Post by bodhi.zazen on 2008-11-14
I do not know why you are having those issues.

If you are interested in security start here :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by markjensen on 2008-11-14
> **mitsos_ said:**
> Why AVG? If you want an AV under Linux you can use the free AV clamav from the synaptic manager which is free.

I'm not impressed with clamav.   Not sure about AVG, but I know that avast is just an apt-get away.

**sudo apt-get install avast4workstation**

(might need to open up your repos, if you haven't done so already)

I highly recommend using the package manager, instead of fighting it and installing tarballs manually.

---

### Post by EvilRobotDrew on 2008-11-14
I would recommend that if you want to install anything go through Applications -> Add/Remove Applications, change "Show" to either all Open Source Applications or All Applications. You can search for specific programs, or browse. 

you can also use the Synaptic Package Manager in System -> Administration

you can also use the command line, but unless you know the name of the package you need, this isn't always helpful to n00bs

other installations that you may want (OpenOffice 3.0 for example) usually have a detailed walkthrough somewhere online. I would recommend that you avoid manually installing programs for the time being, at least until you feel more comfortable with linux, besides using add/remove applications or synaptic, or the command line makes sure that ubuntu will update the program as updates are rolled out and tested.

---

### Post by fiddler616 on 2008-11-14
To be honest, I would just not use an anti-virus utility if I were you.

---

### Post by LowSky on 2008-11-14
> **tberli said:**
> I am wondering why can't I open any of my downloaded files? 

Windows files do not work in Linux, they are not compatible. The is a program called WINE that can help you use Windows progrmas but it isn't always perfect.

---


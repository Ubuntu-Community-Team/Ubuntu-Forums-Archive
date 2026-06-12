---
title: "Antivirus for Ubuntu (computer at work - may share files with Windows users)"
date: 2008-05-01
forum: Recurring Discussions
---

### Post by leotemp on 2008-05-01
I assume i still need some form of anti virus, is there a specific application or sweet that works best with ubuntu or do I just install my application of choice under Wine?

---

### Post by SunnyRabbiera on 2008-05-01
Nope, no anti virus really needed in linux unless you wish to monitor a windows share :D

---

### Post by 8.04Linux_god on 2008-05-01
Dude you must be new to ubuntu or linux in general here is one of the gretest things with linux users WE DONT NEED IT. most or if any viruses wont do anything to linux if they are any the cummity can sole the problem within day   thats the gret thing about linux so no you dont need any anti virus

---

### Post by SunnyRabbiera on 2008-05-01
Remember that most viruses out there are made for windows, granted Linux has viruses of its own but most of them are conceptual or wont work without root access, and the root account is disabled by default in ubuntu :D

---

### Post by leotemp on 2008-05-01
Well all of that is good and fine but theres now way im risking my job by not protecting against the "outside chance" is there an application that one might recommend for those of use that don't rely on Windows being a larger target?:confused:

---

### Post by thiebaude on 2008-05-01
What else can we say.

---

### Post by i_have_a_sempron on 2008-05-01
get firestarter....good firewall configuration tool with a GUI

---

### Post by perlluver on 2008-05-01
You can try clam av it is in the repos, or Avast has a free version for Linux.

---

### Post by SunnyRabbiera on 2008-05-01
I would not worry about it, you are much more safer here then you are on windows...
all the proposed viruses for linux are just that... proposed, and the ones that do work as I said root access and as I also said Ubuntu disables root by default.
Let go of your paranoia and embrace the freedom that is linux :D

---

### Post by jimv on 2008-05-01
Here's a doc with some antivirus options for Linux.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by leotemp on 2008-05-01
uh, well i guess im just looking for a simple answer, is there an application out there known specifically to run well on linux, I can assure you theres no way my machine will be allowed to co mingle with others at my job unless its protected and waxing philosophy with my admin about how i don't need it anymore wont work.

---

### Post by c4v3m4n on 2008-05-01
Antivirus is really unnessecary in linux.  It's protected by itself and without root power they can't do anything.

---

### Post by lswest on 2008-05-01
you can always install ClamAV, but that scans for windows viruses (it's available in synaptic)

---

### Post by SunnyRabbiera on 2008-05-01
> **leotemp said:**
> uh, well i guess im just looking for a simple answer, is there an application out there known specifically to run well on linux, I can assure you theres no way my machine will be allowed to co mingle with others at my job unless its protected and waxing philosophy with my admin about how i don't need it anymore wont work.

well if you use the word "Linux" you will certainly get some leeway, assuming your employers know what it is...
and if they dont, there are plenty of books and articles on the matter.

---

### Post by psycosmyth on 2008-05-01
clamav is availible in the repositories. You can be certain that you will be safe using av with linux. Guarddog is a good firewall front-end.
There is malware that might trip up Firefox or a bad file in a download but it's just ignored by the system and things just work on and on.
You could also use Opera or Konqueror as more hardy browsers.

---

### Post by gameryoshi600 on 2008-05-01
linux doesn't need an antivirus. theres only a few out there for linux but they were big in 2003. so no need to be paranoid about getting a virus :D

---

### Post by leotemp on 2008-05-01
LSWEST, thank you, thats the answer I was looking for. regardless of whether it affects my machine I don't need files with MS or Mac viruses ending up on my co workers machines, then the admin comes in the room, turns off my giant monitor and starts slamming my fingers in the drawers.. not good.

---

### Post by perlluver on 2008-05-01
[Click here.]("http://files.avast.com/files/linux/avast4workstation_1.0.8-2_i386.deb") That is the link for Avast for Linux.

---

### Post by Jordanwb on 2008-05-01
I don't think you get how Linux works (neither do I). There is the root user, root is a super user (like Admin) who can do anything. However you do not have access to it, so when you want to do something that requires admin privleges you have to type your password. Since no one - such as a virus - has access to it, it cannot perform Admin actions. Since I'm a newb in sorts can someone confirm this.

[Edit]

Wow while typing this there were like 8 new messages

---

### Post by Bothered on 2008-05-01
If you really want an antivirus program clamav is available in the repositories (avscan/klamav are GNOME/KDE GUIs).

Although, as has already been said, antivirus is not generally needed for Ubuntu. The most common reason to use antivirus is to protect other Windows systems on your network. See here: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by leotemp on 2008-05-01
> **Jordanwb said:**
> I don't think you get how Linux works (neither do I). There is the root user, root is a super user (like Admin) who can do anything. However you do not have access to it, so when you want to do something that requires admin privleges you have to type your password. Since no one - such as a virus - has access to it, it cannot perform Admin actions. Since I'm a newb in sorts can someone confirm this.

Which is great but I'm not going to risk my lively hood on a calculated risk when i could spend a short amount of time to install an app and at least try to have covered my *** in case somehow someone does find a way of screwing over my new OS, i don't think thats unreasonable at all.

---

### Post by Bothered on 2008-05-01
> **leotemp said:**
> Which is great but I'm not going to risk my lively hood on a calculated risk when i could spend a short amount of time to install an app and at least try to have covered my *** in case somehow someone does find a way of screwing over my new OS, i don't think thats unreasonable at all.

Indeed it is your computer. You can of course choose to use antivirus software if you wish.

---

### Post by gn2 on 2008-05-01
What the OP is concerned about is passing on an infection.

While his machine would not be affected by any virus currently in the wild, he could pass on a virus from any file he sent/shared to other PC's on the network, which is not his network, it's his employer's.

In these circumstances having a virus scanner is a good idea.

There are a few options, Avast, AVG and ClamAV.

[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

[http://free.grisoft.com/ww.download?prd=afl](http://free.grisoft.com/ww.download?prd=afl)

ClamAV is in the repos

---

### Post by Barrucadu on 2008-05-01
There is no risk. Linux viruses cannot spread without root access, which is only granted by entering your password.
With that said, if you do install an antivirus and find a Linux virus (not just a Windows virus in a file you copied, which won't be able to do anything anyway), please post here and I'll eat my hat. I like my hat, and don't want to eat it. That is how confident I am.

---

### Post by lswest on 2008-05-01
thanks for the thanks, and no problem, though yes, avast also offers an AV for linux, but i've never tried it.

---

### Post by leotemp on 2008-05-01
> **gn2 said:**
> What the OP is concerned about is passing on an infection.

While his machine would not be affected by any virus currently in the wild, he could pass on a virus from any file he sent/shared to other PC's on the network, which is not his network, it's his employer's.

In these circumstances having a virus scanner is a good idea.


Exaclty and I in know way mean to imply that Linux is insecure just that I need to actually take the steps to insure maximum security so if something does happen im not that jerk in the office that just assumed everything would be fine, meanwhile the rest of the office is on fire and people are gathering pitch forks and torches with the intent to put said forks in my rear.

thanks for the help all!

---

### Post by aysiu on 2008-05-01
I've retitled the thread so that people know it's more to do with scanning for Windows viruses and impressing other people with "protection" than real security.

---

### Post by leotemp on 2008-05-01
> **Barrucadu said:**
> There is no risk. Linux viruses cannot spread without root access, which is only granted by entering your password.
With that said, if you do install an antivirus and find a Linux virus (not just a Windows virus in a file you copied, which won't be able to do anything anyway), please post here and I'll eat my hat. I like my hat, and don't want to eat it. That is how confident I am.

heh, i believe if you put the hat in a proper bag you could have both!

---

### Post by Sef on 2008-05-01
> What the OP is concerned about is passing on an infection.

While his machine would not be affected by any virus currently in the wild, he could pass on a virus from any file he sent/shared to other PC's on the network, which is not his network, it's his employer's.

In these circumstances having a virus scanner is a good idea.

This is very true.  GNU/Linux machines won't be infected, but can pass on malware to Windows users.  Hence an anti-virus is recommended for machines networked to Windows computers.

> There is no risk. Linux viruses cannot spread without root access, which is only granted by entering your password.
With that said, if you do install an antivirus and find a Linux virus (not just a Windows virus in a file you copied, which won't be able to do anything anyway), please post here and I'll eat my hat. I like my hat, and don't want to eat it. That is how confident I am.

Would you like mustard, mayonnaise, or ketchup with your hat? :-P

---

### Post by Bothered on 2008-05-01
> **Barrucadu said:**
> There is no risk. Linux viruses cannot spread without root access, which is only granted by entering your password.
With that said, if you do install an antivirus and find a Linux virus (not just a Windows virus in a file you copied, which won't be able to do anything anyway), please post here and I'll eat my hat. I like my hat, and don't want to eat it. That is how confident I am.

Oh dear, I think fate is being tempted.

---

### Post by Barrucadu on 2008-05-01
I'll try to find some good hat-eating music, just in case.

---

### Post by leotemp on 2008-05-01
Alright, everybody calm down, i feel like a little kid that threw a rock at a bee hive "Oh look, their really mad now. OUCH!"

---

### Post by quinnten83 on 2008-05-02
> **leotemp said:**
> LSWEST, thank you, thats the answer I was looking for. regardless of whether it affects my machine I don't need files with MS or Mac viruses ending up on my co workers machines, then the admin comes in the room, turns off my giant monitor and starts slamming my fingers in the drawers.. not good.

Wow,can i get a job in your IT department? I like their style!

---

### Post by quinnten83 on 2008-05-02
> **leotemp said:**
> Exaclty and I in know way mean to imply that Linux is insecure just that I need to actually take the steps to insure maximum security so if something does happen im not that jerk in the office that just assumed everything would be fine, meanwhile the rest of the office is on fire and people are gathering pitch forks and torches with the intent to put said forks in my rear.

thanks for the help all!
I'm starting to notice that your company seems to have a tendency to drastically overreact to things...

---


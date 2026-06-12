---
title: "If Ubuntu were Windows"
date: 2007-11-17
forum: Recurring Discussions
---

### Post by IISpII on 2007-11-17
I have notices that Ubuntu has gained a lot of popularity lately, and i was thinking that if Ubuntu had become as popular and as widely used as windows is, would that make Ubuntu just as crappy as windows is, i mean would it become crawling with malware and people trying to break into you computer, and steal you files.

Please tell me your input on this subject and also if this is to come true what we should to about it.

---

### Post by scorp123 on 2007-11-17
> **IISpII said:**
>  would that make Ubuntu just as crappy as windows is Well, there are some aspects in Ubuntu (mainly unfixed bugs) that qualify it for being "crappy". :lolflag: .... But I love it anyway :)

> **IISpII said:**
>  i mean would it become crawling with malware and people trying to break into you computer, and steal you files.   Maybe? I just read some news that more and more Trojan programs are written for Mac OS X because it too has become more popular and is therefore an interesting target. But then again UNIX-like operating systems --and Ubuntu and Mac OS belong to that group-- are designed in a fundamentally different way than Windows and it's way harder for malware to actually find a way into your system. Not impossible, no ... but harder; e.g. there is no "Active/X" and the available web browsers are not tied into the core OS or the GUI (as "Internet Explorer" is on Windows!). So a virus programmer has to find different paths.

In the case of the recent Mac OS X virus the malware posed as "QuickTime Update" that you "needed" on some infected web sites in order to fully see the content -- of course the users did not realise that the web page they were looking at were infected with anything. So people clicked on this thinking they are installing a web browser plugin; and when the dialogue asking for the "root" password popped up they of course typed it in and instead of the promised QuickTime plugin they got themselves a virus infection ... (such stuff is very rare on Apple Mac's too)

I could imagine something similar happening on Ubuntu. e.g. a hacker (or rather: a cracker) gains control over one of the repo servers and then manipulates a package so it also installs a backdoor. Users around the globe would then be notified by update-manager that there is a "new update" available and so many people install this ..... And voila, there is your malware spreading across many Ubuntu systems.

That's why I found the recent reports about Debian and/or Ubuntu repo servers having been hacked for a brief moment rather disturbing (that was a few months ago if I remember right ...) ... Such a hacked repo server could be a potential weak spot. But the admins acted correctly by taking the servers in question offline (so the rest of us can't get any fake updates or any potentially manipulated packages from there) and searching all the packages up and down for any strange changes ... 

To really be on the safe side I sometimes compare what "update-manager" is offering me as an update with recent security bulletins (e.g. if there are any news reports floating around on the web that confirm there being a problem with the package "update-manager" wants to update ....). I'd rather be paranoid than sorry afterwards :)

---

### Post by K.Mandla on 2007-11-18
As this is a frequently discussed point, the issue is being moved to ... Recurring Discussions.

---

### Post by BorisK on 2007-11-18
Well if Ubuntu was widely used, there would be many more admins to secure the repo server and detect vulnerabilities.

---

### Post by smartboyathome on 2007-11-18
I don't know if a virus could spread through your system without being run. The problem is that I think DPKG doesn't allow files to be replaced or deleted while installing, so you would have to get a user to install the package and THEN run the program in order to get it to infect the user. This, of course, can be done by gullible users, but I don't see anything like windows happening on Ubuntu.

---

### Post by aysiu on 2007-11-18
Read this thread:
[Ubuntu/Linux/Windows and Viruses/Malware](http://ubuntuforums.org/showthread.php?t=323028)

---

### Post by SunnyRabbiera on 2007-11-18
well if ubuntu does become more popular it could become a potential target for malicious entities.
But because of linux's open nature its never going to be like windows, perhaps like apple where the occasional virus or trojan will pop up but nothing on the windows scale thanks to most viruses being created by linux users (and yes it is true, but its mainly because its very easy to code such a thing in a unix type enviroment)

---

### Post by inversekinetix on 2007-11-18
with so many windows boxes compromised the next logical step has to be to widen the net and go after other peripheral OSs.  It's only logical that if there is money to be made someone will do it.  Remember the weakest link is between the chair and the keyboard.  A good social engineer can get your regular joe to do almost anything.  Just a matter of time until theres a flood of attacks against OSs other than windows.

---


---
title: "viruses"
date: 2009-08-28
forum: Recurring Discussions
---

### Post by ave2 on 2009-08-28
coming from a windows background Im still trying to wrap my head around this.... I understand that there are only a handful of viruses that have caused trouble in the past [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
I dont install a lot of software etc so shouldnt get anything that way, neither am I on a network. But was wondering if there were any that you can get from simply browsing the web or from inserting an affected flash drive

---

### Post by NoaHall on 2009-08-28
No. It's incredibly unlikely. And if you do get any, they won't be able to affect you, because they are made to attack Windows, not Linux.

---

### Post by pmlxuser on 2009-08-28
In the unlikely event that one does it will be gone in minutes because the community is like a security firm, always providing ways of dealing with any un welcome thing.

But don't worry i have been using ubuntu for 3 years an have not seen one yet....

---

### Post by sydbat on 2009-08-28
Before this gets moved to Recurring Discussions, I suggest the OP use Google to search for related topics on this forum (as the internal search is really not that good, IMO). A quick Google with [_ubuntuforums.org: virus_]("ubuntuforums.org: virus") shows almost 44,000 results (with 'antivirus' the results are about half).

---

### Post by aysiu on 2009-08-28
If you're really that worried, use Firefox with the NoScript extension and learn how to configure AppArmor profiles.

---

### Post by tenghoward on 2009-08-28
There aren't a lot of viruses aim at Linux due to low percentage in OS market. Should a virus pops up it won't last long. Kernel update come very quickly and can disabled the virus by then. 

If you really are worry install avast! or other anti-virus for linux. Use ad-block and disable script in firefox.

---

### Post by aysiu on 2009-08-28
> **tenghoward said:**
> There aren't a lot of viruses aim at Linux due to low percentage in OS market. Should a virus pops up it won't last long. Kernel update come very quickly and can disabled the virus by then. 

If you really are worry install avast! or other anti-virus for linux. Use ad-block and disable script in firefox.
Should a virus pop up, how would having Avast! or another antivirus software installed help?

---

### Post by doas777 on 2009-08-28
> **aysiu said:**
> Should a virus pop up, how would having Avast! or another antivirus software installed help?

installing software (especially AV/sec scanner software) after becoming infected is a bad idea. it gives the malware an opportunity to compromise the AV system before it can even begin to protect itself. most significant malwares either try to hide polymorphically, or directly attack common AV systems to prevent detection.

---

### Post by aysiu on 2009-08-28
> **doas777 said:**
> installing software (especially AV/sec scanner software) after becoming infected is a bad idea. it gives the malware an opportunity to compromise the AV system before it can even begin to protect itself. most significant malwares either try to hide polymorphically, or directly attack common AV systems to prevent detection.
And installing antivirus before becoming infected is also useless--that's my point.

---

### Post by doas777 on 2009-08-28
> **aysiu said:**
> And installing antivirus before becoming infected is also useless--that's my point.

agreed.
I was just operating on the hypothetical posed above ("should a virus pop up ...").
in that case, a simple update to an installed AV and a scan might just work. worth a try prior to a full rebuild.

I don;t expect there to be any more linux viruses (unless closed software becomes common), but i do expect other forms of nasties, particularly trojans and worms as the years go on. right now, it's just easier and more profitable to look for a server with weak ssh keys: [http://www.theregister.co.uk/2009/08/28/apache_hack/](http://www.theregister.co.uk/2009/08/28/apache_hack/)

---

### Post by aysiu on 2009-08-28
I prefer prevention to cleanup.

Viruses will not just "pop up" if you use strong passwords, avoid enabling network services you don't know how to lock down, use Firefox with NoScript, use configured AppArmor profiles, and do not pirate software/music/movies or install software outside the repositories.

---

### Post by bodhi.zazen on 2009-08-28
> **ave2 said:**
> coming from a windows background Im still trying to wrap my head around this.... I understand that there are only a handful of viruses that have caused trouble in the past [https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
I dont install a lot of software etc so shouldnt get anything that way, neither am I on a network. But was wondering if there were any that you can get from simply browsing the web or from inserting an affected flash drive

Linux is not windows and, just as with microsoft word, you need to let go of your windows security mentality.

Linux does have malware, but Linux security does not include antivirus.

_The way of Windows_ - Closed source, many security holes, relies on 3rd party fee-for-service applications to plug holes, source code goes undocumented and unpatched for decades.

So while there  are hundreds of thousands of know viruses the source code remains unpatched and you remain vulnerable.

_The way of Linux_ - Open source, fewer security holes, does not rely on 3rd party fee-for-service applications, documented security holes are patched.

So while there are a few hundred reported Linux viruses, assuming your system is up to date, those vulnerabilities were patched many years ago and you are invulnerable to them.

See also : [Master Foo and the Nervous Novice]("http://catb.org/%7Eesr/writings/unix-koans/nervous.html")

If you wish to learn to secure Ubuntu , please see :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

[How to Secure Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=671604") 

[USN list | Ubuntu - Security alerts]("http://www.ubuntu.com/usn")

---

### Post by MelDJ on 2009-08-28
could i just ask: 
 If i dual boot ubuntu and windows, and i download something with windows viruses in ubuntu , will my windows drive be infected

---

### Post by khelben1979 on 2009-08-29
> **MelDJ said:**
> could i just ask: 
 If i dual boot ubuntu and windows, and i download something with windows viruses in ubuntu , will my windows drive be infected

If you or your system copy the infected files from the Ubuntu partition to your Windows partition, yes! Otherwise, if you let your Windows partition be unmounted on your Linux system: no!

---

### Post by lisati on 2009-08-29
The only two times I've had hassles involving a virus was when I suffered [PEBKAC errors]("http://en.wikipedia.org/wiki/PEBKAC"). I wasn't using Ubuntu at the time. The first was a careless "reply to all" on receipt of a virus via an email mailing list (the backscatter kept on coming in for about a year: amongst other things bounces, read receipts and nastygrams telling me to "go away" [or words to that effect]) and the second involved knowingly opening an infected zip file (required a reinstallation of Windows). 

The moral of the story: being careful and sensible will go a long way toward avoiding diffifulties and minimising damage.

---

### Post by bodhi.zazen on 2009-08-29
> **MelDJ said:**
> could i just ask: 
 If i dual boot ubuntu and windows, and i download something with windows viruses in ubuntu , will my windows drive be infected

The only way to infect your windows drive would be if you transferred the file to windows without scanning it first.

---

### Post by TeoBigusGeekus on 2009-08-29
Be a bit cautious with Wine as well.
Read this funny thread:
[http://ubuntuforums.org/showthread.php?t=72598]("http://ubuntuforums.org/showthread.php?t=72598")

---


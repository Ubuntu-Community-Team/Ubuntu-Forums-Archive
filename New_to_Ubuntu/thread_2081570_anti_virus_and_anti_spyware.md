---
title: "anti virus and anti spyware"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by cladder58 on 2012-11-07
do you need anti virus and spy ware or is it built in.
i want to use the computer for banking so i want to be safe
i was told you need it so you do not pass it on to windows base computers.
what is the best ones to use

---

### Post by newb85 on 2012-11-07
There are many recent threads on this subject.  Please do a search for antivirus and read some of the threads that come up.

---

### Post by Paqman on 2012-11-07
Have a read of [this venerable thread]("http://ubuntuforums.org/showthread.php?t=510812"), and allow it to lay your fears to rest somewhat.

---

### Post by 3rdalbum on 2012-11-07
> **cladder58 said:**
> do you need anti virus and spy ware or is it built in.

Short answer: No, and No. You don't need anti-virus and anti-spyware, and it's not built into Ubuntu.

Long answer: There's currently no viruses or spyware for Ubuntu. You don't need software to protect you against something that doesn't exist. While it's probable that somebody will write a virus for Ubuntu at some point, it's rather difficult because of Ubuntu's security systems, and viruses on minority operating systems tend not to spread very easily.

Medium answer: Don't worry about anti-virus or anti-spyware software, it really does nothing.

---

### Post by PinkFloyd102489 on 2012-11-07
> **3rdalbum said:**
> Short answer: No, and No. You don't need anti-virus and anti-spyware, and it's not built into Ubuntu.

Long answer: There's currently no viruses or spyware for Ubuntu. You don't need software to protect you against something that doesn't exist. While it's probable that somebody will write a virus for Ubuntu at some point, it's rather difficult because of Ubuntu's security systems, and viruses on minority operating systems tend not to spread very easily.

Medium answer: Don't worry about anti-virus or anti-spyware software, it really does nothing.

Namely because any program that is able to run under Linux can have it's source code checked for malicious intent.

---

### Post by Paqman on 2012-11-07
> **PinkFloyd102489 said:**
> Namely because any program that is able to run under Linux can have it's source code checked for malicious intent.

There's a lot of reasons, but that is one of them.

---

### Post by Atomic-Fanboy on 2012-11-07
Yo.  You probably don't need an antivirus program. However, you CAN install clamAV if you want. You really should use a firewall though. Either run:

```
sudo ufw firewall enable
``` after bootup, or get gufw and set the firewall that way - ```
sudo apt-get install gufw
```

---

### Post by newb85 on 2012-11-07
> **PinkFloyd102489 said:**
> Namely because any program that is able to run under Linux can have it's source code checked for malicious intent.

There are a lot of reasons, but that is *not* one of them.

While it may not be the way most software is installed in Ubuntu, it is definitely possible to acquire .deb files for which source code is unavailable.  One example that comes to mind is the drivers for my Brother printer, which I had to download in good faith that Brother is more interested in making their devices usable to the Linux community than they are in distributing malware.  (If that assumption was incorrect, they're very patient...)

It is also possible to directly download binaries.  Fortunately, in Ubuntu, anything you download lacks execute permissions by default, and you have to change permissions before you can run it.

The bottom line is this: make sure you know the source of all packages you install and all files you make executable.  Packages in the four main repositories are trustworthy.  There are some trustworthy Ubunut/Linux news & review blogs that recommend packages you can trust (and which you can often install by adding a PPA to your system).  Sometimes scripts are used for troubleshooting in the forums.  It's possible for someone to put together a malicious script and post it.  (Anyone with the title "Ubuntu Member", "Forums Staff", or "Forums Moderator" is fine, though.)

---

### Post by El Tito on 2012-11-08
I have clam av. I use it mostly to scan my windows partition (dual boot).
I think there are also viruses in linux, but due to its low user number, the developers of
viruses are more interested in windows and mac (I suppose).

---

### Post by alkh3myst on 2012-11-08
What the other respondents on this thread are neglecting to tell you is that you are absolutely correct about one thing. "i was told you need it so you do not pass it on to windows base computers" Exactly. Downloaded media files, even jpegs can and do sometimes contain Windows malware. A careless Windows user you send an infected picture of Big Ben to, can easily end up with major problems, and you'll be blamed. The smug attitude that we don't need antivirus/malware apps because **our** computers can't get infected, is why Linux has a reputation for spreading malware. I consider this attitude to be irresponsible, and just plain selfish. 

Clam AV, as mentioned above is a good start, but "BitDefender for Unices" is easier to use, saving your time for *important* things. You download it, request a product key, which BitDefender will email to you, then install it using the Terminal. The interface is pretty intuitive, and can be learned with a minimum of anguish. Complete installation instructions for Ubuntu 12.04 are here: [http://connectwww.com/how-to-install-bitdefender-antivirus-scanner-for-unices-on-ubuntu-11-04/1214/](http://connectwww.com/how-to-install-bitdefender-antivirus-scanner-for-unices-on-ubuntu-11-04/1214/)

I've been using BitDefender for years without any problems. Good luck, although you should have no difficulties. 

):P

---

### Post by mastablasta on 2012-11-08
another option is Avira antivir for linux. maybe avast has a linux version now as well.
 
however all these guard against windows viruses which as said do not work on linux but you can still pass them on (to a windows computer in your home network for example)
 
oh yeah about spyware - ubuntu come prelaoded with firewall which is disabled by default as it doesn't listen to any ports (at leats i think that is the reason). anyway you can enable it but it's better to do it with some graphical unterface if you are not into command line: [https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
 
if you use a router and you have a firewall there i think that one is maybe enough.

---

### Post by newb85 on 2012-11-08
> **alkh3myst said:**
> What the other respondents on this thread are neglecting to tell you is that you are absolutely correct about one thing. "i was told you need it so you do not pass it on to windows base computers" Exactly. Downloaded media files, even jpegs can and do sometimes contain Windows malware. A careless Windows user you send an infected picture of Big Ben to, can easily end up with major problems, and you'll be blamed. The smug attitude that we don't need antivirus/malware apps because **our** computers can't get infected, is why Linux has a reputation for spreading malware. I consider this attitude to be irresponsible, and just plain selfish.

I agree that we need to be responsible with the reputation of Ubuntu/Linux, but the fact still remains that Windows users need to have their own protection, as they're perfectly capable of getting themselves infected without our help.

---


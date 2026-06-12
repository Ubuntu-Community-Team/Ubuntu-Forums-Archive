---
title: "Is there anti-virus software for Ubuntu"
date: 2008-09-09
forum: Recurring Discussions
---

### Post by suomalainen on 2008-09-09
Ubunteros,

I've had Ubuntu 7.10 on my desktop for nearly a year now.

With that said I do not run any anti virus or spyware or any of these type of applications.

I'm curious to now know if year later I may have even one virus or something???

QUESTION: what anti-virus is available to scan my PC?

Thank You

---

### Post by Perfect Storm on 2008-09-09
Anti-virus applications is not needed in Linux.

Thoough if you have E-mail server or using a Linux box to scan your Windows machines there's anti-virus applications that scans for windows virus.

---

### Post by anjilslaire on 2008-09-09
There are no significant viruses out in the wild for linux. However, you can install clamav from the repositories to check any files you may be sending to Windows users.

That being said, you don't likely have any infections affecting your OS.

---

### Post by tuxxy on 2008-09-09
You only need an anti-virus if you regularly sharing files or accessing a second windows drive, to prevent the spread of the windows virii.

Current linux AV programs available are, Avast, Clam AV etc

---

### Post by bumanie on 2008-09-09
Any virus scanner available only scans for viruses that affect windows machines, however, the open source clamav is available in the reositories if you want to try it. Follow [this guide]("http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html") You can compile the latest scan engine and definitionsyourself from the clamav site if you wish.

---

### Post by suomalainen on 2008-09-09
Thanks all!

The reason I'm asking this question is because I went to the following web site using linux-Ubuntu:

[http://scanner.vav-x-scanner.com/27/?advid=1297&ref=&p=1010000000](http://scanner.vav-x-scanner.com/27/?advid=1297&ref=&p=1010000000)

A pop up appeared asking if I want a scan for viruses so I choose "ok"

Attached is the pic of what the results were.

So as you can see, I'm under the impression that I have a virus on my system.

---

### Post by anjilslaire on 2008-09-09
If you were using a Windows system you would have just infected yourself with something nasty.

The site itself it loaded with malware.

---

### Post by hakimaki on 2008-09-09
Ignore that.  If anything, I just use ClamAV to scan my NTFS drive for downloads that will be used in my windows partition.

---

### Post by tuxxy on 2008-09-09
Yes its a trick used to  make you download the application, if you would like to stay safe just delete all your temp files/cookies on every browser close.

---

### Post by suomalainen on 2008-09-09
Ok.... I just installed Clam Tk virus scanner.

However, I want to update the virus signatures but get error message which is attached to this post as a pic.

What do I need to do?

Thanks once again.

---

### Post by suomalainen on 2008-09-09
I just also got this new error message. Not too sure what it means or if it applies to me. But if it does apply how is the requested action performed?

Thanks again everyone!!!!

P.S.. see attached pic

---

### Post by suomalainen on 2008-09-09
oops attached the wrong pic. Here is the correct one.

Many apologies....

---

### Post by tuxxy on 2008-09-09
> **suomalainen said:**
> Ok.... I just installed Clam Tk virus scanner.

However, I want to update the virus signatures but get error message which is attached to this post as a pic.

What do I need to do?

Thanks once again.

Try running the application using a sudo from the terminal

---

### Post by suomalainen on 2008-09-09
How does that install new virus signatures exactly?

Here's the eror message I go, in case, pic isn't clear enough:

Some distributions do not automatically edit
freshclam.conf and clamd.conf under /etc.
Please edit those before attempting signature updates.

---

### Post by Jack Bonner on 2008-09-09
> **suomalainen said:**
> Thanks all!

The reason I'm asking this question is because I went to the following web site using linux-Ubuntu:

[http://scanner.vav-x-scanner.com/27/?advid=1297&ref=&p=1010000000](http://scanner.vav-x-scanner.com/27/?advid=1297&ref=&p=1010000000)

A pop up appeared asking if I want a scan for viruses so I choose "ok"

Attached is the pic of what the results were.

So as you can see, I'm under the impression that I have a virus on my system.


That site is most likely a malware site designed to trick Windows users into letting the site gain access to their system to 'scan it for viruses' but instead plants malware and adware onto their system instead. it's quite common on the internet, i'm surprised that you haven't come across these sites before.

---

### Post by ronnielsen1 on 2008-09-09
>  			 		   		 		 		Anti-virus applications is not needed in Linux.
Um, McAffee begs to differ :!:
I keep forgetting to install it though :lolflag:

It took me about 6 months to lose the windows mentality of Oh no something's going to happen to my computer and files - Once I lost that I just sat back and relaxed :guitar:

---

### Post by hyper_ch on 2008-09-09
generally: no antivirus needed.

---

### Post by anewguy on 2008-09-09
Well, believe it or not, this time I'm going to stay out of the need - don't need debate!  :)

Instead, I'm going to add a question that fits the thread:

If anti-virus, etc., is not needed in Linux, why do I keep getting automatic updates that say they are security updates?  What is the difference in that terminology in Linux versus Windows?

Thanks!
Dave :)

---

### Post by Perfect Storm on 2008-09-09
Security updates is usually holes that get closed so that evil hackers can't use it to get access to your computer - This have nothing to do with virus.

---

### Post by suomalainen on 2008-09-09
Does anyone know and can tell me how to go to "root" so I may install signatures....

I posted the pic above if that make more sense.

Thank you

---

### Post by anewguy on 2008-09-09
That's what I needed to know - the difference is in terminology in Linux versus Windows (generically, "security update" is used by users [not necessarily Microsoft] to indicate a hole for a virus as well).

Now that I know that in Linux this is referring ONLY (?) to access, not viral, activity, I understand it better.

Thanks!
Dave :)

---

### Post by Perfect Storm on 2008-09-09
> **anewguy said:**
> That's what I needed to know - the difference is in terminology in Linux versus Windows (generically, "security update" is used by users [not necessarily Microsoft] to indicate a hole for a virus as well).

Now that I know that in Linux this is referring ONLY (?) to access, not viral, activity, I understand it better.

Thanks!
Dave :)

Well, it isn't an issue as there's no virus for linux out in the wild (maybe a few handful, but they aren't a threat).

---

### Post by lazyart on 2008-09-09
root is obtained by using sudo or gksudo.

Root=administrative access=the ability to install software and change vital system settings.

In Windows XP you get this by default and this is why malware infects that platform-- because by default you can install software and change vital system settings.

In Linux you do not have that by default and therefore software can't just install behind your back-- you will get an alert when something is being installed and if any vital settings are being changed.

A security update is wholly different than a virus threat.  The only way to fix a security update is to keep your system updated.  Understand also that clamav DOESN'T PROTECT YOUR LINUX MACHINE FROM GETTING INFECTED.  By nature your machine already is protected.  What clamav does is prevent you from passing off windows viruses to other windows users.

THEREFORE-- put away your clamav and go play Frozen Bubble.

---

### Post by suomalainen on 2008-09-09
Folks!

Am I missing something here or what? It's being stated in this thread that linux Ubuntu hasn't any viruses!!!!

Regardless, it was suggested, here, that if I wanted to have an antivirus program to install ClamTk. And so that's what I did.....

Right now this program is currently performing a scan. At the moment 5 viruses have been detected.

Question: I thought you said Ubuntu doesn't get viruses?

Help / suggestions happily accepted.... :)

---

### Post by hyper_ch on 2008-09-09
(1) it scans only for windows viruses
(2) windows viruses dont have any impact on linux...
(3) by scanning all files on your linux system it produces false positives
(4) by deleting all those files you might render your system unusable.

---

### Post by ronnielsen1 on 2008-09-09
I'd be curious on the output. I bet they're complaining about long file names

---

### Post by suomalainen on 2008-09-09
I guess it would be wise to "Goggle" each  possible virus detected and see what that file is and/or does?

Then make a judgement call as to whether to delete or not.

So, I guess it's still possible to down load windows viruses?

---

### Post by Perfect Storm on 2008-09-09
> **hyper_ch said:**
> (1) it scans only for windows viruses
(2) windows viruses dont have any impact on linux...
(3) by scanning all files on your linux system it produces false positives
(4) by deleting all those files you might render your system unusable.

+1

An anti-virus application can make havoc as in-experience users may think they got infected and starts messing with files that shouldn't be messed with, because of false positives.

---

### Post by Perfect Storm on 2008-09-09
> **suomalainen said:**
> 

So, I guess it's still possible to down load windows viruses?

Sure, a file you downloaded may contain a windows virus, but it's harmless on a linux system.

---

### Post by lukjad on 2008-09-09
I wouldn't worry too much about viruses in Linux. While there may be a few, they are not truly much of a danger since they do not spread very well. Just use good safety measures like only installing from trusted sites and software providers.

PS

> **tuxxy said:**
> [SNIP] to prevent the spread of the windows virii.[SNIP]
The plural of *virus* is *[viruses]("http://en.wikipedia.org/wiki/Plural_of_virus")*.

---

### Post by anewguy on 2008-09-09
I'm a little confused here.  The security updates are to stop from someone from getting and messing with my system.  In Windows, that would mean the ability to also install a virus or trojan.  Since everyone seems to indicate that for Linux (1) anyone needs root access to do anything  - and - (2) the number of Linux viruses is extremely small and "next to impossible to get", does that mean that the security updates are rather moot for just an average user?  Don't get me wrong - I apply every update - I'm just curious.  

As an ex-system's programmer and ex-sysadmin, I see these more as threats to business or multi-user system than to a single user system.  Are my assumptions correct?

Thanks again!

Dave :)

---

### Post by suomalainen on 2008-09-09
My issue is that I have "P" drive and it's accesible under Windows XP and Ubuntu.

SO I need to figure out what to do.

---

### Post by knix on 2008-09-09
> **anewguy said:**
> I'm a little confused here.  The security updates are to stop from someone from getting and messing with my system.  In Windows, that would mean the ability to also install a virus or trojan.  Since everyone seems to indicate that for Linux (1) anyone needs root access to do anything  - and - (2) the number of Linux viruses is extremely small and "next to impossible to get", does that mean that the security updates are rather moot for just an average user?  Don't get me wrong - I apply every update - I'm just curious.  

As an ex-system's programmer and ex-sysadmin, I see these more as threats to business or multi-user system than to a single user system.  Are my assumptions correct?

Thanks again!

Dave :)

Yes. they are more important on a server or multiuser system. Typically, it's a way the can login remotely without remote login enabled. This may be through an application installed on the system which has a hole, or a protocol that is insecure. It usually is not through a file.


> 
My issue is that I have "P" drive and it's accesible under Windows XP and Ubuntu.

SO I need to figure out what to do.

I would recommend using a virus scanner if you plan on adding anything to your P drive.
I'm downloading the deb right now so I can try it out.

---

### Post by lukjad on 2008-09-09
> **anewguy said:**
> I'm a little confused here.  The security updates are to stop from someone from getting and messing with my system.  In Windows, that would mean the ability to also install a virus or trojan.  Since everyone seems to indicate that for Linux (1) anyone needs root access to do anything  - and - (2) the number of Linux viruses is extremely small and "next to impossible to get", does that mean that the security updates are rather moot for just an average user?  Don't get me wrong - I apply every update - I'm just curious.  

As an ex-system's programmer and ex-sysadmin, I see these more as threats to business or multi-user system than to a single user system.  Are my assumptions correct?

While they are not *as* important, it is one of the the edges that Linux has over say Windows and Mac. If someone stops applying updates then the holes in the system will be more easily exploited. However, unless you have someone gunning for you or you like to frequent hacking or cracking cites (just for the articles! :razz:) then you don't have to panic over how soon you install them.

---

### Post by lazyart on 2008-09-09
> **anewguy said:**
> I'm a little confused here.  The security updates are to stop from someone from getting and messing with my system.  In Windows, that would mean the ability to also install a virus or trojan.  Since everyone seems to indicate that for Linux (1) anyone needs root access to do anything  - and - (2) the number of Linux viruses is extremely small and "next to impossible to get", does that mean that the security updates are rather moot for just an average user?  Don't get me wrong - I apply every update - I'm just curious.  

As an ex-system's programmer and ex-sysadmin, I see these more as threats to business or multi-user system than to a single user system.  Are my assumptions correct?

Thanks again!

Dave :)

Linux is not Windows.
A security hole is not a virus.
To prevent against security hole exploitation, you update your system, just like Windows update does.
To prevent being infected with a virus, install a virus scanner and keep the definitions updated.
Or, install Linux.

If your system hosts a web server, mail server or anything publicly accessible and a security hole if found, you'd better patch it or the system is vulnerable to DoS attacks, malicious scripting, buffer overruns, etc.  On top of that your data could be compromised.  That is not much of an issue with desktops, but generally being patched is better than not.

To reiterate- clamav scans for windows viruses present in files.  Much like you can carry a recessive gene and pass it on to your children, you can carry an infected file and it won't affect your system... but once it's passed on to a Windows machine it can become a "dominant" gene.

TuxRacer is another great way to spend your time vs. configuring clamav updates. :)

---

### Post by aysiu on 2008-09-09
I've moved this to Recurring Discussions

---


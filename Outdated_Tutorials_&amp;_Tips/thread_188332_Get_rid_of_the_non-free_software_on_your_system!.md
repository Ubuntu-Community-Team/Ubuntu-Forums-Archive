---
title: "Get rid of the non-free software on your system!"
date: 2006-06-03
forum: Outdated Tutorials &amp; Tips
---

### Post by zenlunatic on 2006-06-03
**Warning**: this may break your system.  NO WARRANTY.  I'm not responsible for what this does to your computer (although I will try to help you).

First do this
```
$ sudo -s
```
Next
```
# apt-get install vrms
```

Virtual RMS should probably  report to you all the non-free packages on your system.  If not run the following command:

```
# vrms
```

Now fire up synaptic.  Go to search and find the true names of the packages that are listed (it may cut off some of them so you have to find them.

Click on those packages and mark for COMPLETE REMOVAL.

Reboot.

RMS would be proud :)

---

### Post by pay on 2007-02-21
This is a cool program. Thanks.

---

### Post by Iandefor on 2007-02-21
I'd throw in a warning about playing with kernel-related packages. I personally can't X working right without nvidia's binary blobs and if I removed those I'd kill X until it was dead.

---

### Post by pay on 2007-02-22
It doesn't seem to detect all proprietary programs though. I just installed some printer drivers and they weren't detected.

---

### Post by Iandefor on 2007-02-22
> **pay said:**
> It doesn't seem to detect all proprietary programs though. I just installed some printer drivers and they weren't detected.That's another problem with vrms: it doesn't detect everything. It finds stuff from the main repositories, I believe, and then it falls over flat.

---

### Post by Toxicity999 on 2007-02-23
wouldn't recommend this to anyone who does anything 'fun':

linux-generic             Complete Generic Linux kernel
linux-restricted-modules- Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules- Non-free Linux 2.6.20 modules on x86/x86_64
linux-restricted-modules- Non-free Linux 2.6.20 modules helper script
linux-restricted-modules- Restricted Linux modules for generic kernels
nvidia-glx                NVIDIA binary XFree86 4.x/X.Org driver
rar                       Archiver for .rar files
tango-icon-theme          Tango Icon theme
unrar                     Unarchiver for .rar files (non-free version)

---

### Post by madmetal on 2007-02-23
nice program!

---

### Post by neighborlee on 2007-02-24
> **zenlunatic said:**
> **Warning**: this may break your system.  NO WARRANTY.  I'm not responsible for what this does to your computer (although I will try to help you).

First do this
```
$ sudo -s
```
Next
```
# apt-get install vrms
```

Virtual RMS should probably  report to you all the non-free packages on your system.  If not run the following command:

```
# vrms
```

Now fire up synaptic.  Go to search and find the true names of the packages that are listed (it may cut off some of them so you have to find them.

Click on those packages and mark for COMPLETE REMOVAL.

Reboot.

RMS would be proud :)

maybe so...and  maybe oss is kewl for obvious reaons..BUT no one has YET made free nvidia drivers so frankly this hardly  a good thing to run if you need such drivers...your warning is fine but it doesn't go far enough for unsuspecting users...we really dont need another oss vs non-oss debate do we ;)..its old and very tired.

cheers
nl

---

### Post by pay on 2007-02-24
This wasn't a oss vs non-oss debate. It was just a suggestion for those that have already made up their mind. I like it because it gives you an idea of how many non-oss programs you have > 3 non-free packages, 0.2% of 1458 installed packages.

---

### Post by madmetal on 2007-02-24
full of non-free software.. :-({|= :-\" 

    Non-free packages installed on ubuntu

gsfonts-other             Additional fonts for the ghostscript interpreter
  Reason: Partly no modifications allowed, partly shareware
libdivx0-binary           DivX MPEG-4 library
libdivxdecore0-binary     DivX MPEG-4 library (decoder)
libdivxencore0-binary     DivX MPEG-4 library (encoder)
linux-restricted-modules- Non-free Linux 2.6.17 modules helper script
skype                     Free Internet Telephony - The whole world can talk for
sun-java5-bin             Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-jre             Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-plugin          The Java(TM) Plug-in, Java SE 5.0
unrar                     Unarchiver for .rar files (non-free version)
  Reason: Modifications problematic

   Non-free packages with status other than installed on ubuntu

nvidia-glx                ( dei)  NVIDIA binary XFree86 4.x/X.Org driver
  Reason: Proprietary license

---

### Post by neighborlee on 2007-02-24
> **madmetal said:**
> full of non-free software.. :-({|= :-\" 

    Non-free packages installed on ubuntu

gsfonts-other             Additional fonts for the ghostscript interpreter
  Reason: Partly no modifications allowed, partly shareware
libdivx0-binary           DivX MPEG-4 library
libdivxdecore0-binary     DivX MPEG-4 library (decoder)
libdivxencore0-binary     DivX MPEG-4 library (encoder)
linux-restricted-modules- Non-free Linux 2.6.17 modules helper script
skype                     Free Internet Telephony - The whole world can talk for
sun-java5-bin             Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-jre             Sun Java(TM) Runtime Environment (JRE) 5.0
sun-java5-plugin          The Java(TM) Plug-in, Java SE 5.0
unrar                     Unarchiver for .rar files (non-free version)
  Reason: Modifications problematic

   Non-free packages with status other than installed on ubuntu

nvidia-glx                ( dei)  NVIDIA binary XFree86 4.x/X.Org driver
  Reason: Proprietary license

ok im tired of this nonsense...I knew it would turn into a nvidia debate as of course atm the drivers are non-oss...and look here another worthy mention by someone apparantly feels it necesssary..fine..lets not forget that nvidia is the oNLY gig in town atm so imo its insincere to target their drivers as non-oss..has anyone got anything with equal quality and free..I didn't think so..

I am just getting sick of seeing nvidia this non-oss target...its not right given that they never 'had' to release anything for us given our pauldry marketshares. ( although sure 'now' dell is being asked by customers for  linux, which is def. a good sign ) : 

[http://www.dell.com/content/topics/global.aspx/alliances/en/linux?c=us&cs=555&l=en&s=biz](http://www.dell.com/content/topics/global.aspx/alliances/en/linux?c=us&cs=555&l=en&s=biz)
( I only mention this as my good friend told me about it a few days ago and I just thought about it ,,and granted its only redhat and suse )

anyway the whole nvidia/non-oss thing, is moot and misplaced obviously without something to show for all their yelling....

cheers
nl

---

### Post by deanlinkous on 2007-02-27
and the pupose of your post is to provide what insight?

---

### Post by Toxicity999 on 2007-02-28
Who was arguing? No one I saw. I didn't even see this 'debate' you spoke of. some people posted there lists, with little commentary. No need to go software nazi on us and say what we all had agreed upon already :KS

---

### Post by neighborlee on 2007-03-04
> **deanlinkous said:**
> and the pupose of your post is to provide what insight?

to show that just because 'proprietary' is hightlighted, that not all of us are fanatics about non-oss..some of us 'use' it daily..

It is now 'moot' anyway since mark is set on including it ( at least OPT in) in next ubuntu version.

Even the gentoo guy ( daniel) doesnt see this as a problem even though many have argued with him to the contrary.

OSS is great, but I dont like trend I see regarding removing non-oss just as a ideology thats all..it lumps all such apps into the same corner and I think its wrong, because alot of non-oss is great stuff,- and atm its all we have ;) ( plus I think it sends the wrong message to vendors considering supporting linux with their NON-oss software )


I am not done with this thread, so dont bother expecting to see anymore comments or replies from me. ;)

cheers
nl

---

### Post by deanlinkous on 2007-03-04
> **neighborlee said:**
> 
I am not done with this thread, so dont bother expecting to see anymore comments or replies from me. ;)

cheers
nl
makes sense, as much sense as the rest of your post :lolflag:

---

### Post by loclarkey on 2007-03-07
I know this isn't the place to ask questions, but seriously:  why is the linux kernel listed as non-free software?

---

### Post by bravemosquito on 2007-03-08
> **loclarkey said:**
> I know this isn't the place to ask questions, but seriously:  why is the linux kernel listed as non-free software?

Yeah, why? :roll: Is Linux kernel free or not?

```
linux-386                 Complete Linux kernel on 386.
linux-restricted-modules- Non-free Linux 2.6.15 modules on 386
linux-restricted-modules- Non-free Linux 2.6.17 modules on 386
linux-restricted-modules- Restricted Linux modules on 386.
linux-restricted-modules- Non-free Linux 2.6.17 modules helper script
skype                     Free Internet Telephony - The whole world can talk for
unrar                     Unarchiver for .rar files (non-free version)
```

---

### Post by deanlinkous on 2007-03-08
maybe there is stuff in the linux kernel that is non-free or maybe because those restricted-modules are non-free and they depend on the kernel? any ideas?

---


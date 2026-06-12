---
title: "Viruses in ubuntu through wine!"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-06-05
hey...

If I were to accidentally download a windows virus on my ubuntu machine, or a trojan or spyware (any malware basically), and then run it in wine, will it damage my ubuntu system?

That is, will it affect anything outside of my windows fake directory (the wine c drive directory)? Can it write or erase files on my other ubuntu directories (other than the fake windows directory)? Can it execute files on my ubuntu machine (not in my virtual windows, wine)? 

Also, say I suspected a certain windows .exe file of being a trojan or spyware or a malicious program, and I wanted to know what it exactly does when it is executed, are there any tools that I can use to monitor the activities of all the programs run in wine? Say, a tool that tells me if a program run in wine makes any connection to the internet or spreads in the system etc...

I know that you can use an anti-virus in ubuntu to check files for windows viruses.

thanks all

---

### Post by Joeb454 on 2008-06-05
If you specifically ran it in Wine. I think it would most likely trash your Wine install ;)

Though I don't think it would do anything to Ubuntu, but you should probably still back it up, just in case :)

---

### Post by Dr Small on 2008-06-05
Check out this thread. You may find your answer in it:
[http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

---

### Post by ardvark71 on 2008-06-05
> **newbuntuxx said:**
> hey...

If I were to accidentally download a windows virus on my ubuntu machine, or a trojan or spyware (any malware basically), and then run it in wine, will it damage my ubuntu system?

That is, will it affect anything outside of my windows fake directory (the wine c drive directory)? Can it write or erase files on my other ubuntu directories (other than the fake windows directory)? Can it execute files on my ubuntu machine (not in my virtual windows, wine)? 

Also, say I suspected a certain windows .exe file of being a trojan or spyware or a malicious program, and I wanted to know what it exactly does when it is executed, are there any tools that I can use to monitor the activities of all the programs run in wine? Say, a tool that tells me if a program run in wine makes any connection to the internet or spreads in the system etc...

I know that you can use an anti-virus in ubuntu to check files for windows viruses.

thanks all

Hi...

No, the virus you suspect can NOT infect or damage your Ubuntu system in any way, unless there is something I don't know about. :)

Edit: I guess there can be consequences to Ubuntu according to Dr. Small's link...you might want to download a virus scanner like ClamAV.

I don't the answer to your last question but I'm sure someone on here would.

Best Regards...

---

### Post by oldsoundguy on 2008-06-05
It IS possible a Windows virus could trash the contents of WINE, but it sure won't get into your Linux kernel.

When in doubt, go to the administration and un-install WINE, re boot, and re-install it.  You WILL lose all the Windows stuff you installed in WINE, but that is the price you pay for trying to run Windows stuff (which we all know is swiss cheese) on Linux

IF you are running a server or are really concerned:
[http://www.f-prot.com/download/home_user/download_fplinux.html](http://www.f-prot.com/download/home_user/download_fplinux.html)
FREE!!!!!

I have been using F-Prot on Windows boxes for years and have never had a virus install on the Windows machines .. took time to root out the garbage that came in and got held up, but no damage. (last major issue came in on a supposedly new and sealed CF card!  Had a really NASTY virus installed on it in China!  .. lesson: scan your plug in cards and drives before using!)

The big issue now is not virus .. it is spyware and hijackers .. and that won't happen in Linux.

---

### Post by newbuntuxx on 2008-06-06
thanks guys..i just want to put what you said in point form:

1. When running a virus in wine, it will damage your wine installation

2. If you are running wine with root privileges, then the virus may spread to other directories in your file system and may damage them.

3. If wine is set to use your Z drive, which I assume is your /, then the virus can spread to your file system and damage it.

4. If wine is executed with normal user privileges and it is only using the fake windows directory, then the virus can only affect that wine directory. 

Now, I have a few questions, and I may be repeating myself, so i apologize:

1. How do I make sure that my WINE is run with normal user privileges, and that it is using a wine directory within my user account and not using the "/"

2. Since Wine is a virtual operating system, is it possible to monitor the activities of the programs that you run in WINE? 

3. If the above is not possible, then, is there a similar virtual system that can be used to execute programs and watch their activities?

Thanks alot guys...

---

### Post by sam_delta on 2008-06-06
> **newbuntuxx said:**
> 

1. How do I make sure that my WINE is run with normal user privileges, and that it is using a wine directory within my user account and not using the "/"


wine wont run as root unless you type "sudo wine somehting" or for some reason it prompt you for your password, so in short words, if you dont type your password when you run wine, it wont run as root.

sam

---

### Post by kesman on 2008-06-06
running
```

winecfg

```
or
```

wineconfig

```

can't remeber which it was, you can set the used "drives" for wine. You can manage how your CD-drives and "my documents" are mounted from your linux filesystem to wine. Just disable anything but "C:" which is usually something like /home/user/.wine/c_drive and you'll be safe, no matter what, unless you run wine with sudo.

---

### Post by newbuntuxx on 2008-06-06
Thanks a lot kesman, that was really helpful. and thanks for the explanation sam_delta, it turns out that i never ran wine with root privilges, so, no harm done. I'll make sure that its only using my /home/user/.wine directory.

just two questions left, if anyone can provide an answer, i'll be grateful:

2. Since Wine is a virtual operating system, is it possible to monitor the activities of the programs that you run in WINE? 

3. If the above is not possible, then, is there a similar virtual system that can be used to execute programs and watch their activities?


thanks a lot

---

### Post by sam_delta on 2008-06-06
well, this quote might help you. wine is not a emulator, so i belive there is no way to monitor specific activity made by wine (unless theres a way i dont know of)you might be able to monitor wine as any other linux program , but i believe thats not what your looking for.
>  Wine is that it's a "compatibility layer" (WINE itself stands for WINE IS NOT an EMULATOR). Being a compatibility layer it translates commands sent from windows programs into commands Linux understands, thus allowing the program to runquote from [http://ubuntuforums.org/showthread.php?t=72598&page=6](http://ubuntuforums.org/showthread.php?t=72598&page=6)

you might want to look into VMware , a virtual machine, its pretty good and you can install windows on it, safer for your linux install

sam

---

### Post by mohenjo on 2008-06-06
sam_delta's Wine quote also speaks to whether or not a virus can damage your linux setup.  Since most viruses are written for Windows, and designed to mess up areas of Windows, it should have little to no effect on a linux machine.  Take the Windows Registry for example.  This is a prime target for destructive viruses, because deleting things from the registry can halt a Windows system.  If Wine was to interpret registry damaging lines of code into linux code, the linux system would pretty much laugh, as it doesn't use a registry.

There's also the question of how a program installed and run from Wine would be infected.  There's no need to run MS Outlook when there are a number of pretty good open source pieces of software which can communicate with Exchange, so email viruses won't spread into your Wine applications.  If you're running Internet Explorer through Wine (I don't even know if that's possible, but let's pretend) then I suppose you could mess up your IE install with all the spyware and other junk that's out there, but again, that shouldn't mess with your Linux install.

---

### Post by oldsoundguy on 2008-06-06
There is an install program to place IE in Wine .. and it IS needed by some.  Web designers. They need to have a copy in order to check their code to make sure that it is readable, for instance.
And there are some web sites where the ONLY browser that will work on the site is IE because some joker was too lazy to make it universal or is CLUELESS or has used the MicroSLOTH program exclusively to design the site!

---

### Post by newbuntuxx on 2008-06-08
thanks for the replies guys....I actually started using VMware as per sam_delta's advice, link to download and install for hardy:

[http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/](http://ubuntu-tutorials.com/2008/05/03/install-vmware-server-105-on-ubuntu-804-hardy/)

and it is simply amazing. Just finished installing XP pro. It works like a charm.

I also removed WINE. So, now I enjoy the security and flexibility of linux, and I get to use the windows software that I need. Too good to be ture :)

---


---
title: "Every small mistake - I must reinstall Ubuntu ?"
date: 2016-02-03
forum: New to Ubuntu
---

### Post by helm10101 on 2016-02-03
Hello,

I am a new Linux user. every time I have a problem regarding some issue, I am looking for ways to solve it on online forums such as this or other places on the internet.
Sometimes, for the general things the things I find work well.
But for specific things, and that really important ones, like my ongoing issue with installing AMD drivers and Catalyst control panel (ongoing on this forum), - there are so many options, every place you see a different answer as to what to type in terminal. I try to follow everything that I think is related to my issue until It will work. on the way I always follow commands without explanation that do stuff (you see in the terminal it does something) but I don't know what exactly, and the issue is still not solved. 
So far I reinstalled Ubuntu 3 times, because I just can't solve some issues, and when I try to follow the stuff I find, it will just ruin the Operating system.
How can I know all the stuff that I installed, all the changes that I did, when I followed the online commands? and what exactly do they do?

hopefully you can make things more clear to me,

Thanks

---

### Post by leunam12 on 2016-02-03
One thing you can do is when you install again, if you have not done this yet, is install your system files to a small partition (I use 24GB) that way you can make a backup relatively quick before running commands and if something goes wrong all you have to do is restore your system partition from backup. I use clonezilla for backup, there are other systems, do some research.

---

### Post by newbie-user on 2016-02-03
It is very important to not blindly follow commands that are posted on the Internet. Look at the man pages for each command so that you learn what each command does. There are many ways to get things done in Linux and that's why you see lots of tutorials doing things one way or another.

So to see a list of all the commands you've issued, type "history" at the command prompt. To figure out what each command does, type "man [name of command]", and it will show you the how-to manual for the command. For example: man nano

---

### Post by HermanAB on 2016-02-03
Well, in the beginning it sure feels that way and you probably will install many times more before you learned what you need to know.

It sure helps that it is really easy and quick to re-install, but it will also help if you try to read as much as possible about the problem that you are trying to overcome, before running some obscure commands.

---

### Post by Habitual on 2016-02-03
A great place to start is [URL="https://help.ubuntu.com/"]Official Ubuntu Documentation
[/URL]

---

### Post by Bashing-om on 2016-02-03
helm10101; Oh for goodness sake;

My communications skills reek, and diplomacy never has fit me .
But, let me try and address your issue(s).

Let's begin by adjusting your perspective. You are setting before a marvel of the open source world. A operating system that does run on a myriad of platforms: IBM, Solaris, Asrock. Abit, Intel, AMD, Realtech .. and on and on and on across a very broad spectrum of hardware. Whereas - for instance Microsoft and Mac - closed source - are designed to run on specific hardware generally you get it as a bundled system.

Open source, with the advent of new hardware many times the manufactures just do not consider linux and either do not provide us support or is very slow in coming. Maybe even to the point of vendor lockin and other impediments to adapting the hardware to the open source environment. Bottom line, new hardware is new problems . Wonder of wonders, open source does adapt ! But it does take time.

Learning your operating system, once you get beyond the point and click GUI, is a learning curve. No one but you can climb it for you. The good news here is that the documentation abounds . one of the greatest difference here from that of closed source . 

Number one rule, NEVER execute a command that you do not understand . And the means to comprehend is on you system. 
All linux distros come with the manual installed. Consulting the manual will at least give you a clue of why/what/when and where.
in terminal get an introduction to this manual by executing the terminal command ( here ya just got to take my word for it !):
```

man man

```
each and every command has a man page to explain it , as well as many applications:
Further system documentation, have a look and go hog wild:
```

ls -al /usr/share/doc/

```

What is installed ? Well the package manager keeps track . Have a long read:
 [https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites](https://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_debian_package_management_prerequisites)

what have you changed .. well, the log files will tell you .. just a matter of learning what file is generated from what source .
have a look:
```

ls -al /var/log/apt/
ls -al /var/log/dpkg.log

```
See something of interest .. hey open up a log file reader - or a text editor and have a good read.
Additionally I might add .. It is a good idea to keep a change log of ALL alterations that you make to the base install.

There is no magic elixer one can take to gain knowledge, it takes time effort and want to on your part. Please bear in mind, none of us were born knowing what we know ... and all of us have broken our systems many many times on our own curve of learning. It has been and still is true that when you break this system - you get to keep the pieces and put it back together. When you break the bounds of what can be done, you are going to break the system. Now you are ready to learn something !

Now if you think I am an advocate of open source
[INDENT][INDENT][INDENT]well, you are right
[/INDENT][/INDENT][/INDENT]

---

### Post by Geoffrey_Arndt on 2016-02-03
Helm 10101:

Just a few thoughts about the issue(s) you've been working through:

>   Good advice from Forum responders above . . I especially agree with the action of creating a "Test Environment" to manage your changes (in IT this is done in ITL's (Integration Test Labs).   I like using a full-install of Ubuntu on a USBv3 Flash-Stick to simulate a Production Environment.   Another option used by tens of thousands of organizations (public/private) is the Virtual Environment (kvm, qemu, virtualbox, vmware, Docker, etc.).   Business today could not effectively operate without these Virtual tools/systems.

>   The whole "reason" why AMD is such an issue is that AMD equipped hardware is pre-designed and tested for the Windows environment.   There are scarce to zero resources spent to test their drivers on Ubuntu or Redhat (RHEL), or Suse (SLES).  And so . . . . what's the proper response?   AMD/ATI, and nVidia can't get too excited about allocating money/time into a PC market that hovers between the 1 & 3 percent range (on the consumer side).   

>   So again, what's the proper response if you can't easily or successfully "retrofit" your hardware for Ubuntu . . . . . ?   Well, for a starter, when you get your next PC . . . . either do your homework (research) up front BEFORE you buy (helps to get an ALL Intel system), or just go to a Linux vendor such as System76, Zareason or many others and pre-order a Linux equipped PC.   Now, I do understand, if you're a serious gamer, these options are not 100% effective for top-end gaming.

Anyway . . . as said above, a full install on a USBv3 Flash-Stick (32 GiB or more) works wonders for me . . very useable, and perhaps Clonezilla is a way to restore the OS (although I've never tried that).

---

### Post by QIII on 2016-02-03
> **Geoffrey_Arndt said:**
> The whole "reason" why AMD is such an issue is that AMD equipped hardware is pre-designed and tested for the Windows environment.   There are scarce to zero resources spent to test their drivers on Ubuntu or Redhat (RHEL), or Suse (SLES).  And so . . . . what's the proper response?   AMD/ATI, and nVidia can't get too excited about allocating money/time into a PC market that hovers between the 1 & 3 percent range (on the consumer side).

Um.... No.

AMD engineers actually work very closely with the open source community.  AMD is a long-time member of the Linux Foundation.  The reason AMD is so "difficult" is that people don't install the drivers properly.  Before AMD bought ATI, is was certainly the case that ATI didn't give a hoot.

@helm10101:  Without knowing the model of your graphics adapter it is hard to give advice.  We also don't know what you have tried in the past.

---

### Post by Geoffrey_Arndt on 2016-02-03
> **QIII said:**
> Um.... No.

AMD engineers actually work very closely with the open source community.  AMD is a long-time member of the Linux Foundation.  The reason AMD is so "difficult" is that people don't install the drivers properly.  Before AMD bought ATI, is was certainly the case that ATI didn't give a hoot.

@helm10101:  Without knowing the model of your graphics adapter it is hard to give advice.  We also don't know what you have tried in the past.

QIII . . . from what I read and hear from members of our local linux users group, support has improved - - and AMD recently announced an open source version of their graphics "basic" driver (I can't recall the exact name of that at the moment).  So, better than it was.  I just prefer FOSS or other open source support as Intel and other companies like Qualcomm/Atheros have done.   Makes retrofitting Windows designed hardware a lot easier IMHO.

G

---

### Post by helm10101 on 2016-02-04
Thanks everyone, it was really helpful. I will definitely use the 'man' command from now on, and read the documentations! 

It really is nice to have a system that is open source (the whole Linux system, including Ubuntu), with so many options to choose.
The downside is obviously the learning curve, which is much harder, I think, than using Windows for example.
I am no software engineer, but I wonder if it is possible to make a version of Linux that is easy to use, which installs the drivers automatically, or that have installation softwares like in Windows, rather than having to download stuff, than using terminal to install them. Example is that in Windows, I have the auto detect utility from AMD website, you just click it and it installs your driver + software.
Or, in case I want to manually choose my driver, I got to the vendor website, download and install. and if I happen to choose the wrong driver, it won't let me install, or prompt me that it is a wrong driver, and not just install it, and let you know you did something wrong only after you reboot, and get "Low Graphics Mode" (in my case:D) without option to recover
On Ubuntu, if I got it right, you need to install driver, restart, install the other extension for this driver, restart, and then install the software and restart again?

By the way, I think there's something more basic I probably am having trouble with: installing stuff. From what I understand, you have a repository with all the available installations for Ubuntu, and what you do is, you download a package that contains a bundle of stuff that are related to the same thing, and from that one, you choose that package that you need?

Also, my thread about my AMD hardware (AMD Radeon R5 M230)  is here: [http://ubuntuforums.org/showthread.php?t=2312180](http://ubuntuforums.org/showthread.php?t=2312180)

Thanks again!

---

### Post by mastablasta on 2016-02-04
> **Geoffrey_Arndt said:**
> QIII . . . from what I read and hear from members of our local linux users group, support has improved - - and AMD recently announced an open source version of their graphics "basic" driver (I can't recall the exact name of that at the moment).  So, better than it was.  I just prefer FOSS or other open source support as Intel and other companies like Qualcomm/Atheros have done.   Makes retrofitting Windows designed hardware a lot easier IMHO.

G

Their long term aim seems to be to go full opensource on drivers. or withhold only portions as closed source.

> **helm10101 said:**
>  Example is that in Windows, I have the auto detect utility from AMD website, you just click it and it installs your driver + software.
Or, in case I want to manually choose my driver, I got to the vendor website, download and install. and if I happen to choose the wrong driver, it won't let me install, or prompt me that it is a wrong driver, and not just install it, and let you know you did something wrong only after you reboot, and get "Low Graphics Mode" (in my case:D) without option to recover
On Ubuntu, if I got it right, you need to install driver, restart, install the other extension for this driver, restart, and then install the software and restart again?

no, in Ubuntu you install the driver, set it up/initialise it whatnot, reboot, then install software. you don't need to reboot to install software. you need to reboot when you install closed source drivers since they add stuff to kernel I believe. you case is special anyway as it is a hybrid and for some of them AMD didn't provide any good GUI solution that would work out of the box. I do not have a hybrid GPU, so all I did was click install driver and reboot the OS and that was it. AMD drivers knew what to do, which driver to install etc. 

> 
By the way, I think there's something more basic I probably am having trouble with: installing stuff. From what I understand, you have a repository with all the available installations for Ubuntu, and what you do is, you download a package that contains a bundle of stuff that are related to the same thing, and from that one, you choose that package that you need?

repositories have packages and applications. when you install a package/application it check which other packages it needs and installs them. the packages are often shared which is why Linux programs are much smaller than windows. but on the other hand you can often have multiple version of same program (old, new) installed on windows which is not always possible on Linux. google play or apple store are repositories if that helps in any way.

---

### Post by HermanAB on 2016-02-04
Technically, installing a driver that was compiled as a module doesn't require a reboot.  You can load and unload modules on the fly.

---

### Post by Rocky_Bennett on 2016-02-04
> **helm10101 said:**
> Hello,

I am a new Linux user. every time I have a problem regarding some issue, I am looking for ways to solve it on online forums such as this or other places on the internet.
Sometimes, for the general things the things I find work well.
But for specific things, and that really important ones, like my ongoing issue with installing AMD drivers and Catalyst control panel (ongoing on this forum), - there are so many options, every place you see a different answer as to what to type in terminal. I try to follow everything that I think is related to my issue until It will work. on the way I always follow commands without explanation that do stuff (you see in the terminal it does something) but I don't know what exactly, and the issue is still not solved. 
So far I reinstalled Ubuntu 3 times, because I just can't solve some issues, and when I try to follow the stuff I find, it will just ruin the Operating system.
How can I know all the stuff that I installed, all the changes that I did, when I followed the online commands? and what exactly do they do?

hopefully you can make things more clear to me,

Thanks



So you are saying that Ubuntu is just like Windows. I have probably broke Windows 10 at least 15 times in the last few months where the only thing to do is to reinstall it from scratch. I have only broke Ubuntu twice in the last few months where I had to reinstall it, and both times were my fault.

---

### Post by buzzingrobot on 2016-02-04
The web is very full of bad Linux guidance. (And bad Windows guidance for that matter.)  Some is well-intentioned, some is just clickbait. 

 Be sure any advice you find applies to your **specific** hardware and software.  

Be wary of blindly copying terminal commands from unknown sites that don't bother to explain what's going on. There's a good chance the site's author can't explain it, but just plagiarized content from somewhere else. 

If a site's advice doesn't work, think twice about going back.

Always start with the documentation and forums for Ubuntu, or any other distribution you happen to be using. Not that many differences exist between most distributions, but the one's that do exist are usually important.

---

### Post by Rocky_Bennett on 2016-02-04
> **buzzingrobot said:**
> The web is very full of bad Linux guidance. (And bad Windows guidance for that matter.)  Some is well-intentioned, some is just clickbait. 

 Be sure any advice you find applies to your **specific** hardware and software.  

Be wary of blindly copying terminal commands from unknown sites that don't bother to explain what's going on. There's a good chance the site's author can't explain it, but just plagiarized content from somewhere else. 

If a site's advice doesn't work, think twice about going back.

Always start with the documentation and forums for Ubuntu, or any other distribution you happen to be using. Not that many differences exist between most distributions, but the one's that do exist are usually important.




Good advice.

---

### Post by Mark Phelps on 2016-02-04
One thing that you need to learn that makes Linux very different from Windows is that you don't go rummaging around for drivers.  That's really a bad idea.

Open-source drivers come bundled by default and, unless you are doing intensive 3D gaming, you don't really need to go hunting down AMD drivers because the open-source drivers are installed by default.

Update: Just saw your other thread about the AMD driver problem ...

When you click the option you want, the driver is installed.  IF you then want to see if fglrx got installed, open a terminal and enter "fglrxinfo".

Also, if you have a machine that has dual graphics, then you are likely out of luck in Linux, as those require special drivers which, generally, are not available for Linux.

---

### Post by Rocky_Bennett on 2016-02-04
Have you opened up SOFTWARE AND UPDATES and scrolled over to ADDITIONAL DRIVERS and let Ubuntu automatically install any additional drivers?

---

### Post by monkeybrain20122 on 2016-02-04
You have a hybrid graphic card and normal ways of installing the driver probably is not going to work. Read [this ]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD")carefully before you proceed any further.

---

### Post by helm10101 on 2016-02-05
> **Rocky_Bennett said:**
> Have you opened up SOFTWARE AND UPDATES and scrolled over to ADDITIONAL DRIVERS and let Ubuntu automatically install any additional drivers?

That was the first thing I did, and it find that I have AMD, but it chooses the X.org driver, although it shows some more proprietary AMD drivers.
What I did was to choose one of the other proprietary drivers that were listed there, and when I rebooted, I got Low Graphics Mode

---

### Post by monkeybrain20122 on 2016-02-05
> **helm10101 said:**
> That was the first thing I did, and it find that I have AMD, but it chooses the X.org driver, although it shows some more proprietary AMD drivers.
What I did was to choose one of the other proprietary drivers that were listed there, and when I rebooted, I got Low Graphics Mode

Yeah I think it is kind of obvious (if I have to guess) that when you reboot you boot into the Intel card. Like I told you since you have a hybrid card you have to take special steps.

---

### Post by helm10101 on 2016-02-05
So, I have to find a way to install the AMD, but boot into the intel card, but how do I do that? I'm tired of the Low Graphics Mode.
I think that even if I will later use recovery mode to purge fglrx, I will still have the Low Graphics Mode problem, because I saw that it changes the boot up Configuration file

---

### Post by monkeybrain20122 on 2016-02-05
Well check out my link and google "Ubuntu AMD hybrid graphic card" if that link doesn't fix your problem. I don't have any experience with hybrid graphic to offer you help, I only know enough to stay away from them. :)

---

### Post by trag on 2016-02-20
When you play around doing stuff on your Linux PC you always run the risk of something breaking,I recommend you create a restore point before hand so you can go back before the change,Install Timeshift from the Ubuntu software center and create a restore point first.With regards to your AMD drivers installation there is a solution out there that worked for me.I went to this web site   [https://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install](https://www.thefanclub.co.za/how-to/ubuntu-amd-catalyst-install) , I created a restore point and installed the app which did a fine job of installing the appropriate driver and the ccc center on my machine. Some purist's would scoff at this as being a cheat but I don't care.I would like to recommend a few websites that are excellent resources for Beginners to Linux,I will include the links for you. 
[http://linux.softpedia.com/](http://linux.softpedia.com/)     [http://www.howtogeek.com/t/linux/](http://www.howtogeek.com/t/linux/)     [http://www.upubuntu.com/](http://www.upubuntu.com/)  [https://www.maketecheasier.com/category/linux-tips/](https://www.maketecheasier.com/category/linux-tips/)  [http://www.noobslab.com/](http://www.noobslab.com/)  [http://www.webupd8.org/](http://www.webupd8.org/)  [http://ubuntuhandbook.org/](http://ubuntuhandbook.org/)  [http://www.makeuseof.com/service/linux/](http://www.makeuseof.com/service/linux/) 
I hope you visit each one of these sites and along the way find others that will help.
Best of Luck
Trag

---


---
title: "why should i use ubuntu"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by biggiemokey on 2008-08-26
I used to have Ubuntu Hardy on my computer through Wubi, which claimed to have full Ubuntu functionality.  I ended up uninstalling it - despite the fact that it loaded up quicker and I really liked the functionality, it just didn't work...Certain things, like ActiveX controls, Java, Flash just wouldn't show, and there was a "play" icon in a gray circle.  Also, even though I was on a nice Dell XPS desktop (which desperately needs reformatting, but still) the fan would be louder than with Windows XP and the computer would heat up.

So my question is, did I do something wrong by having a computer in bad shape run Wubi?  Or does Ubuntu always have little problems like that, such as servers being down when you're trying to download AVI codecs???  I really like the Open Source movement, and asked a few questions on here to try and figure out how to dual boot, but after my experience I'm not so sure.  Was it a fluke or is Ubuntu always like that?

---

### Post by ooobuntooo on 2008-08-26
> **biggiemokey said:**
> I used to have Ubuntu Hardy on my computer through Wubi, which claimed to have full Ubuntu functionality.  I ended up uninstalling it - despite the fact that it loaded up quicker and I really liked the functionality, it just didn't work...Certain things, like ActiveX controls, Java, Flash just wouldn't show, and there was a "play" icon in a gray circle.  Also, even though I was on a nice Dell XPS desktop (which desperately needs reformatting, but still) the fan would be louder than with Windows XP and the computer would heat up.

So my question is, did I do something wrong by having a computer in bad shape run Wubi?  Or does Ubuntu always have little problems like that, such as servers being down when you're trying to download AVI codecs???  I really like the Open Source movement, and asked a few questions on here to try and figure out how to dual boot, but after my experience I'm not so sure.  Was it a fluke or is Ubuntu always like that?

You need to install the Ubuntu restricted extras.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Zero Prime on 2008-08-26
I have to ask, why would you want activeX running on your computer?

---

### Post by Tux.Ice on 2008-08-26
if you dual boot , like i do youre experience will be much better.

---

### Post by nicedude on 2008-08-26
No Wubi just stinks, it is not a real linux install but instead is Linux ran inside Windows. For a starters that means you cant get the same speed etc with Wubi as you would with a full real install of Ubuntu. Now all that said don't expect everything in Ubuntu to be simple as sometimes learning how to get something working might take some research. But as to why use Ubuntu? , duh to FREE YOURSELF from a megalomaniac crappy OS maker who shall remain nameless & instead join the open source community to which aforementioned corporate bullies will never participate.

---

### Post by ugm6hr on 2008-08-26
ActiveX won't work.  Flash / Java works fine if you install them.

As for the fan - depends on your mobo's linux drivers.  Or sometimes on BIOS settings.

As for the question...  Why should you use Ubuntu?

Only you can decide the answer to that.

---

### Post by xravexheavenx on 2008-08-26
> **Zero Prime said:**
> I have to ask, why would you want activeX running on your computer?

I am wondering the same thing as Zero.

The majority of legit sites do not use ActiveX anymore because of the vulnerabilities if has to potentially compromise your computer.

If you REALLY need ActiveX for something you can just run IE though WINE.  

Also, your box may be working harder because it is indeed running 2 operating systems instead of just one.  WinBlows annihilates system resources in most cases and there isn't much left for Ubunutu to use.  Your best bet is to simply get the LiveCD and boot from that and play with it and if you like it, resize your WinBlows partition and do a dual-boot.

---

### Post by vorgusa on 2008-08-26
the restricted extras definitely help out in functionality.  Having to do with your other remarks, remember you were running two OS's at the same time and having any issues will just compound that.. 

For the ActiveX comment, you can not get ActiveX to work on Windows using firefox, so it is not going to work on Ubuntu... you are going to have to need IE for that.  And in general there will always be issues you find in Ubuntu that you will not find in Windows and the other way around too.. they are different OS's

---

### Post by Bloch on 2008-08-26
> Was it a fluke or is Ubuntu always like that?

It is often like that, in my experience over 5 years of linux on my desktop. (I have never extensively used a windows XP desktop so I can't compare with the dominant OS)

However many of the problems are due to the proprietary nature of codecs, flash etc. They cannot be installed by default with the ubuntu system. Flash (including youtube) often runs poorly, crashes when set to fullscreen etc.

There have always been a few outstanding bugs or annoyances that affected me in all the versions of ubuntu I have used - that has to be said.

The latest one: I would like to set my keyboard to Polish as default, while leaving the system language as English. The System->Preferences->Keyboard method fails -  the bug has been recognised and listed.

---

### Post by mlentink on 2008-08-26
> **xravexheavenx said:**
> 
Also, your box may be working harder because it is indeed running 2 operating systems instead of just one.  WinBlows annihilates system resources in most cases and there isn't much left for Ubunutu to use.  

> **vorgusa said:**
> Having to do with your other remarks, remember you were running two OS's at the same time and having any issues will just compound that.. 

I really think this is a misconception.
Wubi installs Ubuntu into a virtual partition, but it is not a virtual PC of any kind. So even if you have installed Ubuntu through Wubi, at boot time you choose either windows or Ubuntu. Either one runs, *but not both* at the same time.  
There may be a small performance penalty involved by using virtual partitions rather than real ones, but other than for large files or database intensive applications I tend to doubt you will ever really notice it.

---

### Post by halitech on 2008-08-26
> **biggiemokey said:**
> I used to have Ubuntu Hardy on my computer through Wubi, which claimed to have full Ubuntu functionality.  I ended up uninstalling it - despite the fact that it loaded up quicker and I really liked the functionality, it just didn't work...Certain things, like ActiveX controls, Java, Flash just wouldn't show, and there was a "play" icon in a gray circle.  Also, even though I was on a nice Dell XPS desktop (which desperately needs reformatting, but still) the fan would be louder than with Windows XP and the computer would heat up.

I haven't actually used WUBI to install but if you want something easier, try Unetbootin to do your install. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) it runs as a program in windows and lets you select various different distros. I've used it on my laptop and it worked great.

> So my question is, did I do something wrong by having a computer in bad shape run Wubi?  Or does Ubuntu always have little problems like that, such as servers being down when you're trying to download AVI codecs???  I really like the Open Source movement, and asked a few questions on here to try and figure out how to dual boot, but after my experience I'm not so sure.  Was it a fluke or is Ubuntu always like that?

only thing you should do before setting up a dualboot is run defrag a few times to make sure all the data is moved to the beginning of the drive. Far as the avi codecs, I've never had a problem getting anything to install so not sure what happened to you.

---

### Post by drubin on 2008-08-26
> **ugm6hr said:**
> 

As for the question...  Why should you use Ubuntu?

Only you can decide the answer to that.

The main reason why I switched over, was to try new things. (plus it is FREE), Reason i stayed was the community I find the support for Ubuntu and most other forums of linux is far higher.  They are a lot more friendly and willing to help new people out. Even for the simplest of things there is not of this RTFM... and such.

The reason for trying ubuntu would be  experience new things, is HIGHLY customizable(you can have cool themes colors you can change ANYTHING with some work.), and it is FREE(free as in rights, and cost).

What makes you use it every day is up to each person to decide for them selfs.  

I do hope you try the install (dual boot is always a great idea). Here are 2 links you can read to help you decide [Is ubuntu right for me]("http://ubuntuforums.org/showthread.php?t=63315") | [Which one to pick]("http://www.psychocats.net/ubuntu/whichbuntu")

---

### Post by steveneddy on 2008-08-26
> **Tux.Ice said:**
> if you dual boot , like i do youre experience will be much better.

+1

wubi is only for a trial.

Dual booting is what all the cool kids are doing. Go ahead, try it. You'll get hooked like the rest of us.

---

### Post by drubin on 2008-08-26
> **steveneddy said:**
> +1

wubi is only for a trial.

Dual booting is what all the cool kids are doing. Go ahead, try it. You'll get hooked like the rest of us.

That is how I started, Never needed to boot into windows again after I had fully set up ubuntu. Plus I can access all my files on my windows drive any way!!

---

### Post by liquidfunk on 2008-08-26
A think to remember is that Ubuntu isn't the only distribution of Linux.

 It took me a while to find the perfect distro for me. I stuck with Fedora 6 for a while. Then tried out Ubuntu and finally switched. 

 I'm sure I'll go back when Fedora 10 is out. I love the way it works, and how attractive the graphics are. 

 Your choice though, if your fans are a bit crazy on Ubuntu, try a distribution with a later Kernel that may have sorted it out. 

 For example, Ubuntu 8.04 uses the 2.6.24-19-generic kernel whereas the latest Fedora uses the 2.6.25 kernel. A lot of things get fixed between those versions. 

 So have a play with more than one if you have the time. Make sure you back your stuff up first.

 (As bad as this may sound, I tend to tell people not to try Ubuntu as their first Distro, purely because I don't want Linux to become Ubuntu).

---

### Post by t0p on 2008-08-26
Question: "Why should I use ubuntu?"

Answer: "Because you *want* to!"

If you don't want to use ubuntu, then don't.

But if you *do* want to use this wonderful OS, then do it.  *Use* it!  Cos it's a lot more fun than only using half of what your computer is capable of...

---

### Post by halitech on 2008-08-26
> **t0p said:**
> Question: "Why should I use ubuntu?"

Answer: "Because you *want* to!"

If you don't want to use ubuntu, then don't.

But if you *do* want to use this wonderful OS, then do it.  *Use* it!  Cos it's a lot more fun than only using half of what your computer is capable of...

+1

I think you just hit the nail on the head and summed it up 4 words :D

---

### Post by philinux on 2008-08-26
Quotes from the wubi site faq's


> What is the performance?

The performance is identical to a standard installation, except for hard-disk access which is slightly slower than an installation to a dedicated partition. If your hard disk is very fragmented the performance will degenerate.

Is this running Ubuntu within a virtual environment or something similar?

No. This is a real installation, the only difference is that Ubuntu is installed within a file as opposed to being installed within its own partition. Thus we spare you the trouble of creating a free partition for Ubuntu. And we spare you the trouble to have of having to burn a CD-Rom

---

### Post by Bliepo32 on 2008-08-26
Why should you use Ubuntu? Well, there are many reasons why you might want to use Ubuntu. Everyone has other reasons, but I will tell you about mine. My reason was mostly because I wanted to try it. I had of course heard of Linux, and was playing with the idea to install Linux for some time. When I heard of Ubuntu, I decided to give it a try.

So I installed it, booted and... got a blue screen. I was one of the people who had an ATI X[blablabla] videocard. I searched on the forums, and quickly found a guide which showed me how to fix it. After that, it worked fine.

After I got the screen working, I started to experiment with Ubuntu. I was completly unfamiliar with linux. First thing I noticed was that there was nothing like a C: drive. Then off course, there was the terminal. Off course, in all my time of working with Windows, I also worked with DOS. But I soon noticed that the terminal was far more powerful that DOS. Far more powerful.

Anyway, when I saw the terminal, I immediately wanted to know more about it. And when I installed the server version of Ubuntu, I more or less ended up being forced to use it. I googled around for BASH tutorials, and found them. They learned me about the way drives are mounted in Linux, why there wasn't a C: drive and much more (didn't get through the advanced part though). I must admit though, that I replaced the server version by the desktop version later on.

Now, I can work with Ubuntu quite well. Off course, there is still a lot to learn. But with all the expertise around here, and the great help, I am sure it will not be any problem at all.

---


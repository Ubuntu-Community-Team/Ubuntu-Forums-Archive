---
title: "I'm Not Trying To Learn Programming or Whatever!"
date: 2017-03-31
forum: Recurring Discussions
---

### Post by mobileberna on 2017-03-31
Let me start by saying, I LOVE THE XUBUNTU OS! The laptop i have is old and doesn't really support anything. I'll get staright to the point:
Why is installing stuff so difficult? Why do I have to open the "terminal" so much?! I don't want to learn "commands" or whatever! I just want to install stuff on my laptop! I don't know how to create specific packages or anything. As much as i love this OS, it frustrates me. I don't wan't to switch back to Windows, but I feel as if i may not have a choice seeing as installing software is a pain in the neck! Is there a way i can install anything without opening up the terminal and having to learn prompts? This OS is just time consuming for stuff that really shouldn't be that difficult. Here's an example: i have a notification telling me my background daemon is dead. Cool (whatever that is). I need to install something or whatever...I can't, I'm not computer literate enough to understand what the heck Xubuntu wants me to do; all i know is that it wants me to open the terminal and run some prompts. Due to the fact that i'm a moron, I have no idea what to do. I can figure some things out, but overall, I can't do anything without having to come to the forums for help and support. LIGHTBULB! Is there a terminal manual i can download and print or something? I'm not completely retarded, just ignorant to the Linux language. I think a lot of Windows users would switch to Xubuntu and greatly enjoy it, if it were more user friendly and retards like me could install things. Is there a flavor already in existence that doesn't require the "terminal" or something? Ok, im busted: I hate the "terminal". I want to be able to use my computer without having to actually talk directly to my computer...i want to be able to click "install" and be done...no terminal! Ok, maybe i'm being mentally lazy and simply don't want to learn how to tell my computer what to do, but...don't judge me! UGH! Fine! If there is a manual or something, i'll study it and learn this system...but if we can just do away with the terminal or something, that would make my life easier...#firstworldproblems tsktsktsk

---

### Post by wildmanne39 on 2017-03-31
*Thread moved to **Recurring Discussions**.*

Hello, people here would like to help you, if have a specific question that you need help with please ask it and being brief and to the point will help us to help you, one question per thread please.
Thanks

---

### Post by yetimon_64 on 2017-03-31
> **mobileberna said:**
> ... Why do I have to open the "terminal" so much?!... 
You really don't "need" to as such, most tasks nowadays can be via GUI tools. However as a helper here if I have a choice of posting a few easy to copy/paste commands to help with your problem as compared to having to draft a far more detailed step by step GUI guide that can get very long at times, well, the terminal commands will usually win out. 

You can help us to help you by simply copying/pasting commands; it is better for your own safety in the long run to learn in the process, as you will over time learn which commands are potentially damaging etc. 

One thing to remember is if a user here posts dangerous commands there are many eyes watching and someone will usually report such activity pretty swiftly resulting in such users being banned from the site or their posts can require moderation before further posting etc (i.m.o. this site is very well administered). 

> **mobileberna said:**
> ...LIGHTBULB! Is there a terminal manual i can download and print or something?...
This may help you a bit, if you are interested enough to wade through it (can be downloaded as a pdf file as well from the next link) ... [http://linuxcommand.org/index.php](http://linuxcommand.org/index.php)

> ...but if we can just do away with the terminal or something, that would make my life easier...And make my life as a helper here much much harder; a bit like removing the engine from your car then asking me to help push you along the road manually just because you didn't know how to fix the engine yourself. I'd prefer to tell you how to fix the engine rather than "busting a gut" pushing you along the road while you sit comfortably in the drivers seat (and THAT just isn't going to happen ;-)).

> ... if have a specific question that you need help with please ask it and being brief and to the point will help us to help you, one question per thread please. A big +1.

@ OP, I would also advise you to format you posts a bit more for ease of readability if you want to increase your chances of a response. Usually I avoid such "wall of text" type posts with only one or two tiny points in them that need addressing, as they can at times be very difficult to read/comprehend, sometimes to the point of being irritating (yours wasn't too bad though). 
Again this is an instance where you can help us in helping you, keeping in mind ALL helpers and staff here are volunteering their own time for your help needs.

Regards, yeti. (btw, this is also posted from an Xubuntu install ... its good alright :))

---

### Post by mörgæs on 2017-03-31
Think of it as learning to ride a bike. When you have learnt how to then you would not like to return to the pre-biking days. 

Try these tutorials and trust that it's worth the while. It's simple and easy and I mean simple and easy for everyone, not only experienced programmers. 

[http://ryanstutorials.net/linuxtutorial/navigation.php](http://ryanstutorials.net/linuxtutorial/navigation.php)
[http://ryanstutorials.net/linuxtutorial/aboutfiles.php](http://ryanstutorials.net/linuxtutorial/aboutfiles.php)
[http://ryanstutorials.net/linuxtutorial/filemanipulation.php](http://ryanstutorials.net/linuxtutorial/filemanipulation.php)

Post a thread in the appropriate forum if you have questions. The whole forum is ready to help you.

---

### Post by ajgreeny on 2017-03-31
It would help us a great deal if you also told us what all the "stuff" is that you can't install at the moment.
And the reason we often tell you to use a terminal command when giving answers in this forum is that if I use Xubuntu, which incidentally, I do, I can not give much useful advice on Ubuntu or Lubuntu or Kubuntu etc etc in GUI terms.  Most answers using terminal commands will transfer across the different DEs without a problem, so that is the answer we give.

If you are going on to the internet and downloading installers for applications that you currently use in Vista, **DON'T** do things that way.  Just about everything that most users need or want is available in the repositories of the OS and a lot of what you find on the net is going to be either useless, pointless, or very difficult to install compared with using the repositories.
Remember [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm")

I recommend you to start with three of simple commands, the first two in order to get up to date, and the third to install synaptic package manager as I know you have done in the past from a previous thread of yours, [https://ubuntuforums.org/showthread.php?t=2354961&p=13617264#post13617264](https://ubuntuforums.org/showthread.php?t=2354961&p=13617264#post13617264)
```
sudo apt update
sudp apt upgrade 
sudo apt install synaptic
```
After that use synaptic from the Xubuntu menu as your package manager.  It is incredibly flexible, and can be used from this point on to search for, install or remove applications (packages), and also to update your OS.

---

### Post by Bucky Ball on 2017-03-31
> **ajgreeny said:**
> 
```
sudo apt update
sudp apt upgrade 
sudo apt install synaptic
```
After that use synaptic from the Xubuntu menu as your package manager.  It is incredibly flexible, and can be used from this point on to search for, install or remove applications (packages), and also to update your OS.

+1.

@mobileberna: I hear what your saying, but once you have things the way you want them, you shouldn't need to use the terminal much at all. I've used Xubuntu, or something close to it, for years now and most the time I forget I'm using a computer, if that makes sense! I have everything set up with shortcut keys so rarely need to move my hands from the keyboard, the OS has been customised by me for the way I work so I can just go ahead and be productive (or doodle and dawdle around the internet :)).

Just to throw this in ... I use Xubuntu-core which gives you a very basic Xubuntu and not much else. I then install Synaptic, as suggested, and install what I need from there. No fluff or bloat, just the things I want/need. Makes life simple.

If I remember rightly, I didn't sit down in front of Windows or Mac OSx the first time and have any idea what I was doing. Frustration. Within a few years I was a Win 'power user'. Just takes time. You weren't born knowing Linux, but sounds like you are willing to learn and that is a good thing because you will need to go on a bit of a learning curve if you intend sticking with it. For me, and many others, well worth the effort. :)

Good luck. :)

---

### Post by pete5 on 2017-03-31
I am a fairly new Linux user. (Lubuntu is my distribution of choice.)

Coming from Windows I initially found the seemingly excessive use of the terminal and 'obscure' commands frustrating. However, the command line is very powerful and does not have the limitations of the graphical tools. This is why you find help forum answers tend to be of the 'run this command' variety.  

Even with Windows, when something doesn't work right there are times when going to the command line to diagnose and fix it is easier, if not required.

Installing programs using the System Tools - Software graphical tool is really pretty simple. So is installing updates using the Software Updater. This ought to be sufficient for routine tasks, but if you are trying to fix a problem, then command line tools may be better. 

The Linux command line is not as hard to learn as you may think. Once you start understanding the real Linux underneath the graphical user interface of your particular distribution you will be a lot more comfortable with the OS. Really it's not much different from Windows in that respect. I'm not defending Micro$oft's propensity to change things for no good reason, but people who only knew specific point and click operations in their particular version of Windows or in only a few programs they started by clicking an icon on the Desktop had trouble moving from 98 to XP to Vista to 7 to 10, while those who understood the concepts adapted to the changes pretty quickly.

 One thing that really helped me is to analyze the code given in posts about problems, by looking up commands on line to find out what they do.  

 In my case, I am trying to learn Linux 'programming' but even if you just want to be really comfortable with the OS you are using, it helps to understand something about how it is structured and how it works. 

There are many concepts that actually are not that different between Windows and Linux, but other things are a lot different. Command syntax is usually quite different, and also the Linux directory structure is very different. But in either OS, if you are limited to point and click in application programs and don't understand anything about directories, files, and so on, then you are at a disadvantage.

There are many free tutorials. A good free intro is available at [http://www.linuxquestions.org/.]("http://www.linuxquestions.org/")

I found this e-book to be easy to understand. It's worth $.99 and you don't need a Kindle, you can just read it on line.
[https://smile.amazon.com/Ubuntu-Beginners-Guide-Eighth-Updated-ebook/dp/B004Y1NMDI/ref=sr_1_fkmr0_1?s=digital-text&ie=UTF8&qid=1490975947&sr=1-1-fkmr0&keywords=ubuntu+beginners+guide+-+eighth+edition+update](https://smile.amazon.com/Ubuntu-Beginners-Guide-Eighth-Updated-ebook/dp/B004Y1NMDI/ref=sr_1_fkmr0_1?s=digital-text&ie=UTF8&qid=1490975947&sr=1-1-fkmr0&keywords=ubuntu+beginners+guide+-+eighth+edition+update)

What you find is that most of these guides do emphasize the command line. This is because different Linux distributions use different graphical user interfaces, but the underlying Linux is essentially the same. Xubuntu is going to look different than Ubuntu, etc. Also things change with each new release. .I like actual physical books, but  unlike Windows for which there is only one current version with millions of users and therefore potential customers,  It's not profitable to write and publish books or even e-books for each Linux distribution.

You might find this perspective interesting.  [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---


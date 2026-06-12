---
title: "Lubuntu slow loading browser, new pages, programs"
date: 2013-12-13
forum: New to Ubuntu
---

### Post by klblackw on 2013-12-13
My computer is a Dell 4300, Pentium 4 1.6 GB with 636 MB Ram and a SATA HD 160 GB. Lubuntu 13.1. Installation via iso disk.

The system is up and running fine.....except that it is terribly slow loading the browser or new pages. I use Chromium but Fire Fox is the same. In fact programs tend to be slow to load.

I used Task Manager to look at the CPU and RAM usage during the browser opening. Memory wasn't taxed, using less than half the 621 MB available. However, the CPU is maxed out at 100% during the loading.

I chose Lubuntu since it is the light version....vs regular Ubuntu. I also tried Puppy linux with the same result.

Help. Is this a hardware problem? or is there possibly some setting of Lubuntu that I have overlooked.

PS: I am a computer user-programmer since 1960 worked with every MS OS since DOS. But, I'm fairly new to Linux. Though, I've had Ubuntu on a computer for several years...just playing with it. Am trying to get more proficient.

Thanks,

Ken

---

### Post by DuckHook on 2013-12-13
Hi Ken and welcome to Lubuntu and the forums.

Thanks for posting with sufficient HW specs and important details to give us a good head start. What I'm wondering is: what do you mean by slow? Can you give us a rough estimate of how long it takes to load? Actually time it if you can. Also, how many tabs do you typically inherit from prior sessions and have to open during invocation? Last but not least, once you have either of the browsers running and it is well into its slow mode, please open a terminal and post output of```
cat /proc/sys/vm/swappiness
``````
free -m
``````
top -in3
```The last command puts *top* through three iterations and then exits. Hopefully, the last iteration will capture the CPU usage of your browser. You can leave *top* running all the time simply by running ```
top
```...in a terminal to see what processes are taking up your processor cycles at the current moment. <q> will quit *top*. As a rule, graphical tools like *Task Manager* are nowhere near as informative in Linux as command-line query tools (they're not informatve in Windows either, but that's another topic for another day). Please enclose output in [CODE] tags (the "#" button at the top of *Advanced Replies*) for better readability.

On the face of it, I would say that a Pentium 4 may be the issue, since it is a rather slow CPU by modern standards, but it all depends on ones definition of "slow", so we will await your response.

---

### Post by klblackw on 2013-12-14
Thanks....
It took about 15 seconds for Chrome to crank up to one tab "new tab page"
It took about 8 seconds to open "Intellicast" weather 

cat ......swappiness = 60

free -m
mem = 621 total, 533 used, 88 free, 0 shared, 45 buffers, 280 cached
+/- buffers = 207 used, 414 free
swap = 948 total, 0 used, 948 free

top -in3
PID 1607, USER ken, PR 20, NI 0, VIRT 230m, RES 52m, SHR 25m, S R, %CPU 37, %MEM 8.5, Time + 3:29.05 (first Chrome rept)
PID 1593, USER ken, PR 20, NI 0, VIRT 225m, RES 73m, SHR 27m, S R, %CPU 17.8, %MEM 11.8, Time+ 1:48.74 (2nd Chrome rept)

Once on a page it works fairly well...but there is a little sluggishness in scrolling at times.

Thanks,

Ken

---

### Post by mpxxuk on 2013-12-14
I find Firefox seems to work much better, although it does take a while to start.  Once it has started, though, it runs extremely fast on my Intel Atom 1gb ram netbook.

---

### Post by klblackw on 2013-12-14
On this computer, Firefox is no better....and I'm invested in Chrome elsewhere.

---

### Post by DuckHook on 2013-12-14
> **klblackw said:**
> It took about 15 seconds for Chrome to crank up to one tab "new tab page"
It took about 8 seconds to open "Intellicast" weatherThis is, indeed, very slow. The rest of your system looks fine, as you did mention. I was wondering about swap, but your system is not going to swap, so that isn't the reason.

Frankly, I'm stumped. If it was only the one browser, I would have suspected a corrupted cache, but it's too much of a coincidence for it to be both browsers, so I don't even suspect that anymore.

Is the rest of your system slow? What happens when you bring up, say, Lubuntu Software Center, or Sylpheed? Problem is that nothing else on a default Lubuntu install is as resource-heavy as your two browsers, so it's hard to compare them against anything of like weight. Did you install anything like GIMP or LibreOffice? If so, please let us know how slow they are. Did you have Windows loaded before Lubuntu? If so, which version and what was your speed experience? Comparing 12-year old XP to modern Linux is hardly fair, but may give some clues.

Hope other forum members have some ideas here. If all else fails, you may be better off with another distro outside of the 'buntu family. In your case, CrunchBang comes to mind. If you are okay with leaving the Debian tree altogether, then Chakra, Manjaro or ArchBang, as well as Mageia. Hurts my pride to send you to another distro though without making at least some further effort to chase down your issue here.

---

### Post by mörgæs on 2013-12-15
Hi, I assume that

> **klblackw said:**
> Pentium 4 1.6 GB

was a typo and your processor is 1.6 GHz, which indicates that you have one of the weakest Pentium 4's. I don't think there's much point in distrohopping, as Chromium will be just as heavy on another platform. 

You could try a lighter browser like xxxterm and/or add some more RAM. Else I think you just have to accept the speed as it is.

---

### Post by klblackw on 2013-12-16
Thanks....All.

DuckHook...This is a clean install...nothing else on the HD. I haven't installed anything but Chrome. Abiword takes about 6 sec. Other little utilities that came with Lubuntu load quickly < 1 sec. 

I tried Puppy it was also slow.....loaded into memory from a CD.

So....morgaes....I guess that you may be right about the 1.6 GHz Pentium 4. I'm terribly surprised...since it ran XP very nicely with IE of the time. I still wonder if there isn't something else..??? Back when it was running XP, I used it to run my CNC foam cutting program, etc. with no problems.

PS, I've been viewing YouTube videos....they load reasonably, and play just fine.

Again, Thanks to all.

Out Here........

---

### Post by mörgæs on 2013-12-16
XP might have felt faster because you had different software installed, for example a lighter (or obsolete) browser as opposed to the latest Chromium. As Duckhook mentioned modern browsers and their plugins are quite demanding.

Disabling plugins with Flashblock and the like will speed up the browsing.

Did you try xxxterm?

---

### Post by Lucasartsupporter on 2013-12-16
There is not that problem in my Pentium IV 2.4 GHz and 2 GB RAM computer.

I supose you already know it, but the system requirements of Lubuntu according to its website are:

> A Pentium II or Celeron system with 128 MB of RAM is probably a  bottom-line configuration that may yield slow yet usable system with a  reduced lubuntu desktop.
> 13.10 32 bit ISO require your CPU to have Physical Address Extensions,  or PAE. "PAE is provided by Intel Pentium Pro and above CPUs, including  all later Pentium-series processors (except most 400 MHz-bus versions of  the Pentium M).


Related to free memory in Lubutu 13.10, I have read it uses zRAM which avoid using a swap partition by crompressing their data and putting it in the 'free memory', so I think there is not as free RAM as task manager tells. Anyway, Lubuntu uses very few RAM memory in my computer and it is running the clamAV daemon which takes the majority of it.

I has not got any deep Linux knowledge, but you might try unsinstalling Chromium, since it has been left out of Lubuntu's LiveCDs, and installing Google Chrome, if you could not get a solution. Altough Google Chrome are in conection with Chromium and it is not free software, I think it is better than changing into another Linux distro. If it does not work, you would have only waste a while.

---

### Post by mörgæs on 2013-12-16
> **Lucasartsupporter said:**
> There is not that problem in my Pentium IV 2.4 GHz and 2 GB RAM computer.


Yes, a 50 % faster CPU and three times the memory makes a big difference. In addition to that, your CPU might even have more cache than the 1.6 GHz. 


> **Lucasartsupporter said:**
> 

I supose you already know it, but the system requirements of Lubuntu according to its website are:


The official Lubuntu requirements are not in connection with facts as seen in the real world. Yes, one might be able to install a minimal Lubuntu on that old iron, but it will not be able to serve any useful purpose.

---

### Post by DuckHook on 2013-12-16
You don't need AV in Linux. Especially on an older machine, running an AV daemon process is worse than pointless and wastes precious resources that ought to be preserved for apps that are actually useful. AV is a Windows problem. Let them deal with it.

Your Pentium IV 2.4 GHz has almost a whole 1 GHz, and more than 1 GB RAM head-start over OP's. It bears noting that the base system already consumes a lot of the processor cycles and memory on a modern OS. This is set overhead so it doesn't diminish proportionately when system specs do. The Lubuntu self promotion blurb is typical marketing over-promise. As one who tinkers with lots of old HW, I guarantee you that trying to run any 'buntu on a Pentium II with 128 MB RAM will have you either throwing the machine or yourself out the window.

@OP

As light as Lubuntu is, it cannot be compared to XP which is over 12-years old now, which, translated from IT years into human years, would make it roughly 120-years old in human terms. It was made for machines of yesteryear whereas any of the 'buntus are made for current HW (with older HW compatibility). At any rate, if Puppy was also slow—and it's one of the lightest distros going—then friend *mörgæs* is absolutely right and it makes no sense to go distro-hopping. Any performance increase will be marginal. It's your combination of HW with your choice of browser that is choking your load times.

Re: zram

This is compression technology and like all such technology, you can't get something for nothing. There has to be a trade-off. With zram, the trade-off is increased virtual memory space at cost of increased fragility, slower system due to more CPU load with compression/decompression on most memory hits, and increased complexity. Notwithstanding above, it is interesting technology without reports of many major drawbacks.

Re: Exchanging Chromium for Chrome

No harm trying, but since Chrome is just branded Chromium with, if anything, even more system demands from additional bells and whistles, I don't see how it could be an improvement.

Last note on security:

Although AV is worse than useless, other security measures are not adopted nearly well enough by new users. [Here]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") is a recent post where I summarize what should be done. If you ignore my exasperated ranting tone, you may find the info therein useful, including the further links to excellent security threads/sites.

---

### Post by klblackw on 2013-12-16
DuckHook,

I'm not running AV....I basically understand your thoughts about this.

I found some speed loading Chrome, by closing all the extensions that came with it.....from 16 sec to about 10 sec.

By the way Lubuntu boots fairly quickly.

Another slow thing. When I initially select my vast Bookmarks list...the list is slow to start...but the individual items come up quickly I am logged into Chrome so that I acquire my Bookmarks from my main computer.....that is keyed to the same email address.

When, I logged off the Chrome sign-in, it also loaded faster.....not having to sync the data from the cloud.

As I stated earlier, Chrome runs YouTube video's very well.

I appreciate your comments. But, as of right now, I'm going to consider the installation to be about as good as I can get it. and press on with other aspects.

Thanks,

---

### Post by DuckHook on 2013-12-16
> **klblackw said:**
> ...I'm not running AVSorry. Should have quoted to avoid confusion. The first part of post was actually a reply to Lucasartsupporter. The second part, after @OP was directed to you.> I found some speed loading Chrome, by closing all the extensions that came with it.....from 16 sec to about 10 sec...When, I logged off the Chrome sign-in, it also loaded faster...You may have found the various keys to your slow load times with very little help from us. :)> ...I'm going to consider the installation to be about as good as I can get it...Of course. Real life always trumps diversions such as my flights of fancy. Good luck and Happy Lubuntuing!

---

### Post by amjjawad on 2013-12-16
Hi,

From long experience with Lubuntu (former Team Leader) and Old Hardware, I'd highly recommend to stay away from Chromium/Chrome as much as possible.

Firefox is faster but on that machine, I don't think it can do much - two tabs and your machine will suffer.

Although zram-config is installed with Lubuntu 13.10 by default, it is the 'Kernel' that is not going to play/run nicely on 'old' hardware.

To compare, try Crunchbang (based on Debian) or maybe try [Bento]("http://linuxvillage.org/en/2013/11/bento-ubuntu-remix-rc/")

Use lightweight browser is a very good idea too!

You confirmed that the booting is quick and the system overall is quick, your problem within your browser as far as I can tell.

I have insatlled Xubuntu 12.04 on a machine with VIA C7 CPU with 512MB RAM so your machine should be better I guess. It worked nicely because the kernel is 3.2 series. With 13.10, it is Kernel 3.11 series and definitely, 3.11 is not like 3.2 :)

Hope that helps!

---

### Post by klblackw on 2013-12-16
Thanks,

amjjawad: On this machine, Firefox isn't faster. I do not like or trust Firefox. Chrome is my browser of choice for all my machines.....so I plan to stick with Chrome.

I have Chrome working fairly well now, after a few adjustments....mostly eliminating extensions. So, I consider this to be a closed problem.

Also, I will stick with Lubuntu.....for at least a while.

Cheers......

---

### Post by amjjawad on 2013-12-17
> **klblackw said:**
> Thanks,

amjjawad: On this machine, Firefox isn't faster. I do not like or trust Firefox. Chrome is my browser of choice for all my machines.....so I plan to stick with Chrome.

I have Chrome working fairly well now, after a few adjustments....mostly eliminating extensions. So, I consider this to be a closed problem.

Also, I will stick with Lubuntu.....for at least a while.

Cheers......

Hi,

Yes, I have read that but I am just sharing my long experience with old machines and Lubuntu with you :)

It seems you do like Chrome/Chromium but have you ever see this?
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1096603](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1096603)

This bug might be still alive!

I am not asking you to switch to other system but it is always good to try other systems to compare. SliTaz or AntiX will fly on that machine but again, just to compare :)

I am glad that your browser is better now :)

---

### Post by Lucasartsupporter on 2013-12-18
Hi.

I know I have not got enough computing knowlegde in order to write about this performance problem properly, but I cannot avoid thinking if Lubuntu runs quickly, if navigators run webapps smoothly (for instance javascrip Facebook app), which I do not know, and they spent less time on loading websites than opening a new blank tab, it could not be an ordinary available computational power problem as some of these actions are heavier than open a single blank tab (I think so).

It might be a configuration problem, a bug... I do not know it, what do you consider?



@DuckHook

I do not know if you are going to keep your advice on ClamAV when you know Wine is installed into the computer, which is necessary to run some Windows software like English learner's educational CD, for example. I do not like this, but I am not the only person who uses the computer. Might ClamAv and its daemon prevent any Windows malware problems? And I have heard ClamAV detect a few Linux viruses, is it right?

I am going to read your post about security at this weekend since I am going to have more free time to spend on checking its information.



@amjjawad

Lubuntu is a great OS, it is simple and extremely fast. It is a good and meaningful project, especially now because of the near end of Windows XP support. And I wonder if it might be a handy tool in Africa. It is well known that many old computers arrive African countries, in the end. I saw a documentry about this. The involved Companies say they are useful equipment in spite of the fact that most of them do not work. They go to dumps straight away where children take the precious metals in an unhealthy way and a few computers are repaired so as to be sold. It is a saddening matter.

 I consider I should tell you I have used Lubuntu in a few "Windows XP" computers and all of them worked faster than previously. I have read what you both have just written about Windows XP 'age', but I cannot avoid replying that there are loads of Windows XP upates from its beginning and my experience is not as you said. I should add that I am an encouraged Windows user who defragments and checks the hard disk, uses an antivirus, uses an standard user account instead of an 'root' account and this kind of things.   

Do you mind me asking if you are still involve in Lubuntu development? There is a thing I cannot manage to understand. Why do users have to write the root password to install updates when they look for them? I know one can add repositories and some of them might not be secure, but those repositories are installing updates without users' permission if they choose automatic updating as usual. I do not know the reason, but I consider being able to install updates from every user account is more user-friendly.

Another issue I cannot solve is creating menu directories. I have written some menu entries for programs, which is easy after reading LXDE tutorial for this matter. Another tutorial for menu directories/folders might help beginners.




I would not like to bother you, but I asked a question about installing Lubuntu in an USB pendrive some weeks ago which has not received any answers. Any comment will be welcome.
[http://ubuntuforums.org/showthread.php?t=2192507](http://ubuntuforums.org/showthread.php?t=2192507)

PS: My computer suffers a Grub problem. It is a over a minute's delay before starting to boot Lubuntu, there is not hard disk activity according to the hard drive led and the even more trustful sound of the computer. But I ought to investigate it before posting it.

---

### Post by amjjawad on 2013-12-19
> **Lucasartsupporter said:**
> Hi.

I know I have not got enough computing knowlegde in order to write about this performance problem properly, but I cannot avoid thinking if Lubuntu runs quickly, if navigators run webapps smoothly (for instance javascrip Facebook app), which I do not know, and they spent less time on loading websites than opening a new blank tab, it could not be an ordinary available computational power problem as some of these actions are heavier than open a single blank tab (I think so).

It might be a configuration problem, a bug... I do not know it, what do you consider?

We are back with this question to the start point. Kindly check the previous comments/posts that I have made :)
Many have old machines - [check this ]("http://phillw.net/hardware/BnA9pw11")- and run Lubuntu and as I said, I've been a super active contributor to Lubuntu for 2 years. I have installed Lubuntu on different machines from P2 with 64MB RAM and 4GB HDD to Core i5 second generation and 4GB RAM so please trust these comments are not from personal opinions but real life experience (2 years).
Your machine is 'not' powerful enough to be fast. Loading a page has nothing to do with opening new tab :) 

> @DuckHook

I do not know if you are going to keep your advice on ClamAV when you know Wine is installed into the computer, which is necessary to run some Windows software like English learner's educational CD, for example. I do not like this, but I am not the only person who uses the computer. Might ClamAv and its daemon prevent any Windows malware problems? And I have heard ClamAV detect a few Linux viruses, is it right?

I am going to read your post about security at this weekend since I am going to have more free time to spend on checking its information.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)


> @amjjawad

Lubuntu is a great OS, it is simple and extremely fast. It is a good and meaningful project, especially now because of the near end of Windows XP support. And I wonder if it might be a handy tool in Africa. It is well known that many old computers arrive African countries, in the end. I saw a documentry about this. The involved Companies say they are useful equipment in spite of the fact that most of them do not work. They go to dumps straight away where children take the precious metals in an unhealthy way and a few computers are repaired so as to be sold. It is a saddening matter.
Trust me, i know a lot about Lubuntu ;)
Thanks for sharing this, much appreciated and just for the record, [StartUbuntu]("https://wiki.ubuntu.com/StartUbuntu") Project wasn't named StartUbuntu at the beginning when I created it, it was called "[StartLubuntu]("https://lists.ubuntu.com/archives/lubuntu-users/2013-April/003988.html")" but then quickly, I changed the name so other flavours could jump in and help. Point is, we believed Lubuntu would play a major role to be the best candidate to replace Windows XP :)

 > I consider I should tell you I have used Lubuntu in a few "Windows XP" computers and all of them worked faster than previously. I have read what you both have just written about Windows XP 'age', but I cannot avoid replying that there are loads of Windows XP upates from its beginning and my experience is not as you said. I should add that I am an encouraged Windows user who defragments and checks the hard disk, uses an antivirus, uses an standard user account instead of an 'root' account and this kind of things.   
If you ask me, Windows XP is super amazing the moment you install it. Give it one week, most likely you will start the nightmare of keep it as fast as possible but it will never be as fast as the day it got installed and give it maybe one more week and you will re-format. I guess I have used XP for many years and I am so glad that I am all Linux now :D

>  Do you mind me asking if you are still involve in Lubuntu development? 
[I resigned]("https://wiki.ubuntu.com/amjjawad/Lubuntu-Team")!

> There is a thing I cannot manage to understand. Why do users have to write the root password to install updates when they look for them? I know one can add repositories and some of them might not be secure, but those repositories are installing updates without users' permission if they choose automatic updating as usual. I do not know the reason, but I consider being able to install updates from every user account is more user-friendly.

Will this answer some questions?
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I have been using nothing but Lubuntu for the last two years but I have migrated lately to Xubuntu. I have noticed then it is not asking for password when I update my Wifi settings from the network manager while Lubuntu does ask. I also noticed that I don't need to enter my password when the GUI Updater gives me the red notifications right next to the time applet which I hate to see (makes me feel like something is going to be broken :P) so I install the updates without any password. Before, I have never updated my system using the GUI. Always

```
sudo apt-get update
sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y
```

So, it is for the developer of Lubuntu to answer that question as why there is an extra step for Lubuntu while other flavours have no such step.


> Another issue I cannot solve is creating menu directories. I have written some menu entries for programs, which is easy after reading LXDE tutorial for this matter. Another tutorial for menu directories/folders might help beginners.

See[ this]("http://askubuntu.com/questions/196614/how-do-i-edit-the-menu-in-lubuntu")

Also [this]("http://zleap.net/lubuntu-menu-editing/")

I think you can find many links with "Lubuntu menu editor" on google search :)


>  I would not like to bother you, but I asked a question about installing Lubuntu in an USB pendrive some weeks ago which has not received any answers. 
You mean [this]("http://ubuntuforums.org/showthread.php?t=1872303")?

You are NOT bothering me at all. I have jumped in to help so don't worry ;)

> Any comment will be welcome.
[http://ubuntuforums.org/showthread.php?t=2192507](http://ubuntuforums.org/showthread.php?t=2192507)
Will have a look!

> PS: My computer suffers a Grub problem. It is a over a minute's delay before starting to boot Lubuntu, there is not hard disk activity according to the hard drive led and the even more trustful sound of the computer. But I ought to investigate it before posting it.

More about GRUB:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[GRUB Customizer]("http://ubuntuforums.org/showthread.php?t=1664134")

[Boot-Repair ]("https://help.ubuntu.com/community/Boot-Repair")

These links will be handy one day so make sure to bookmark these.

If you feel something is wrong with your GRUB, you need to start a new thread for this one. However, I find it normal. While Lubuntu is lighter than Ubuntu, it is not the lightest of all. There are many other systems which are lighter. 

Booting time depends on many factors and again, if you feel it is taking so long more than it should, start a new thread please and there are so many skilled people about GRUB can help.

Hope these answers help and feel free to ask anything!

---


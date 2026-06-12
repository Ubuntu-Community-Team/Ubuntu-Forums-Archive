---
title: "Switching to a Ubuntu variant"
date: 2012-02-26
forum: New to Ubuntu
---

### Post by jtsc on 2012-02-26
Hello, everyone!

I recently upgraded directly from L(ynx) to O(celot), trying N(arwhal) for a few days in between. This hasn't been a happy experience. The main problem is that Ubuntu is now very, very slow. (Although I'm glad to see that the network manager memory leak in N was removed from O, so thanks to the developers for that.) I also find it much less attractive, a lot of functions that I had come to rely on have been broken, and I apparently have even less ability than before to customize my options.

A friend who knows far more about Linux than I has told me that this is all part of the upgrade to Gnome 3, and that the best solution for now is to either install Gnome 2 on top of Gnome 3, or to switch to a non-Gnome distro.

With that in mind, I have two questions.

(1) If I switch to another flavor of Ubuntu (Lubuntu, Xubuntu, or Kubuntu), will installing it be like switching to a new release of Ubuntu (where, barring bad luck, everything in the home directory is the same after the upgrade), or will it be like installing a brand new OS?

(2) Is there anywhere where I can find a list of reasons *not* to switch to one of the variants? The description pages of Lubuntu, Xubuntu and Kubuntu are all very attractive, and it would be easier to choose which one to switch to if I knew their respective weaknesses.

Thanks for your help!

---

### Post by snowpine on 2012-02-26
If you tell us about your hardware specs, you might get a more targeted recommendation.

Lubuntu, Xubuntu, Kubuntu are just Ubuntu with different desktop environments or "skins." You can install any of them from the Software Center, and then they will be available as options from your login screen. You can choose between Gnome/Xfce/LXDE/KDE depending on your mood that day.. You do **not** need to reinstall; that would be a waste of your time. ;)

---

### Post by Lisiano on 2012-02-26
I'm guessing you have Ubuntu currently, your friend is partially right, there was a move away from Gnome2, but Ubuntu moved to Unity instead of Gnome3, I only saw a glimpse of Gnome3 on my cousins netbook and it did seem to have a bit more customization possible than in Unity. Either way, as snowpine said, you can just add any other Ubuntu flavour to your install, the main downside is that if there is a release upgrade (To Precise Pangolin 12.04) then you will have to upgrade both Ubuntu and whatever extra flavour you downloaded.
In terms of customizability, I'd say KDE or Kubuntu has more than any other flavour, in my humble opinion. Also KDE uses the most resources due to it being "Eye Candy".
Anyway, to add any flavour of Ubuntu, just press the you want [Kubuntu]("apt://kubuntu-desktop"), [Xubuntu]("apt://xubuntu-desktop"), [Lubuntu]("apt://lubuntu-desktop").
Or open a Terminal (Ctrl+Alt+T) and type in one of these 3 lines.
[Kubuntu]("apt://kubuntu-desktop")
```
sudo apt-get install kubuntu-desktop
```
[Xubuntu]("apt://xubuntu-desktop")
```
sudo apt-get install xubuntu-desktop
```
[Lubuntu]("apt://lubuntu-desktop")
```
sudo apt-get install lubuntu-desktop
```

Note: Everything will stay the same, including installed software.
If you wish to remove the other *buntus then you can follow the guide from Psychocat
[Pure Kubuntu]("http://psychocats.net/ubuntu/purekde")
[Pure Xubuntu]("http://psychocats.net/ubuntu/purexfce")
[Pure Lubuntu]("http://psychocats.net/ubuntu/purelxde")

---

### Post by cmcanulty on 2012-02-26
2 issues to be aware of 1)gnome classic is still available in 11.10 and to be in 12.04 also,which gives you 5 years.2)when I try xubuntu with ubuntu my panels are a weird mix of the 2 and don't work well at all on my laptop. On my desktop they coexist peacefully.
[http://www.webupd8.org/2011/12/guide-to-classic-gnome-session-in.html]("http://www.webupd8.org/2011/12/guide-to-classic-gnome-session-in.html")

---

### Post by Dreamer Fithp Apprentice on 2012-02-26
If you search the forum, or even just browse it a bit at random, you will find you are hardly unique in finding the new default UI in Oneiric Ocelot dismaying. In fact, a general search with a search service like Ixquick or the other ubiquitous g-word, with words like "oneiric ubuntu gnome" in the and field will pull up a ton of posts in countless blogs and tech help sites all over the internet. So you will find PLENTY of advice to choose from. I don't believe any software upgrade in IT history has ever caused so big an outpouring of dismay and suggestions for coping with it. There are two main choices within Ubuntu proper, without installing another distro altogether or reinstalling an older version. One is probably already installed. When you log in after logging out or rebooting there is a little icon that looks like a gear you can use to set your default environment. However you set it, it will remain that way until you change it again. "Gnome classic (no effects)" is somewhat like the UI that was the default standard through 10.10 Lucid Lynx. If you don't have too many scripts to adapt you can tweak it until it is a fair imitation of the Lucid UI.  See post # 8 in this thread
[http://ubuntuforums.org/showthread.php?p=11698572#post11698572](http://ubuntuforums.org/showthread.php?p=11698572#post11698572)
for a screenshot of what my desktop looked like with this option and some comments on the issue. At that point I was pretty optimistic about that approach, but the screenshot you see was about as far as I was able to go with it. Trying to recreate my scripts under Gnome  3 was a bloody nightmare. If you don't have any script based tweaks you are fond of, you might like it. But I'm far more satisfied with Mate. If you search the internet in general and this forum specifically you will find some laughably hysterical screeds about how horrible Mate is and how stupid we all must be to not like Obnoxious Ocelot. I suspect we have some offended gnome devs still smarting from Linus Torvald's pithy judgement of Gnome 3 who are pretending to be unbiased users. I can't see any other explanation of their passionate Mate-hate. Some people like to claim Mate is a one horse show, but peruse the mate forum and you will see that this is clearly not the case. For what it is worth, I've tried the new default UI, the gnome 3 based "gnome classic (no effects)", and Mate, all in the last couple of weeks. In the past I've used the KDE desktop (I forget what they call it) under Ubuntu,  Sabayon linux, MS DOS with and without 4DOS, most versions of MS Windows, with and without 4NT, DR-DOS, FreeDOS, real honest-to-god Unix (a loooong time ago), and have briefly tried a few other distros. So I do have some context and it is not as if I've only used one UI style. My prejudices, if you want to call them that, may not be the same as yours. I despise cutesy-poo stuff, windows that swirl down an invisible drain hole when you click them off, pointers that look they are on fire, websites done by ignoramuses that make you horizontal scroll to read them, microscopic fonts, pale yellow printing on white background, and in general, anything, IT or not, where the artisan was more concerned about impressing people with how cool and different and creative he is than he was about producing a useful product. I once saw a con man sell a brick-and-mortar retailer his services in producing a website. At that point, a lot of Joe Sixpacks hadn't ever seen a computer yet and the con showed this guy an animated gif of a waterfall (which I'm sure he just copied off some website) and told him it was the result of days of creative labor and it would impressively decorate the mark's website. After he left, I clued in the mark that he was being ripped off. He didn't appreciate it at all. All in all this con ripped the mark off for several thousand dollars before disappearing. I only said ITYS once. I guess that is off-topic, but I can't help remembering how IMPRESSED that guy was with an animated waterfall gif when I contemplate G3 and Unity. So now you know what mental space I'm coming from, so you can take it for what it is worth: I tried real hard to get along with Gnome 3, gnome classic (no effects) and spent several days tweaking it. It still smelled like that waterfall. I spent half a day with Mate and knew it was for me. Check out their site:
[http://mate-desktop.org](http://mate-desktop.org)
You can add their repository:
[http://packages.mate-desktop.org/repo/ubuntu](http://packages.mate-desktop.org/repo/ubuntu) oneiric main
and install it from synaptic. There are several threads discussing it here in these fora. 
Or if you just want to go to a new distro anyway, or feel more comfortable with using "official" repositorys, get Linux Mint which I've read, but haven't personally verified, has Mate in their own main repository. Mint is Ubuntu derived anyway I understand, so you should find it reasonalbly familiar. I plan to check it out myself soon.

---

### Post by jtsc on 2012-02-26
Thank you for your speedy replies. Good to know I won't have to install whichever I choose from scratch.

Here are my hardware specs:

memory... 993 MiB
processor... intel core duo cpu t2400 @ 1.83GHz x2
graphics... intel 945gm x86/mmx/sse2
hard drive... 75.7 GB

The computer is a Lenovo Thinkpad z61t, which I got at the end of 2007 (which I believe is when they retired that line), but the hard drive failed while it was still under warranty and was replaced with an reused one.

---

### Post by jtsc on 2012-02-26
Glad to know I'm not alone, Dreamer Fithp. I'll be sure to look at those options too.

---

### Post by snowpine on 2012-02-26
My (slightly educated) guess is that your integrated Intel 945gm graphics are struggling with the demands of the Unity desktop environment, and you would get a nice performance boost from using Xfce (xubuntu) or LXDE (lubuntu).

---

### Post by Lisiano on 2012-02-26
> **Dreamer Fithp Apprentice said:**
> I don't believe any software upgrade in IT history has ever caused so big an outpouring of dismay and suggestions for coping with it.
Really? What about Vista or as we russians like to call it, "Visla" (Play of words, means that it hangs and freezes a lot)

> **Dreamer Fithp Apprentice said:**
> If you search the internet in general and this forum specifically you will find some laughably hysterical screeds about how horrible Mate is and how stupid we all must be to not like Obnoxious Ocelot.
To everyone their own, personally I learned to live with Unity, as long as I have my terminal and Compiz, I'm happy.

> **Dreamer Fithp Apprentice said:**
> I suspect we have some offended gnome devs still smarting from Linus Torvald's pithy judgement of Gnome 3 who are pretending to be unbiased users. I can't see any other explanation of their passionate Mate-hate. I might've read it wrong but I think Linus wrote somewhere that he didn't like Gnome 3. Also, I didn't understand at first what you meant under Mate (Gnome 2 as Google helped me find out). 

Also please format your text a bit.


@jtsc You should be able to run any of the Ubuntu flavours as long as you don't use any 3D. So I'd recommend either LXDE or XFCE

---

### Post by wildmanne39 on 2012-02-26
Hi Dreamer Fithp Apprentice, if you used spacing and punctuation your posts would be a lot more readable.

Please remember this is a support forum, there are other forums for ranting about what you do or do not like about ubuntu.
Thanks

---

### Post by jtsc on 2012-02-28
Progress report: I've added Xubuntu and it's pretty snappy. (It's even snappier with respect to things that have nothing to do with graphics, like copying files onto an external drive.) I'm going to spend a few days getting used to the Xubuntu gui and seeing what options I have before deciding whether to stick with this or try something else.

The one fly in the ointment is that rebooting the computer still takes much more time than it used to. (Specifically, my laptop spends a lot of time on the "Booting from (0,0)" screen.) I'm not sure if this is a function of O across all *ubuntu, or a lingering effect of Ubuntu/Unity, or what.

Thanks again for all the help.

---

### Post by Lisiano on 2012-02-29
I'm not sure but I think it's because when you added xubuntu-desktop, a program that pre-loads files needed to boot your system (Forgot the name, I'll find it once I get home) is still pre-loading lightdm, unity and some other stuff, then latter the system needs to load the new files. I'll tell how to reset that program once I get home or get access to a Linux PC (on a tablet).

---

### Post by Lisiano on 2012-03-01
```
echo $BAD_FRENCH_WORD > /sys/devices/system/brain
```
Sorry for the wait. The software name is ureadahead
To reset it, type this in a terminal (Ctrl+Alt+T)
```
sudo rm -f /var/lib/ureadahead/*pack
sudo ureadahead --force-trace
```
Then on the next reboot, ureadahead will retrace the boot sequence. After your PC boots to X (A GUI/Login screen) it will wait around 30 seconds and stop, this is so that some files like icons and auto-start applications have a chance to get loaded while/before you type in your password and potentially reduce login time.
The boot after that will use the new trace and should reduce the boot time.

---

### Post by jtsc on 2012-03-12
Thank you so much for the tip, Lisiano! I'm going to try that later today.

So far Xubuntu has been a mixed experience. Xu is relatively snappy  immediately after I'm logged in (although not as snappy as Ubuntu under L, sadly), but it gets worse and worse over time. I'm going to play around a little with which programs I used to see if this is purely a function of time since last reboot, or whether it has something to do with how I'm using the memory.

---

### Post by kevdog on 2012-03-12
Sounds like you need a swap partition set up.  Do you have this?

---

### Post by s1wood on 2012-03-14
I've been reading this thread and have now tried out Kubuntu and Lubuntu desktops on my netbook. Is there any performance difference between installing Lubuntu on its own and running it as a desktop option with Ubuntu?

Susan

---

### Post by Lisiano on 2012-03-15
There shouldn't be any degrading performance, unlike Windows there is no need for reboots and your system should be the same after a year as it was when you booted it. So yes, how much RAM do you have and did you set up a Swap partition?


@s1wood There shouldn't be any difference if you install Lubuntu standalone or with any other Ubuntu flavour. If you mean which is the fastest, then in this order from slowest to fastest:
[LIST=1]
[*]Kubuntu
[*]Ubuntu
[*]Xubuntu
[*]Lubuntu
[/LIST]
The performance is traded for eye-candy mostly.

---

### Post by Peripheral Visionary on 2012-03-15
On my Xubu 12.04 (Beta, admittedly) my swap partition is 1 gb - twice my computer's 512 mb of RAM. But it still gets slower and slower over the course of a couple of hours. I've removed abuncha stuff I don't use, given Xubu twice the room it needs on the hard drive, and run
```
sudo apt-get clean
``` a few times. Before I run out and spend money for more RAM, is there anything else I should try before I try Lubuntu? I fear that Xubu has outrun my old Dell.

---

### Post by BertN45 on 2012-03-15
In do not know for 12.04, but I run Xubuntu 11.10 easily in a virtual machine of 256 MB. You are running a beta version. What you describe looks like a memory leak, A daemon, driver or programs that does not release all memory. Over time it will accumulate and then the system starts swapping programs/data to disk and gets slower and slower. The size of the SWAP partition will not solve it, swapping makes the system slow. Normally the problem should be solved in the next days or weeks.

With a machine of 512MB I would not install all flavors, you might get some functions started, you do not need for that desktop. Giving the fact that we are dealing with betas, you also might run in some additional issues by installing all the stuff. With your current memory size I would go for a clean install of Xubuntu. If you buy another 512Mb, I would go for Ubuntu itself that is somewhat more robust then the others. After booting Lubuntu will need around 90 MB, Xubuntu around 140 MB. Ubuntu and Kubuntu will be very very slow in 512MB.

Anyway save your data files and make a clean install to remove all left overs from the past (for example with or without pulseaudio), which just might have created your problem.

With your amount of memory use the 32 bit versions, the extra 10% in speed you will loose because it will need 50% or so more memory and swap more.

---

### Post by Peripheral Visionary on 2012-03-16
> **BertN45 said:**
> 
Anyway save your data files and make a clean install to remove all left overs from the past (for example with or without pulseaudio), which just might have created your problem.

Yup. _I think my efforts to preserve an existing /home partition caused the problem_. I have a fresh install of Xubu 12.04 and just gave it the whole drive. I think my problem is solved, but after a few hours of uptime I'll know. Thanks!

---

### Post by mraandtux on 2012-03-16
> **jtsc said:**
> I have two questions.

(1) If I switch to another flavor of Ubuntu (Lubuntu, Xubuntu, or Kubuntu), will installing it be like switching to a new release of Ubuntu (where, barring bad luck, everything in the home directory is the same after the upgrade), or will it be like installing a brand new OS?

(2) Is there anywhere where I can find a list of reasons *not* to switch to one of the variants? The description pages of Lubuntu, Xubuntu and Kubuntu are all very attractive, and it would be easier to choose which one to switch to if I knew their respective weaknesses.


1: You can install it like adding a software package or you can reinstall it like a clean system.
2: Always ask search engines for pros and cons of them.

---

### Post by jtsc on 2012-03-24
> **kevdog said:**
> Sounds like you need a swap partition set up.  Do you have this?

Yes, I believe so (at the very least, my usage of the swap partition is being tracked, so I assume it must be there!) At the time of this writing, I'm using 509 MiB out of 2.9 GiB. Also, 993 MiB of RAM.

My experience with earlier versions of Ubuntu was no performance degradation over time, but since the latest versions of Ubuntu I have needed to reboot every day. However, with some tweaks I'm finding that I can run Xubuntu for 6 days before it becomes measurably slower, which is sufficient for my purposes.

I'm not sure if I mentioned, but there was problem with overheating with the latest install of Ubuntu, and in Xubuntu this become a very serious and worrisome problem. I've looked at a lot of complicated solutions that allow you to take manual control of the machine fan, but the simplest solution I've found is to remove the battery from my laptop. The machine is still unusually hot, even when it's supposed to be hibernating, but taking out the battery has downgraded it from problem to annoyance.

I think I've gotten around the technical kinks of Xubuntu and I'm ready to invest time in customizing the settings to see if I can make it more usable.

---

### Post by jtsc on 2012-03-31
By now I've confirmed that there's some sort of minor memory leak or something with Xubuntu. This time I've had it up for 4 days and the system thinks that 300mb of memory are in use (although the processes running only account for 100mb) and 2.0 gb of the swap is in use (I don't know of any way to track what the swap is being used for). As a result things are noticeably slower. Haven't decided yet whether to keep playing around with Xubuntu, resign myself to rebooting every other day, or experiment outside the *ubuntu family.

---

### Post by snowpine on 2012-03-31
You may find this page useful to get an accurate handle on your RAM/swap usage: [http://linuxatemyram.com](http://linuxatemyram.com)

It is normal for RAM and swap to gradually increase over a period of days. Normally this type of caching actually makes your system *faster* but as you've noticed, there can be a delay, for example, when switching from an active application to an application that has been moved to swap.

Or there could be a memory leak as you suspect; I am not a Xubuntu user so I'll have to take your word for it. ;)

---

### Post by d4m1r on 2012-03-31
> **jtsc said:**
> Thank you for your speedy replies. Good to know I won't have to install whichever I choose from scratch.

Here are my hardware specs:

memory... 993 MiB
processor... intel core duo cpu t2400 @ 1.83GHz x2
graphics... intel 945gm x86/mmx/sse2
hard drive... 75.7 GB

The computer is a Lenovo Thinkpad z61t, which I got at the end of 2007 (which I believe is when they retired that line), but the hard drive failed while it was still under warranty and was replaced with an reused one.

No wonder the latest version of Ubuntu is running poorly on that machine...it is ANCIENT ](*,)

I would recommend to switching to classic mode or gnome2 as they are less resource intensive or maybe lookup a different distro that is minimalistic and will run better on your old PC. The best option would be to upgrade or get a new PC but that ain't cheap.

---


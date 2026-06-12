---
title: "Increasing page loading speed, RAM, memtest"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by AbleTassie on 2014-02-12
[SIZE=3]I have an older laptop TOSHIBA Satellite L25 S1216 circa early 2006 with 1.25 GB of RAM (DDR2). I would like to increase speed. One  of my goals is to increase the speed at which I can move to different  pages in a PDF document during an online WebEx document sharing  interview. It currently takes time (about 8 seconds) to "load" when I  move to a different page. This time can add up over the course of an  interview. **Even the rate at which typed characters appear on my screen is slow sometimes.**

[/SIZE][SIZE=3] A couple simple RAM tests seem to indicate RAM is working OK. But I have figured out how to get into the grub boot menu  and use memtest to test the RAM I presently have. There are two grub options:  (a) memtest 86+ and (b) memtest 86+, serial console 115200.[/SIZE][SIZE=3] I plan to run memtest86+ overnight.

**QUESTION#1:** Is there a significant difference between these two above options (a) and (b)?
[B]
QUESTION#2:[/B] I like Ubuntu 12.04 LTS very much, but it appears that a "lighter desktop version of Ubuntu" like Lxde (Lubuntu) or xfce (Kubuntu) might increase speed. [B]Is this correct?
[/B][/SIZE][SIZE=3][B]
QUESTION(S)#3:[/B][/SIZE][SIZE=3] I am thinking of moving up to 2GB of RAM by replacing the factory 0.25 GB (250MB) RAM chip with a 1GB RAM chip that matches (in terms of clock speed 667MHz) the 1GB I previously added (years ago) to the factory  0.25GB.** Would this likely help? **

The TOSHIBA specs for the laptop say that dual-channel support requires two memory modules of same capacity and clock speed. The capacities of the two current memory chips differ (1GB & 0.25GB) and I think the clock speeds may differ too (667MHz & I think the 0.25GB is 533MHz). [/SIZE][SIZE=3]**Perhaps I need to add two new memory chips that are the same? **But this would be more expensive.[/SIZE][SIZE=3] 

TOSHIBA currently recommends this chip for my PC:

[Kingston 1GB PC2-5300 667MHz DDR2 Notebook Memory Module]("http://www.toshiba.com/us/accessories/Memory/Computer/667MHz/KTT667D2/1G")

Thank you,

R.

[/SIZE]

---

### Post by oldrocker99 on 2014-02-12
You don't need to install another version; you can open Synaptic (assuming it's installed) and install LXDE or XCFE, both of which are a lot lighter-weight than Unity. Or you can open a terminal and:

sudo apt-get install lubuntu-desktop

or

sudo apt-get install xubuntu-desktop

Either one is easy to learn and use, and both are less resource-intensive than Unity.

Good luck and do post your results.

---

### Post by AbleTassie on 2014-02-12
[SIZE=3]OK, I am installing lubuntu right now. I noticed that new pdf pages load faster when less applications are open. Any answers to my other questions will be greatly appreciated.

R.
[/SIZE]

---

### Post by AbleTassie on 2014-02-12
> **oldrocker99 said:**
> You don't need to install another version; you can open Synaptic (assuming it's installed) and install LXDE or XCFE, both of which are a lot lighter-weight than Unity. Or you can open a terminal and:

sudo apt-get install lubuntu-desktop

or

sudo apt-get install xubuntu-desktop

Either one is easy to learn and use, and both are less resource-intensive than Unity.

Good luck and do post your results.

I put the command sudo apt-get install lubuntu-desktop into the terminal. But I'm not sure if the install of Lubuntu was complete, because the desktop screen looks the same as it does for Ubuntu 12.04 LTS. When I restart the computer, however, there is a Lubuntu logo. 

In the grub menu, there is an Ubuntu option, but not a Lubuntu option.  

QUESTION: How can I tell for sure if Lubuntu was successfully installed?

I can't say for sure that navigating around in a pdf document is quicker after my install (successful or unsuccessful) of Lubuntu.

Thanks,

R.

---

### Post by deadflowr on 2014-02-12
Lubuntu-desktop is just that, a desktop.
It doesn't install a new operating system.

To access, somewhere in the login screen
(I state this because I don't know if that changed for you or not)
You can switch desktops.

In the Ubuntu login screen, to change the desktop click on the button in the corner where you enter in your login name and password.
A selection should now appear with lubuntu as one of them. Select it and press enter then enter you login stuff(password) and try logging in.

Other login screens usually have a dropdown on a panel that you can use to switch the desktop.
Most will say something like "default"

I hope some of this makes sense.

---

### Post by AbleTassie on 2014-02-13
Thanks deadflowr, I used your comments to figure out how to get to the Lubuntu desktop. I think that pdf pages do load faster with Lubuntu. 

QUESTION: Does Xubuntu or another "flavor" of Ubuntu use even less resources than Lubuntu?

Any answers to my original questions on RAM memory will be greatly appreciated.

Looks like I'll run memtest 86+ tonight while sleeping, since I don't really know what memtest 86+ serial console is.

Thanks,

R.

---

### Post by Youri_van_Dijk on 2014-02-13
It's difficult to judge whether adding ram might help. Though I think your current setup might have some issues as Toshiba notices you need to have matching clock speeds and capacity and the 1 and original sized are very much different... Is the complete size of ram detected in Ubuntu? I'm not an expert and I think a lot of people here will find it difficult to indicate a clear yes/no answer. When using such an old machine it might be better to save the money and use it to invest in a more recent (second hand?) machine.

In terms of performance the only distro I know that could be lighter is Bohdi Linux. Kubuntu should be less applicable as it requires more resources. Lubuntu needs a minimum of 512 Mb ram while Bohdi requires only 128. I'm not sure wether you could just install that from the command line though. To noob for school :P

---

### Post by Youri_van_Dijk on 2014-02-13
Btw regarding xubuntu it seems it is a little heavier than lubuntu. Source: [http://mylinuxexplore.blogspot.nl/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html?m=1](http://mylinuxexplore.blogspot.nl/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html?m=1)

---

### Post by deadflowr on 2014-02-13
As far as going even further down the rabbit hole of desktops, you could run a plain window manager, which can bring down the resources even lower.
Something like awesome or fluxbox.
I don't know what Enlightenment is exactly, but it is wicked quick.

About your ram though,

1)more is always better.

2)your ram's speed will only run as fast as the lowest speed of the ram you have.
As you(I think) stated, you have 667mhz and 533mhz.
The machine would be running at the lower number(533mhz).

So in this respect, it is best to get matching ram.
That way you aren't just through away potentially helpful assets.

---

### Post by Bucky Ball on 2014-02-13
By installing *ubuntu-desktop anything there is a good chance you are making your machine more bloated as you are essentially installing Xubuntu into Ubuntu, both running on the Ubuntu kernel. Installing *ubuntu-desktop is the wrong advice for people wanting to try a DESKTOP ENVIRONMENT and I wish people would stop giving it. It can cause unexpected problems, duplication, redundancy and bloat. Install xfce4 or lxde ONLY. They are the desktop environments used by Xubuntu and Lubuntu respectively and they DON'T drag in all the default apps and dependencies, which is exactly what you do when you install *ubuntu-desktop. Your menus will show the Ubuntu default apps AND the Xubuntu/Lubuntu default apps, many of which do exactly the same thing but have different names.

For instance, if you had Lubuntu and Xubuntu-desktop installed with Ubuntu you would have Nautilus, Thunar and PCmanFM filemanagers. Three file managers ...

It can make a real mess and is not easy to get back from there. On a lower spec machine it can be a nightmare. Been there. ;)

* Rant off. Just to clarify, install xfce4 or lxde from the repos, log out, choose either from the 'Sessions' pop up menu, login.

---

### Post by Youri_van_Dijk on 2014-02-13
And for now... Perform a clean install of lubuntu or bohdi Linux :)

---

### Post by sudodus on 2014-02-13
> **Youri_van_Dijk said:**
> And for now... Perform a clean install of lubuntu or bohdi Linux :)

+1

But I would add ***Lubuntu 13.10***, because the Lubuntu specific program packages of all other versions have passed end of life (including Lubuntu 12.04).

---

### Post by sudodus on 2014-02-13
[SIZE=2]> **RMcGinnis said:**
> I have an older laptop TOSHIBA Satellite L25 S1216 circa early 2006 with 1.25 GB of RAM (DDR2). I would like to increase speed. One  of my goals is to increase the speed at which I can move to different  pages in a PDF document during an online WebEx document sharing  interview. It currently takes time (about 8 seconds) to "load" when I  move to a different page. This time can add up over the course of an  interview. **Even the rate at which typed characters appear on my screen is slow sometimes.**

 A couple simple RAM tests seem to indicate RAM is working OK. But I have figured out how to get into the grub boot menu  and use memtest to test the RAM I presently have. There are two grub options:  (a) memtest 86+ and (b) memtest 86+, serial console 115200. I plan to run memtest86+ overnight.

**QUESTION#1:** Is there a significant difference between these two above options (a) and (b)?
[/SIZE]
No
> 
[SIZE=2]**QUESTION#2:** I like Ubuntu 12.04 LTS very much, but it appears that a "lighter desktop version of Ubuntu" like Lxde (Lubuntu) or xfce (Kubuntu) might increase speed. [B]Is this correct?
[/B][/SIZE][SIZE=2]
Lubuntu with LXDE is ultra-light; ***[COLOR=#006400]Lubuntu 13.10 is an option for you[/COLOR]***
Xubuntu with XFCE is medium light; ***[COLOR=#006400]Xubuntu 12.04 LTS and Xubuntu 13.10 are options for you, particularly with 2 GB RAM[/COLOR]***
Kubuntu with KDE is nice-looking but heavy
Ubuntu with Unity [/SIZE][SIZE=2][SIZE=2]is nice-looking but heavy
[/SIZE][/SIZE]> [SIZE=2][B]
 QUESTION(S)#3:[/B] I am thinking of moving up to 2GB of RAM by replacing the factory 0.25 GB (250MB) RAM chip with a 1GB RAM chip that matches (in terms of clock speed 667MHz) the 1GB I previously added (years ago) to the factory  0.25GB.** Would this likely help? **
[/SIZE][SIZE=2][SIZE=2]
As stated above, 2x1GB (matching 667MHz) RAM will make it perform better
[/SIZE][/SIZE][SIZE=2]> The TOSHIBA specs for the laptop say that dual-channel support requires two memory modules of same capacity and clock speed. The capacities of the two current memory chips differ (1GB & 0.25GB) and I think the clock speeds may differ too (667MHz & I think the 0.25GB is 533MHz). **Perhaps I need to add two new memory chips that are the same? **But this would be more expensive. 

TOSHIBA currently recommends this chip for my PC:

[Kingston 1GB PC2-5300 667MHz DDR2 Notebook Memory Module]("http://www.toshiba.com/us/accessories/Memory/Computer/667MHz/KTT667D2/1G")

Thank you,
R.[/SIZE]

---

### Post by Flipyap on 2014-02-13
Removing the lesser RAM-chip might even increase speed as well. Non-matching chips are usually a bad idea.

---

### Post by Yellow Pasque on 2014-02-13
> **RMcGinnis said:**
>  I am thinking of moving up to 2GB of RAM by replacing the factory 0.25 GB (250MB) RAM chip with a 1GB RAM chip that matches (in terms of clock speed 667MHz) the 1GB I previously added (years ago) to the factory  0.25GB.Would this likely help?

Yes, especially if you're dealing with large PDF's. Moving from 533MHz single channel to 667MHz dual channel should speed up the CPU, but it should help the GPU even more, since integrated graphics tend to be more starved for memory bandwidth than modern CPU's (at least the GPU's without their own dedicated RAM).

$25 for a 1GB stick of name-brand DDR2-667 that's recommended by the laptop manufacturer is money well-spent, assuming you're not planning on junking the laptop in a couple months..

---

### Post by AbleTassie on 2014-02-13
> **Bucky Ball said:**
> 
It can make a real mess and is not easy to get back from there. On a lower spec machine it can be a nightmare. Been there. ;)

* Rant off. Just to clarify, install xfce4 or lxde from the repos, log out, choose either from the 'Sessions' pop up menu, login.

**PROGRESS REPORT:** I downloaded and burned an iso image CD of Lubuntu 13.10. I installed Lubuntu 13.10 on my PC and erased Ubuntu 12.04 LTS. 

Navigating around in a large pdf document is definitely faster in Lubuntu 13.10 than it is in Ubuntu 12.04 LTS. I ran Memtest 86+ last night while sleeping and there were no errrors. 

I'll probably try removing the 250MB of slower clock speed RAM tomorrow and see if that improves speed as well. Also there is a good chance I'll add 1GB to my RAM to bring it up to 2GB total. People seem to agree that 2 RAM 1GB chips that are identical is the most optimal selection of RAM chips. BUT, they say that just getting another 1GB RAM chip of the same clock speed (667MHz) as my current 1GB chip MIGHT be good enough. The Kingston chip recommended by TOSHIBA ([SIZE=2][Kingston 1GB PC2-5300 667MHz DDR2 Notebook Memory Module]("http://www.toshiba.com/us/accessories/Memory/Computer/667MHz/KTT667D2/1G")[/SIZE]) appears to be optimal. But others, such as Crucial ([http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=F04AD583A5CA7304](http://www.crucial.com/store/mpartspecs.aspx?mtbpoid=F04AD583A5CA7304)) may be as good. 

Some Windows users think that if I could monitor "page file" usage, I could determine the degree to which more RAM would increase speed. 

QUESTION: Is there any way to monitor page loading in Lubuntu? 

Any other comments from anybody will be welcomed.

Thanks,

R.

---

### Post by Bucky Ball on 2014-02-13
If Lubuntu has a system monitor you could look in there. You can also open a terminal and type in 'top'. At the top of that screen you will see details of CPU and RAM and how much they are being used. 

Just put in another 1gb of RAM. That will do fine. If you can afford more, go for it! It will speed things up. /swap file should be 2Gb or thereabouts. If you intend to hibernate then it should be the same size as the amount of RAM you have installed.

---

### Post by sudodus on 2014-02-14
Lubuntu has a system monitor, but I prefer ***htop*** for such purposes. Page loading in Windows corresponds to swapping in linux (the entry 'Swp' at the top of the htop screen). You should also watch the RAM usage (the entry 'Mem' at the top of the htop screen).

```
sudo apt-get install htop
```

---

### Post by AbleTassie on 2014-02-14
> **sudodus said:**
> Lubuntu has a system monitor, but I prefer ***htop*** for such purposes. Page loading in Windows corresponds to swapping in linux (the entry 'Swp' at the top of the htop screen). You should also watch the RAM usage (the entry 'Mem' at the top of the htop screen).

```
sudo apt-get install htop
```

Thank you Sudodus. I am not sure how to interpret htop.  The horizontal bar graph shows CPU runs about 2%, but when I navigate in the pdf, CPU spikes up to about 100% and the horizontal bar graph for CPU fills up with green vertical lines . The horizontal bar graph for Mem is full of green bue and red vertical lines and the numbers 219/1127MB at the far right, and does not seem to change much. Swp does not seem to change, one vertical red line at the far left and the numbers 0/1712MB at the far right. 

Here is copy from top (suggested by Buckyball), so it looks like a lot of memory is being used: 

top - 00:24:12 up  3:29,  2 users,  load average: 0.01, 0.09, 0.12
Tasks: 115 total,   1 running, 114 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.7 us,  0.3 sy,  0.0 ni, 98.3 id,  0.7 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   1154776 total,  1045184 used,   109592 free,    52600 buffers
KiB Swap:  1753956 total,      184 used,  1753772 free,   765700 cached



Thanks,

R.

---

### Post by sudodus on 2014-02-14
RAM usage (memory) is displayed in different ways in [FONT=courier new]**top**[/FONT] and [FONT=courier new]**htop**[/FONT]. You see both ways in [FONT=courier new]**free**[/FONT] or [FONT=courier new]**free -m**[/FONT]. Htop indicates that you have enough memory, 219/1127MB is used when you read the pdf file.  CPU spikes up to about 100%, so I think that in this case the CPU is the bottleneck. That will *not* be cured by more RAM.

It would probably be a similar situation when you play video unless you have an advanced video chip/card and a proprietary driver, that can use the GPU to do some of the decoding (that would otherwise [over]load the CPU).

---

### Post by Yellow Pasque on 2014-02-14
> **RMcGinnis said:**
> so it looks like a lot of memory is being used.

It looks that way, but it's not. [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Yellow Pasque on 2014-02-14
> **sudodus said:**
> CPU spikes up to about 100%, so I think that in this case the CPU is the bottleneck. That will *not* be cured by more RAM.

Correct, but it may be aided by faster RAM, especially if moving from single to dual channel configuration. The Xpress200 (690G) GPU is pretty pokey, so extra memory bandwidth may allow it to give greater 2D acceleration and take more load off the CPU.

---

### Post by AbleTassie on 2014-02-14
Sudodus and Juan,

Thanks. Looks like the CPU is the bottleneck. How can I help the CPU out? 

Looks like I can try removing (as Juan suggested) the slower 533MHz 250MB RAM chip (and leaving the 667MHz 1GB RAM chip in place) to see if this helps out the CPU. Maybe that will help. Not sure about upgrading to higher amount of RAM (i.e. 2 matched 667 MHz 1GB chips) as Juan seems to suggest. Not sure if this will help the CPU out or not. Maybe if removing the 250MB chip helps, this might suggest that adding 2 matched 1MB RAM chips might help, even if it is mainly the CPU that is overtaxed. What do you think? 

I have figured out how to take screenshots of htop, and thought I'd post  some screnshots. But unfortunately the screenshot utility Kazam makes  the CPU usage about 100% on a continual basis. So I was looking at the  HELP screen in htop. I see no way to freeze the htop screen, open kazam  and then take a screenshot. For those who are interested in htop, here is a link to the creator's htop page [http://hisham.hm/htop/index.php?page=main](http://hisham.hm/htop/index.php?page=main)

As I said before, a clean Lubuntu install definitely seems to speed up navigating (loading pages) in the pdf file for WebEx desktop sharing. According to htop, JAVA during a WebEx session takes up a lot of CPU% when it is on.

Thanks so much for your help,

R.

---

### Post by AbleTassie on 2014-02-14
> **Temüjin said:**
> Correct, but it may be aided by faster RAM, especially if moving from single to dual channel configuration. The Xpress200 (690G) GPU is pretty pokey, so extra memory bandwidth may allow it to give greater 2D acceleration and take more load off the CPU.

Juan, Sudodus, or others,

I know it looks like the main problem is with the CPU. 

QUESTIONS: But is there any way to measure a parameter (using perhaps a utility like htop) that would predict if removing the slower 250MB 533MHz RAM chip (and leaving the faster 1GB 677MHz in place) will increase speed & performance? 

Is there any way to measure a parameter that would predict if using 2 matched 1GB 667 MHz RAM chip will increase speed/performance? 

Thanks

R.

---

### Post by Bucky Ball on 2014-02-15
I think you are starting to chase shadows. The more RAM you have in the machine the faster it will go, period. Chucking two matched sticks in will increase the performance to such a small degree you may not notice. The CPU is only going to go as fast as it is designed to go, period. Chucking 200Gb of RAM in is not going to change that. The processing bottleneck will remain.

---

### Post by AbleTassie on 2014-02-15
> **Bucky Ball said:**
> I think you are starting to chase shadows. The more RAM you have in the machine the faster it will go, period. Chucking two matched sticks in will increase the performance to such a small degree you may not notice. The CPU is only going to go as fast as it is designed to go, period. Chucking 200Gb of RAM in is not going to change that. The processing bottleneck will remain.

Thanks Bucky Ball, I appreciate your input,

If it were you, would you spend $40-$50 for two new RAM chips and give it a try to see if it helps speed? Or would you save the $40-$50 and eventually put the money toward a new computer?

The present page loading speed for a pdf test document seems OK, maybe it will be significantly slower for a larger pdf document for a WebEx desktop sharing interview -- I can test with a larger pdf doc. Aside from pdf documents & WebEx desktop sharing, the computer locks up fairly often too (no response to mouse pointer, cursor or keyboard, etc), requiring a reboot by turning off the power. And I am thinking that this locking up could be because the CPU becomes overloaded.  I wonder if more RAM would help this locking up problem.

Thanks,

R.

---

### Post by deadflowr on 2014-02-15
> If it were you, would you spend $40-$50 for two new RAM chips and give  it a try to see if it helps speed? Or would you save the $40-$50 and  eventually put the money toward a new computer?

Not addressed to me, but my take would be to save up and buy a newer machine.
I would also, in the mean time, look over machines and figure out the one which would give me the best out of the box experience
for the price I could afford.
Don't just buy something because you can afford it. That sometimes leads to finding out it has weaker than expected bits and pieces you'll have to fix up.

---

### Post by sudodus on 2014-02-15
> **deadflowr said:**
> Not addressed to me, but my take would be to save up and buy a newer machine.
I would also, in the mean time, look over machines and figure out the one which would give me the best out of the box experience
for the price I could afford.
Don't just buy something because you can afford it. That sometimes leads to finding out it has weaker than expected bits and pieces you'll have to fix up.

+1

---

### Post by AbleTassie on 2014-02-17
[SIZE=3]As most of your guys suggest doing, I am inclined to forget spending money on more RAM. The argument that increasing RAM will not increase speed seems compelling. I've atached an htop screenshot (with Kazam running) that shows 100% CPU usage, but less than 100% RAM usage. Such 100% CPU usage happens frequently, even when Kazam is not running.

THEORY: I am not a computer scientist, but I was thinking that if you think of the CPU as a shovel (with maximum capacity in terms of operations per second) that has to move a series of piles of bits (or bytes) that are sent to it, then how fast the CPU can move these series of piles of bytes MAY also depend on how quickly the piles of bytes are sent to it. That is, it MAY also depend on RAM speed to some extent as Juan Valdez argues.

TEST OF THEORY: One way to test this theory may be to test speed (of navigation in a pdf document) with different combinations of the RAM chips I already have: 1) only 250MB (0.25GB) of 533MHz RAM alone, (2) 1GB of 677 Mhz RAM alone and (3) my present combination or both 250MB (533MHz) and 1GB (677MHz).

If anybody is interested, I can post the results of this test if I perform it.

Any more comments anybody has will be welcomed. I think, however, we are getting towards the end of this thread and a solution.  

Thanks again to everybody for their responses.

R.

[/SIZE]:KS

---

### Post by sudodus on 2014-02-17
> **RMcGinnis said:**
> [SIZE=3]
If anybody is interested, I can post the results of this test if I perform it.
[/SIZE]

Yes please :-P

---

### Post by AbleTassie on 2014-02-18
> **sudodus said:**
> Yes please :-P

Thanks for your interest Sudodus. I will attempt to run the test and post results. This may take some time due to the press of every day concerns, and I am also awaiting the arrival of a new hard drive -- my current drive has 20 bad sectors. I think this bad drive is probably the reason I have not been able to use Windows XP for the past three years. So in the end this turned out to be a good thing -- I discovered Linux. 

I may never use Windows XP again, although I'll probably figure out how to dual boot Windows XP and Ubuntu, just so I can tell others it is possible to dual boot the two. I think more people will have an interest in Linux as time goes on. But out of a need for "security" they may want to dual boot Linux and Windows. I have been telling others I know about Linux, specifically about Ubuntu.

I think a few people are interested and will give it a try. Many people though, as you know, just take what comes without exploring too much. But thankfully that does not appear to be the case for the Ubuntu community.[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

QUESTION: By the way, do you (or others) think that the load my CPU is working under could explain the computer "locking up" or crashing as it sometimes does?


Thanks again,

R.[IMG]http://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

### Post by sudodus on 2014-02-18
When the CPU is running at 100% it means that it is the bottleneck, and things are slower than they 'should'. For example, if you play a video clip and the CPU is at 100%, it will be lagging, skipping frames or performing badly in some other way, depending on how the video player is set to manage the situation.

So yes, it might be the reason. But a failing disk can also be the reason. If there are some 'half-bad' sectors, that need re-reading, it makes things slow.

---

### Post by Bucky Ball on 2014-02-18
Just a note and off-topic. XP will no longer be supported as of April (I think, could be July). After that it will be a security nightmare I'd think so if you're intending to go online with XP anytime after that it would not be a great idea. Maybe you've inadvertently become a Ubuntu-er by default, unless you are going to upgrade to Win7/8 in future. ;)

---

### Post by AbleTassie on 2014-02-25
[SIZE=3]Thanks Bucky Ball and Sudodus,

I installed my new hard drive, but I have not yet had the time to do my experiment with speed and the different combinations of RAM chips I already have. But I will post the results if/when I do the experiment.

Regarding the danger of many viruses when WIndows XP no longer being supported after April, some people who like MS Windows say that this is: 
[/SIZE][SIZE=3]"Most likely just [FUD]("http://en.wikipedia.org/wiki/Fear,_uncertainty_and_doubt"). We are still running Windows 2000 (and even Windows NT 4.0) here with no difficulty." And they cite the freeware at these two links:   [Microsoft antimalware support for Windows XP]("http://blogs.technet.com/b/mmpc/archive/2014/01/15/microsoft-antimalware-support-for-windows-xp.aspx")   [Best Five Freeware Replacements for Microsoft Security Essentials on Windows XP]("http://news.softpedia.com/news/Best-Five-Freeware-Replacements-for-Microsoft-Security-Essentials-on-Windows-XP-416445.shtml")

I think they may be overly optimistic in terms of of the hazards with WIndows XP for the average person though. I think I'll stick with Ubuntu when I interact with the internet. Regarding upgrading to Windows 7/8, my computer is not supported for Windows 7/8, so It would likely take me a very long time to get drivers, etc. SO this is not practical for my computer. Even if I get a newer machine, I like Ubuntu and will probably not go back to WIndows in any form, at least not very much.

Thanks again,

R.[/SIZE]

---

### Post by sudodus on 2014-02-26
You are welcome,

Good luck, and come back with questions whenever you need help :-)

---

### Post by Bucky Ball on 2014-02-26
> **sudodus said:**
> You are welcome,

Good luck, and come back with questions whenever you need help :-)

+1. I'm with sudodus. No comment. The info you provide is from Win users who had no idea about security flaws with Win in the first instance. No point pouring water into a leaky bucket ...

Even though the thread is 'solved', in depth discussion about the security of XP when it is no longer supported is off-topic. I suggest starting a new thread in ***Other OS Chat*** regarding this. One would imagine a feisty and robust discussion might ensue.

---

### Post by AbleTassie on 2014-02-27
Thanks Bucky Ball and Sudodus, When I get some time I  may start a new thread about the security of Windows XP in the Other OS  Chat forum. I am sure I'd get an earful.

R.

---


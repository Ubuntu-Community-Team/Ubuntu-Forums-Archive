---
title: "Arch Linux"
date: 2009-09-26
forum: Recurring Discussions
---

### Post by Dobbie03 on 2009-09-26
I don't know I am so tempted to try this out but if I mess it up I can' be bothered setting up my computer again with Kubuntu.

Seriously, I have a average knowledge of Linux am I jumping into something way over my head installing Arch??

---

### Post by -grubby on 2009-09-26
Read the Arch [Beginner's Guide](http://wiki.archlinux.org/index.php/Beginners_Guide). If it scares you, you may want to take a step back and evaluate your choice to use Arch.

---

### Post by Skripka on 2009-09-26
> **-grubby said:**
> Read the Arch [Beginner's Guide](http://wiki.archlinux.org/index.php/Beginners_Guide). If it scares you, you may want to take a step back and evaluate your choice to use Arch.

OP: Most of all the 55 pages or so of Beginner's Guide is explaining what and why you are doing.  It ain't as scary as it reads, but you need to be comfy with your Terminal.

---

### Post by clonne4crw on 2009-09-26
It depends on how comfortable you are working in a command-line only enviroment. If you're not, then stick to the more use-friendly distros.

---

### Post by overdrank on 2009-09-26
Create a separate partition, or you use a spare system so your production machine is safe. :)

---

### Post by Dobbie03 on 2009-09-26
> **overdrank said:**
> Create a separate partition, or you a spare system so your production machine is safe. :)

I have to talk my wife into letting me take over her machine for that :)

---

### Post by lovinglinux on 2009-09-26
> **MattDobson said:**
> I have to talk my wife into letting me take over her machine for that :)

Use Virtualbox for learning.

---

### Post by CJ Master on 2009-09-26
> **lovinglinux said:**
> Use Virtualbox for learning.

+1. Use virtualbox the first time to get comfy.

---

### Post by nmaster on 2009-09-26
you could use partimage to keep an image of your current setup. [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

i think virtualbox sounds like a better idea tho.  much easier.

---

### Post by Skripka on 2009-09-26
> **lovinglinux said:**
> Use Virtualbox for learning.

Last I heard Arch didn't VM well.

---

### Post by ninjapirate89 on 2009-09-26
What an odd coincidence. I just got finished installing Arch in vbox. Took a while but I finally got a basic GNOME desktop up and running. Biggest accomplishment of the week for me. :D

---

### Post by tjwoosta on 2009-09-26
> Last I heard Arch didn't VM well. 

Arch is notorious for having issues in a VM, but I have never personally had problems. I always use Virtualbox to test distros and have never had any major issue with any of them.

---

### Post by ninjapirate89 on 2009-09-26
I didn't have any problems that were related to vbox. I only had problems related to not knowing what I was doing. :P

---

### Post by Vert on 2009-09-26
I installed Arch on my laptop last weekend. It took me an hour to get to a fully working KDE4 Desktop with Nvidia Graphics and NetworkManager running my NICs. If you read the beginner's guide AND the guide to installing Arch (if you've never used a text installer or simply don't feel comfortable with it). Remember it's best to install Arch next to another computer that has Internet connection so you can read and install/configure at the same time. After you do it once or twice, you'll be amazed at how fast you can get a fully customized Desktop. Also, I used Ext4 for my root partition. The text installer will give a warning about this, but it booted for me just fine (and haven't had problems to date). Have fun and it's a great learning experience!

---

### Post by tjwoosta on 2009-09-26
If you dont have two computers you can just switch virtual consoles (alt-f1 through alt-f6 are all seperate vc's) and use links to search the web. Its only a simple text based web browser but it gets the job done.

---

### Post by gn2 on 2009-09-27
> **MattDobson said:**
> I have a average knowledge of Linux am I jumping into something way over my head installing Arch??

No, it's really quite simple if you follow the idiot's guide.

---

### Post by hessiess on 2009-09-27
Just try it out, the hardest part is the instalation, after that it just looks after itself, just run `sudo pacman -Syu' occationally.

---

### Post by LookTJ on 2009-09-27
> **-grubby said:**
> Read the Arch [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide"). If it scares you, you may want to take a step back and evaluate your choice to use Arch.
I would recommend this as well.
> **lovinglinux said:**
> Use Virtualbox for learning.

> **Skripka said:**
> Last I heard Arch didn't VM well.
Last time I tried Arch in a VM, it didn't play friends with me.

---

### Post by SuperSonic4 on 2009-09-27
KDEmod is also pretty good and easy to add if you want KDE with arch - their website has instructions for it (and also instructions for getting a chakra live cd, albeit one in alpha). Check out the blue link in my sig if you're interested :]


Once installed it's simple enough to maintain. Just keep an eye out on the arch homepage for any problems upstream, especially when updating core components like the kernel

---

### Post by wojox on 2009-09-27
Chakra takes 99% of the fun out of installing Arch.

---

### Post by SuperSonic4 on 2009-09-27
> **wojox said:**
> Chakra takes 99% of the fun out of installing Arch.

I agree completely, I'm just letting the OP know that the option exists.

to the OP: I'd recommend installing arch then adding KDE/KDEmod if applicable, you will get a more tailored install

---

### Post by ddrichardson on 2009-09-27
The only thing I don't like about Arch is the attitude to bug reports, which if you supply a patch with usually get denied on the grounds that you should put it in the AUR. I understand the Arch Way but sometimes I question this.

As someone who has written Ubuntu documentation, I think Arch's wiki is better.

Switching from Ubuntu, I'd advise users to get into the habit of reading before saying yes - AUR packages could be anything.

---

### Post by Skripka on 2009-09-27
> **SuperSonic4 said:**
> I agree completely, I'm just letting the OP know that the option exists.

to the OP: I'd recommend installing arch then adding KDE/KDEmod if applicable, you will get a more tailored install

Yep, I'd add that you'll also learn everything you're supposed to from the Arch install.  Throwing a Chakra disk in your CD drive is a sure-fire way of finding yourself in over your head, and fast.

---

### Post by Skripka on 2009-09-27
> **SuperSonic4 said:**
> 
Once installed it's simple enough to maintain. Just keep an eye out on the arch homepage for any problems upstream, especially when updating core components like the kernel

ALWAYS check the Arch homepage for update news, and the Packages/upgrades forum for issues regarding updates.  You never know when something major/minor might get broken by an update.  It very seldom happens, but it can and does every now and then.

i.e. Amarok2 from Extra got broken due to a depend problem a few days ago-and required reverting to the last version of libtag-extras to even run.  Which fortunately got fixed this morning.

---

### Post by hessiess on 2009-09-27
> **Skripka said:**
> ALWAYS check the Arch homepage for update news, and the Packages/upgrades forum for issues regarding updates.  You never know when something major/minor might get broken by an update.  It very seldom happens, but it can and does every now and then.

i.e. Amarok2 from Extra got broken due to a depend problem a few days ago-and required reverting to the last version of libtag-extras to even run.  Which fortunately got fixed this morning.

And theare were some update problems with Vim recently too.

---

### Post by hoppipolla on 2009-09-27
I did a similar jump a little while back (Suse to Slack) and I was ok! Then again, I guess Slack does have quite a few UI tools, I don't know what Arch is like in this respect O.O

---

### Post by Skripka on 2009-09-27
> **hessiess said:**
> And theare were some update problems with Vim recently too.

Don't use Vim, so I missed those...tho' read about it on the Arch front page before -Syu, and followed the instructions.

---

### Post by hessiess on 2009-09-27
> **Skripka said:**
> Don't use Vim, so I missed those...tho' read about it on the Arch front page before -Syu, and followed the instructions.

I didn't notice the message on the home page and upgraded it, which caused a tun of error messages to be displayed when vim was started. Running the command on the Arch home page and re-installing vim fixed it.

---

### Post by Dobbie03 on 2009-09-27
Thanks everyone for your help.  I was considering installing Arch with the KDEmod.  I will ponder and come back to you guys with results. :)

Cheers.

---

### Post by kk0sse54 on 2009-09-27
> **MattDobson said:**
> Thanks everyone for your help.  I was considering installing Arch with the KDEmod.  I will ponder and come back to you guys with results. :)

Cheers.

Why bother with Kdemod when Arch offers split KDE packages?

---

### Post by dragos240 on 2009-09-27
How about running it in a VM?

---

### Post by RiceMonster on 2009-09-27
> **dragos240 said:**
> How about running it in a VM?

read the thread:

> **lovinglinux said:**
> Use Virtualbox for learning.
> **Skripka said:**
> Last I heard Arch didn't VM well.
> **tjwoosta said:**
> Arch is notorious for having issues in a VM, but I have never personally had problems. I always use Virtualbox to test distros and have never had any major issue with any of them.

---

### Post by Dobbie03 on 2009-09-27
God this is f'n annoying, I am trying to download Chakra for the second time (it is downloading so slowly).  The first time I downloaded it and it refuses to burn the .iso to a dvd or cd.  Any ideas?

---

### Post by Bigtime_Scrub on 2009-09-27
> **Skripka said:**
> Last I heard Arch didn't VM well.

I have found this to be true myself. I've wanted to try Arch for a long time and I tried to boot into it from Virtual Box. It had many issues, the main one being that when it was time to install the base system, it would fail to connect to a mirror. I tried a lot of them and it always came back the same. I chaulked it up to some virtual machine problem and I never tried again. I installed slackware and BSD so it can't be that hard can it?

---

### Post by ~sHyLoCk~ on 2009-09-27
> **ddrichardson said:**
> The only thing I don't like about Arch is the attitude to bug reports, which if you supply a patch with usually get denied on the grounds that you should put it in the AUR. I understand the Arch Way but sometimes I question this.

Try sending a patch to debian. :P

> **ddrichardson said:**
> 
As someone who has written Ubuntu documentation, I think Arch's wiki is better.

Switching from Ubuntu, I'd advise users to get into the habit of reading before saying yes - AUR packages could be anything.

Seriouly this is good advice. Lately I have seen an increasing no. of ubuntu users flooding the arch forum with "help me im a noob" threads. People want to show off and feel powerful by using arch but don't want to go through the pain of reading documentation.

---

### Post by Skripka on 2009-09-27
> **MattDobson said:**
> God this is f'n annoying, I am trying to download Chakra for the second time (it is downloading so slowly).  The first time I downloaded it and it refuses to burn the .iso to a dvd or cd.  Any ideas?

Yep.

1) Skip Chakra.  Their handholding (bad idea) installer is not even at beta quality yet.

2) Install Arch the normal way.  

3) Then add Vanilla KDE, or KDEMod.  The old fashioned way.


To being with, Chakra is not a good idea, pragmatically or even philosophically...the Chakra devs, nice guys though they may be, [parted]("http://chakra-project.org/about.html") with [The Arch Way ]("http://wiki.archlinux.org/index.php/The_Arch_Way")a while back.


I run Vanilla KDE from Extra and love it-official support and timely updates and split packaging--you only get the very last with KDEMod.

---

### Post by Dobbie03 on 2009-09-27
The problem is I just dont have any idea on how to get Arch set up.  I know I might sound simple, but I just can't work it out.

---

### Post by Skripka on 2009-09-27
> **MattDobson said:**
> The problem is I just dont have any idea on how to get Arch set up.  I know I might sound simple, but I just can't work it out.

You start at the first page of the Beginner's Guide (I printed it out for my reference before I installed Arch the 1st time), and read and do downwards step-by-step.  Take time, and read and understand what you are doing and why.  It SHOULD take an hour or two the first time-most of which is reading (and very little doing).

Making Arch is like following a recipe from a cookbook. :)

---

### Post by ~sHyLoCk~ on 2009-09-27
> **MattDobson said:**
> The problem is I just dont have any idea on how to get Arch set up.  I know I might sound simple, but I just can't work it out.

A simple [guide]("http://pdg86.wordpress.com/2009/09/22/tutorial-easy-arch-linux-setup-guide-usb-included") I wrote.

---

### Post by tjwoosta on 2009-09-27
> The problem is I just dont have any idea on how to get Arch set up. I know I might sound simple, but I just can't work it out.

If you cant figure out how to install arch I wouldn't recommend installing chakra either because as mentioned earlier it would be like diving in head first before testing the depth. You will miss out on valuable problem solving knowledge.

In any case try using aria2 to download the .iso (aria2 is a high speed download utility with the ability to resume downloads and correct errors)

```
aria2c http://lekebilen.com/chakra-i686-090218-alpha2.iso
```

then check the md5sum before burning just to be sure
```
md5sum chakra-i686-090218-alpha2.iso
```

Chakra should be b2912b17f56e1bce58398b490af708c5, if not something went wrong and your .iso is corrupt.

---

### Post by Dobbie03 on 2009-09-27
> **tjwoosta said:**
> If you cant figure out how to install arch I wouldn't recommend installing chakra either because as mentioned earlier it would be like diving in head first before testing the depth. You will miss out on valuable problem solving knowledge.

In any case try using aria2 to download the .iso (aria2 is a high speed download utility with the ability to resume downloads and correct errors)

```
aria2c http://lekebilen.com/chakra-i686-090218-alpha2.iso
```

then check the md5sum before burning just to be sure
```
md5sum chakra-i686-090218-alpha2.iso
```

Chakra should be b2912b17f56e1bce58398b490af708c5, if not something went wrong and your .iso is corrupt.

Thank you very much.

---

### Post by ddrichardson on 2009-09-28
> **MattDobson said:**
> The problem is I just dont have any idea on how to get Arch set up.  I know I might sound simple, but I just can't work it out.
Really? The beginners guide is absolutely excellent, if a little verbose.

---

### Post by Dobbie03 on 2009-09-29
Well I have printed it and this coming weekend I am going to lock myself away and install Arch, come hell or high f'n water  I will learn to use this :)

---

### Post by mdsmedia on 2009-09-29
That was the attitude I had when I installed Arch. I was told the initial effort was worth it, so when I ran into hurdles, I googled, I fiddled, and I got Arch installed, with a nice XFCE desktop, and so far a few apps.

There was quite a sense of achievement when I got it working. Also a sense of having learned quite a bit about the layers involved in Linux. I installed Firefox/Shiretoko before I'd installed XFCE, for example, so I had Firefox on a basically naked X.

---

### Post by fuzzyk.k on 2009-09-29
Arch is a minimalistic in nature, Most of the configurations that we take for granted in other friendly distro's will have to be done manually, personally i learnt alot from it, but it requires time and patience

---

### Post by Dobbie03 on 2009-09-29
> **mdsmedia said:**
> That was the attitude I had when I installed Arch. I was told the initial effort was worth it, so when I ran into hurdles, I googled, I fiddled, and I got Arch installed, with a nice XFCE desktop, and so far a few apps.

**There was quite a sense of achievement when I got it working**. Also a sense of having learned quite a bit about the layers involved in Linux. I installed Firefox/Shiretoko before I'd installed XFCE, for example, so I had Firefox on a basically naked X.

Thats what I am expecting, I am sure it will be even more special as I know so little about Arch, so I expect the learning curve to be massive.

> but it requires time and patience 

I am adamant I will install this so both of those will be overflowing a plenty from my time\patience cup. :)

---

### Post by samjh on 2009-09-29
Make sure you:
[list=1][*]Back up your files from your current system before installing Arch.
[*]Print the Beginner's Guide, and make sure to read it thoroughly.
[*]Have a working LiveCD handy (the Ubuntu one is perfect), just in case things don't work out and your computer punches you in the face.
[*]Reserve at least two hours of your time for the installation of the base system and bare-bones desktop environment.
[*]Be prepared to do at least another hour of post-installation configuration to get your CUPS, scanner, and other accessories working.[/list]

Setting up a full-blown Arch system is a bit like learning to do your own routine car maintenance.  It won't make you a Linux expert (far from it), but it will make you appreciate how much goes into a Linux system.  Arch isn't really all that scary though.  The most frightening part is getting used to spending long periods of time in a text-only environment and fiddling with configuration files.  Once you get used to it, everything is pretty easy.

---

### Post by Dobbie03 on 2009-09-29
> **samjh said:**
> Make sure you:
[list=1][*]Back up your files from your current system before installing Arch.
[*]Print the Beginner's Guide, and make sure to read it thoroughly.
[*]Have a working LiveCD handy (the Ubuntu one is perfect), just in case things don't work out and your computer punches you in the face.
[*]Reserve at least two hours of your time for the installation of the base system and bare-bones desktop environment.
[*]Be prepared to do at least another hour of post-installation configuration to get your CUPS, scanner, and other accessories working.[/list]

Setting up a full-blown Arch system is a bit like learning to do your own routine car maintenance.  It won't make you a Linux expert (far from it), but it will make you appreciate how much goes into a Linux system.  Arch isn't really all that scary though.  The most frightening part is getting used to spending long periods of time in a text-only environment and fiddling with configuration files.  Once you get used to it, everything is pretty easy.

Thank you for the advice.  I am expecting it to take a long time, I am going to read the guide a few times over the next week in preparation. It is exciting really, I want to do it now....but I can wait...only just.

---

### Post by samjh on 2009-09-29
Don't be too obsessed about it.

I did a dress rehearsal using VirtualBox (unlike many posters in this thread, I've never had a problem using Arch inside VirtualBox) before I did my first "live" installation.  It went by without a hitch.

Beware the 2009.8 installer, however.  The disk partitioning section crashed a few times during my most recent install (I switched to Windows 7 RC and Ubuntu 9.04 for a while).

---

### Post by kevCast on 2009-09-29
Bad things come to mind when I think of Arch...

---

### Post by SomeGuyDude on 2009-09-29
> **MattDobson said:**
> The problem is I just dont have any idea on how to get Arch set up.  I know I might sound simple, but I just can't work it out.

Simple != easy

The first time you install Arch is the worst, and probably takes the longest, because you're so unsure of what you need to do that you'll end up having to read, re-read, and probably re-do when you ended up missing something.

Which is funny because, overall, there are only about a dozen steps to actually do.

---

### Post by RiceMonster on 2009-09-29
> **kevCast said:**
> Bad things come to mind when I think of Arch...

cool story bro

---

### Post by CJ Master on 2009-09-29
> **RiceMonster said:**
> cool story bro

o&#633;q &#654;&#633;o&#647;s &#643;oo)

---

### Post by RiceMonster on 2009-09-29
> **CJ Master said:**
> o&#633;q &#654;&#633;o&#647;s &#643;oo)

you got the c wrong, and what's with the l?

o&#633;q &#654;&#633;o&#647;s 1oo&#596;

---

### Post by CJ Master on 2009-09-29
> **RiceMonster said:**
> you got the c wrong, and what's with the l?

o&#633;q &#654;&#633;o&#647;s 1oo&#596;

I got the C wrong, but my L looks better.

---

### Post by raul_ on 2009-09-29
I think the whole "oh the first time is a shock" is just to NOT scare people away. I went through my first Arch install in a breeze (much nicer than Ubuntu's btw, no problem about the live sessions, I/O errors, but that's another story). My only shock was when typing something in the terminal was an error about my locale popped up. If it's the only problem, that's a good sign, IMO =)

---

### Post by kevCast on 2009-09-29
> **RiceMonster said:**
> cool story bro
It really wasn't a story, more of a statement.

---

### Post by CJ Master on 2009-09-29
> **kevCast said:**
> It really wasn't a story, more of a statement.

cool story bro.

---

### Post by RiceMonster on 2009-09-29
> **CJ Master said:**
> cool story bro.

I lol'd

---

### Post by ~sHyLoCk~ on 2009-09-30
A picture is worth a thousand words

[IMG]http://cdn3.knowyourmeme.com/i/19111/original/cool_story_bro_trollcat.jpg[/IMG]

---

### Post by Dobbie03 on 2009-09-30
> **samjh said:**
> Don't be too obsessed about it.

I did a dress rehearsal using VirtualBox (unlike many posters in this thread, I've never had a problem using Arch inside VirtualBox) before I did my first "live" installation.  It went by without a hitch.

Beware the 2009.8 installer, however.  The disk partitioning section crashed a few times during my most recent install (I switched to Windows 7 RC and Ubuntu 9.04 for a while).

I won't obsess.  I just want to give this an honest attempt.

---


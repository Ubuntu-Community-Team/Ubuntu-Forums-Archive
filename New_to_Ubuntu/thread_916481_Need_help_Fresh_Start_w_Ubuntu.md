---
title: "Need help: Fresh Start w/ Ubuntu"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Vendettaseve on 2008-09-10
Hello everyone.

Today my windows XP malfunctioned terribly, and I am now stuck in safe mode (Booting normally hangs after login). I have been thinking about getting Linux(Kubuntu or Ubuntu) for quite some time now and this has forced my hand. 

Could someone please instruct me on the best way to switch over to Linux. 

I would really like to wipe my hard drive completely, remove everything and start fresh with Linux only. I have looked around the net alot and have been fruitless in my search(Save for a hundred posts crying about running XP and Linux at the same time.

Any help or advice that can be given will be appreciated, Keep in mind I do realize that some things will not work the same(or at all) on Linux that did on XP. So 10 posts warning me about that will not be necessary.

Thanks :D

V

Ps. I have quite a bit of music and video files I will be hanging onto, Mp3/wma/wmv files will still work on Linux yes?

---

### Post by joyson20 on 2008-09-11
If you install the codecs(gstreamer) availabe in the ubuntu repository you can play these files...moreover mediubuntu repo also provides most of the codecs...but these are legally restricted for free use in countries like USA....

---

### Post by linux5uper on 2008-09-11
What I did after a disastrous Vista crash, was to go to 

[www.ubuntu.com](www.ubuntu.com)

and download a fresh ISO image + burn it on a CD. If you've done any kind of OS reinstallation in the past, installing Ubuntu 8.04 will be a piece of cake for you. Post-installation I always follow the following guide

[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

and hang around in this forum for additional info.
That's the basic idea I guess.

---

### Post by panhandle on 2008-09-11
Do you have any of the live CDs?

If so, the installation wizard is pretty straightforward and intuitive. The manual mode will allow you to set the size of the partition if you do decide to dual boot. 

Otherwise, you can select the automatic full installation which will overwrite your hard drive and require only a small amount of user input. Here is a youtube link tthat shows the entire process: [http://www.youtube.com/watch?v=IlQGk0PcqbI&feature=related](http://www.youtube.com/watch?v=IlQGk0PcqbI&feature=related)

Or you can just boot the live CD without installation if you just want to experiment.

I was a bit unclear as to whether you still have access to your windows partition. Do you? If so, you can download the iso as the previous post states and move from there.

---

### Post by Vendettaseve on 2008-09-11
I have never completely changed OS before, Just upgraded (Win95-98-2000-xp) Is there anything specific I have to do with the file system, Bios etc or can I wipe the HD completely and the Disk does the rest? 

Thanks


Edit: I am currently on my PC right now, I have minimal access to everything as I am running in safe mode (Windows will not start in full mode) I have another PC I can burn the ISO onto a disk with as well. I do NOT want to partition my HD and have both OS.

---

### Post by Zzl1xndd on 2008-09-11
If you download and burn the standard ISO you should be fine. I would suggest running the live CD first to see how your hardware works with Ubuntu. 
 

Just make sure you select the use entire drive option if you want to get rid of windows.

Any other help you need just ask.

---

### Post by Frogbarf on 2008-09-11
¿Can you browse the web and burn a CD with your machine as it is, or do you have access to another machine you can do that on? If so then just follow the instructions at[http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso"). 

Tips:

1. Verify the checksum for the .iso file you download just like the nice man says to do.
2. Burn the Ubuntu install CD at the slowest possible speed.
3. Before starting installation, back up all the audio & video files you want to keep. Installing Ubuntu Linux will normally wipe your hard drive clean and re-partition it.
4. "According to what I've read" if you want a Win/Ubuntu dual boot machine, you have to install Windows first, then Ubuntu.

PS#1: Re-reading the thread I see that all of these points are already in hand.

PS#2: Be sure to come back and tell us how it went, even if just to say "textbook case, no hiccups"

PS#3: Get yourself a cheap bound notebook and a good indelible pen, and every time you monkey with your system, jot down what you did, including URLs.

PS#4: If you install system software, it's a good idea to reboot afterwards. I went through hell trying to get desktop effects (Compiz) hopping, and the secret ingredient to success turned out to be a reboot.

PS#5: Also take the time, once you're up and running, to explore the various Ubuntu websites so you know which one to use for which purpose. For example, you use Launchpad.net to report bugs, this forum is in ubuntuforums.org, and there are others beyond those.

---

### Post by skippuff54 on 2008-09-11
remember to back up that media u want to save. obviously when u install a new OS it will all be gone...the answer to ur question though is yes there's all kinds of media software for linux, more so than win as far as i can tell...at least that is free and highly customizable

it's also a good idea to take inventory of ur hardware so that just in case somethin works unexpectedly, u know where to start in terms of drivers, chipsets etc. just jot down stuff like ur soundcard, video card etc and keep that in mind if somethin comes up

---

### Post by Vendettaseve on 2008-09-11
Thanks everyone for the large ammount of help. 

Im currently WinRaring all my files that I want to hang onto and sending them to the other computer.  Before something goes awry however, Is there WinRaR or equiv for Linux? Linrar perhaps lol :D

---

### Post by Ryadt on 2008-09-11
> **Vendettaseve said:**
> Thanks everyone for the large ammount of help. 

Im currently WinRaring all my files that I want to hang onto and sending them to the other computer.  Before something goes awry however, Is there WinRaR or equiv for Linux? Linrar perhaps lol :D

You've got unrar-free...
```
sudo apt-get install unrar-free
```
to install it.

---

### Post by Vendettaseve on 2008-09-11
A relatively pertinant question just dawned apon me.

Will I be able to connect to the other networked PCs that are currently running Vista to get the files that Im transfering over there right now back onto this PC once Linux is installed and all that? As I know Windows has a habbit of not communicating well with other OS (Even other versions of windows)

Seems like something I should ask beforehand :D

your help is appriciated.

V

---

### Post by tarps87 on 2008-09-11
If you install samba you can, once you have installed Ubuntu under applications -> add software/add programs search for samba, there will be a package called samba and one called gsamba, samba is a simpler program. The samba you install is just a GUI but it will also install the actual samba protocol. You may need to change the workgroup to connect to the vista share.

---

### Post by stalkingwolf on 2008-09-11
Also make sure when you burn the ISO you burn it as Image and use a slow
burn speed.  I use 2x or 4x depending which is available.

---

### Post by Bulat Sirazetdinov on 2008-09-11
> **Ryadt said:**
> You've got unrar-free...
```
sudo apt-get install unrar-free
```
to install it.

Warning: "unrar-free" doesn't support RAR 3.0 archives.
But there's "unrar" (not free :) ) that is shareware (40 days of use allowed before registration).

P.S. "unrar" and "unrar-free" are packages available to download and install with "apt" or Synaptic Package Manager (GUI front-end for "apt"). Those package managers are built-in into Ubuntu.

---

### Post by roger_1960 on 2008-09-11
Hi

You have lots of good advice above!  I strongly suggest that you do try the Live CD installation first to check that your PC (hard drive) is OK ...seriously, why did windows crash so badly?.....

---

### Post by Vendettaseve on 2008-09-11
Windows crashed so badly because it is the nature of windows to stop working from time to time and Im tired of its constant needs. I beieve the problem may have been linked to the reg files however Im not terribly sure. Any info that I can find ont the subject generaly just says "Windows crashed because thats what windows does" with minimal explination and what not.

My HD is in good shape, Iv been playing around with my files and getting the disk ready to be converted for most of the night and some of today and everything is going fine. Have not had any problems packing up files and moving them over to my other computer while in safe mode. 

I have virus scanned the packages on my other computer and they are all clean so it looks like windows did it to itself -_- As I had fallen asleep at the kebard the other day wich allowed windows to sneak in one of those annoying automatic updates and reboot my PC on its own, when it stated up again Windows did not work.

Thanks for your help :D

---

### Post by dnguyen1963 on 2008-09-11
Hi,
I recently switched over to Ubuntu.  I have searched the net and read the forums.  However, I found the best way to install Ubuntu was to go to the local library and check out the book/CD.  The instructions in the book match up with the supplied version of Ubuntu very well (less confusion).  Do not worry if you cannot find the latest verison of Ubuntu (7.04 and above works fine) because, after the installation, Ubuntu will find and intall all the available updates.

Good luck and have fun!

---

### Post by The Cog on 2008-09-11
You would be better using zip than rar to archive your files.

Beware that the Ubuntu installer defaults to using the whole drive for the install. This deletes all existing disk contents, including your makers utilities partition (if there is one). When you get the live CD running, run the patition editor (System->Administration->Partition editor) and have a look at whats there before just overwriting the whole thing. If there is a utilities partition, you may prefer to use the partition editor to delete every other partition and then use the installer optiion to use the free space instead.

---

### Post by Vendettaseve on 2008-09-11
I have finished moving all important files to another computer and have burn the Ubuntu live CD. 

However I am running into a problem. When I go to boot up ubuntu from the cd to make sure it will run well on my machine it hangs at the very end of loading. 

the orange bar will bounce back and forth for about 1 minute then it will begin loading, then stop 1 and a half bars away from the finish point and just sit there. My computer is making no signs that it is loading anymore(No activity from the CD drive, No flashing red light etc) I have left it there for about 30 mins now and still nothing has happend.

What should I do?

---

### Post by virtuallinux on 2008-09-12
If you haven't already, restart and pick the menu item that says "Check this CD for Defects"

---

### Post by Vendettaseve on 2008-09-12
Yep already done that, Says the cd is perfect.

---

### Post by tarps87 on 2008-09-12
When you see the orange bar press ctrl+alt+f1 and when it hangs see what the last line says. You may need to use the alternative cd which means you won't be able to try it before you install it, this happened with the live cd of Ubuntu 7.10 on my laptop but installed fine with the alternative

---

### Post by skippuff54 on 2008-09-12
check the cd for scratches. i just read another post with nearly the same issue.

try the cd on another computer if possible. do u know if ur other computer might be 64-bit?

---

### Post by skippuff54 on 2008-09-12
u should also use the md5 checksum provided on the download site to make sure ur download is flawless.

---

### Post by tarps87 on 2008-09-12
> **skippuff54 said:**
>  do u know if ur other computer might be 64-bit?

If you are using a 32 bit (i836) install/cd it will work on a 32 or 64 bit machine, if you are using a 64 bit install/cd on a 32 bit machine this could be your problem but I wouldn't expect it to boot at all.
Another think to check is did you burn it at a low speed or use an automatic setting?

---

### Post by Vendettaseve on 2008-09-12
I am beyond agitated now.

I have downloaded this cd about 5 times, burnt it 10 and still the same result. When I try to install the orange bar stops at about 80% of the way across and just sits there, my computer stops making sounds and lights. I have tried Mint Linux, as well as the 64 bit Ubuntu and neither of wich has worked.

What could possibly be the cause of this.... :(

V

---

### Post by tarps87 on 2008-09-12
Have you tried pressing ctrl+alt+f1 before it freezes?

---

### Post by Vendettaseve on 2008-09-12
No, What does that do?

---

### Post by tarps87 on 2008-09-12
It will take you to a linux 'terminal' it will show you what is happening behind the GUI loading screen the last line will be what it was trying to do when it freezes. It won't fix the problem but it should tell you what the problem is, if you don't understand what it means post it here and someone will be able to tell you.

---

### Post by Vendettaseve on 2008-09-12
Add Open Suse to the list of things that freeze while loading -_-

Alright Il give Ubuntu another try with the terminal open and let you know what happens. Should not take long.

---

### Post by tarps87 on 2008-09-12
Are these all live cd's?

---

### Post by Vendettaseve on 2008-09-12
Back, I ran the thing while it was loading, got 1 error and also what it froze on while loading.

I did not get the whole error message as it moved on too quickly but this was the gist of it.

Loading Hardware Driver:     Eprom Failed

It stopped working on:

Starting Hardware Abstraction Layer Hald


Does this clear anything up? Why will none of these run on my computer? this is begining to grate on my nerves in a way only windows could, apparently Linux is just as frustrating -_-

---

### Post by tarps87 on 2008-09-12
I kown this was a problem with Ubuntu 7.10 (Gusty), but I'm afraid that's about all I know about it. Hopefully someone else will know more about it and been able to solve this. The only solution I have found is to use Ubuntu 6.06
I am sorry I can't not be of more help, I will let you know if I find a solution

---

### Post by Vendettaseve on 2008-09-12
Thanks mate


Im going to check my device manager real quick too to make sure there are no conflicts etc.. as that might have to do with the problems Im currently having.

Sadly I have tried other kinds of linux too and they also freeze, well just Suse and 64 bit Ubuntu. I hope something comes up soon :(

---

### Post by Vendettaseve on 2008-09-12
Could it be a problem with my Hard Drive do you think? Im going to go buy a new one thats bigger anyways I suppose :D

---


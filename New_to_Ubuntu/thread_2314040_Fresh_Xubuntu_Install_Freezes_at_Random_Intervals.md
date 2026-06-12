---
title: "Fresh Xubuntu Install Freezes at Random Intervals"
date: 2016-02-18
forum: New to Ubuntu
---

### Post by Burgy on 2016-02-18
Recently my 'rents decided to upgrade their PC so they decided I could have their old PC and I wanted to fiddle with it for fun mostly, but my friend has a PC with lower specs than this one so I thought I'd install a lightweight operating system and see what I can do.

To start I popped open the hood and got all the dust out of the inside with some compressed air because it's gotten pretty bad sitting in the same place for about a decade. After I downloaded and setup a bootable USB pendrive but the PC only supported booting from USB-ZIP and I didn't feel I knew enough to try and figure out how to trick my PC into thinking it was a USB-ZIP.
I decided to write a few disks since it did have a CD-ROM drive, I wrote Ubuntu 15.10, Ubuntu 14.04 and the Mini.iso to separate disks and after dealing with many issues in regards to graphical issues (apparently in regards to Nvidia drivers) on 15.10 and 14.04 I decided to try Xubuntu out for size since it should be a better fit for this PC anyways. 

Xubuntu installed without a hitch, though it took forever with my ever so slow DSL connection. After booting, I was thrown straight into command-line and "startfxce4" didn't work, so I installed fxce and rebooted and everything worked fine for about 10 minutes until it froze (similar to the Ubuntu installs). 
Now randomly, if I have no apps open or even if I have 20+ open I will freeze and be unable to do anything. I was wondering if anyone had any insight to this. 
Sorry for the vague explanation but any help is appreciated.
Thanks!

Specs (Dell Dimension e521):
Proccesor - AMD Sempron 3400+
Integrated Graphics - Nvidia GeForce 7300 LE
RAM - 512MB

---

### Post by DuckHook on 2016-02-18
Welcome to Ubuntu and the forums, burgy.

Your machine is old and was severely underpowered for its time even when it was new. The CPU was an entry-level unit and the graphics sub-system was not only underpowered, but stole its video memory from system RAM. Since you only have 512 MB to start with, we are talking serious limitation here.

As I see it, you have three choices:

1. Install more RAM (bring it up to at least 1 GB) and see if this will allow you to run Lubuntu (which is the lightest official Ubuntu flavour), or

2. Install a truly light distro like Slitaz, which will likely work acceptably, or

3. Install Ubuntu mini.iso or server and restrict use to the command line. This machine can still effectively work as a file or print server, a router/gateway, a torrent server, a backup machine, or indeed any number server applications. However, the moment you put a GUI onto it, you will likely kill it.

I would tend to #3, but it's taken me years to get comfortable with the Linux command line and this is not a good solution for everybody.

---

### Post by Bucky Ball on 2016-02-18
> **DuckHook said:**
> 
1. Install more RAM (bring it up to at least 1 GB) and see if this will allow you to run Lubuntu (which is the lightest official Ubuntu flavour)

This gets my vote, although be careful to check how much RAM the old dear can take and what type. The processor may still not be up to it, though. 

Lubuntu, forget Ubuntu I'd think. Although with 2 or 4Gb of RAM in there, who knows? Miracles have happened, apparently. :D

---

### Post by Burgy on 2016-02-18
Thanks for the heads up, I'll order some more RAM soon. We were planning on upgrading the CPU as well so that's alright.
It used to be running Windows Vista so I just assumed that it would be able to run lighter flavours of Ubuntu, lol.

Thanks again! I'll update as soon as my parts get in.

---

### Post by DuckHook on 2016-02-18
> **burgy1998 said:**
> ...I just assumed that it would be able to run lighter flavours of Ubuntu, lol.You are correct in assessing that Xubuntu is one of the lighter flavours, but for all that, it is still a modern OS. Your machine was built to just barely run XP which is now a 15-year old OS. I'm surprised that your parents were satisfied with its Vista performance, but even that OS is now 10-years old.> Thanks again! I'll update as soon as my parts get in.I trust that you were able to buy at a good price. I make it a hobby to work on a variety of old machines, and I usually find that it isn't worth the money to try upgrading them. Rather, it is better to find the right distro that works *with* the machine than trying to change the machine work to with a favoured distro. Too much the tail wagging the dog, if you take my meaning. But if you were able to find the components on the cheap, then that's a good thing too.

---

### Post by Geoffrey_Arndt on 2016-02-18
Before spending money for ram or cpu (which isn't always foolproof for old systems, and may not be compatible with pc motherboard anyway.) . . . . . try a super light weight distro such as antiX . . . which is based on Debian.    Can run fine on 512 mb.

See:   [http://distrowatch.com/table.php?distribution=antix](http://distrowatch.com/table.php?distribution=antix)

---

### Post by Burgy on 2016-02-18
Okay, so! I installed Lubuntu and uninstalled Xubuntu, the problem persists for me still.

I haven't ordered the parts yet but I had found an AMD Athlon processor that fits in the AM2 socket on my mobo. It was in a bin from the old Computer Science class I was a part of, they just have a bunch of old PC parts sitting around in bulk here.
[http://www.amd.com/en-us/products/processors/desktop/athlon-ii](http://www.amd.com/en-us/products/processors/desktop/athlon-ii)

And I have more than 512MB RAM already, there was after market RAM already installed so I assume that was when they took it into upgrade to Vista whoever updated it for them installed more RAM? I forgot what the amount was but it was just above 2GB I believe. I'll post the exact amount after this class, I have spare last period and i'll be able to run home and check.

Is there someway to see a log of what's going on similar to logcat on Android? That way I could pastebin the log and give more info on the issue.

---

### Post by Geoffrey_Arndt on 2016-02-18
Does that bin have an old Intel based mobo . . . . . ?   If so, problem likely solved.    Amazing how all Intel systems make running Linux a snap.

---

### Post by Burgy on 2016-02-18
> **Geoffrey_Arndt said:**
> Does that bin have an old Intel based mobo . . . . . ?   If so, problem likely solved.    Amazing how all Intel systems make running Linux a snap.
I can check in a second actually, thanks for the tip!

EDIT: Unfortunately not any that are intact. There were two mobos here but they have cracks in the base and I don't think they would be operational haha

---

### Post by DuckHook on 2016-02-18
I'm on the road for the next few days so, hopefully, other forum members will be around to respond to you. To answer your question:

Ubuntu keeps its logs in /var/log

You can see what is happening to your system with```
cat /var/log/syslog
```If you want to redirect output to a file to pastebin, do```
cat /var/log/syslog > ~/Desktop/syslog.txt
```This will produce a file on your desktop called syslog.txt with the contents of syslog. You can then simply copy and paste those contents back to this thread or to pastebin. International users should note that "Desktop" will be different in different languages.

Before we automatically assume that the issue is OS related, let's see if I've got the facts in order:

You mention that the various 'buntus successfully load and run for a short while but then freeze after about ten minutes. The next time you start the computer, don't log in at the prompt. Instead, hit <Ctrl>+<Alt>+<F1> to get to a command line console. Then log in with your username and password and let it run for a while. Does it still freeze after ten minutes? If not, how long does it run? Indefinitely? In the command line console, run```
top
```to see what processes are using the most CPU cycles and memory. Are there any glaring problems that stick out?

Your problem might be due to physical issues. You mention that you cleaned the old girl out with compressed air. Did you dislodge any component while doing so? Please make sure that the HDD cables, power cables, graphics card and memory modules in particular are properly seated. Are all fans working? It is possible that the unit is overheating after 10 minutes. Is the MB in good shape? I've dealt with cracked MBs, wonky PSUs, failing HDDs, and many exotic issues all of which are unavoidable with aged machines. They are hard to track down and give weird results that one would not at first think would be caused by HW.

Also, it is time to get a more complete picture what your system is really comprised of. In the short time that your machine runs, bring up a terminal and post the results of the following command back to this thread:```
sudo lshw
```This will generate a lot of output, so again you may wish to redirect to a file with:```
sudo lshw > ~/Desktop/lshw.txt
```

Last but not least, I am concerned about your install method. You mentioned in quick succession: Ubuntu, mini.iso, Xubuntu, fxce (I assume you meant xfce), recently Lubuntu, and all over a DSL connection. I'm wondering if the download might be corrupted. However, this is unlikely three times in a row. Did you torrent the downloads? This is the recommended method since torrents are largely self-correcting.

---

### Post by Burgy on 2016-02-18
For Ubuntu I downloaded the .iso's in my torrent client. But I just downloaded the mini.iso in Chrome and followed along the steps in the installer.

To install Xubuntu I ran
```
sudo apt-get install xubuntu-desktop
sudo apt-get update
sudo reboot
```
And rebooted, had the issue again and after reading your comment about trying Lubuntu I ran
```
sudo apt-get install lubuntu-desktop
sudo apt-get update
sudo reboot
```
```
sudo apt-get purge xubuntu-desktop
sudo apt-get autoremove
sudo reboot
```

In command line there are no issues and I'm fairly certain it will run indefinitely given the time it took to download Xubuntu-desktop (roughly 2 hours). 

I'll run the logs and things in a little bit.

(Processor: 2x AMD Athlon 64 x2 Dual Core Processor 3800+ 
RAM: 1983Mb so a little less than two gigs.)

---

### Post by DuckHook on 2016-02-18
> **burgy1998 said:**
> In command line there are no issues and I'm fairly certain it will run indefinitely given the time it took to download Xubuntu-desktop (roughly 2 hours). 

I'll run the logs and things in a little bitIf you first tried to install Ubuntu on top of the mini.iso, then you are probably still running all of the bloat that came with Ubuntu desktop. When you switched first to Xubuntu and then to Lubuntu, you only applied a different skin to the same underlying structure. If that structure is corrupted or running the wrong video driver, then changing to Xubuntu-desktop or Lubuntu-desktop will do nothing to solve your problem. You are still inheriting the underlying infrastructure with each change.

Don't be fooled by```
apt-get purge Xubuntu-desktop
```This doesn't actually get rid of Xubuntu. It only gets rid of the metafile that calls every one of Xubuntu's components to be downloaded and installed. The individual elements of Xubuntu are still present. I now note that you mentioned that you fiddled around:> dealing with many issues in regards to graphical issues (apparently in regards to Nvidia drivers) on 15.10 and 14.04...before installing Xubuntu. I'm guessing that this fiddling involved loading some sort of NVidia driver before loading Xubuntu-desktop. If so, then you will have been working with the same problem driver in each of your Ubuntu, then Xubuntu, then Lubuntu iterations.

You will need to torrent a fresh and complete version of Lubuntu from its download site using another computer. Then install this complete version over your current installation by choosing to erase the entire disk and install over it. No mini.iso + Lubuntu-desktop shortcut this time. This may actually solve your issues without any further HW upgrades.

It makes no sense to fiddle with further detective work including examining log files etc until you have taken this step.

---

### Post by Burgy on 2016-02-18
No, no. I installed Ubuntu with a full iso from disk and had these problems originally.
Then tried the mini.iso and formatted the drive while installing to get to Xubuntu. But it didn't have the graphical desktop until I ran the command to install xubuntu-desktop. 
But I'll definitely try installing Lubuntu from a full iso download.

Sorry for not clarifying that I installed from the full iso first.

Ran the commands you asked me to run:
Top: Everything looked fairly normal, nothing was using mass amounts of CPU or Memory, Firefox was using 13.2% of memory but that was the highest process.
lshw output: [URL="http://pastebin.com/MQQ0WZD4"]http://pastebin.com/MQQ0WZD4

[/URL]

---

### Post by DuckHook on 2016-02-18
> **burgy1998 said:**
> ...I installed from the full iso first.Thanks for clarifying that.

According to your lshw output, you no longer have a Sempron installed, but a much nicer dual-core Athlon 3800+. You must have already made the CPU switch. The system is also recognizing your 2GB of SRAM, so everything on the CPU and memory front is peachy. The only bottleneck would appear to be the video sub-system.

There are a few things we can try before resorting to further HW upgrades, although, I must say, you've been very resourceful and are already most of the way to turning your old bucket of bolts into a decent working machine. In other words, with your memory and serendipitous CPU upgrade, you are really only a decent video card away from having a little tiger again, so you may actually wish to scrounge for a better video card and solve the problem that way.

To try making the current video behave, you can try two things:

1. Use nomodeset with the Nouveau driver (the open source community driver, which is actually very good these days). Instructions to follow, or

2. Install the proprietary nVidia drivers. It's been a long time since I've used the proprietary drivers and I'm not that familiar with your video card, so my advice is limited here, but other forum members may have more experience.

To set nomodeset, do so only if you have *not* installed the proprietary driver and do as follows:```
sudo nano /etc/default/grub
```Find the line that reads:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```...and add the phrase *nomodeset* between the quote marks so that it reads:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```Then:```
sudo update-grub
``````
sudo reboot
```I'm not counting on this to fix the problem because your GUI does actually come up whereas modeset issues usually prevent the GUI from coming up at all. But it's usually good idea to start with the simplest solutions first.

EDIT:

Just did a Google search on your behalf and it appears that Nouveau doesn't play that well with your video card. Many users report problems with it. You will have to install the proprietary nVidia driver, specifically, the legacy 304.xx driver. According to *oldfred*, it is available in the repositories, and as forum members know *oldfred* is *always* worth listening to. Make sure that you have not installed other proprietary drivers, because they gum up the works. The 304.xx must be the first proprietary driver that you install. Instructions [here]("http://ubuntuforums.org/showthread.php?t=2226780&p=13037354#post13037354").

Also, it seems that this legacy driver works in 14.04 but may not with newer versions. You should be using 14.04 anyway, as it is an LTE release and is supported to 2019.

---

### Post by Burgy on 2016-02-18
Thank you so much for you help with this! I've been downloading the 14.04 iso for a while and am glad you said that. I'll probably be able to post an update tomorrow with results. 
[B][I]
Just for clarification: I need to set NOMODESET, then I should purge existing Nvidia drivers and then install the nvidia-304 package?
[/I][/B](Is there a way to check if the proprietary drivers are already installed, I don't believe I installed them manually but just to be safe before I set NOMODESET)

---

### Post by DuckHook on 2016-02-18
> **burgy1998 said:**
> [B][I]Just for clarification: I need to set NOMODESET, then I should purge existing Nvidia drivers and then install the nvidia-304 package?
[/I][/B](Is there a way to check if the proprietary drivers are already installed, I don't believe I installed them manually but just to be safe before I set NOMODESET)You can rest easy. Stupid me. Your lshw output already tells us that you are running Nouveau. Therefore, no need to purge anything.

Go ahead and set nomodeset using my previous instructions. Just on a lark, try running for a period on Nouveau with nomodeset and see if that doesn't solve your problems on its own. Only if system continues to freeze should you then use proprietary driver using oldfred's instructions.

---

### Post by Burgy on 2016-02-18
> **DuckHook said:**
> You can rest easy. Stupid me. Your lshw output already tells us that you are running Nouveau. Therefore, no need to purge anything.

Go ahead and set nomodeset using my previous instructions. Just on a lark, try running for a period on Nouveau with nomodeset and see if that doesn't solve your problems on its own. Only if system continues to freeze should you then use proprietary driver using oldfred's instructions.
Will do! Thanks again.

---

### Post by DuckHook on 2016-02-18
BTW, if you want to see what driver you are currently running, look at your lshw output under "display". You will see a line that reads:```
configuration: driver=nouveau latency=0
```

---

### Post by Burgy on 2016-02-18
I'm actually half happy that this install didn't go as smooth as I expected. I've learned a lot lol!

So I've set nomodeset and I am noticing differences, thinks are running a little slower now and there are some graphical issues occasionally but no freeze yet. We'll see how this goes!

**Edit:** 
Okay! Burned a disc with 14.04, installed. Removed the Nouveau drivers and then installed the nvidia-304 drivers and everything was working mint for the half an hour I was fiddling, I got Steam installed and Cave Story was running at a respectable frame rate. I am letting it run for a little while longer while I watch an episode of my show to see if it ends up freezing or if we are all good!

[B]Edit 2:
[/B]It's still up and running perfectly, so happy right now. Thank you all so much for your help and have fun on your trip @DuckHook :)

---

### Post by DuckHook on 2016-02-19
> **Burgy said:**
> It's still up and running perfectly, so happy...Glad things worked out. Happy Lubuntuing.

---


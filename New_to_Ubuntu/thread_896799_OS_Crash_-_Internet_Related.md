---
title: "OS Crash - Internet Related"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by Chazbot on 2008-08-21
Good day!
  I am very new to Linux, in fact this is only my third week with it. Like a timid and cautious sort I first installed it (that is, Ubuntu 8.04-flavored Linux) on my ancient clunky laptop to see what it could do. I was, needless to say, quite impressed. Confused? Frequently. But impressed. 
  So I said to myself, "I wonder what it's like with some real power behind it." Since on this machine, my desktop, I had two physical hard drives, I thought I'd mount Linux on the smaller one and have a dual boot system (I play a lot of games, it just made more sense to leave XP intact for playing them than to try to emulate them). All this is preparatory to buying my next system before the end of the year, some sort of laptop which I'll run as solely an Ubuntu machine. But there's a hitch in the getalong.
   On the laptop, I'd never had any problem connecting to our home network, it hooked right up and ran smoothly. My desktop hooked right up too, but it did NOT run smoothly. It SEEMS that using the internet is what's causing the OS to crash. I say the OS is crashing, because the image freezes on the screen and my Caps Lock and Scroll Lock lights blink on and off rythmically. Only a hard reboot will restore functionality. Everytime it crashes, there is a demonstrable internet activity going on. I can't get system updates because after about the first file or so, it locks. I have to access these forums from the XP side of the system because leaving Firefox open for a while will crash it. I can run the little games and things that don't go outside the computer without trouble though. 
   Given that my laptop is not having this failure, this tends to indicate to me that the problem is not the router, it's something in the hardware or configuration of my desktop itself. The first culprit is the wireless card, especially as one of the things I learned before I switched is that not all wireless cards support Linux. It is a Ralink MIMO Wireless LAN Card. 
    I don't get error messages so I don't even know what errors to quote to you but if someone can point me to where this is logged I'll be happy to post them. Thank you for your time.

Chazbot

---

### Post by Sealbhach on 2008-08-21
Maybe it's Firefox that's crashing,perhaps try a different browser just to test if that's the case. You can install Galeon through the terminal:

```
sudo apt-get install galeon
```

See if you can use the internets for long without crashing.

A lot of people have reported Firefox freezing and crashing.

.

---

### Post by Chazbot on 2008-08-21
but it's not just firefox, the updater tool for Ubuntu itself crashes it. Pidgin too.

---

### Post by elmoosecapitan on 2008-08-21
I am always under the impression that if your 'CapsLk' and 'ScrLk' blink, then there is a hardware failure, not necessarily OS independent. Check:
```
more /var/log/syslog
more /var/log/messages
more /var/log/kern.log
```
for any thing that that looks out of the ordinary, for example the word 'PANIC'

---

### Post by Chazbot on 2008-08-21
Looking through the logs, I found only one thing of interest. Nothing marked PANIC I'm afraid, only this warning in syslog:

Network Manager <WARN> nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. Failed to execute child process "/user/sbin/nscd" (no such file or directory)) 

I'd provide the logs in total but I can't seem to get my floppy drive to work for some reason, it says 'back end doesn't support' or something to that effect. Only now do I realize I should have used my flash drive. Will update when I have them.

---

### Post by damis648 on 2008-08-21
Kernel panics are a tricky thing, as I have learned. You are connecting, wired, yes?

---

### Post by Chazbot on 2008-08-21
nope, wireless. the Ralink MIMO card is a wireless one with a fancy-schmansy antenna

---

### Post by pi.boy.travis on 2008-08-21
Are you using an open source driver, or a closed source one?  What does System-Administation-Hardware Drivers say?  I am talking about the menu in the upper left hand corner.

---

### Post by Chazbot on 2008-08-22
there are only open-source drivers on my system at present. I need to get a closed-source one for my graphics card but, again, can't download.

---

### Post by pi.boy.travis on 2008-08-22
Is there a way to temporarily connect your computer via Ethernet?  I had to do that with my laptop to get the wireless working.

---

### Post by Chazbot on 2008-08-23
well, I lugged the compy upstairs today, after an hour fighting the ethernet it finally started working as intended. Got the whole thing upgraded, hey this is great! I started testing the wireless, yeah everything looked REAL good. So I lugged it back downstairs, hooked everything back up, fired her up and started toward the Ubuntu forums to report the problem resolved... and it crashed. *ANGRITY BRAIN*

I still blame the Ralink MIMO wireless card. The locking problem did not occur with the wired connection. I suspect what is happening is that a download starts to require more resources, and the card makes availalble one of its extra input channels (it has three antenna) and this somehow crashes my Ubuntu. Ideas?

---

### Post by Chazbot on 2008-08-24
*24-Hour bump*

---

### Post by pi.boy.travis on 2008-08-24
Well, the only other thing I can think of is that perhaps the install was faulty.  Did you run "check CD for defects" from the live CD menu you used to install the system?  I have seen some pretty weird things happen because of faulty install CDs. . .  I would backup your important files, burn a new CD, and give it another go!

"A clean install fixes all"

---

### Post by Chazbot on 2008-08-25
bollux, I'll do it this week and report back, thank you!

---

### Post by Chazbot on 2008-09-12
Well, it was only today I could set aside the time to attempt the clean install. I downloaded a fresh ISO from a different mirror, burned it to a clean disc, and checked the disc using the included utility. The same issue still happens. It happens running in live mode too. I cannot shake, given the circumstances, the beleif that the trouble really does come from the Ralink MIMO Wireless Card.

---

### Post by pi.boy.travis on 2008-09-12
You mentioned in your original post that you will be buying a new laptop in the near future.  If you are buying a computer that you know will be used for Linux, you should do some research on supported hardware.  It pays to do your homework when it comes to buying hardware!  The best solution in my opinion is to build your own computer.  It may seem like a daunting task, but it isn't really too hard.  This also requires a little homework, but it is well worth it in the long run.  You will cut costs, control every aspect of the machine, and (most importatly) you will know exactly how your machine works.

As for your existing problem, did you check for available proprietary drivers?  If you hook the computer up to a wired connection, and go to System-Administratoin-Hardware Drivers, you might find that other drivers are available.

Hope this helps!

---

### Post by Chazbot on 2008-09-12
I built the computer I'm using currently, seven years ago. I'm not a stranger to the process on desktops, but I'd be much too intimidated to try it for a laptop. As for the other, I didn't think of that, I'll give it a shot thanks!

---

### Post by pi.boy.travis on 2008-09-12
Also, if you don' find drivers there, a Google search for Ralink MIMO Wireless Card linux drivers might also yield something useful.  The Broadcomm chip in my Dell only works occasionally and with a lesser range without proprietary drivers.  Open source software is cool, but sometimes proprietary solutions must be used. . . 

Hope this helps

---

### Post by Chazbot on 2008-09-22
RIDICULOUSLY CONFUSED!!

After some research, I learned that my Airlink 101 card uses a specific RALink chipset, the RT2661 +RT2529L. The RALink folk have a pretty good list of Linux drivers, the appropriate one was located [here]("www.ralinktech.com.tw/data/drivers/2008_0723_RT61_Linux_STA_v1.1.2.2.tar.bz2"). So I download the merry file on my laptop and port it over to the desktop, unzip and... huh? There aren't any installation instructions. There IS configure so I open up the terminal, cd over to the directory and do /.configure ...no luck. I try make install and that tells me I don't have permission to create directories. I tried just make and that did... something to the files in the unzipped folder, but nothing that seemed to be an install. The README is filled with commands I don't understand, but not a single one seems to be 'install'. How do I use this code?

---

### Post by Mornedhel on 2008-09-22
Assuming this is the standard configure-make-make install since all three do something.

```
./configure
make
sudo make install
[enter password on prompt]

```

---

### Post by hyper_ch on 2008-09-22
and before you start compiling you need to install
```

sudo apt-get install build-essential

```

---

### Post by Chazbot on 2008-09-22
bash: ./Configure: Permission Denied

Um, so far as I know I'm a top level user (I am the only user of this machine). Also, the capitalization is deliberate the 'Configure' in the package is capitalized

EDIT: I will have to do that, I forgot I made a complete re-install of Ubuntu on this box previously in this support chain. I HOPE that doesn't mean I'll have to lug the accursed thing back upstairs

---

### Post by hyper_ch on 2008-09-22
it's:
```

./configure

```

---

### Post by Mornedhel on 2008-09-22
This is weird. Anyone else hear of a configure set to non-executable by default ? Then again, it's not the usual configure if it's spelled with an uppercase C.

> Um, so far as I know I'm a top level user (I am the only user of this machine).

No, you're not. You're a sudoer. You're someone who can get temporary administration rights to execute some commands, with "sudo", as in the third line "sudo make install". The only "top level user" is root. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) .

Let's try again.
```

chmod 755 Configure
./Configure
make
sudo make install
```

If it fails on ./Configure, that means it's possible the file just contains configuration instructions. In which case you should try to open and read it. (This would also explain why it's not executable.)

---

### Post by Chazbot on 2008-09-22
that just gives me a 'not found' error, which may relate to the build-essential thing. Unfortunately when I try to get it I have the following returned: 
"Package build-essential is not available, but is referenced to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package build-essential has no installation candidate"

EDIT: Didn't see that reply before this post, trying the preceding idea now

---

### Post by Chazbot on 2008-09-22
ok, now the chmod did something. I'm just not sure what! :D 

I entered it then ./Configure and got this:

----------- Ralink RT61 Station Configuration -----------

Linux kernel source directory [/usr/src/linux-2.6.24-19-generic]:

completely unsure of what to do next, I just tried entering 'make' into the prompt provided, which told me 

'Linux source tree 'make' is incomplete or missing!

Configuration failed"

and then returned me to a normal prompt

---

### Post by hyper_ch on 2008-09-22
you need to the build-essential package and for that you need to be online.

---

### Post by Mornedhel on 2008-09-22
> **hyper_ch said:**
> you need to the build-essential package and for that you need to be online.

That and the kernel sources (from the kernel-source package).

However, both are also installable from the CD.

---

### Post by Chazbot on 2008-09-22
oh bother I put in a reply before I left home and it didn't take, I had to leave for class, I'll try those ideas tommorrow, thanks again for your quick responses!

---

### Post by Chazbot on 2008-09-22
A series of problems:

I didn't find anything with kernel in the title on the CD. A search through the package names on packages.ubuntu.com gave me a series of seventeen different ones, some for nvidia some for avm fritz honestly I couldn't make sense of it, which do I need? My mobo is an Asus with a pre-installed nvidia graphics card, but I use an ATI card to handle the graphics processing.

Secondly, the build-essential package... it hurts us, oh how it hurts us. I spent about an hour of fun with this one. I found it on the cd with very little digging but when I tried to run it it told me it needed... a package I can't remember right this minute. Oh yes it was libc6-dev and another one similarly named. So anyway I get those two and YAY another error message. This time it tells me that "Dependency is not satisfiable: g++". I mentally presume that 'not satisfiable' means 'update it, dummy' and so I go to the Ubuntu Packages site again and download g++_4.2.3-1ubuntu3_i386.deb. That one tells me that g++-4.2.3 is not satisfiable. So I download g++-4.2.3-2ubuntu7_i386.deb. This tells me libstdc++ is not satisfiable so I download libstdc++6.4.2-dev_4.2.3-2ubuntu7_i386.deb which... tells me g++-4.2 is unsatisfiable. I have two packages, each which tells me the other one is unsatisfiable and therefore will not install; catch 22. (I had a couple crashes in there, but I found one mirror that doesn't seem to cause the crash that started this whole mess).
It's then that the possibility that 'not satisfiable' does not necessarily mean either missing OR out of date finally penetrated my skull. So, I come back to you with what amounts to a large, emphatic, "**HUH?!**"

EDIT: Also, thanks for that RootSudo link, I understand it now! (and have actually cleared up an older problem on the laptop with the sudo command/modifier/whatever)

---

### Post by Mornedhel on 2008-09-23
Sorry about "kernel-source". It's linux-source, actually. I always make the same mistake...

Could you start Synaptic (from System > Administration > Synaptic Package Manager) ? Notice that several packages have an Ubuntu logo next to their name in the list. Those are the ones available from the CD.

There, in Settings > Repositories, you can tell it to use the CD for package installation. Just to be sure, deactivate the other normal repositories. Then you install the packages as you would normally do, by right-clicking them and marking them for installation, then clicking Apply once you've made your selection.

Since both build-essential and linux-source are marked as available on the CD, this means all their dependencies are as well (they will automatically be marked for installation if they aren't installed already).

---

### Post by Chazbot on 2008-09-23
Alright, I had some problems, long story short I took the desktop upstairs and plugged in directly, where I will leave it until I can resolve the issue. I installed the build-essential and linux-source packages, now what? Following the commands originally given, I would do:

./Configure 

Which would yield:
> 
-------------------- Ralink RT61 Station Configuration -------------------- 

  Linux kernel source directory [/usr/src/linux-2.6.24-19-generic]: 

Typing the next step, 'make' into this yields: "Linux source tree 'make' is incomplete or missing!" However, using it outside this Station Configuration tool does a whole bunch of things in rapid succession, most of which seem to be error messages like this:

> /home/chazbot/Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module/rtmp_data.c:656: warning: ISO C90 forbids mixed declarations and code


Sooo... what next?

UPDATE: I did sudo make install from the directory, and again, some things happened. I can post the log if you like, but I got no error messages. Is the driver installed then?

---

### Post by Mornedhel on 2008-09-23
First things first. Installing linux-source provides you with a .tar.bz2 archive of the Linux kernel source. In a terminal, go to /usr/src and type :

```
sudo tar xvjf linux-source-2.6.24.tar.bz2
```

You may need to alter the filename slightly to adjust for a different version. Enter your password when sudo prompts you to and watch as the archive is decompressed. Once this is done, you have enough material to answer the driver configuration question. Start the procedure again (go back to where Configure lives, execute it, etc.).

When it asks you where your kernel source is (because that's what    "Linux kernel source directory [/usr/src/linux-2.6.24-19-generic]:" means), enter the full location :

```
/usr/src/linux-source-2.6.24
```

From there, wait for the configuration utility to finish, answering further questions (if any) and writing down error messages (if any).

*Then*, when Configure has done everything and you're presented with a shell prompt again (you know, the someuser@somelocation:~$ prompt), proceed with make and make install.

---

### Post by Chazbot on 2008-09-23
alright, I THINK everything with that is correct but I'd like you to make sure, this is what the terminal looks like, I've bolded all the things I input for clarity

> -------------------- Ralink RT61 Station Configuration -------------------- 

  Linux kernel source directory [/usr/src/linux-2.6.24-19-generic]: **/usr/src/linux-source-2.6.24** 
 
  Linux kernel source directory : /usr/src/linux-source-2.6.24
 
  Module install directory : /lib/modules/2.6.24-19-generic/kernel/drivers/net
 
chazbot@chazbotscompy:~/Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ **make**
chazbot@chazbotscompy:~/Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ **sudo make install**
[sudo] password for chazbot: 
install -m 755 -o 0 -g 0 -d /lib/modules/2.6.24-19-generic/extra
install -m 644 -o 0 -g 0 rt61.o /lib/modules/2.6.24-19-generic/extra
Network device directory /etc/sysconfig/network-scripts
Module configuration file /etc/modules.conf 
grep: /etc/modules.conf: No such file or directory
append 'alias ra0 rt61' to /etc/modules.conf 
/sbin/depmod -a
chazbot@chazbotscompy:~/Desktop/2008_0723_RT61_Linux_STA_v1.1.2.2/Module$ 


---

### Post by Mornedhel on 2008-09-23
Make did not output anything ? Huh.

Well, reboot and cross your fingers now.

Whether it works or not, you can now say proudly you've installed something from source.

---

### Post by Chazbot on 2008-09-23
The crash still occurs. 
I'm either going to buy a cheap wireless card I know Ubuntu supports, or give up on it on my desktop and wait to get a new laptop. I'll be keeping it on my current laptop regardless.

---

### Post by Mornedhel on 2008-09-23
Well, at least we tried.

If you are looking for a wireless card, may I suggest the following link :

[http://www.ubuntuhcl.org/browse/search+wireless_networking?category=25](http://www.ubuntuhcl.org/browse/search+wireless_networking?category=25)

---


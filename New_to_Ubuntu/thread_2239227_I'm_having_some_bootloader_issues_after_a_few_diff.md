---
title: "I'm having some bootloader issues after a few different installs/uninstalls/installs"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by serowden on 2014-08-12
Forgive me, I am overly wordly... TLDR, Skip to !! TLDR !!

Just in case it's relevant to anything, the machine is quite a relic. I pulled it out of a garage and decided to see what I could do with it. It needed reformatting badly so I started over initially. 

It has an Intel Pentium 4 CPU at 1.80GHz. 256MB RAM 

At first, I had installed a server version of Ubuntu. I wanted to learn to host my own stuff. Well... somewhere into the process, I realized that learning Linux on a server isn't the best idea. I always planned to learn the command prompt, but I didn't expect to do it without some kind of GUI. I find learning easier when I have a console terminal or whatever in the GUI because it's not such culture shock, to be in a world full of new commands I don't know and new functioning OS I don't know... all on top of being a machine that serves my files to the Internet and ideally would be secure. 

So I put it back in the garage for a while until I found an old XP disc. The spark to learn Linux faded because I didn't feel like doing the problem solving/learning to get the server off and start over finding a new disto. 

I installed XP. Immediately had numerous problems. Couldn't connect to the Internet. Computer didn't know what Network Adapter it had. No drivers. None on the install disk. Almost nothing works. Computer can't open even the most basic Windows media files. Well,it took me a while to find out how to identify my adapter and get the proper drivers elsewhere, which then allowed me to start improving on the XP installs complete inability to be useful at all. Then I come to find, there is no way for me to get any Windows Updates. And we're not talkin, a really old XP that seriously needs to be updated for a few hours. And there's just no way to do it.

So then I start to get actually irritated with MS. Mind you, I have a much better machine running Windows 7, so it's not a big deal that I couldn't get XP very usable on an old POS. But just the principle got me thinking about the reasons I considered learning Linux in the first place.

So, I tried installing a newest version of Lubuntu and Xubuntu. I made CD-ROM boot disks. Both times, I couldn't get anywhere. THe loading screens just... didn't load. They tried.But they just spent unholy amounts of time at loading screens. Being that these were considered lightweight distros, I started to feel discouraged about Linux again, mostly because I am not ready to repartition, format, or install any new OS on my primary PC. This is mostly because I use it to play game and have a large amount of stuff on the HD I don't honestly have the backup space anywhere to mess with that. That's why I'm doing all this experimenting on the old machine.

Sooooooo, that's when I found Puppy Wary 5.5. I successfully did a full install replacing XP. This was my first real taste of Linux.

Shortly after, I decided to try installing differently. I put XP back on it, then I used the Puppy Wary boot disk's partition editing tools. I had one partition for the whole hard drive at the time. I shrunk it to be a partition big enough to hold windows itself, FAT32; also a partition big enough for Puppy Wary, file system the one that ends with a 2 that I can't remember tbe exact name of. I made a third "swap" partition as big as my RAM, mostly because the Puppy documenation said to. I still don't know why I have it or what it does, but whatever for now. Then I basically made a fourth FAT32 partition with all the remaining space.

Everything worked except the bootloader program setup on Puppy called Grub2 or whatever it is. I opened it, tried to use it, but it jut didn't work. No matter what command, from install to help, in the Grub installation, just did nothing but seemingly refresh the program as if it closed and restarted again instantly. Luckily, it had an alternative bootloader program called GRUBDOS or something similar to that. I'll say this, as an aside, many Linux utilities and software I've seen are not named with the general quality of names in mind i'll forget their names easily if I don't use them often ha.

So I got this other bootloader to work somehow. It basically just did it for me and installed the thing where it wanted to and updated the file that needs to be updated for me/ The documentation I had didn't cover this GRUBDOS so I just resigned to accept that it somehow worked and that I wasn't going to get to learn about this Grub2 or how to set up my bootloader.

So it was a success... Until... I really found that as I tried to use Puppy more and more,  it seemed very limited and not equipped with the most basic things that Linux should have on it that it just didn't -- and the process for getting it was beyond my level of following it. so I started to feel like I was using the long distro. To me, Puppy felt like a gimmick of what Linux needed to be.

Case in point, I had started using Puppy to learn bash and the cli -- basic stuff, like navigating files. After that, I started trying to learn C. But, I couldn't compile any of my source code. The Puppy Package Installer didn't have any compilers to be found. It didn't have GCC, which is apparently a most fundamentally basic Linux program. There was a long list of dependencies of the GNU website listed I had no idea how to get to make the OS supprt me using it to program (or try to). No simple download page at gcc.gnu.org, but rather a whole day's work of learning how to install everything a computer would need to at least begin to be able to think about doing anything in C.

So then, without touching my FAT32 file system partitions or my SWAP, I used the Lubuntu 11.10 install disk to format my Puppy Linux Partition and install Lubuntu there. To my joy, I found this version (while not fast by any means) was workable on the machine. I actually managed to succesfully install it...

UNTIL...

It got to the part in the install process where it tried to use the same grub2 thing to se up the bootloader. It faiils. Computer crashes. I eventually have to restart. I suspect Lubuntu is installed with no way to load it from my old boot meu. THe options to select Wary and XP are still there. Of course, only the XP one works.

!! TLDR !!

What can I try to add Lubuntu to my current bootloader? And why does grub2 seem to be the bane of this machine from across two completely different distros.

Thank you for reading my background story. I decided to be thorough. Maybe more thorough than necessary? If you have any suggestions or tips from what I've said on any subject (but particilarly the last bit), I'd be honored.

---

### Post by mörgæs on 2014-08-12
The only part I read was 256 MB ram. Before going further into the project I recommend upgrading to 512 (or even better, 1 GB).

---

### Post by serowden on 2014-08-12
You're probably right. Using the computer to do anything sucks. Puppy Wary 5.5 ran acceptably for what I wanted to do with it... which is just learn about Linux. I know RAM is cheap. I know I would benefit hugely from doing so. But plenty of documenation says it can be done with less RAM, which is the point of using this particular distro isn't it?

Anyway.

I tried Grub2 for Windows. Got an error AddFileToArray input file open error at C:\Grub2\winsource\starter.theme.cfg, then at template.windows.auto.cnf, then just grub.cfg, and ultimately install of Grun2 fails. 

Even if I did buy more RAM, I still wouldn't know how to even get the bootloader I need to install itself and run, on three different operating systems it seems.

I'd edit GRUB4DOS if I knew where its information was, and what information I Would use to summon Lubuntu... if it even completed installing with the Grub2 interruption.

---

### Post by fireflower on 2014-08-19
Adding more RAM might not even work. Any RAM this user buys will have modern speeds and modern timings. Remember that computer speed is limited by the speed of the slowest part; that legacy CPU and legacy motherboard will hold the new RAM back, like a rocket engine pushing a city bus. Even then, combining fast and slow parts may cause new problems. What if the RAM and CPU can't even talk to one another?

Even Lubuntu, which is targeted at resurrecting old computers, does have minimum specifications for a **graphical** install: 800 MB RAM. Since this user has a fraction of that, we can't be surprised they're having problems. There is an **alternate** install, but that requires 400 MB RAM. And then there is the **minimum** install, that requires 128 MB RAM. This user should try the [minimum install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall"). It is unfortunately a bit more involved, but thems the breaks.

---


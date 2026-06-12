---
title: "how to get `this' ideal setup?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by geekyhawkes on 2011-10-09
Hey guys, I'm thinking of starting over on my old mythbuntu machine and want to achieve the following:

Dual boot windows xp / Ubuntu with xfce installed (sorry don't like unity but am so used to all the gnome tools that I want them avail in xfce).
I have an Asus m3-78em motherboard that has nvidia raid support but I'm not sure if I should go hardware raid or use software in Linux?

Hard drive wise I have 2x250gb data hdd that I want to use in raid 1 ( I think, I'm not sure I would see much extra sped for raid 0 so thought why not have the backup?), I also have  500gb hdd that I'm using as my 'data drive so don't want that in raid just available through fstab.

The motherboard supports dual monitors (1 dvi and 1vga), will Ubuntu just pick that up? 

So what I I getting at s what order should I do things? Is the idea of dual boot raid just too difficult? Is hardware raid the easier way to get what I want between x and Ubuntu?

Thanks for any help.

Andy

---

### Post by geekyhawkes on 2011-10-10
Can no one at least give me an order to try and set the up? Or a steer on the raid for dual boot?

---

### Post by Frogs Hair on 2011-10-10
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by anewguy on 2011-10-10
If the information pointed to by Frogs Hair in their post above doesn't provide what you need, please keep this in mind:

Forum rules dictate no bumping of your thread until at least 24 hours after the last post someone made.  What this means is that 14 hours after your opening post your posted again asking if anyone was going to help you - that is bumping - moving your thread to the top of the queue.

If you have done additional troubleshooting or investigation and have more information to share, then the above doesn't normally apply.

Combining the bump with the text "Can no one at least give me...." really comes across as rude, like in "come on!".

Not trying to knock you down, so please don't interpret it that way.  Just wanted you aware of the forum rules, and that sometimes innocent wording may come across very different from how it might have been intended.

Simple adherence to the forum rules and perhaps a slightly different phrasing may get you more information when you post.

Also, a lot of times people aren't aware that Google/Yahoo!/Bing, etc., can be your best friend in a lot of these cases.  You may want to try a net search with:

ubuntu <your version number here> installing raid

and see what pops up.

Best of luck - I've always wanted to try raid myself in Ubuntu but just haven't gotten around to it yet.  I'll be watching this thread to see how you do so be sure to keep us updated!

Dave ;)

---

### Post by geekyhawkes on 2011-10-10
Sorry for the bump, all valid. I've read the how to for software raid, I guess my question is how will this work with 2 o/s? Surly winxp won't see the raid setup in Linux, that's what pushed me to thinking with careful config I could be using raid on both wins and the Ubuntu setup, or is that just too ambisious?

And thinking about it a bit more, I guess I cold use software raid, create a decent size partition in raid 1 with xp and Ubuntu running on it, hence giving me some redundancy in the system partitions.  The rest of the space on the drives could then be software raid 0 for Ubuntu use / software installation. 

Not the most efficient use of the space really, but I only keep xp as I need it for the odd firmware flash on my nas / smart one / xbox DVD drive etc so it can live with a pretty small partition. 

Hdd wise I have 2 x 250gb drives so I hows the follwing sound:

1x50gb partition, bootable with xp installed first then Ubuntu installed after ( thinking its the easiest way to get grub working with both).
In the Ubuntu install set up the raid 1 partition then on the second drive of 50gb hoping Ubuntu will just mirror the xp settings as and when.

Allocate the remaining 200gb on each drive shared with some swap and some ext4 in raid0 for performance then set these partitions as a decent Mont point for software installs (/etc/dev? Suggestions welcome for this please). 

Does this sound sensible way of doing things? I don't mind trouble shooting, just prefer to get most of the issues out of the way in advance if I can. I'm thinking Ubuntu 11.10 as the baseline with xfce installed after.

---

### Post by thatguruguy on 2011-10-10
Why install ubuntu first, and then xfce?  Why not just install [Xubuntu]("http://www.xubuntu.org/")?

---

### Post by anewguy on 2011-10-10
If you have the CPU and memory to support it, maybe you'd be better off backing up all of your Windows data, etc., and be sure you have or have created the Windows restore disk(s) for your PC, then blowing away everything and starting with Ubuntu only, getting raid working as you want, then running Windows in a virtual machine in Ubuntu.  In this way there would be no confusion.  I really rather doubt you can set raid in both OS's to the same set of disks.

Dave ;)

---

### Post by TigerNutte on 2011-10-10
> **geekyhawkes said:**
> Can no one at least give me an order to try and set the up? Or a steer on the raid for dual boot?

I don't know mate, I've made the mistake of installing Ubuntu on Dual boot with windows 7 64 bit & having a nightmare trying to get my now defunct DVD drive to work. Have spent 2 months searching & researching how to fix this issue. Am on an Asus M51Vr & the DVD multi-drive worked beautifully until I ran the newly installed Ubuntu Natty. I have since learned from 2 months of research that I needed to install cdrom using terminal. I don't mind using terminal, actually I enjoy working within the system.....IF I know what I'm doing. Unfortunately am only new to the new whole world of using terminal & anything I try doesn't work. There doesn't seem to be much help with installing an already present "cdrom" drive. I installed it into a slim external USB case & attached it to the Mac I have & it worked so in essence WTF Ubuntu? Now I just want to have my "cdrom" drive working & go back to crap Windows as it's easier to work with!

So my suggestion is Stick with windows or go mac until there's more support for Linux

---

### Post by thatguruguy on 2011-10-10
> **TigerNutte said:**
> I don't know mate, I've made the mistake of installing Ubuntu on Dual boot with windows 7 64 bit & having a nightmare trying to get my now defunct DVD drive to work. Have spent 2 months searching & researching how to fix this issue. Am on an Asus M51Vr & the DVD multi-drive worked beautifully until I ran the newly installed Ubuntu Natty. I have since learned from 2 months of research that I needed to install cdrom using terminal. I don't mind using terminal, actually I enjoy working within the system.....IF I know what I'm doing. Unfortunately am only new to the new whole world of using terminal & anything I try doesn't work. There doesn't seem to be much help with installing an already present "cdrom" drive. I installed it into a slim external USB case & attached it to the Mac I have & it worked so in essence WTF Ubuntu? Now I just want to have my "cdrom" drive working & go back to crap Windows as it's easier to work with!

So my suggestion is Stick with windows or go mac until there's more support for Linux

Two months of research, and yet you didn't ask a single question here.

---

### Post by anewguy on 2011-10-11
And......such things as "WTF" are not allowed on the forum.  Refrain from any future usage.

---

### Post by geekyhawkes on 2011-10-11
I have tried VM winxp and its fine but I as I mostly use xp for flashing/firmware type stuff I haven't had much success with vmware flashing hence why I want both os.  

One thing that me recently is that I have 2x250gb drives and a 500gb so could I stripe across te 250gb drives for speed then raid  1 to backup the stripe onto the 500gb? If I took this route clearly I would need to use Ubuntu software raid as the drives are all different sizes so make use of a partition by partition solution. I guess that way I can just keep a bit of space  on the smaller drives for winxp as described above?

I'm sure I have everything I need just not sure about the easiest wsy to dual boot and keep some raid, I have read around a fair bit and it seems easiest to install Ubuntu over xp to get it working?

Reason I want Ubuntu with xfce is that I like the gnome tools like gedit etc but don't like unity, true I could install all the tools I like in xfce but I was just being lazy thinking these would be added for me with an Ubuntu install.

---

### Post by Lisiano on 2011-10-11
Won't making a Raid-0 on (Let's call them sda (250), sdb (250) and sdc (500)) sda1 and sdb1 then making a Raid-1 on md0 and sdc1 limit your performance to the speed of sdc? You lose the speed gain of Raid-0 if you do it that way since Raid-1 performance is limited by the slowest member of the Raid. Instead maybe make a Raid-0 on sda1, sdb1, sdc1, then install XP to sdc2, swap to sdc3? Or a Raid-5.
Just my &#8364;0.02.

---

### Post by anewguy on 2011-10-11
As previously mentioned, I doubt very much you can have raid on a set of disks in Ubuntu and then dual-boot to use Windows, especially since you're talking about a striped set.  You mention that what you have read has said to put Ubuntu over Windows - I read that as no Windows - just Ubuntu, but I could be wrong.  I really think you are looking for a BIG headache trying to do this with dual-boot.

If you are using Windows for flashing and for firmware development, have you looked to see if there are any tools in Linux for doing this?  With Unix/Linux's background, I would think there would already be engineering tools like that available.

Just curious!

Dave ;)

---

### Post by oldsoundguy on 2011-10-11
OP, you did not mention the usage intent of your Myth machine.  IF this is to be a PVR, forget using Windows.  That will just mess things up big time.  Not sure if this will work in Xbuntu, but I installed Ubuntu and then went the repository route to install Myth in order to have the utilities available from Ubuntu itself (printing being the major utility .. and easier wireless networking).  The documentation on same is all over the web, so there is help to be had in setting up.  No need for a raid setup when you do it that way.  I have a 40 GB hard drive for all the control software and a  1 TB to hold the recordings.

---

### Post by thatguruguy on 2011-10-11
Why not just install [Mythbuntu]("http://www.mythbuntu.org/")?

---

### Post by geekyhawkes on 2011-10-11
Sorry I should have been clearer, I'm binning mythbuntu, sad but true but after 2years I have found that I can get most of the functions I used from myth from just my hacked ps3 and multi an/showtime. 

As far as looking to Ubuntu / Linux for the flashimg / random bits of windows I use I have looked and often failed. I can flash my tablet and android phone from Linux but Xbox DVD drive flashing and buffalo nas  upgrading is/ just too frustrating and not effective from Linux, I know it sounds bad but somvicethings just work with windows as the tools are out there and easy, I love Linux and open source but I also love simpole effective solutions and sometimes that is via windows. 


So I guess I am getting towards my solution ish. 

I want to have a simple dual boot option, so don't need raid in windows, that was just too difficult for very little in the way of rewards. 


I do want raid in Ubuntu, and I think I want the performance gain of stripping and/ figure why not use the 500gb drive to copy the stripe in case of hdd failure? 

I guess the questions I have left are: 

Is this all worth the hassle?

Should I just call it a day and stripe between a 250gb ubutu install and then keep a seperate hdd for the windows xp install? Just feels like a bit of a hack not dual booting and swapping the drive in and out, but it is simple and works

Thanks for all the help guys, this is a bit of leap into the dark for me.

Also, how much swap should I allocate, my machine has a 64bit and at 2.8ghz and 2gb or ram so I was thinking 4gb of swap would be plenty right?

---

### Post by geekyhawkes on 2011-10-11
Also, this guide [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

Suggests that my boot space shouldn't be in raid, doesn't mean I will see performance drop?


I'm thinking after all the help: 

Sda - 250gb sda1 Ubuntu in raid 5
Sda2 swap not raid

Sdb - 250gb sdb1 Ubuntu in raid 5
Sdb2 swap not raid

Sdc - 500gb sdc1 Ubuntu in raid 5
Sdc2 winxp not in raid
Sdc3 swap not in raid. 

Just the answer over boot space in raid or not and then what size swap should I allocate, also I guess I should partition it all up in Ubuntu then get windows up an running after and deal with the grub issues if it isn't easy? Should I have the winxp partition as fat32 or ntfs? I'm guessing the Linux partitions would be best in ext4?

---

### Post by Lisiano on 2011-10-12
Good setup this time. But I would like to ask why 3 swaps? 1 should be plenty but it's your decision. IMHO you should set it around the same amount as you have RAM (Due to hibernating to swap), 2x if you don't have a lot (Less than a gig) and you can ignore it if you have way more than 4gb (Unless you wish to hibernate).
As for /boot. Currently I have 4 kernerls, a 2.7mb background, grub 2, memtest86+ and grub invaders, totaling just a bit over 100mb. A gig would be enough even if you decide to never ever clean it out. (Unless you somehow get 40 kernels that is). Also it MUST be on it's own partition if you Raid the root or encrypt it. Grub is not aware of the existence of a Raid, much like encrypted partitions.

---

### Post by geekyhawkes on 2011-10-13
No need for 3 swaps then, I was just trying to keep the drive layouts the same, my ocd kicking in. I guess I could make the area I had allocated for swap on sda to use as a boot partition, as you said a gb should be enough.

---


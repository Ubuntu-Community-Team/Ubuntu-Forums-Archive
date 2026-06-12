---
title: "Manual Partition vs Auto Partition"
date: 2010-01-17
forum: Recurring Discussions
---

### Post by Rytron on 2010-01-17
Hi.
Do you do a manual partitioning during an Ubuntu install or do you let Ubuntu do the partitions automatically?

---

### Post by mick222 on 2010-01-17
always manual partition as i like a seperate home partition

---

### Post by earthpigg on 2010-01-17
one thing that causes a lot of people grief is that there is no automatic partition.

there is guided partition, but people think automatic, and miss the part where they move the slider over to make the partition larger than 2.5gb.

---

### Post by lidex on 2010-01-17
Manual

---

### Post by sisco311 on 2010-01-17
> **Rytron said:**
> Hi.
Do you do a manual partitioning during an Ubuntu install or do you let Ubuntu do the partitions automatically?

Manual partitioning _before_ an Ubuntu install. 

I use debootstrap to install Ubuntu from Arch and pacman to install Arch from Ubuntu.

---

### Post by raymondh on 2010-01-17
Manual ... and before installing (as well)

---

### Post by Sef on 2010-01-18
Moved to Community Cafe.

---

### Post by Marvin666 on 2010-01-18
Manually.
I've never let an installer actually do any partitioning.

---

### Post by SmittyJensen on 2010-01-18
automatic -- guided/use entire disk.

---

### Post by user1397 on 2010-01-18
Manually 99% of the time (mostly because I'm either dual-booting and/or making a separate /home partition.

That's not to say that I 'prefer' one method or the other, they each have their purpose.

---

### Post by Eisenwinter on 2010-01-18
I do it manually, I prefer to set up the partitions exactly how I want them.

For example, right now I have a boot, a root, and a home.

I also don't have a swap partition, since I don't use many "big" programs.

---

### Post by The Toxic Mite on 2010-01-18
I partition manually because I like to have a separate /home partition.

---

### Post by perspectoff on 2010-01-18
I run a multi-boot system (Windows 7, Debian, Ubuntu, Kubuntu), so have a partition for each.

I also keep one partition for virtual image tools, another partition for groupware, and another for a technical program that I don't want any OS stuffing up. Oh yeah, and a boot partition.

There is no way I would trust an "automatic" partitioner.

Always manual.

I use the tips at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by Icehuck on 2010-01-18
FDISK or CFDISK only. 

The Ubuntu install with GParted is just dumb. It always suggests partitioning schemes that wack other partitions(e.g. I have 40 gb free space but it wants to wack windows!). At least when I install Opensuse, it realizes I have other operating systems installed and doesn't screw with those partitions.

---

### Post by The Toxic Mite on 2010-01-18
> **Icehuck said:**
> FDISK or CFDISK only. 

The Ubuntu install with GParted is just dumb. It always suggests partitioning schemes that wack other partitions(e.g. I have 40 gb free space but it wants to wack windows!). At least when I install Opensuse, it realizes I have other operating systems installed and doesn't screw with those partitions.

You _can_ keep the Windows partition using GParted ;)

---

### Post by fromthehill on 2010-01-18
always manually
you never know when ubuntu decides you only need 4GB empty space on your vista partition:)

---

### Post by malspa on 2010-01-18
always manually, always before installing

---

### Post by Rytron on 2010-01-18
> **The Toxic Mite said:**
> I partition manually because I like to have a separate /home partition.

Hi. So when you install the next new version of Ubuntu, is your home directory left untouched? Do you simply install the next Ubuntu OS and not have to copy all your files back onto your PC from an external drive (or other media)?

---

### Post by The Toxic Mite on 2010-01-18
> **Rytron said:**
> Hi. So when you install the next new version of Ubuntu, is your home directory left untouched? Do you simply install the next Ubuntu OS and not have to copy all your files back onto your PC from an external drive (or other media)?

I don't leave it untouched, because (I fear) the installer might not be able to pick up the /home directory, and thus I would probably need to create a new user.

---

### Post by Xbehave on 2010-01-18
Manual because I spend time designing my HDD layout preinstall, if you don't then guided is probably more useful.

---

### Post by mick222 on 2010-01-18
>  I would probably need to create a new user.

I usually create a new user as by the time i get round to upgrading my home folder has a lot of crap i want rid of.Also when i first tried to use a seperate home folder i used the same username for suse and ubuntu ,that was a real disaster.

---

### Post by Icehuck on 2010-01-18
> **The Toxic Mite said:**
> You _can_ keep the Windows partition using GParted ;)

Yep, but you have specify your partitions manually. Other partitioners actually looks and makes a suggestion based on what's already there.

---

### Post by Rytron on 2010-05-29
Although I selected '*Auto Partition for my main PC*.' & '*Auto Partitions for all of my computers.*' when I made this thread. I have finally decided that manual partitioning is the best way. Both my Desktop & Laptop are now manually partitioned.

:P

---

### Post by libssd on 2010-05-29
Manual, primarily because it lets me set the swap size (default swap is too big for a 1gb netbook).

---

### Post by Penguin Guy on 2010-05-29
I always manually partition using GParted - I like to have all my partitions exactly the way a want them. FYI, I have one partition per OS and a separate one containing all my files.

---

### Post by Rytron on 2010-05-29
> **Penguin Guy said:**
> I always manually partition using GParted - I like to have all my partitions exactly the way a want them. FYI, I have one partition per OS and a separate one containing all my files.

Cool. So you can access your files from each OS?

---

### Post by NMFTM on 2010-05-29
Every time I re-partition my computer I manually resize my partitions. And every time I come closer and closer to having the perfect setup.

---

### Post by SinkingRocket on 2012-08-12
on my new wi7 pc i find it hard to manually partition cuz i have so many drivers paths from since i bought it.. so i just went and created a 20GB free partition and in ubuntu installer i couldnt bother to do it manually n just clicked on "run it alongside win" n let it partition that 20GB to whats best lol... in my previous laptop which had vista it was straight forward only two driver paths n i was able to partition manually without being confused.. its been a long time since i got back to using ubuntu n i forgot how and what fits best in how much to partition so having a "guided"/auto partition is indeed handy for new users n others,,,like me hihi

---

### Post by sffvba[e0rt on 2012-08-12
[IMG]http://i299.photobucket.com/albums/mm313/Zenzirouj/ThreadNecro.gif[/IMG]


404

---


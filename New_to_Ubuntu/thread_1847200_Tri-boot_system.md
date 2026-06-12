---
title: "Tri-boot system"
date: 2011-09-20
forum: New to Ubuntu
---

### Post by Moofu on 2011-09-20
I started using Ubuntu about a year ago by dual booting 10.10 with Windows 7 starter on my netbook. I'm just starting to build my own computer and recently acquired a 750GB HDD. I'm wanting to build a media computer so I can use my netbook purely for school. I want to be able to use it to rip DVDs for playback on both this PC and my netbook. This is the idea I had:

1 partition for Ubuntu 11.04
1 partition for Fedora (just to try it out, I might continually swap it out with other distros for testing)
1 partition for XBMC
1 partition for /home

I remember reading somewhere a while ago that you can only have 4 primary partitions. I think that might have just been with windows though, can't really remember. I've never used XBMC either, so will this setup work? Also I realize there is no swap partition here, if the 4 partition thing holds true do I need to kill the Fedora one so that I can create swap?

Is this setup at all plausible?

---

### Post by egalvan on 2011-09-20
Your layout WILL work, but it is restrictive.

Yes, a max of four PRIMARY partitions are allowed.

But a slightly better method is making one partition an EXTENDED partition.

An extended partition can contain from one to 256 (I think) LOGICAL partitions.

Change that last partition to an Extended one,
then inside it make your swap and home partitions.
You can also make partitions to install test distros to.

you can even have multiple /home partitions, one for each of your distros..
just give them different labels...
for example,

home-xbmc
home-ubuntu
home-testing

(actually, you don't HAVE to have different labels, it just makes it MUCH easier for humans to keep track of which /home belongs to which distro.
the distro just knows that its using a certain partition, which is mounted at a specific location on the / tree)


me, myself and I, personally, I ALWAYS make three primary and one extended partition on any boot drive...
I ALWAYS leave the first partition empty in case MS-Windows needs to be installed, I make the second a Linux swap, and the third I make NTFS-formatted to allow easy transport between Linux and MS.

---

### Post by Moofu on 2011-09-20
Thanks! That helps A LOT. What is the difference between a primary, extended, and logical partition though? I've tried reading up on it, but it hasn't made very much sense to me. Also what is the logic between having a /home partition for each distro? Isn't the point to be able to access the same data between all of them? Well that and backup in case something happens to the OS.

Still relatively new at this so I wanna make sure I'm not getting my concepts mixed up.

---

### Post by srs5694 on 2011-09-20
> **Moofu said:**
> Thanks! That helps A LOT. What is the difference between a primary, extended, and logical partition though?

The original partitioning scheme for PCs supported just four partitions. This quickly became limiting, so somebody came up with a hack: Use one of those four *primary* partitions as a placeholder for what is essentially a second partitioning scheme that doesn't have this 4-partition limit. The "special" type of primary partition became known as an *extended* partition, and the partitions it holds are called *logical* partitions.

This system is ugly and it causes a lot of confusion and grief, but it works, and long-time users of computers have long since learned all the ins and outs of this system. Thus, it's remained in place for 30 years. As a side note, this system is doomed because of unrelated limits, but its replacement, known as the GUID Partition Table (GPT), is not yet common except on Macs.

> I've tried reading up on it, but it hasn't made very much sense to me. Also what is the logic between having a /home partition for each distro? Isn't the point to be able to access the same data between all of them? Well that and backup in case something happens to the OS.

There are many reasons to create a separate /home partition, even on a computer with just one distribution installed. Creating a separate /home partition for each distribution would keep user data files separate for the different distributions. That could be either a plus and a minus, depending on your needs. I expect in most cases it would be a minus; however, you should be aware that most people recommend not using the same user home directory for more than one distribution. The reason is that program configuration files may have different formats or refer to different system files on the different distributions, so using one distribution's configuration file in a different distribution can result in weird problems.

There's a critical distinction between the /home directory or partition and the user home directory, though. The latter is a subdirectory of the former, as in /home/moofu if your username is moofu. If you share a /home partition across distributions, you should ensure that you use different home directories -- say, /home/moofu-u and /home/moofu-f for Ubuntu and Fedora, respectively. This is most easily accomplished by using different usernames in each distribution; however, it's also possible to set up a user home directory that has a name that's unrelated to your username. Some distributions make this easier than others. Unfortunately, Ubuntu's one that makes it harder to set this up.

---


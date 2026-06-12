---
title: "No way forward, no way back."
date: 2008-06-08
forum: New to Ubuntu
---

### Post by collapsing wave on 2008-06-08
downloaded hardy heron
 tried to install, it crashed to 
 udevd-event [1557] : run program: '/sbin/modprobe' abnormal exit and stumbled upon the forum at
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/225749)

disabled the Lan, in the bios setup, (which was pretty good considering i didn't know what a bios was 24 hours ago-not a joke)
got the screen up and running. 
However I figure I have bitten off way more than I can chew and need to approach this with just a little more background reading.

I managed to partition the HDD to squeeze vista out and now I have no space in windows to work, a vast amount of space with Ubuntu, but running only from the install disk with the Lan disabled.

I found the post about uninstalling at
[http://ubuntuforums.org/showthread.php?t=113630&highlight=ubuntu+uninstall](http://ubuntuforums.org/showthread.php?t=113630&highlight=ubuntu+uninstall)
but cant get it to work after spending hours trying to figure out how to get an .iso onto a disk and figuring out how to get the CDrom to run before the HDD (still not joking, i assure you)
the CD rom refuses to boot and windows starts. I even bought a flash drive to try to get that to boot thinking I'd finally got clever but all I get is

no bootable partition in table

so if some kind soul will tell me how to access the bug fix at #225749. so I can get into ubuntu without using the install disc and with the Lan intact, or can tell me how to kill it so that I can go back to windows for a regroup, more sensible partition sizes, and about a month of figuring out what all this stuff is about. I have bitten off more than I can chew and am choking!:(

THe laptop is a brand spanking Toshiba L300 satellite pro, celerion 550@2.00GHz, 1 gig RAM, 120 gig HDD. with no data to loose.

Send lawyers, guns and money. Please!

---

### Post by collapsing wave on 2008-06-08
any body, some body?

---

### Post by philinux on 2008-06-08
With windows loaded can you browse the cd and see whats on it?

---

### Post by ugm6hr on 2008-06-08
> the CD rom refuses to boot and windows starts.

This doesn't make sense.  How did you try to "install" Ubuntu if you can't boot from a CD?  Did you use Wubi?  If so - the rest of this doesn't apply.  Try asking in the Wubi subforum.

If not:

Can still get into Vista?  If so - you can resize partitions from within Vista.

For safety - install EasyBCD first (google it) within Vista.

Then boot into the Ubuntu LiveCD (as you have been doing) - and go into GParted (Partition Editor) to delete the Ubuntu partitions.

Then back into Vista to resize the Vista partition.

As for installing Ubuntu - why not try the AlternateCD?

---

### Post by collapsing wave on 2008-06-08
philinux- the CD was a .iso file from the unpacked program found on the link 
[http://ubuntuforums.org/showthread.p...untu+uninstall](http://ubuntuforums.org/showthread.p...untu+uninstall)

ugm6hr- I think i wasn't so clear that it was not the ubuntu install CD i was having trouble with. my apologies.
have followed the instructions, thankyou, but now can't get vista to do its thing. 
1 have 6 chunks the HDD is cut into
but it won't let me expant the vista partition into the grrn froo space. do I just delete the green free space partition. if you don't know or don't care then i'll go hunt the answer down on the vista forums. 
However i now have ubuntu installed but it will only load off the install disk with the LAN disabled as a workaround. What do i need to do where, to get the update for the package
2.6.24-18.32ubuntu6
I can see there is a fix I just don't understand what it is, and what to do with it when i get it...

---

### Post by philinux on 2008-06-08
How are you manageing to post here are you on another machine?

---

### Post by collapsing wave on 2008-06-08
yep
one laptop, one desktop, one annoyed girlfriend, one too many coffees!

---

### Post by ikarus2k on 2008-06-08
Let me see if I understood this correctly:

1. You can boot into Vista, but have very little space
2. You can boot into Ubuntu, but only with LAN disabled
3. Your HDD is in 6 "chunks", so I assume 1 Vista (NTFS) partition, 3 Ubuntu partitions and unallocated space between them

You want to:

1. Enlarge the Vista partition to encompass some of the free space, that's no problem
2. Update Ubuntu to support LAN

Did I get it right? I am not very sure what you want to do :(

Edit:
If you can boot into Vista, I would do the following, it's the easiest:
- delete all non-NTFS partitions (this will remove Ubuntu), partition according to your windows needs, but leave at least 10GB at the end of the drive for Ubuntu.
- if your PC doesn't boot from the CD (anymore), go into BIOS and it should be the second option there (something like Advanced ...; depends on your BIOS, so specify that here)
- when you install Ubuntu and it asks for partition info, just tell it to use the unallocated space.
- DONE

---

### Post by sdowney717 on 2008-06-08
since you can boot into Vista, I would start over.
Boot Vista
Delete the partitions assigned to linux
Expand Vista so it is useful again.
Reinstall linux using 1/3 the space you used before, perhaps even trying fedora or another alternate distro just to see if it works.

look at [www.distrowatch.org](www.distrowatch.org)
Have fun with this dont sweat it too much.
You can setup a multi boot system using vista ubuntu fedora etc...

---

### Post by collapsing wave on 2008-06-08
that is spot on ikarus2k, 
the update is there. i think it has something to do with this 

[FONT="Garamond"][For everybody bitten by this bug: Could you please go into BIOS setting, try to disable your LAN (Ethernet controller), and see if Ubuntu 8.04 Live CD would boot?

There is a bug in r8169.ko module in Linux kernel 2.6.24 which causes a Kernel Oops when it sees new not-yet-unrecognized Ethernet controller. r8169 in 2.6.24 recognizes RTL8101E, but not RTL8102E. That "Oops" causes some memory corruption or whatnot, and the system fails to boot.[/FONT]
that i got from here- [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/225749](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/225749)

but to be honest i could be barking up the wrong tree entirely...

---

### Post by sdowney717 on 2008-06-08
When reading thru it looks as if that bug is now closed and fixed. 
If true, then redownloading the install should have the fixed kernel.

---

### Post by ugm6hr on 2008-06-08
> **collapsing wave said:**
> ugm6hr- I think i wasn't so clear that it was not the ubuntu install CD i was having trouble with. my apologies.
have followed the instructions, thankyou, but now can't get vista to do its thing. 
1 have 6 chunks the HDD is cut into
but it won't let me expant the vista partition into the grrn froo space. do I just delete the green free space partition. if you don't know or don't care then i'll go hunt the answer down on the vista forums. 
However i now have ubuntu installed but it will only load off the install disk with the LAN disabled as a workaround. What do i need to do where, to get the update for the package

I am still confused about what you are trying to do and what you have done.

It sounds like you have not installed Ubuntu properly.  As for why - there are a number of reasons.  There is no good explanation why switching LAN off will boot from LiveCD but not installed Ubuntu.

I would still suggest:
Install EasyBCD
Delete Ubuntu partitions from Ubuntu LiveCD
Increase Vista partition size from Vista (perhaps leaving about 10-15GB "unallocated / free space" for re-trying Ubuntu).

If you do this **in this order**, and the problem is with Vista's partitioning tool, then I can't help.

I would suggest trying to clarify exactly how you "installed" Ubuntu though - since Wubi vs LiveCD require very different uninstall procedures.

---

### Post by collapsing wave on 2008-06-08
ok
I followed these instructions that you gave me

1. For safety - install EasyBCD first (google it) within Vista.

2. Then boot into the Ubuntu LiveCD (as you have been doing) - and go into GParted (Partition Editor) to delete the Ubuntu partitions.

3. Then back into Vista to resize the Vista partition.

the problem was with 3 it wouldn't let me resize it. staying as free space. If I boot with the lan enabled i get the error message i gave in my first post.

(BTW i started this process on a new laptop with a new download disk 7pm my time 30 hours ago so there should be no dodgy data anywhere. hopefully )

this is where i'm at. Ill try to load ubuntu again and get back to it tomorrow. thankyou to anyone that helped.

---

### Post by ugm6hr on 2008-06-08
> the problem was with 3 it wouldn't let me resize it. staying as free space

I have only used Vista's partitioner once (before I wiped it), so I'm afraid I don't know exactly how it works.  But if it doesn't expand a partition to fill free space, it's pretty useless.

Does it allow you to at least create new partitions in the free space?

How did you shrink Vista in the first place?  I have heard that GParted can misbehave with Vista partitions, but not sure if that still applies with Hardy.

---

### Post by sdowney717 on 2008-06-08
with vista you can create and delete partitions and shrink and resize ntfs partitions. And you can delete non windows partitions.

---

### Post by collapsing wave on 2008-06-17
Still struggling with the install, one week on... 

downloaded alternate CD and checked it, then chose install from the menu. Worked my way through it ok until i got to install network and it wouln't let me, then at software it wouldn't let me, either. Something to bo with the ntwook settings I gather. so i went on to installing the grub menu and completed the install.
Reboot
hold breath
 and get 
ALERT! /dev/disk/by-uuid/553cfead-c9ad-4880-af83-8cfacf62c10d does not exist. Dropping to a shell!

Please help.

---

### Post by collapsing wave on 2008-06-17
Why won't it go?

---

### Post by athianos on 2008-08-02
You've experienced some similar issues to me. I've found the following helpful.

I've found that choosing a slow burning option when burning the live cd/ installation cd really helps. Check the cd for errors too. It could save you hours of frustration. 

I've had no need to install network at the installation stage. Just choose not to install network at this time, then proceed with the installation.

After your install, use a wired connection and Ubuntu will be able to connect to the internet so that you can install the applications you need to get your wireless working. As far as I understand, installing the network in the installation stage is so that you can connect with other computers on your home or office network, rather than the internet.

If successful, install network manager through applications>add/remove in your main menu and search for network manager. 

You can also use your terminal (found in applications in the main menu)

use the following commands.

sudo apt-get install "name of program"

ALSO:
Try installing hostapd

[This link]("http://ubuntuforums.org/showthread.php?t=75017") will tell you how and why. "

If your realtek driver is really causing you problems, search for the appropriate drivers by typing in the name of your device. 

Typing "lsusb" into a terminal can produce some valuable information, as can "iwconfig"

The story on my wireless saga can be found here.[http://ubuntuforums.org/showthread.php?t=861418]("http://ubuntuforums.org/showthread.php?t=861418") Most of it is going up and down garden paths. My advice here is to include 'solution' 'fixed' or 'solved' in your searches in the forums. Words like 'problem' 'can't' and other such 'negative filtering' tends to yield inconclusive suggestions which can lead to further problems. Positive filtering and phrasing seems to speed my linux life along. Funny that. ;)




Regarding your vista installation. Your problem seems similar to mine. Vista would not boot after altering the drive partitions. Even attempting to fix the installation failed. It seems Vista doesn't like other operating systems messing with 'its' harddisk.

To show 'em who's boss, check out [this thread]("http://ubuntuforums.org/showthread.php?t=373074&page=5") 

NTFSPROGS provided me with the tools I needed to trick Vista into fixing itself with the new settings of disk partitions. If your hard drive is truly partitioned without room for Vista to operate, use "gparted" to correct it.

I hope this helps. 

A

---


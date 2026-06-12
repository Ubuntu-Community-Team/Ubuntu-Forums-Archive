---
title: "how do I get rid of Vista?"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-02
I keep looking around at how to do this but I keep getting bits and pieces of what to do laced with horror stories of boot failure.  I'm dreadfully concerned of this and want to know what's up with simply getting rid of WIndow's (ok no there's actually more;  I want to install Debian (or I'm not sure what/for what)because I'm gonna have a lot of free space.)  My current situation is that I bought this computer with windows installed and then made it dual boot with ubuntu.  GRUB is in there too somewhere.  I have opened gparted.  but again I don't get dev/hd's and whats what and If and how without a total boot malfunction.  can I get a ROCK SOLID LINK on this or I'm getting the idea Windows is kinda stuck in there?

---

### Post by Macintosh Sauce on 2008-08-02
If you just wanted to have Ubuntu, why don't you just reformat your HD and install Ubuntu from the CD? That is the best way IMO... Windows magically disappears. :)

---

### Post by hovzio on 2008-08-02
You could use gparted to format the ms partition, its not very hard. You can also use it to resize partitions and so on. Use a live cd or install with:

sudo apt-get install gparted


When you do a fresh install of ubuntu you also have the option of using the whole hard drive (formating it all) and setting up home partitions and so on.:)

---

### Post by adamogardner on 2008-08-02
This is disgruntling.  To have no remnants of microsoft on my machine I have to scrap the ubuntu I'm using?  I worked so hard to get this thing going right.  As far as reformatting the ms partition using gparted; I have gparted and It's not that easy for me. I have no excuses.  It's confusing.

---

### Post by DGortze380 on 2008-08-02
just use gparted to reformat your vista partition, format it to ext3 and use it for data storage.

---

### Post by kk0sse54 on 2008-08-02
Pop in a ubuntu liveCD and open up Gparted. From there just delete your vista  partition and expand your Ubuntu partition. You Ubuntu install will be kept intact and you vista partition will be gone. Remember though always back-up important data before doing any partition work.

---

### Post by Ingenue on 2008-08-02
> **C!oud said:**
> Pop in a ubuntu liveCD and open up Gparted. From there just delete your vista  partition and expand your Ubuntu partition. You Ubuntu install will be kept intact and you vista partition will be gone. Remember though always back-up important data before doing any partition work.

I can back this one up! I did exactly this and it worked perfectly. No data loss just smooth sailing. Good advice C!oud.

---

### Post by Crafty Kisses on 2008-08-02
> **Macintosh Sauce said:**
> If you just wanted to have Ubuntu, why don't you just reformat your HD and install Ubuntu from the CD? That is the best way IMO... Windows magically disappears. :)

That's probably the easiest way, or you could use gparted.

---

### Post by NightwishFan on 2008-08-02
Nvm yeah didnt read enough just use gparted as was said. Well help you out if you need anything. (Debian owns ;])

---

### Post by jualin on 2008-08-02
Just be careful you don't delete your Ubuntu partition, :lol: (i did this once by mistake)

---

### Post by hansdown on 2008-08-02
Why not do a clean install, and; use entire disk? Worked great for me.

---

### Post by adamogardner on 2008-08-02
I want to use other operating systems in place of Windows.  I want to do this with the aim of learning as well as making my machine as versatile as possible, so that I can learn as much as possible.  With this in mind, What distros other than a live Ubuntu cd would one recommend to compliment Ubuntu).?  I mean Is vista the answer to this question?

---

### Post by Ingenue on 2008-08-02
> **adamogardner said:**
> I want to use other operating systems in place of Windows.  I want to do this with the aim of learning as well as making my machine as versatile as possible, so that I can learn as much as possible.  With this in mind, What distros other than a live Ubuntu cd would one recommend to compliment Ubuntu).?  I mean Is vista the answer to this question?

I've been interested in Gentoo, but thats just me. :)

---

### Post by jualin on 2008-08-02
OpenSuse looks great, Fedora seems pretty nice even though I didn't like the Package Manager and also it didn't recognize Ubuntu after installing. I would also try PCLinuxOS if you are into KDE or Debian if you are into hardcore "awesomeness". I am afraid to try the last one myself since I heard is pretty terminal oriented, that's why I am trying to get familiarize with teh terminal so I can eventually go and use Ubuntu's father Debian :lolflag:

---

### Post by adamogardner on 2008-08-03
> **Ingenue said:**
> I've been interested in Gentoo, but thats just me. :)

Why?

So Debian for "awesomeness"?  That's what I was thinking.  But will the "father" Make my machine maximally versatile in function and experience ie."the macdaddy computer"

---

### Post by jualin on 2008-08-03
> **adamogardner said:**
> Why?

So Debian for "awesomeness"?  That's what I was thinking.  But will the "father" Make my machine maximally versatile in function and experience ie."the macdaddy computer"

I have seen Debian before and it looks exactly like Ubuntu. The main difference that I saw was the user friendliness. Many GUI programs that come with Ubuntu don't come with Debian therefore you may need to either install them or use the command line. I have heard that it runs faster and is more stable, but I haven't been able to confirm this since I have never installed it on my computer. Another thing is that they come out with a new version once a year or sometimes longer (the last one was done on 2007/04/08). Now I don't know why the common user would prefer Debian over Ubuntu or what are the clear advantages of running Debian except stability. Maybe someone who has use it can expand on the topic. They are coming out with a new Debian on September so you may want to wait until they release it or try the Beta Version which is already out. I am guessing it has something better than most distros when it has been around for so long and still pretty popular (#6 in Distrowatch.com and going up!) Good luck!

---

### Post by BGFG on 2008-08-03
I installed Debian yesterday, for the second time. the first time i hit ctrl+alt+backspace got a black screen and never recovered, not for lack of help from the forums though. The people in here are great.
First time i also used Logical Volume management, which is a great tool but a sonova' to mount from another system. It was on a 250 gig drive and i found that it was a bit slower that Ubuntu. No benchmarks or anything just general system feel.
So yesterday i re-installed using the netinstall cd which works great. this time, manual disk config. Took a few mins to get the hang of but finally:
/10gig/15gigHOME/2.7gig SWAP. colour me proud. 
System responds faster now, but since i shrunk the disk space that is obvious.
All in all. I'm an Ubuntu baby but Debian is definitly a great place to learn and hone skills. Plus stability. (cept for the new X) I can't get my max res of 1400by900 yet.

As for getting rid of Vista ? What is your config like ?
Vista/Ubuntu on same partitioned drive or separate drives ? If separate drives you can format the vista drive and set the Ubuntu one as the first boot device.

if you want to go straight to debian, you can install it over the vista drive in one shot and debian  will simply discover Ubuntu and add it to the bootloader no problem.

If you plan on using all your new space to share media with your Ubuntu installation then i would not suggest LVM for beginners like us. It behaves a bit 'exclusively' with it's disk space.

---

### Post by Ingenue on 2008-08-03
> **adamogardner said:**
> Why?

Here is some information about Gentoo from Distro watch. 

> Gentoo Linux is a versatile and fast, completely free Linux distribution geared towards developers and network professionals. Unlike other distros, Gentoo Linux has an advanced package management system called Portage. Portage is a true ports system in the tradition of BSD ports, but is Python-based and sports a number of advanced features including dependencies, fine-grained package management, "fake" (OpenBSD-style) installs, safe unmerging, system profiles, virtual packages, config file management, and more.

Other than that...I have several friends at work who RAVE about Gentoo. Of course they are all Web Developers and Programmers. Much more advanced in Linux know-how than I. From what I can tell it is geared toward power users. It has been accused of some instability issues in the past. 

So for me, I'm not going to be installing anytime soon. I'm only two weeks into Ubuntu! But I do find the project intriguing.

---

### Post by ashtonisdrugfree on 2008-08-03
gparted is confusing for many people. the easiest thing to do is to pop in a live cd... run gparted  and format the first hd/partition listed. The first in the list is usually the one with windows installed on it.  after the format, shut down, pop in the debian cd and install to that partition.

---

### Post by jualin on 2008-08-03
> **ashtonisdrugfree said:**
> gparted is confusing for many people. the easiest thing to do is to pop in a live cd... run gparted  and format the first hd/partition listed. The first in the list is usually the one with windows installed on it.  after the format, shut down, pop in the debian cd and install to that partition.

Be careful with that advice since many people have different configurations. The first one is not always windows. The best way of identifying the partition is comparing the file system, NTFS or FAT32 for windows, and the size, and if you running the LiveCD, I even recommend a step further and mounting that partition that you think is running windows and make sure that it is. Trust me, I have made that mistake before and is not very nice having to reinstall when you didn't back up your files. May the Linux be with you :lolflag:

---

### Post by BGFG on 2008-08-03
> **ashtonisdrugfree said:**
> gparted is confusing for many people. the easiest thing to do is to pop in a live cd... run gparted  and format the first hd/partition listed. The first in the list is usually the one with windows installed on it.  after the format, shut down, pop in the debian cd and install to that partition.

True, but a few mins to sit back and absorb it and it's really easy. I especially like that the graph shows the physical position of the partition on the disk. 
Would be cool if the forums had a live messaging feature so we could give guys a live walk through tech support :)

---

### Post by adamogardner on 2008-08-03
Well let me ask?  If I remove a bunch of things from Vista (I don't know what - suggestions?) Can I condense the Vista partition and still have it work effectively?  here is a screenshot of gparted.  windows is the big green one at top left, correct?  What are the small ones? And do this installing Gentoo?  Where do I get Gentooooooooo????

---

### Post by BGFG on 2008-08-03
> **adamogardner said:**
> Well let me ask?  If I remove a bunch of things from Vista (I don't know what - suggestions?) Can I condense the Vista partition and still have it work effectively?  here is a screenshot of gparted.  windows is the big green one at top left, correct?  What are the small ones? And do this installing Gentoo?  Where do I get Gentooooooooo????

Well i'd suggest burning off your media or just backing it up elsewhere. then defrag your drive because ntfs drops data all over the place.
For defraging - Defraggler by piriform.
[http://www.defraggler.com/](http://www.defraggler.com/)

Then use the built in Vista feature in Disk Management to shrink your vista partition as much as possible (easy peezy)
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

As for Gentoo:
[http://www.gentoo.org/](http://www.gentoo.org/)

And any other distribution, just google it, first link is usually the home site :)

Good Luck.

---

### Post by Ingenue on 2008-08-03
Good luck with whatever distro you choose. If you do go with Gentoo, let me know your impressions please.

---

### Post by cjm5229 on 2008-08-03
If you wish to remove Vista, all you need to do is repartition your HD with GParted. Boot from a live CD (Ubuntu 8.04 will do), then go to System>Administration>Partition Editor, You can then just delete the Partition that Windows is on.You can only have 4 Primary partitions on a single HD so I would recomend that you resize your Ubuntu Parition all the way to the left, then shrink it as much as you need. Create an extended Partition from the rest of the HD. This would be where you should create a Home Partition, Swap Partition, and however many Partitions you need to have for the Root Files of the other OS's you paln to install. Be sure to save any Data that you want to keep because the odds are the first time you do this you will mess everything up.  Most other OS's will not detect your Ubuntu installs or other Linux installs, so I generally install Ubuntu last. Right now I have Hardy Heron, Intrepid Ibex Alpha 3, and PCLinuxOS, installed on mine.I share the Home Partition, but use different users for each OS so that I don't have configuration conflicts.  Gparted may give errors if the partitions you are changing are mounted, in which case ```
sudo umount -a
``` in a terminal should help. 

For someone new to linux, Gentoo and Slackware Distro's will probably not be the best idea. PCLinuxOS is good, Mint is good, Suse, and Fedora are also really good. Debian always seemed to me like using Ubuntu from two releases back, but is very stable. 
Good Luck and Enjoy Window's free Computing.:)
Carl.

---

### Post by BGFG on 2008-08-03
Thanks for your post Carl. I was actually wondering if i could share a home partition among distributions. Nice to know i can. Something to try in future.
Agree with your comment on Debian too.

---


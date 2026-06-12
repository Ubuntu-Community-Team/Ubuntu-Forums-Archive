---
title: "Unable to install on old laptop"
date: 2013-03-23
forum: New to Ubuntu
---

### Post by Drowz0r on 2013-03-23
Hello everyone

I'm having trouble installing Lubuntu on an old laptop. It's a 1GHz Celeron, 256MB RAM machine that worked perfectly with windows XP (no chugging or anything). It's a Patriot 2410... some brand I've never even heard of.

I burnt lubuntu to a DVD and it worked fine until the software install part, where it dies on "popcon" or around the state where it's copying 866 or so files.

After it failed multiple times, saying the files were corrupt or some such I burnt a new DVD with a fresh iso download but I had the same problem in the same place.

The machine seems to meet the requirements for lubuntu.

The machine will just be used by my 4 year old son. Want him to start getting used to alternative, Linux stuff early on - rather than being completely indoctrinated by Windows.

Any advice peoples?

Thanks in advance.

---

### Post by DuckHook on 2013-03-23
Will the laptop run a LiveDVD session with the same DVDs?

If so, from LiveDVD, post output of ```
sudo lshw
``````
lspci -vn
```

---

### Post by Drowz0r on 2013-03-23
There does not appear to be an option to boot Lubuntu from DVD (install only).

Seeing as it dies half way through the install, obviously the previous partition holding Windows XP is no more, so I cannot boot into an existing OS and run Lubuntu from disk there either.

---

### Post by arpanaut on 2013-03-23
go here: [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/)
scroll down to  lubuntu-12.04-desktop-i386.iso 
and download and burn to cd/dvd, that iso will give you the ability to try lubuntu in a live session 
and see if your hardware is compatible.

---

### Post by Rex Bouwense on 2013-03-23
With only 256 Mbs of RAM you are at the lower end of being able to install and run Lubuntu comfortably.  So if you have problems installing, please consider using the alternate installer.

---

### Post by fantab on 2013-03-24
> **Drowz0r said:**
> I'm having trouble installing Lubuntu on an old laptop. It's a 1GHz Celeron, 256MB RAM machine that worked perfectly with windows XP (no chugging or anything). It's a Patriot 2410... some brand I've never even heard of.

If you want to use modern OS with degree of ease then seriously, consider upgrading your RAM (1GB is recommended, +512MB is minimum).

For the given machine install with "[Lubuntu Alternate Installer]("https://help.ubuntu.com/community/Lubuntu/Documentation/AlternateInstall")". It is meant for low spec machines.

---

### Post by DuckHook on 2013-03-24
As a collector of old hardware, I think I have a sense of where the OP is coming from: some hardware isn't worth even an additional $10 investment. The interesting challenge becomes one of finding the best use for the thing rather than "bringing it up to date".

@OP

I have run Lubuntu on 256 MB of system RAM. You won't be able to run more than one or two apps at a time, but sometimes, this is all you need. Browsers, however, are memory hogs, and, in its default configuration, the system will quickly go to swap, which has the effect of making the system feel extremely sluggish. You can remedy this to a large extent by setting swappiness to a low number like 10. Instructions are [here]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F"). However, if your video chip has no dedicated video memory of its own, then your laptop is designed so that it must share the already limited amount of system RAM it has with the video subsystem. This is why many members recommend beefing up your RAM. If this were your production machine, such would be my recommendation as well. However it is clear that you are intending this machine as a solution looking for a problem, so here is my suggestion:

Get your little son a better machine capable of running a proper OS and that is capable of growing with him. Use this ancient thing instead as a command-line-only server/gateway. Some uses include: file server, print server, install rsync to make it a redundant NAS, torrent server, media/music server, vpn-capable router/firewall, or just use it as a spare machine you can monkey with and learn the command line on.

To install a basic command line OS, @fantab's recommendation of the alternate installer is just as valid as for a minimal GUI.

---

### Post by Drowz0r on 2013-03-24
> **arpanaut said:**
> go here: [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/)
scroll down to  lubuntu-12.04-desktop-i386.iso 
and download and burn to cd/dvd, that iso will give you the ability to try lubuntu in a live session 
and see if your hardware is compatible.

Sorry I should have specified I'm using 12.04 iso - there isn't an option for a live trial.

---

### Post by Drowz0r on 2013-03-24
> **DuckHook said:**
> As a collector of old hardware, I think I have a sense of where the OP is coming from: some hardware isn't worth even an additional $10 investment. The interesting challenge becomes one of finding the best use for the thing rather than "bringing it up to date".

@OP

I have run Lubuntu on 256 MB of system RAM. You won't be able to run more than one or two apps at a time, but sometimes, this is all you need. Browsers, however, are memory hogs, and, in its default configuration, the system will quickly go to swap, which has the effect of making the system feel extremely sluggish. You can remedy this to a large extent by setting swappiness to a low number like 10. Instructions are [here]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F"). However, if your video chip has no dedicated video memory of its own, then your laptop is designed so that it must share the already limited amount of system RAM it has with the video subsystem. This is why many members recommend beefing up your RAM. If this were your production machine, such would be my recommendation as well. However it is clear that you are intending this machine as a solution looking for a problem, so here is my suggestion:

Get your little son a better machine capable of running a proper OS and that is capable of growing with him. Use this ancient thing instead as a command-line-only server/gateway. Some uses include: file server, print server, install rsync to make it a redundant NAS, torrent server, media/music server, vpn-capable router/firewall, or just use it as a spare machine you can monkey with and learn the command line on.

To install a basic command line OS, @fantab's recommendation of the alternate installer is just as valid as for a minimal GUI.

Thanks for the info. This machine is actually perfectly capable of running windows XP with no lag or chugging so I was a little surprised Lubuntu isn't really feasable on it. Is there perhaps a lighter weight alternative to Lubuntu whereby this machine can be used as a back-up, almost like netbook, to search for fixes if my main machine goes down? It'll only need a browser really...

---

### Post by black veils on 2013-03-24
> **Drowz0r said:**
> Thanks for the info. This machine is actually perfectly capable of running windows XP with no lag or chugging so I was a little surprised Lubuntu isn't really feasable on it. Is there perhaps a lighter weight alternative to Lubuntu whereby this machine can be used as a back-up, almost like netbook, to search for fixes if my man machine goes down? It'll only need a browser really...

bodhi linux is a bit lighter, becuse it uses the enlightenment (e17) desktop, it is based on ubuntu. you will need to go to the bodhi app cente website to install application suite, as it starts off bare deliberately. work from there.

midori web browser with user agent set as iphone is useful.

i don't know if you might find an improvement in trying peppermint os, also based on ubuntu.

but if you just want to make sure you have an emergency system on cd/dvd/usb, then get puppy linux precise, you can do web browsing and file manager stuff. its very fast, it loads totally into ram.

---

### Post by fantab on 2013-03-24
Lubuntu and Xubuntu by themselves are light weight. Its the 'Ubiquity" installer that needs more RAM... hence we use the "alternate installer". Windows XP works, but I am sure it does not work as well as it does on a machine with more RAM. Like DuckHook said, you are restrained with only 256MB RAM.

---

### Post by MoebusNet on 2013-03-24
If one of the *buntu's doesn't meet your needs, you can always try out Puppy Linux:

[http://www.puppylinux.com/](http://www.puppylinux.com/)

It is a very light install and typically doesn't need much RAM. "A complete operating system with suite of GUI apps, only about 70 - 160MB and boots directly off the CD (or USB, SD, hard drive, etc.)." It can also be installed to your hard drive.

---

### Post by DuckHook on 2013-03-24
> **Drowz0r said:**
> ...This machine is actually perfectly capable of running windows XP with no lag or chugging so I was a little surprised Lubuntu isn't really feasable on it.

It's important to remember that Lubuntu, though lightweight, is still founded on a modern kernel that is very much up to date. XP on the other hand is now ancient technology with a die-date of April 8 next year. It's already amazing that Lubuntu can run on most equipment that XP can given the more than one-decade age difference. However, it won't run on absolutely everything, and I've got some really old Dell laptops that it refuses to install on (just like yours). There are workarounds, mostly involving pinning old kernels and device drivers, but this is really only for tinkerers and not worth the trouble for casual users who just want their stuff to work.

 > Is there perhaps a lighter weight alternative to Lubuntu whereby this machine can be used as a back-up, almost like netbook, to search for fixes if my main machine goes down? It'll only need a browser really...

Many respondents have already mentioned distros like Bodhi and Puppy, all good recommendations. I would add Crunchbang to that list. I love it for its true simplicity. It just uses a window manager instead of a full-blown Desktop Environment, and its extreme Spartan look is so clean that it is as aesthetically pleasing as Nordic furniture (if that's your thing).

---

### Post by roly33 on 2013-03-24
I'd use the machine as a Server and get a better one, since it's for your son you'll need something that can be updated with newer releases and even allow your son to change to the regular Ubuntu distro.

Roland

---

### Post by Drowz0r on 2013-03-27
Ah ha, well the alternative installer did work after, but it was lag central as others adviced.

I'm trying to give bodhi linux a shot but after burning it to DVD it can't seem to find anything to boot from... seems odd.

btw thanks everyone for the posts - I am reading them all.

---

### Post by jim Kane on 2013-03-27
> **MoebusNet said:**
> If one of the *buntu's doesn't meet your needs, you can always try out Puppy Linux:

[http://www.puppylinux.com/](http://www.puppylinux.com/)

It is a very light install and typically doesn't need much RAM. "A complete operating system with suite of GUI apps, only about 70 - 160MB and boots directly off the CD (or USB, SD, hard drive, etc.)." It can also be installed to your hard drive.

Yes agreed thats what i was going to post
i use Puppy on a 700M cpu 250MB ram old laptop, works really well.


jk

---


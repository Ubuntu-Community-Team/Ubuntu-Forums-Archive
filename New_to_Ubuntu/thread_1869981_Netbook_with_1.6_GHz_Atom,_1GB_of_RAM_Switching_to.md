---
title: "Netbook with 1.6 GHz Atom, 1GB of RAM: Switching to Ubuntu?"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by Onirae on 2011-10-26
Ok, I'm very seriouysly leave windows behind, but need to make sure that all I am doing now I will be able to do it in Ubuntu

I have a netbook with 1.6ghz atom, 1gb of ram and max resolution of 1024x600

Hope that's not a problem with ubuntu 11.10 and later patches

Also, I use the netbook mainly for surfing, downloading, media and some gaming (old strategy/RPG, GW, NWN, TTD, and the like)

Does wime augment the system requirements or will I be able to play as always?

Instead of Ubuntu, should I get any other build?

Any other question I should make myself?

Thanks all

---

### Post by JRV on 2011-10-26
Try the live CD by downloading unetbootin for Windows and create a bootable USB stick.  From there you can try it and later install it if you so desire.

The surfing, downloading, and media should not be a problem.  
I don't know gaming. I don't understand the abbreviations you mention.

It will run faster with a full install than it will from the USB stick.

---

### Post by kurt18947 on 2011-10-26
I'm not a gamer so I can't help with that.  Do you plan to wipe your Windows partition or install Ubuntu and Windows side by side?  Either way, I'd create at least one disk image of your operating machine before doing anything.  That way if you find that "Oops I do need Windows after all", you can restore to what you have now.  If I were selecting an operating system for your machine, I'd probably install Lubuntu.  Lubuntu seems to run nicely on lower powered machines.  I would also create a live USB and try that before wiping what you have now.  Make sure your video and network and touchpad etc. work with Lubuntu or whatever you choose.  If Lubuntu doesn't work for whatever reason, you could also take a look at PCLinuxOS.  That is not an *buntu derivative but it seems to work pretty well on lower powered machines.

---

### Post by collisionystm on 2011-10-26
What brand netbook?

I would not run 11.10. Use 10.04 or 10.10. The requirements for 11.10 will probably eat your netbook alive. Although, as suggested, try the live-cd.

---

### Post by Lars Noodén on 2011-10-26
> **Onirae said:**
> Instead of Ubuntu, should I get any other build?

As JRV mentions, try the live CD's first.  You might try [Lubuntu](http://lubuntu.net/), since it is very light weight and that can be good for netbooks.  [Xubuntu](http://xubuntu.org/) is also very popular because it is fast and retains a more traditional interface.  Neither have [Mono](http://www.fsf.org/news/dont-depend-on-mono).

Some of the default packages for the other builds can be different, but you can always add what you want from the repositories.

---

### Post by philinux on 2011-10-26
> **Onirae said:**
> Ok, I'm very seriouysly leave windows behind, but need to make sure that all I am doing now I will be able to do it in Ubuntu

I have a netbook with 1.6ghz atom, 1gb of ram and max resolution of 1024x600

Hope that's not a problem with ubuntu 11.10 and later patches

Also, I use the netbook mainly for surfing, downloading, media and some gaming (old strategy/RPG, GW, NWN, TTD, and the like)

Does wime augment the system requirements or will I be able to play as always?

Instead of Ubuntu, should I get any other build?

Any other question I should make myself?

Thanks all
 [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Should run fine. 11.10 runs very well on my acer 1410.  I have 2 gig RAM bit its not using anywhere near 1 gig

---

### Post by beew on 2011-10-26
With that specs you can run Ubuntu but Xubuntu or Lubuntu would be much faster. Also what is your graphic card? 

At this point I would suggest 11.04, 11.10 is just out for ~2 weeks and it is still very buggy, also switching to gtk3 is a big change, some features are missing or broken at this point. I would probably skip 11.10 all together, it is a transitional release even more than 11.04.

---

### Post by Onirae on 2011-10-26
thanks all for the high amount of replies in such little time

to answer some questions, my compaq mini netbook only has a 60gb HD, all eaten up by windows, so my idea is to annihilate everything inside it, and only install linux (with a backup of course). my VGA is a GMA950

i'll download a couple of live cds to try that all the hardware works

as for the games listed, they mostly are Guild Wars, NeverWinter Nights, Sins of a Solar Empire and Baldur's Gate II, so pretty much every game of 1997-2003

Maybe put a windows VM, just in case?

also, installing xu- or lubuntu, do i lose any kind of feature? wine support, codecs, anything?

---

### Post by matt_symes on 2011-10-26
Hi

Image your current hard drive then you can always roll back if you want to.

Useful if you come to sell it at a later date as well.

This does assume you already have a different OS on it.

EDIT: Jut missed your last post :)

Kind regards

---

### Post by beew on 2011-10-26
> **Onirae said:**
> thanks all for the high amount of replies in such little time

to answer some questions, my compaq mini netbook only has a 60gb HD, all eaten up by windows, so my idea is to annihilate everything inside it, and only install linux (with a backup of course)

i'll download a couple of live cds to try that all the hardware works

as for the games listed, they mostly are Guild Wars, NeverWinter Nights, Sins of a Solar Empire and Baldur's Gate II, so pretty much every game of 1997-2003

Maybe put a windows VM, just in case?

Don't think you can run a VM with that kind of specs. The important thing is to check that the graphic and wireless cards work.

And it you want to do some tests, make some live usbs with persistence, CDs are super slow and clunky and you can't save anything. I really don't understand why people are still recommending live CD unless they like to hear the noise it makes in the CDROM :) Make sure you have configure your bios to boot from usb.

---

### Post by madjr on 2011-10-26
> **Onirae said:**
> thanks all for the high amount of replies in such little time

to answer some questions, my compaq mini netbook only has a 60gb HD, all eaten up by windows, so my idea is to annihilate everything inside it, and only install linux (with a backup of course). my VGA is a GMA950

i'll download a couple of live cds to try that all the hardware works

as for the games listed, they mostly are Guild Wars, NeverWinter Nights, Sins of a Solar Empire and Baldur's Gate II, so pretty much every game of 1997-2003

Maybe put a windows VM, just in case?

also, installing xu- or lubuntu, do i lose any kind of feature? wine support, codecs, anything?

Yes, is feasible.

Use **unity 2d** instead of 3d so you can have max performance (also there's not that much difference once you get used to it) 

**wine** supports many games, but is better to make sure:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

And try **playonlinux**:
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

Also this is a good blog to keep updated with gaming on ubuntu and other stuff:
[http://www.ubuntuvibes.com/](http://www.ubuntuvibes.com/)

Good luck and have fun !

---

### Post by beew on 2011-10-26
> **madjr said:**
> Yes, is feasible.

Use **unity 2d** instead of 3d so you can have max performance (also there's not that much difference once you get used to it) 

wine supports many games, but is better to make sure:
[http://appdb.winehq.org/](http://appdb.winehq.org/)

also try playonlinux:
[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

Good luck and have fun !

2d looks like 3d but there are lots of differences, you can't have multiple desktops for one. Many tweakings that rely on ccsm would not work in Unity 2 D. 

I still think OP should use the 11.04 buntus. Xubuntu and  Lubuntu would work much better than Ubuntu on such specs, instead of turning off Compiz to run Unity 2d with Ubuntu, OP can run Xubuntu with full Compiz and much faster.

---

### Post by Onirae on 2011-10-26
great, now just have to decide... what linux release?

currently looking debian, but xu- and lu- are still ahead

edit: lubuntu site down?

---

### Post by philinux on 2011-10-26
> **beew said:**
> With that specs you can run Ubuntu but Xubuntu or Lubuntu would be much faster. Also what is your graphic card? 

At this point I would suggest 11.04, 11.10 is just out for ~2 weeks and it is still very buggy, also switching to gtk3 is a big change, some features are missing or broken at this point. I would probably skip 11.10 all together, it is a transitional release even more than 11.04.

I've done a clean 11.10 install on a desktop and my acer 1410 and have not encountered any problems. Desktop has NVIDIA and lappy has Intel.

---

### Post by Hylas de Niall on 2011-10-26
I'm running Ubuntu 11.10 very happily on a netbook right now.

These are the specs of my machine, a Medion Akoya mini E1210":
1.6GHz intel Atom processor (n270)
1gig ram
intel on-board graphic controller (945GME x86/MMX/SSE2)
on-board audio

It's running fine for me. The only issue i have, which i also had when it was running Win XP, was with applications and games being too big to fit on the screen.

I'd say go for it, but try a couple of live CD's first, just to be sure. I can say from experience that Lubuntu and Xubuntu will run very well indeed on those specs. Ubuntu as well, though probably not as well for more complex games.

"Basically a re-branded MSI Wind U100

---

### Post by Onirae on 2011-10-26
> **Hylas de Niall said:**
> 

These are the specs of my machine, a Medion Akoya mini E1210":
1.6GHz intel Atom processor (n270)
1gig ram
intel on-board graphic controller (945GME x86/MMX/SSE2)
on-board audio


exactly the same specs as me

so you are saying it works perfectly and i dont need lubuntu? should i just download the latest ubuntu and try it?

---

### Post by madjr on 2011-10-26
> **Onirae said:**
> exactly the same specs as me

so you are saying it works perfectly and i dont need lubuntu? should i just download the latest ubuntu and try it?

no hurt in trying.

also stick with the *ubuntus , other distros may not be as easy.

---

### Post by Onirae on 2011-10-26
ok, just to put things harder:

i stumbled upon meego, and loved the interface. cartoonish but not childish. simple. beautiful

anything like it in lu/xu/ubuntu?

also, made up my mind: this weekend i'll try ubuntu, not xu, wu, lu or other subs (unless it goes slow). question is... 11.04 or 11.10?

you guys recommend also putting gnome instead of unity? i read many complains about unity

---

### Post by philinux on 2011-10-26
> **Onirae said:**
> ok, just to put things harder:

i stumbled upon meego, and loved the interface. cartoonish but not childish. simple. beautiful

anything like it in lu/xu/ubuntu?

also, made up my mind: this weekend i'll try ubuntu, not xu, wu, lu or other subs (unless it goes slow). question is... 11.04 or 11.10?

you guys recommend also putting gnome instead of unity? i read many complains about unity

I'll be honest, as always, and say that initially my reaction to unity was "you gotta be kidding me". But after a me enforcing a week trial I really love it.  This might help.
 [http://ubuntuforums.org/showthread.php?t=1742326](http://ubuntuforums.org/showthread.php?t=1742326)

Once you shrink the launcher icon size to 38 it looks great.

---

### Post by Guitar John on 2011-10-26
FWIW, I am running Ubuntu 11.10 on my ThinkPad X100e. 

It has AMD MV-40 (1.6 GHz), 2 GB RAM, 250 GB HDD.  Ubuntu/Unity run just fine on it.

---

### Post by Drowz0r on 2011-10-26
> **beew said:**
> With that specs you can run Ubuntu but Xubuntu or Lubuntu would be much faster. Also what is your graphic card? 

At this point I would suggest 11.04, 11.10 is just out for ~2 weeks and it is still very buggy, also switching to gtk3 is a big change, some features are missing or broken at this point. I would probably skip 11.10 all together, it is a transitional release even more than 11.04.

I dunno, though xubuntu seemed to be for the low end tech or limited resource machines, ubuntu works a lot better on my tablet PC than xubuntu did. I also found xubuntu very buggy in comparison to ubuntu.

I'd recommend you try a few different flavours and do the old trial and error approach but I literally found ubuntu to perform a lot better on both high and low end machines when compared with kubuntu and xubuntu.

---

### Post by Onirae on 2011-10-26
are the requirements much higher in 11.10 than in 11.04?

---

### Post by philinux on 2011-10-26
> **Onirae said:**
> are the requirements much higher in 11.10 than in 11.04?

No. And its better in a lot of ways.

---

### Post by Onirae on 2011-10-26
got almost everything solved

what about a user friendly interface like meego?

---

### Post by Hylas de Niall on 2011-10-26
> **Onirae said:**
> exactly the same specs as me

so you are saying it works perfectly and i dont need lubuntu? should i just download the latest ubuntu and try it?

I can say that it's working perfectly for me on my netbook *with compiz too*.
_I can't outright guarantee_ that you'll have the same luck/success(?) because there are lots of things which didn't work perfectly until after a lot of updates installed on mine (eg it didn't *at first* recognise my graphics chip), but a little patience and everything came right here.
I'm not a linux expert, i just let it do what it wanted, and it all got sorted very nicely.
Try a live CD of Ubu first, and if you're happy with that, and are prepared to wait for updates, I think it will be a happy experience for you.
I hope this helps :)

---

### Post by philinux on 2011-10-26
> **Onirae said:**
> got almost everything solved

what about a user friendly interface like meego?

Meego is a distro. Choice is wonderful.

---

### Post by Hylas de Niall on 2011-10-26
Kubuntu has a nice fall-back netbook interface, i must say.

[http://ubuntumanual.org/posts/403/kubuntu-11-10-beta-test-drive](http://ubuntumanual.org/posts/403/kubuntu-11-10-beta-test-drive)

---

### Post by beew on 2011-10-26
> **Onirae said:**
> are the requirements much higher in 11.10 than in 11.04?

No, not the requirements. It is just that it is buggy at this point and many features are missing because of switch to gnome 3. Examples: You can't do any simple customization like changing themes without the gnome-tweak-tool, it is not included by default; the image viewer does not work for me and a few others,--try right click a jpg or png file, nothing happens; you can't create desktop launchers with right click (there is a work around but it is ridiculous that beginner should have to go through that to do something so simple); there is no easy way to choose default programs to open file with if the program is not listed already, whereas in 11.04 and before you can simply add a custom command; graphic problems for some graphic cards. 

It is true that it is a lot better than 11.04 when it first came out, but after 6 months 11.04 has turned out to be very nice.

I wouldn't install it on my computers without waiting for at least a month with more testings. I am having it installed in an external drive only for testing.

---

### Post by beew on 2011-10-26
> **Drowz0r said:**
> I dunno, though xubuntu seemed to be for the low end tech or limited resource machines, ubuntu works a lot better on my tablet PC than xubuntu did. I also found xubuntu very buggy in comparison to ubuntu.

I'd recommend you try a few different flavours and do the old trial and error approach but I literally found ubuntu to perform a lot better on both high and low end machines when compared with kubuntu and xubuntu.
I think 1.6Gh and 1g of ram is pretty low end. Ubuntu would run on this machine with Unity3D (if you get the right graphic card), I have tried it on an old laptop with these specs, but Lubuntu and Xubuntu are a lot faster even with full Compiz. I agree that thunar and LXDE are somewhat limited and buggy comparing to gnome, but with switch to gnome3 the gap is not so big. gnome is buggy in 11.10 and many features are gone so it is even more stripped down than xfce in some ways.

---

### Post by mebomechanicno1 on 2011-10-26
I speak with the complete authority of someone who knows nothing of how any of this works; only that it does work!  I started flirting with Linux distros about 20 years ago, and found the perfect distro about 2 weeks ago in Ubuntu 11.10.  You may be aware Sony Vaios are notoriously difficult to fit to linux (but I love the design of them) and I have been trying to get one or other distro to work properly on one of my Vaios for years.  11.10 comes along, I make a live USB, I spend Saturday evening playing with it, I wipe the hard drive and install 11.10 on Sunday evening.  As they say here in England "nuff said".  I like it a lot

:KS:KS:KS:lolflag:

---

### Post by mörgæs on 2011-10-26
Changed the title to a more descriptive one.

---

### Post by madjr on 2011-10-26
some guides to get you started:

[http://www.omgubuntu.co.uk/2011/10/ubuntu-11-10-released/](http://www.omgubuntu.co.uk/2011/10/ubuntu-11-10-released/)

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by mastablasta on 2011-10-27
as for the interfaces - new Gnome and Unity don't have as many different themes. Unity even has low customisation options. But others Xubuntu , lUbuntu amd Kubuntu have plenty of various themes available.
 
There are some distributions that have custom menues and interfaces. for example Ubntu has Unity, Linux mint (based on ubuntu and also another very user frienldy distribution) have their MintMenu etc... 
 
Then there are various netbook version as mentioned KDE has netbook plasma interface that will rearange icons a bit to meke it more suitable for netbooks. then all you would need to do is find a more cartoony theme. or the one with larger icons for example: [http://kde-look.org/content/show.php/My+Netbook-Remix?content=116177](http://kde-look.org/content/show.php/My+Netbook-Remix?content=116177)
 
 
the default cartoony theme that i saw is in Puppy Linux, they even have an Ubuntu repository based version. however it works in a very different way form Ubuntu and has a few limits. but might be a good solution for kids (due to their cartoony icons) and people with older mashcines.

---

### Post by Paqman on 2011-10-27
> **collisionystm said:**
> 
I would not run 11.10. Use 10.04 or 10.10. The requirements for 11.10 will probably eat your netbook alive.

Nope, I've got 11.10 running on two netbooks with that spec (I'm assuming it has the same Intel graphics). Unity-2D runs fine.

---

### Post by Hylas de Niall on 2011-10-27
Full Unity _3D_ on my 2008 (same spec) machine :)

---

### Post by Onirae on 2011-10-27
> **Hylas de Niall said:**
> Full Unity _3D_ on my 2008 (same spec) machine :)

GMA950, 1gb RAM and atom CPU?

Also, because xubuntu is community-developed... does it make it less stable than vanilla ubuntu?

---

### Post by Hylas de Niall on 2011-10-27
> **Onirae said:**
> GMA950, 1gb RAM and atom CPU?

Also, because xubuntu is community-developed... does it make it less stable than vanilla ubuntu?

GMA945 :) and yes and yes (as previously listed). -Though my Graphic chip wasn't detected *straight away*, slowing things down a bit.

I can't comment on the stability of Xubuntu 11.10 as i've not tried that release (too pleased with vanilla to want to), but 11.4 *was* great.

---

### Post by Onirae on 2011-10-27
> **Hylas de Niall said:**
> GMA945 :) and yes and yes (as previously listed). -Though my Graphic chip wasn't detected *straight away*, slowing things down a bit.

I can't comment on the stability of Xubuntu 11.10 as i've not tried that release (too pleased with vanilla to want to), but 11.4 *was* great.

could you please tell me how you got the VGA to work? just to have everything prepared for when i'll try it this weekend

---

### Post by Hylas de Niall on 2011-10-28
> **Onirae said:**
> could you please tell me how you got the VGA to work? just to have everything prepared for when i'll try it this weekend

Well, it came right with normal updates. I didn't have to do any tweaking, myself.

I should clarify that she ran well enough even when there *wasn't* a specific driver onboard, so you needn't worry too much. The display was fine, just a little bit slower.

My setup has been running since the beta2 release, so your chip may well be recognised straight off the bat.

---

### Post by Roving Sign on 2011-10-28
I have 11.10 running perfectly on my ACER Netbook AOA150.(same specs as OP) I've never been more happy with a Linux distro...camera and everything works.

You do need to make a bootable USB - as these little computers dont have CD drives.

Make sure you do the install without any devices attached (like an external monitor) I think I had trouble installing until I removed my wireless mouse and extra monitor.

One glitch - there is one screen in the installer that doesnt fit right on the netbook screen. Its the one where you can take a picture with the webcam or pick an image...the "Next" button doesnt fit on the screen, so you have sort of guess where your mouse pointer is - and then click.

---

### Post by Hylas de Niall on 2011-10-28
Yeah, better had ;)

---

### Post by Hylas de Niall on 2011-10-28
> **Roving Sign said:**
> I have 11.10 running perfectly on my ACER Netbook AOA150.(same specs as OP) I've never been more happy with a Linux distro...camera and everything works.

You do need to make a bootable USB - as these little computers dont have CD drives.

Make sure you do the install without any devices attached (like an external monitor) I think I had trouble installing until I removed my wireless mouse and extra monitor.

One glitch - there is one screen in the installer that doesnt fit right on the netbook screen. Its the one where you can take a picture with the webcam or pick an image...the "Next" button doesnt fit on the screen, so you have sort of guess where your mouse pointer is - and then click.

The USB route isn't mandatory if (as in my case) an external CD or DVD-RW can be hooked up instead.

I *think* i skipped the user web-cam pic part during install (was it even there on the betas? I can't recall). In any case, it would probably be a case of just hitting 'enter' to accept the default 'next' option anyway   ....or maybe 'alt' and drag with the mouse to be sure?

---


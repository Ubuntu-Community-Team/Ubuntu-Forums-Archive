---
title: "Why is Sabayon so slow?"
date: 2007-08-10
forum: Other OS Talk
---

### Post by miggols99 on 2007-08-10
I wanted to have a look at Sabayon, to see how fast it was. So I download the lite ISO and burned it. Rebooted to find a nice KDE desktop. But it was so slow! If I typed something, I'd have to wait for the system to catch up. Is there a reason why it's so slow? This is the slowest live cd I've ever used!

---

### Post by emrextreme on 2007-08-10
Did you install your video card drivers properly?

---

### Post by Bachstelze on 2007-08-10
Because it has more programs installed than the other Live CDs, thus takes up more memory. That's all...

---

### Post by ThinkBuntu on 2007-08-10
It's generally slow, when you consider that it's based on Gentoo which should at the very least make it nimble. I've moved on...just not a slick OS by any means.

---

### Post by mips on 2007-08-10
> **miggols99 said:**
> But it was so slow! If I typed something, I'd have to wait for the system to catch up. Is there a reason why it's so slow? This is the slowest live cd I've ever used!

I dunno, you might have a bad experience. I find it very fast, much faster than ubuntu and it's derivatives.

You said you type something and it is slow ? Sounds like keyboard input is lagging ? If it is the problem then handy had a similair issue but it was motherboard related.

---

### Post by misfitpierce on 2007-08-10
Yes that LiveCD is more packed with stuff and again is a Live CD. Sabayon is not that slow your HDD as it isnt constricted by the limit of a CD reader. :)

---

### Post by kellemes on 2007-08-11
> **miggols99 said:**
> I wanted to have a look at Sabayon, to see how fast it was. So I download the lite ISO and burned it. Rebooted to find a nice KDE desktop. But it was so slow! If I typed something, I'd have to wait for the system to catch up. Is there a reason why it's so slow? This is the slowest live cd I've ever used!

Surely you understand you can't test it's speed by using the livesystem, right?

Edit: By the way, you're on one of the fastest systems in town, so why consider Sabayon..:grin:

---

### Post by miggols99 on 2007-08-11
> Surely you understand you can't test it's speed by using the livesystem, right?
 
 Edit: By the way, you're on one of the fastest systems in town, so why consider Sabayon..
I usually test distros to see where they are. I personally will probably never switch distros again :D

---

### Post by Toet on 2008-01-06
I have Sabayon installed on my hard disk, 32 bit version 3.4f. It is truly slow. Going to try the 64-bit later on. Is it just KDE that is slow? Normally I use Gnome, but I like the KDE looks and layout of Sabayon, it is to my likings. But hey if it is supposed to be this slow, it's going to be gone quite fast.

I will try somethings this week with Sabayon to see if I can track down the origin of the slowness.

---

### Post by SomeGuyDude on 2008-01-06
> **Toet said:**
> I have Sabayon installed on my hard disk, 32 bit version 3.4f. It is truly slow. Going to try the 64-bit later on. Is it just KDE that is slow? Normally I use Gnome, but I like the KDE looks and layout of Sabayon, it is to my likings. But hey if it is supposed to be this slow, it's going to be gone quite fast.

I will try somethings this week with Sabayon to see if I can track down the origin of the slowness.

I'm running OpenSUSE right now (64-bit KDE) and it's VERY responsive. Startup is about 30 seconds slower, but once it's up it's incredibly snappy. I'm damn impressed and enjoying the experience, although it's not quite as stable as Ubuntu.

Sabayon, on the other hand, was just a nightmare. Even when I installed it on my system it was like the whole thing was coated in molasses.

---

### Post by handy on 2008-01-06
> **HymnToLife said:**
> Because it has more programs installed than the other Live CDs, thus takes up more memory. That's all...

He installed the Lite version.

---

### Post by handy on 2008-01-06
> **mips said:**
> I dunno, you might have a bad experience. I find it very fast, much faster than ubuntu and it's derivatives.

You said you type something and it is slow ? Sounds like keyboard input is lagging ? If it is the problem then handy had a similair issue but it was motherboard related.

My motherboard GA-K8NS Ultra-939 had a problem with a few distro's, Sabayon was one.  Mips pointed me to some info' about the board, the problem is due to the onboard USB.

So I disabled it in the BIOS & installed a PCI USB card.

End of problems with an otherwise great motherboard.

---

### Post by Toet on 2008-01-07
> **SomeGuyDude said:**
> I'm running OpenSUSE right now (64-bit KDE) and it's VERY responsive. Startup is about 30 seconds slower, but once it's up it's incredibly snappy. I'm damn impressed and enjoying the experience, although it's not quite as stable as Ubuntu.

Sabayon, on the other hand, was just a nightmare. Even when I installed it on my system it was like the whole thing was coated in molasses.

So strange. Sabayon is based on Gentoo. So during installation everything should be compiled on the fly. In theory there shouldn't be anything faster.

---

### Post by mips on 2008-01-07
> **Toet said:**
> So strange. Sabayon is based on Gentoo. So during installation everything should be compiled on the fly. In theory there shouldn't be anything faster.

Thats where you are wrong, Sabayon (& Gentoo LiveCD) installs precompiled binaries. During installation nothing is compiled from source. Once you finished your installation and want to add packages via portage it will compile from source.

---

### Post by SomeGuyDude on 2008-01-07
> **Toet said:**
> So strange. Sabayon is based on Gentoo. So during installation everything should be compiled on the fly. In theory there shouldn't be anything faster.

Assuming mips is right, that'd explain it. All I can tell you is my experience, and Sabayon was UNBELIEVABLY slow. And, frankly, ugly as hell, but I was willing to overlook it had the experience been as good as everyone told me it would be.

---

### Post by handy on 2008-01-07
> **mips said:**
> Thats where you are wrong, Sabayon (& Gentoo LiveCD) installs precompiled binaries. During installation nothing is compiled from source. Once you finished your installation and want to add packages via portage it will compile from source.

The recently released Sabayon 3.5 beta has introduced Entropy the Binary Package Managing infrastructure; there are currently 4000 packages suitable for it, with 10,000 promised to be ready by the time that 3.5 is ready for full release.  

That should speed up & simplify the installation process. ***Edit:** Of packages that is.*

On a related topic; In my last install of Sabayon I thought I'd use the KDE desktop, which I used for some months, but really preferred the Gnome front end.  So, I took a chance & did an upgrade install via the DVD & selected Gnome for my default desktop.  I fully expected a failure with this method, but I was curious.  Anyway it worked reasonably well, I did not have to reinstall the programs that I had personally added to Sabayon, & little fiddling was required to get it how I wanted it.  

Except that NOW my Sabayon which was fast is now very slow at loading programs.  It will burn & rip as fast as ever though.  So there is some confusion existing in there somewhere, which is certainly beyond my meager Linux skill to fix.

So after very recently having my first look at Ubuntu on my mac, (again I *had* used Kubuntu 7.10 = buggy), I think I will replace Sabayon with it, Ubuntu 7.10 really is looking good to me.

---

### Post by Toet on 2008-01-07
> **mips said:**
> Thats where you are wrong, Sabayon (& Gentoo LiveCD) installs precompiled binaries. During installation nothing is compiled from source. Once you finished your installation and want to add packages via portage it will compile from source.

Thanks, that explains a lot.

---

### Post by mips on 2008-01-07
> **Toet said:**
> Thanks, that explains a lot.

Which leaves one to wondering why one would actually install from a livecd as it actually negates the source based distro idea. I think if one needs a gentoo system you must do a stage3 tarball install, yes it's harder but thats the whole point is it not (being optimised & compiled from source) ?

---

### Post by Toet on 2008-01-07
> **mips said:**
> Which leaves one to wondering why one would actually install from a livecd as it actually negates the source based distro idea. I think if one needs a gentoo system you must do a stage3 tarball install, yes it's harder but thats the whole point is it not (being optimised & compiled from source) ?
Indeed it leaves to wonder. I think they lost control a bit, cause I've tried it before some time ago, and I do not remember it to be this slow. I think the menu system they have with the KDE desktop is really good, I like it a lot. It's much cleaner and I could see myself going from Gnome to this kind of KDE, not to the default you find in other KDE distro's, that's not my taste.

Anyways, I will try Gentoo some time again, although I'm always stopped by the error's I meet while installing Gentoo. Also could try DIY, after running LFS one time, and only didn't run it after a while, cause there's no package manager. But with DIY I did not yet see the book for the Gnome packages.

More and more after trying one distro after another I like Ubuntu better.

---

### Post by handy on 2008-01-07
I have been on Sabayon for many months, & really like it, it was not slow until I made it that way (see above), it has a few bugs, but don't they all?

I must say that Ubuntu 7.10 is really something, it is the most polished Ubuntu by a long shot in my view.  Kubuntu 7.10 was buggy from my experience, but Ubuntu is slick!

Ubuntu is where my Sabayon box is going soon.

---

### Post by mips on 2008-01-08
> **handy said:**
> I have been on Sabayon for many months, & really like it, it was not slow until I made it that way (see above), it has a few bugs, but don't they all?

I must say that Ubuntu 7.10 is really something, it is the most polished Ubuntu by a long shot in my view.  Kubuntu 7.10 was buggy from my experience, but Ubuntu is slick!

Ubuntu is where my Sabayon box is going soon.

I also never had any speed issues with Sabayon, for me it was faster than Ubuntu and it's offspring.

I agree with your sentiments on Kubuntu. Ubuntu 7.10 is really slick but I still prefer kde.

For now I'm very happy with Arch though (laptop). I already wiped my Kubuntu 7.10 destop and it's awaiting the Arch64 treatment any day now.

---

### Post by handy on 2008-01-08
I have the impression that Arch is a lot easier to handle than Gentoo, as in a lot less time is involved in setting it up?

---

### Post by mips on 2008-01-08
> **handy said:**
> I have the impression that Arch is a lot easier to handle than Gentoo, as in a lot less time is involved in setting it up?

Definately, it is easier & faster than Gentoo to install/setup.

It's fast & I love KDEmod. I have it on my laptop at the moment which is an old clunker and it runs really well. I just followed the the wiki, what it said I did and everything just worked.

I'm going to do Arch64 on my desktop soon and this time I'm using the 31MB FTP image. I found that using the normal  160MB iso a bit of a waste as after installation I update the system and it downloads 100MB of stuff.

I think you should give it a go ;)

---

### Post by sujoy on 2008-01-08
Well my gentoo install from a stage 3 tarball gives me a 27secs boot up in my laptop. Thats pretty fast i guess. :) Yes it does take time it took me about 3 days to set it up properly and just the way i wanted it to be, but then again following the handbook makes it easier.

Will try out arch on my desktop though

---

### Post by handy on 2008-01-08
> **mips said:**
> Definately, it is easier & faster than Gentoo to install/setup.

It's fast & I love KDEmod. I have it on my laptop at the moment which is an old clunker and it runs really well. I just followed the the wiki, what it said I did and everything just worked.

I'm going to do Arch64 on my desktop soon and this time I'm using the 31MB FTP image. I found that using the normal  160MB iso a bit of a waste as after installation I update the system and it downloads 100MB of stuff.

I think you should give it a go ;)

I had a go roughly a couple of months ago, everything went along really nicely & then the time came for the initial update & it turned into a some kind of dependency hell.

After just having spent days on gentoo, & being stopped by what may have possibly been an incompatibility in my BIOS!  I went to another distro' can't remember which, but I know it was easy, or I would remember it's name! :lolflag:

---

### Post by handy on 2008-01-08
I'll give it another go on my Sabayon box, if it works great, if not I'll move on to Ubuntu.

You may hear a cry for help mips... :lolflag:

---

### Post by aeto on 2008-01-08
Uhh...putting Arch in a laptop and Gentoo in a desktop is what would be ideal. The other way around is just a nono. You don't want to kill your laptop. Besides, you don't want to scare away chics in Starbucks.

edit: of course Arch is faster to set up. as fast as Ubuntu, as fast as PCLinuxOS. Wait, i meant fastER. There is no fancy GUI getting in the way, so you have the GUI that you actually want set up in just a few minutes depending on your network connection to the rest of the world.

To be on-topic, my Gentoo DAW (w/ Sabayon overlay) boots in < 25s. Nothing my Arch laptop could beat, no matter the distro. 10000 RPM, 16GB and 4GHz would be a sane bet.

Just because a distro is source-based doesn't mean it has to compile daemons and kernel modules at boot. That would be EmAcS.

---


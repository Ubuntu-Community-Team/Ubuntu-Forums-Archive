---
title: "Haiku OS"
date: 2008-06-29
forum: Other OS Talk
---

### Post by omar8 on 2008-06-29
I just read about an operating system being designed called Haiku OS. Its apparently based on BeOS which is something I have never heard of. 
What's the advantages/disadvantages of this Operating System?

---

### Post by Kowalski_GT-R on 2008-06-29
There are currently no advantages because the project is at it's early stages.

BUT (:-))

It's the continuation of this OS, called BeOS,here: [http://www.youtube.com/watch?v=Zygz77Zz1i8](http://www.youtube.com/watch?v=Zygz77Zz1i8)
It's an impressive demostration.

BeOS gathered an enthusiastic bunch of followers across the years, and a well deserved fame for being very responsive. It was aimed at the end user, giving him great multimedia capability on normal-specced machines. To achieve this goal it was written from scratch, thus not resembling anything available at the time, main feature being the micro-kernel.

Haiku's advantages (should be) the same as BeOS ones:
[http://www.haiku-os.org/](http://www.haiku-os.org/)

google around for more info, it has great potential.

ciao,

Andre

---

### Post by chucky chuckaluck on 2008-06-29
i like the leaves.

---

### Post by pelle.k on 2008-06-29
> I just read about an operating system being designed called Haiku OS. Its apparently based on BeOS which is something I have never heard of.
What's the advantages/disadvantages of this Operating System?

Check this thread out, lots of nice info about beos / haiku; [http://ubuntuforums.org/showthread.php?t=231297&highlight=haiku](http://ubuntuforums.org/showthread.php?t=231297&highlight=haiku)
Some quotes;
> **free10 said:**
> I think you have to look back more at what BeOS, rather than Haiku now, can do to see the best picture to see how BeOS stacked up to those versions 5 years ago. Yes, those others versions advanced but so has the new open sourced Haiku version in a number of ways, but the more finished version of it is not available for direct comparisons.

Lets look at boot times, from cold start to on the Desktop for BeOS for older or newer versions of Linux/windows or Max. Boot times for most "old" computers from 7 years ago was around 30 seconds, for a BeOS machine. This is about what I saw with a 566 celeron and 128mbs of memory and a 8mb graphics card back then and the new Haiku claims 10-15 seconds or maybe faster.

OK the old BeOS had the ability to play 7 movies at once, or to look at it another way a movie, a song, a browser window open, email, ect, without slowing and bogging down even on old old slow hardware let alone not crashing like other systems may do. If one app crashed it usually does not take the whole system down, and you just kill and restart the app and this can all be done without using the command line/terminal interface in seconds. Most apps open almost instantly with BeOS. Now how do older versions of Linux, Windows, or Apple compare with this, or even the newer versions on much faster hardware?

OK upgrading and new software and hardware drivers with BeOS. Basically click and installed automatically. Right now I have 18 updates with Ubuntu I am avoiding installing with Ubuntu because I have a Nivida card and the Kernel update may bork the whole system making Ubuntu unbootable and unlike like BeOS Linux does not have an easy way to fix that, if it happened and still get back on the Desktop. With BeOS we had a Vesa compliant system or driver, which means we could boot with any video card that supported the Vesa standards, even without the correct driver loaded and then find the correct driver and load it to our machines and do it all very simply without opening a terminal. It was designed to make everything simple and easy and very stable. Most things by the way do not require a reboot with BeOS to take effect either. Most new drivers are stored in a temporary file, so if one gives problems you can just reboot and click don't load those drivers to get rid of the problem and then delete the offending new one, once back on the desktop solving the problem. Unlike Linux no permissions needed to do almost everything. You control out of the box. It is just not that finicky and easy usually to fix, if you mess something up usually.

All apps for BeOS have to have 2 threads and 8 is the norm for it, which means much faster on the apps, especially if your machines have multi CPUs or cores and I believe it is all 64 bit too except for the 32 bit core. I have heard but don't for sure it is easier to develop new software for it, or to port other software to it compared to other systems because of the way it is designed. How true this is now is hard to say.

Haiku should be the new and improved version of BeOS. You didn't have to reformat every so often with BeOS. Few bothered defraging their BeOS drives while others recommended doing it every so often.

The real question maybe should be this. What can Linux, OSX, and Windows do, that BeOS or Haiku can do now or in the past and what still they can't or don't do as well after all these years. BeOS and Haiku problems have been mainly the lack of hardware drivers and apps written for it in the past. The open source community mainly complained the BeOS kernel was not open source, but because of contracts and copyrights and NDAs it couldn't be, but now that argument goes out the window with the new Haiku kernel with its MIT license.

What will Haiku do better in the end depends on the software  apps written for it or ported over for it along with the drivers. Its structure or nature is to do everything better for the end user, from what I have seen and really for the developers of software too. They have one thing or system to write for basically and not many. Anything running on it should be faster and maybe much much faster and more stable. The end user with the drivers and software would find themselves in control of a very fast system that they would learn is more stable and they don't have to worry about as much when they use it, as they do with other systems. No new expenses on hardware that they need to buy, because of new software being used running slow. Hardware would be replaced when it broke or when they flat wanted something new. They may go years and years and never use the terminal or command line. Anything connected to large data translations be it music, graphics, or movies should all go much faster and not slow everything else down while it is happening and even more so on the new dual and above CPU core systems coming out and being bought.

Ease of use, speed, and stability is all that can be gained compared to the alternatives along with lower costs and you leave a lot of problems behind. You know if you switched it around ask what is better about the alternatives, and rule out eye candy, apps, or hardware drivers so you are talking about the basic structure of a system you build from and will use, then you see the real difference of where the advantages lie

---

### Post by cardinals_fan on 2008-06-29
Haiku is becoming very stable now.  They fixed their biggest bug earlier this year.  Hardware support is an abomination, but it's a very fun OS to play with in a virtual machine.  You can download a preconfigured VMware image from their site.  I've always been impressed with Haiku's elegance and speed.

---

### Post by Ptero-4 on 2008-06-30
The good: Microkernel, fast performance.
The not-so-good: Uncustomizable GUI, no desktop effects.

---

### Post by init1 on 2008-07-01
> **cardinals_fan said:**
> Haiku is becoming very stable now.  They fixed their biggest bug earlier this year.  Hardware support is an abomination, but it's a very fun OS to play with in a virtual machine.  You can download a preconfigured VMware image from their site.  I've always been impressed with Haiku's elegance and speed.
Yeah, most distros have a trouble loading in Qemu, but Haiku loaded fine. I look forward to the day when Haiku is stable and can be loaded from a CD.

---

### Post by cardinals_fan on 2008-07-01
> **init1 said:**
> Yeah, most distros have a trouble loading in Qemu, but Haiku loaded fine. I look forward to the day when Haiku is stable and can be loaded from a CD.
I run their preconfigured VMware image in VMware Player.  The only thing I use Qemu for is Windows XP - it hates VMware for some reason.

---

### Post by pelle.k on 2008-07-01
Haiku is *dog* slow in qemu compared to vmware/virtualbox.
btw, check this out; [http://www.haikuware.com/view-details/development/app-installation/senryu-virtual-box-edition](http://www.haikuware.com/view-details/development/app-installation/senryu-virtual-box-edition)
there is vmware and qemu images as well. Some apps are quite dated (from the old beos days), but it's only meant be a demonstration anyway.

---

### Post by MaxIBoy on 2008-07-01
So it's still not mature enough to run on a physical computer most of the time? Or is it? Can I get a bootable CD for it? I really wouldn't mind a stable, crash-proof OS. Something that was responsive and fast-booting on such hilariously outmoded hardware is something I would seriously look into. 


One thing I want to know is, is there a Linux runtime for Haiku? I'd like to be able to run Linux applications on it.

---

### Post by cardinals_fan on 2008-07-01
> **MaxIBoy said:**
> So it's still not mature enough to run on a physical computer most of the time? Or is it? Can I get a bootable CD for it? I really wouldn't mind a stable, crash-proof OS. Something that was responsive and fast-booting on such hilariously outmoded hardware is something I would seriously look into. 


One thing I want to know is, is there a Linux runtime for Haiku? I'd like to be able to run Linux applications on it.
It's not so much the stability causing problems.  It's more the horrible hardware support.  And no, there's no Linux compat layer (yet).

You could look into NetBSD.  It's also fast and is incredibly stable.

---

### Post by MaxIBoy on 2008-07-02
I will, thanks.

Heck, I'll check Haiku out anyway. If it's free, I've got nothing to loose. I've got an extra partition on my laptop for distro hopping, my main one is reserved for Ubuntu.

---

### Post by pelle.k on 2008-07-02
> Can I get a bootable CD for it?
No. for the simple reason that the developers don't think it's mature enough to be tested by the general public.

---

### Post by MaxIBoy on 2008-07-02
That's a red flag for me. I don't like setting things up manually, because I typically screw it up. The first time I tried to partition my hard drive, I messed up my MBR somehow.

(The netBSD installer CD doesn't seem to have an option to use an existing partition-- at least, I got too scared to continue when it only detected one hard drive and offered to use the hard drive.)

---

### Post by cardinals_fan on 2008-07-02
> **MaxIBoy said:**
> That's a red flag for me. I don't like setting things up manually, because I typically screw it up. The first time I tried to partition my hard drive, I messed up my MBR somehow.

(The netBSD installer CD doesn't seem to have an option to use an existing partition-- at least, I got too scared to continue when it only detected one hard drive and offered to use the hard drive.)
You have to partition it with cfdisk - which should have launched when you selected your disk.  NetBSD takes some initiative.

---

### Post by MaxIBoy on 2008-07-02
I was too scared to select a disk, I didn't want to go on until I knew that it wasn't going to reformat the whole thing.

---

### Post by hanzomon4 on 2008-07-03
> **cardinals_fan said:**
> It's not so much the stability causing problems.  It's more the horrible hardware support.  And no, there's no Linux compat layer (yet).

You could look into NetBSD.  It's also fast and is incredibly stable.

I agree and in the current computer industry climate haiku won't get no kinda support from vendors....

---


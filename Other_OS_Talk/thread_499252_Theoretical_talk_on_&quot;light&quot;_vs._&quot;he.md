---
title: "Theoretical talk on &quot;light&quot; vs. &quot;heavy&quot; distros"
date: 2007-07-12
forum: Other OS Talk
---

### Post by timzak on 2007-07-12
It seems that more and more "light" distros are popping up these days.  Puppy, DSL, antiX, Zenwalk, Xubuntu, Fluxbuntu, etc.  I've had an opportunity to try some out on some slow (500ish Mhz) computers and noticed that while memory consumption is lower, processing time doesn't seem any quicker given the same app.  I'm still pegging 100% usage with most tasks (at least with newer applications).

This got me thinking.  What do you guys think?  Given the SAME computer, the SAME application run on each of the above distros, vs. running that app on something like Ubuntu, provided that RAM is available, would the same app feel faster on one of the light distros as opposed to Ubuntu?

Let's say I want to run Gimp.  I have a 500 Mhz machine with 256 MB ram.  I install each OS and run Gimp.  I make sure the work I am doing in Gimp does not consume more than the available memory (to factor out swap partition hits).  Do you think something like Puppy will run Gimp faster than Ubuntu, given that the swap partition is not being accessed?

My theory is that these light distros only feel faster because 1) they consume less RAM off the bat, leaving more available for apps, and 2) they default to lighter-weight apps.  If this is true, then in theory you could run the lighter-weight apps in a "heavier" OS and have the same "feel."  Or you could use a lightweight OS with a heavier app and notice that the OS doesn't feel any faster than a heavier OS.

Does that seem a fair theory?

---

### Post by LaRoza on 2007-07-12
I would gauge "light" and "heavy" based on where they work. If I can get certain distros to boot on computers with little RAM, I consider it "light". If it doesn't work, it is "heavy".

This really depends on the computer of course, so the generic titles "heavy/light" probably refer to an "average" computer, probably 512 MB of RAM.

-edit The apps will be the same no matter what OS is being used, a lighter distro will use less RAM so more will be available for apps, but the processor doesn't benefit. GIMP is GIMP no matter what distro.

---

### Post by timzak on 2007-07-12
That's pretty much how I feel.  So if you have Xubuntu running and all it does is run Rhythmbox and it can do so without running out of ram, there will be no benefit to switching to a lighter distro if you're still going to be running Rhythmbox on it.

---

### Post by ThinkBuntu on 2007-07-12
It's not like these guys are reprogramming these apps to make them lighter, so GIMP launches at similar speeds whether you're using Zenwalk or Ubuntu. But by making a system lean, there are fewer background processes that are often unnecessary, which results often in better performance. I can assure you that Debian is far faster than Ubuntu, and that Zenwalk and Arch are very speedy, and that it's not an illusion.

---

### Post by LaRoza on 2007-07-12
> **ThinkBuntu said:**
> I can assure you that Debian is far faster than Ubuntu, and that Zenwalk and Arch are very speedy, and that it's not an illusion.

I can assure you that Vista with Aero off and installed is slower than Feisty Live with desktop effects enabled on the SAME computer.

---

### Post by igknighted on 2007-07-12
> **timzak said:**
> That's pretty much how I feel.  So if you have Xubuntu running and all it does is run Rhythmbox and it can do so without running out of ram, there will be no benefit to switching to a lighter distro if you're still going to be running Rhythmbox on it.

The idea of a "lighter distro" is a bit misleading.  There certainly are processor factors involved, but none that you cannot adjust on any distro.  Ubuntu could easily run as light as a DSL if you turned off functions that DSL already has turned off.  So "lighter" really just means the default state, nothing inherent to the distro itself.

Some of the tweaks could turn off background systems that could be using processor time.  I'll pick CUPS as an example (I think Ubuntu has this on by default, and if all you do is use the PC for music, it isn't much use)).  If you disable CUPS and other printing subsystems, Ubuntu will speed up and the processor cycles will be released to the system (and RAM as well).  Bluetooth as well.  Also beagle (lots of processor time here).  Many would say suse is "heavy", but if you only install the basic packages (say a no gui webserver) it can install on a very low spec machine and run fine, and you can add whatever GUI (flux, ice, etc.) later if you so choose.  Many would say Xubuntu is light, but if you added bluetooth and other systems it could become fairly heavy, even with Xfce.  So (once again), "lighter" just implies the default state, nothing inherent about the distro.

EDIT: The only inherent differences are with compiling.  Arch is (I believe) compiled to be quicker, and I know if you run Gentoo a lot of the speed comes from custom compiling.  Granted you could recompile a Ubuntu install, but now thats just crazy talk :)

---

### Post by timzak on 2007-07-12
> **ThinkBuntu said:**
> It's not like these guys are reprogramming these apps to make them lighter, so GIMP launches at similar speeds whether you're using Zenwalk or Ubuntu. But by making a system lean, there are fewer background processes that are often unnecessary, which results often in better performance. I can assure you that Debian is far faster than Ubuntu, and that Zenwalk and Arch are very speedy, and that it's not an illusion.

Wait, first you say the same app will run at similar speeds whether on Zenwalk or Ubuntu then you say that Zenwalk is far faster than Ubuntu?  Can you expand on that?

---

### Post by ThinkBuntu on 2007-07-12
> **timzak said:**
> Wait, first you say the same app will run at similar speeds whether on Zenwalk or Ubuntu then you say that Zenwalk is far faster than Ubuntu?  Can you expand on that?
Put simply, Zenwalk bundles less crap, and is based on Slackware, which many consider to be the fastest base.

---

### Post by ThinkBuntu on 2007-07-12
> **igknighted said:**
> EDIT: The only inherent differences are with compiling.  Arch is (I believe) compiled to be quicker, and I know if you run Gentoo a lot of the speed comes from custom compiling.  Granted you could recompile a Ubuntu install, but now thats just crazy talk :)
I once heard that real speed benefits come more from compiling the system's core than from compiling applications, and that the kernel is especially helpful to compile. I custom-compiled Bluefish in Sabayon, and it started no faster than Ubuntu.

---

### Post by igknighted on 2007-07-12
> **ThinkBuntu said:**
> I once heard that real speed benefits come more from compiling the system's core than from compiling applications, and that the kernel is especially helpful to compile. I custom-compiled Bluefish in Sabayon, and it started no faster than Ubuntu.

Yes, but a lot of that is the size of the kernel when loaded to memory.  Also, the less driver modules it loads the quicker it will start up.  I think you can gain performance both ways, by tweaking what gets compiled into the kernel, and the optimizations (i386 vs. i686 vs. k8 (athlon64/opteron)) used in both the kernel compile and the applications.  Arch is i686 optimized, Ubuntu is i386 optimized.  i386 works, but an i686 optimization makes better use of the newer processors.  I don't think you could really ever release a distro custom compiled for higher end AMD chips (k8), but if you could you would see more improvements (thats what I compile my kernels for).  In the end, on high end machines they go so fast anyways that the difference is small and not usually noticed.  But if you were to custom compile apps and a kernel on a 300mhz pII you would probably see improvements by using better optimizations.  I would recommend having a faster PC available to donate cycle times for this, however... that pII will take forever to compile "hello, world!".

---

### Post by igknighted on 2007-07-12
> **LaRoza said:**
> I can assure you that Vista with Aero off and installed is slower than Feisty Live with desktop effects enabled on the SAME computer.

IDK what computer that is... pIII @ 1.5 ghz, 512mb ram maybe?  Vista (with aero) ran just fine for me on the Athlon PC in my sig (a solid machine, but nothing amazing).  It was not super crisp, but better than any live cd (with or without desktop effects) that I have ever used.  Then again, even beryl/compiz isn't incredibly crisp either.  Yes, Vista needs a lot of hardware... but it hardly falls into the discussion, there really isn't any need to bash on a fairly decent OS for no reason when the discussion centers around hardware that OS was never designed to run on.

---

### Post by smoker on 2007-07-12
puppy linux loads completely into ram on boot (approx 80MB), therefore, if you have enough ram spare after puppy has loaded, i would imagine it to be one of the fastest distros around.

it is the fastest i have tried, though the only extras i've added are also lightweight, but i believe heavier apps like openoffice and gimp are available from puppy's pupget or other repositories.

---

### Post by Altarbo on 2007-07-12
> **timzak said:**
> [ . . .]

My theory is that these light distros only feel faster because 1) they consume less RAM off the bat, leaving more available for apps, and 2) they default to lighter-weight apps.  If this is true, then in theory you could run the lighter-weight apps in a "heavier" OS and have the same "feel."  Or you could use a lightweight OS with a heavier app and notice that the OS doesn't feel any faster than a heavier OS.

Does that seem a fair theory?This is exactly what I'm doing now.  Just download the .iso for sever install (provided your distributor has one) and only install the software you need.

This worked really well for me, because I scrapped a computer that a friend of mine was going to threw out, for parts, and got a decent Nvidia card and a 128MB RAM stick.  But my processor is still the original and _slow_ so things like Nautilus that would be bad for low RAM, are just fine for me.  And compiz/beryl could be awful for an old computer, but is great for me, because I can offload some work onto my video card.

Some fast/light distros compile from source.  This actually will make the same app run faster, but it's a double-edged sword, because the slower your cpu the longer compilation time takes.  With apt-get it only takes a few hours for me to download, install, and set up everything I need to have a functional, x-based desktop.  With Gentoo it took days.

- Altarbo

---

### Post by RAV TUX on 2007-07-12
> **timzak said:**
> It seems that more and more "light" distros are popping up these days.  Puppy, DSL, antiX, Zenwalk, Xubuntu, Fluxbuntu, etc.  I've had an opportunity to try some out on some slow (500ish Mhz) computers and noticed that while memory consumption is lower, processing time doesn't seem any quicker given the same app.  I'm still pegging 100% usage with most tasks (at least with newer applications).

This got me thinking.  What do you guys think?  Given the SAME computer, the SAME application run on each of the above distros, vs. running that app on something like Ubuntu, provided that RAM is available, would the same app feel faster on one of the light distros as opposed to Ubuntu?

Let's say I want to run Gimp.  I have a 500 Mhz machine with 256 MB ram.  I install each OS and run Gimp.  I make sure the work I am doing in Gimp does not consume more than the available memory (to factor out swap partition hits).  Do you think something like Puppy will run Gimp faster than Ubuntu, given that the swap partition is not being accessed?

My theory is that these light distros only feel faster because 1) they consume less RAM off the bat, leaving more available for apps, and 2) they default to lighter-weight apps.  If this is true, then in theory you could run the lighter-weight apps in a "heavier" OS and have the same "feel."  Or you could use a lightweight OS with a heavier app and notice that the OS doesn't feel any faster than a heavier OS.

Does that seem a fair theory?

The best "light" distro and the only one that you will see an appreciable difference on & it's based on Slackware:

[Wolvix]("http://wolvix.org/")

&

[Wolvix Cub]("http://wolvix.org/")

---

### Post by ThinkBuntu on 2007-07-12
> **RAV TUX said:**
> The best "light" distro and the only one that you will see an appreciable difference on is based on Slackware:

[Wolvix]("http://wolvix.org/")

&

[Wolvix Cub]("http://wolvix.org/")
I ran the LiveCD out of curiosity after hearing RAV's raves, but I couldn't find intuitively how to install it. Of course, I could've looked it up online. Seemed like a nice distro though. Very well put together Xfce, in my opinion.

---

### Post by RAV TUX on 2007-07-12
> **ThinkBuntu said:**
> I ran the LiveCD out of curiosity after hearing RAV's raves, but I couldn't find intuitively how to install it. Of course, I could've looked it up online. Seemed like a nice distro though. Very well put together Xfce, in my opinion.
Wolvix has the easiest install system I have encountered, you can easily do a full install or a USB install, simply through the Wolvix control center.

See the screenshots below:

---

### Post by ThinkBuntu on 2007-07-13
> **RAV TUX said:**
> Wolvix has the easiest install system I have encountered, you can easily do a full install or a USB install, simply through the Wolvix control center.

See the screenshots below:
Cool. Maybe down the road I'll give it a serious go, because I'm really starting to get on the Xfce bandwagon. As I learn more Unix skills, my tastes in a desktop are certainly changing, and I really enjoy using this DE. I can't live with any of *Box environments, because I do enjoy a standard-style desktop, but still, the lighter the better. The drop-off in functionality from GNOME to Xfce is trivial compared to the physical space needed and RAM usage.

---

### Post by RAV TUX on 2007-07-13
> **ThinkBuntu said:**
> Cool. Maybe down the road I'll give it a serious go, because I'm really starting to get on the Xfce bandwagon. As I learn more Unix skills, my tastes in a desktop are certainly changing, and I really enjoy using this DE. I can't live with any of *Box environments, because I do enjoy a standard-style desktop, but still, the lighter the better. The drop-off in functionality from GNOME to Xfce is trivial compared to the physical space needed and RAM usage.

I would say the transition from GNOME to XFCE is probably the easiest to make....


Much like the transition from Fluxbox to e17.

---

### Post by LaRoza on 2007-07-13
> **igknighted said:**
> IDK what computer that is... pIII @ 1.5 ghz, 512mb ram maybe?  Vista (with aero) ran just fine for me on the Athlon PC in my sig (a solid machine, but nothing amazing).  It was not super crisp, but better than any live cd (with or without desktop effects) that I have ever used.  Then again, even beryl/compiz isn't incredibly crisp either.  Yes, Vista needs a lot of hardware... but it hardly falls into the discussion, there really isn't any need to bash on a fairly decent OS for no reason when the discussion centers around hardware that OS was never designed to run on.

2 gigs of RAM, 2.8 Ghx Dual core processor, good video card.

vista was prinstalled, so a foreign OS on a live disk with memory intense features enabled performing better was significant.

---

### Post by igknighted on 2007-07-14
> **LaRoza said:**
> 2 gigs of RAM, 2.8 Ghx Dual core processor, good video card.

vista was prinstalled, so a foreign OS on a live disk with memory intense features enabled performing better was significant.

Driver issues then perhaps?  If it was an Nvidia card then that is very possible, it took nvidia months to make a decent Vista driver.

I ran Vista on far less and it worked great (with Aero), so I am baffled by your experience.

---

### Post by necrolin on 2007-07-19
> **igknighted said:**
> Driver issues then perhaps?  If it was an Nvidia card then that is very possible, it took nvidia months to make a decent Vista driver.

I ran Vista on far less and it worked great (with Aero), so I am baffled by your experience.

I just got a computer 3 months ago with Vista pre-installed. It's running Ubuntu now because the live cd was faster than Vista running from the hard drive. It seems that depending on the hardware Vista runs either very well or.... not so well (using nice words because I'm a nice guy)  =) . It doesn't always seem to be about how powerful the hardware is either. So, I think that I agree that the problem probably lies somewhere is the drivers, but I'm not surprised when I hear of bad performance with Vista.

The whole light vs heavy distro can be summed up though something like this:

1) Fewer services/deamons/processes running with free up system resources and make the machine run faster
2) Using less hardware intensive applications (blackbox vs Gnome for example) will help too
3)  Recompiling your core software (mainly your Kernel) will also make the machine run better

But honestly, if you have to be getting into things like this to get your system to work well then you should just upgrade your hardware and then do the above if you want to squeeze the last bit of performance possible out of your hardware. Just my opinion.

---


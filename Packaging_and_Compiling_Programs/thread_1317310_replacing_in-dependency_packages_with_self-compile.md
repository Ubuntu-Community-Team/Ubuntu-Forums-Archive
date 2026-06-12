---
title: "replacing in-dependency packages with self-compiled _safely_"
date: 2009-11-06
forum: Packaging and Compiling Programs
---

### Post by RaumTrug on 2009-11-06
Hello there!

my problem is the following: I want to replace 2 packages that are in middle of dependancy chains with self-compiled versions. I want to make sure that the former official packages are completely removed before replacement without having to uninstall other packages that depend on them (the compiled ver.s will be compatible!). I want to be able to track updates that might happen, i.e. I want to watch that the compiled version won't get overwritten by automatic updates, until I find the relevant things I fixed are also fixed in the official version - then I'd wish to uninstall my homegrown stuff and join in the normal package system again!

i.e. I want to replace something broken with my own fixed, but want to be able to revert that action easily in case any problems occurr or the main version gets fixed finally :)

the packages in question are libjack and jackd, I want to fix a bug that prevents input-only alsa devices being selected as master device without using another device as output (because that leads to problems...).

thanks for any help, I'm willing to learn anything, however complicated, to get this done!

---

### Post by SevenMachines on 2009-11-07
Probably the simplest way to do this is to 

$apt-get source jack

then add a patch to debian/patches that fixes your bug if you have one
you can then 
$dch -i 
to add a changelog entry, i'd also add a ~yourname1 to the package version

then 
$debuild -b -us -uc

this should give you some nice new fixed packages. 
if you install these, then you can lock the package using synaptic or just be careful when updating so that the packages arent overwritten until you want them to be.

Ideally, open a bug on jack if there isnt one already and try to get it fixed in ubuntu too!

see the [packaging guide]("https://wiki.ubuntu.com/PackagingGuide/Complete")

---

### Post by SevenMachines on 2009-11-07
I suggest the packaging route only because the other way involves removing jack packages and 'make install' your own, perhaps using checkinstall to allow easy removal, its just likely to be a lot more messy that way, although you might prefer that if your comfortable with it

---

### Post by RaumTrug on 2009-11-07
thanks for the quick response!

I'll fresh-install 9.10 in the next days & test my "fix" properly before I'll engage launchpad with a ticket (once I found out how this linux stuff works, I'm quite new to the usual practices!). I remember it worked with 8.10

anyhow, I just found out that 9.10 uses version 116.1 of jack, while I'd like to use version 1.9.3 (also called jack2/jackdmp) instead because it comes with a nice tool (audioadapter) to integrate multiple sound devices, that worked much better for me than alsa_out that comes with jack1! it suffers the same bug, as both versions use the same alsa driver code.

so my problem extends a little above just apt-getting the sources package, fixing them, and then reinstalling the fixed...with just over-installing jack2 over jack 116 I've been having problems (certain drivers/modules from the old install remained and broke the new install, just apart from this not being clean at all!!!).

so my idea on how to do it quick & messy would be:

1.) to lock the old jack packages (it's done in synaptic in the packages menu, right?), 
2.) uninstall them in order to wipe all of their files (can this be done cleanly somehow without removing the locked package-infos that are needed to let other installed jack clients live on? in "worst" case I'd just delete all installed files...)
3.) "./waf install" jack2!

or are there better ways to get the thing up cleanly (expecially for removing the standard install without breaking the package dep.-chain)?

of course using packages is always the best idea, but tedious to learn to set up; also I'm confused a little about the "waf" build system jack2 is using, does anyone have clues/links on how such systems (like scons, too) can be used to create packages?

thanks for the help anyways, expecially for the link to the packaging guide...I'll try to dig in, but it seems a very complex matter with lot's to learn!

---

### Post by SevenMachines on 2009-11-07
since theres no jack2 package, and jack2 seems in the experimental stage, it makes things a little trickier and leaves a lot of stuff in your own hands, i can imagine there might be a few problems.

you can use checkinstall with --provides and --requires to build a simple pseudo package that can integrate with the package manager which might make things a little simpler with dependencies in apt while trying to replace the available jack packages but i dont know the slightest thing about 'waf' so I dont know if itll work with that build system

all in all i think its most likely you'll need to do pretty much all of this manually by straight source install, if you install it to /usr/local and then edit whatever various configuration files you need to by hand then that might be the safest and easiest way to get it up and running

---


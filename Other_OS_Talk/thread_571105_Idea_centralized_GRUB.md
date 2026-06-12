---
title: "Idea: centralized GRUB"
date: 2007-10-08
forum: Other OS Talk
---

### Post by jinx099 on 2007-10-08
I have an idea for those of us who like to use multiple distros on 1 PC.  I use 1 swap partition for all my distros, so I was thinking, why not have a common /boot partition for all distros as well.  Some distros require a seperate /boot anyway.

So wouldn't it be cool if GRUB was centralized to one partition and each distro created its own menu.lst.(distro) file on the partition.  That way grub could put all the menu.lst.* files together to make it easy to boot multiple distros without playing the chainloader game.

I don't think setting up chainloading is hard to set up, it just seems a centralized solution would be much cleaner and easier to manage.

Anyone like or hate the idea?

---

### Post by Dimitriid on 2007-10-09
Well you could just use a very minimal Linux distro ( under 50mb ), set it up a few mb for it and remove it from grub once your other distros are up ( or just move it down the list ).

If you dont want trouble with the rest of your distros just tell your other distros to install their own grub so the Main grub sends it to the distro grub. That way all upgrades would be smooth too. ( you can set subsequent "grubs" from each distro to not display grub menu and time out in like 1 second so it would only add 1-2 seconds to your boot process )

---

### Post by jinx099 on 2007-10-09
> **Dimitriid said:**
> Well you could just use a very minimal Linux distro ( under 50mb ), set it up a few mb for it and remove it from grub once your other distros are up ( or just move it down the list ).

If you dont want trouble with the rest of your distros just tell your other distros to install their own grub so the Main grub sends it to the distro grub. That way all upgrades would be smooth too. ( you can set subsequent "grubs" from each distro to not display grub menu and time out in like 1 second so it would only add 1-2 seconds to your boot process )

Yes, chainloading, I know, this is what I use.  I am thinking of something automatic.  Say you install ubuntu and have other distros already there, during the install you just point it to the existing /boot and it takes care of the rest.

That way, new kernel upgrades would update the central grub list instead of thier own chainloaded grub.

---

### Post by igknighted on 2007-10-09
> **jinx099 said:**
> Yes, chainloading, I know, this is what I use.  I am thinking of something automatic.  Say you install ubuntu and have other distros already there, during the install you just point it to the existing /boot and it takes care of the rest.

That way, new kernel upgrades would update the central grub list instead of thier own chainloaded grub.

I would wait for grub2 before you suggest anything radical.  Grub in its current iteration isn't really under development anymore from what I understand.

What you are suggesting is certainly possible, but would require certain re-writes to the code and would need to be included in every distro... not really feasible.  Remember that grub is not simply a linux bootloader.  What might be feasible would be to run a script that parses all the menu.lst files and adds them to one central one... but even that would cause issues with getting the drive naming done properly.

To be honest, I liked your idea at first glance.  But thinking about the logistics and the problems you would need to overcome, the chainloader is simply the better solution.  You add the chainloader entry and it does all the kernel entries automagically already, just that one initial step.

---


---
title: "I need gcc 3.4.3 back"
date: 2007-04-26
forum: Programming Talk
---

### Post by zenkaon on 2007-04-26
Hello everyone,

First of all let me say that I love the feel of kubuntu 7.0.4. I have been using either suse or red hat for years and decided to give ubuntu a go. I have to say that apt-get is amazing, I must have spent months of my life trying to get rpms to install, hunting down libraries from other rpms, and so on until you want to scream.

My only problem (amazing - I only have 1 issue with ubuntu - it all just works!!) is that my code was written on RHEL4 using gcc 3.4.3 and crashes horribly when I compile it with the gcc 4.1.2 from ubuntu.

So how do I downgrade back to gcc 3.4.3?

Please note that going through my 10000+ lines of code and changing things is not an option. The problem is related to strings and stringstreams, which I use everywhere. I have also to run this programme on several PC's. The main PC being a 4-processor beast that is running RHEL3 (gcc 3.3.3). This PC will definitely not be changing from red hat.

Cheers
John

---

### Post by jespdj on 2007-04-26
Just use Synaptic to uninstall gcc 4.1.2 and install gcc 3.4.3? AFAIK gcc 3.4 is still available in the package management system.

---

### Post by zenkaon on 2007-04-26
Ah ha - solved this one with:

sudo apt-get remove gcc
sudo apt-get install gcc-3.3

I love apt-get, when removing gcc4 it tells you what depends on gcc and also removes those packages!!

I don't think I'll ever go back to red hat now

---

### Post by wmcbrine on 2007-04-26
You don't even have to uninstall gcc-4. You can run them side-by-side. (Just invoke the old compiler as "gcc-3.4" instead of "gcc".)

But you should still fix your bugs.

---


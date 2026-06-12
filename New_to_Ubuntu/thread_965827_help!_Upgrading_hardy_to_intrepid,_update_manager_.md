---
title: "help! Upgrading hardy to intrepid, update manager froze the system halfway through :S"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by zsouthboy on 2008-10-31
Hardy AMD64

I have fakeraid installed on two drives - raid 1 (home directory is mounted on the raided drives, / is on a separate 60 gb drive)
Vmware server is installed

Those are the only deviations from a normal hardy install.

I ran the update manager, and as I said in the topic, after downloading, it looks like it froze installing at "kvm" with about 5 minutes left.

The screen is not being repainted if i drag the window around - the process hung. Hung the entire machine, wasn't even able to ctrl-alt-delete it :S had to cut power.

Now, upon boot, I can't get in via the latest kernel entry in grub - kernel panic, couldn't load vfs at (0,0)

Next, tried getting in via the latest hardy kernel - that boots, but brinks me to a blank orange screen (looks like it's trying to start GDM?)

I can still SSH in, I tried that, but I don't even know where to begin to try fixing this. It shouldn't have died during the upgrade.

EDIT: Was unable solve this problem. Ended up formatting and starting over after getting the files i needed off.

---

### Post by talsemgeest on 2008-11-01
Well, I guess your system if half Hardy and half intrepid. It's little wonder that it can't start.

If I was in your position, I would boot a live cd and back up all my stuff, then do a clean install of intrepid.

---

### Post by wordchisler on 2008-11-01
My system froze on upgrade also, but at a different point (libhal) resulting in the same kernel panic issue. Is there an issue with intrepid ibex?

I dualboot with windows and share a data partition, so I can actually access most of my files. I just hope with a liveCD I can save the mysql databases from my private server and, if possible the virtualbox drive. 

Hope ibex is worth all this. :)

---

### Post by cosmoshell on 2008-11-01
well pulling the plug isent usely good dont know if this could help next time [http://www.freesoftwaremagazine.com/columns/closing_down_gnu_linux_safely_with_sysrq+](http://www.freesoftwaremagazine.com/columns/closing_down_gnu_linux_safely_with_sysrq+)

can you do a crtl-alt-f1 or f2 f3 f... maby login that way and sudo dpkg --configure all
then sudo apt-get dist-upgrade

---

### Post by zsouthboy on 2008-11-01
I ended up ssh'ing in, and copying all the files i needed onto a USB hard disk.

Installed Intrepid cleanly this morning and am trying to get the system to back to where it was. (good god, networkmananger is terrible)

I will now be much more cautious when using dist-upgrade in the future, I think'll wait a week or two to see what other people end up with.

---

### Post by talsemgeest on 2008-11-01
I would always suggest against doing the dist upgrade. It is a very risky process, there is a BIG chance that it will go wrong. I would suggest that at the next release, you just back up your files and do a clean install from the Ubuntu CD. It is much safer.

---

### Post by wordchisler on 2008-11-01
> **talsemgeest said:**
> I would always suggest against doing the dist upgrade. It is a very risky process, there is a BIG chance that it will go wrong. I would suggest that at the next release, you just back up your files and do a clean install from the Ubuntu CD. It is much safer.I upgraded to hardy via CD, and that went well. If the network upgrade hadn't been listed as the "recommended" method, I would have burned a CD this time, too. Learned the hard way, I guess.

---


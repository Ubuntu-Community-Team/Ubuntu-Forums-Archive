---
title: "Installing 8.04 without trashing everything else"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by rock-hopper on 2008-04-26
Hello, everyone.  I have spent an absolute age trying to find the solution to my problem and have got nowhere with it, so, in desperation, I bring it to you.

I realise that this question will firmly establish me as an eternal stupid newbie, and probably as someone who should never have left the safe, vanilla world of Windows.

I have 7.10 installed on its own HDD with GRUB, as well as having XP installed, again on its own drive with its own boot-loader; I choose which OS I want to use from the Boot Menu option at start-up.

My Ubuntu HDD is partitioned /dev/sdb1 Linux, /dev/sdb2 Linux swap and /dev/sdb3 Linux, with the first as System, the second as Swap and the third as Home, on which I have a lot of stuff and I would rather not go through all the trouble of copying it all off, re-partitioning and copying it all back again if I can avoid it.

Is there any way in which I can just install 8.04 in /dev/sdb1 without trashing everything else?  Any help would be really welcome.  If you *can *help, please try to use words that an MS thrall might understand!

Thank you in anticipation, rock-hopper (clueless).

---

### Post by Aurora@FleetBuzz on 2008-04-26
It seems like you could just do a manual install to  /dev/sdb1 .

You can select this option during the installation process.  It shouldn't disturb your home partition at all.

---

### Post by kellemes on 2008-04-26
> **rock-hopper said:**
> (..) the third as Home, on which I have a lot of stuff (..)

I wonder what stuff you mean..
If it's only **non**-system related stuff, I'd probably go for a fresh install and simply copy it all back.
Hardy will include newer versions of software packages installed on your current system, and therefor chances are the settings for these packages (residing in /home/<username>/.blabla) will not function.
Don't take my word for this, just guessing ;-)

---

### Post by Aurora@FleetBuzz on 2008-04-27
**rock-hopper**, here's a thread that gives a little more detail to what I suggested earlier.
[http://ubuntuforums.org/showthread.php?t=765660](http://ubuntuforums.org/showthread.php?t=765660)
If you look at **neurostu's** note in post #3, you'll see that the key is to designate the directory to which you want to install ubuntu by using the mount point: / (i.e., forward slash).  It should also be formatted to ext3.  Ubuntu will automatically install to this partition.  Don't forget to allow for a swap as well!

---

### Post by rock-hopper on 2008-04-27
That is just what I was looking for, Aurora@FleetBuzz :guitar: !!

Thank you for your kind help in pointing me the right way.

Best wishes, rock-hopper.

---


---
title: "Upgrade frozen, forced shutdown, but now..."
date: 2013-05-29
forum: New to Ubuntu
---

### Post by flutist44 on 2013-05-29
Hi all... 

Completely new to Ubuntu, was just given a netbook using it... I started an upgrade to (i believe) 12.04 when prompted earlier today, but the screen froze about two thirds of the way through.  I forced a shutdown after waiting for awhile, then started the computer up again, only to be confronted with a long list of messages, ending with:
 Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S90binfmt-support  
-Starting bluetooth daemon [OK]
(insert the above point four more times...)
-Checking battery state... [OK]
-Starting bluetooth daemon [OK]
-Starting bluetooth daemon [fail]
-Stopping bluetooth daemon [OK]
-Stopping System V runlevel compatibility [OK]


This is followed by the blinking hyphen "loading" thing (sorry about my lack of technical terms!) and seems to be stuck there... I've let it run for nearly two hours, but it's yet to change to any other message... Tried re-restarting it earlier, but wound up stuck here yet again... How can I get past it to use the computer?? Any and all help appreciated!  Thanks!

*edit:  Tried letting it sit overnight in case it was just loading- no change... Waited for the battery to drain, then plugged it back in- still nothing... Help!!

---

### Post by ShadowVegan on 2013-05-30
When does the list appear? Before the login screen? After signing in to your user account?

Also, if you were prompted to update, it was probably just a software update, not updating to a new version. You get prompted to update software once a day.

---

### Post by grahammechanical on 2013-05-30
It is the forced shut down part the way through the update that has caused this and not your lack of technical terms. You now need to think seriously about doing a fresh install of Ubuntu. Often this is the quickest and simplest way of fixing things.

Do you see a boot menu when you switch on the machine? If not hold down the Shift key and what we call the Grub menu should appear. List for us the lines in that menu and someone may explain how to boot into a previous Ubuntu kernel or Recovery Mode>Resume.

Regards.

---

### Post by mennopieters on 2013-05-30
I would suggest to boot from an install CD, preferably Ubuntu or Debian, which allow to mount the system disk. Make sure you configure network on the installation CD and open a command prompt. From there check that the root file system is mounted (type mount and look for /target).

If not, try mounting your partitions manually:

mkdir /target

run "fdisk -l" to find your partitions and mount the first Linux partition (often like /dev/sda1 or /dev/hda1). That is the most likely candidate for your root partition.

mount /dev/sda1 /target

Now start a shell inside /target:

chroot /target bash

If you have any other partitions besides a root partion (like /home, /tmp, etc), type: mount -a

Now you can try to fix your installation with apt and dpkg:

apt-get update
apt-get dist-upgrade

if that fails you may try: "dpkg -configure -a" and try the "apt-get dist-upgrade" again. It may take a couple of iterations.

After you finish unmount all partitions:

umount -a

Exit the target partion:

exit

and restart (remove the CD/DVD):

reboot

Good luck!

Menno

---

### Post by flutist44 on 2013-06-05
Hi everyone-  

Thanks for the suggestions- I definitely know to come here with any other technical problems!  A friend of mine showed up the next day and entered some codes into the command line (which I know how to access and use now, thankfully!) and it's working fine!

---


---
title: "Trying to understand boot loading"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by SpikeyB on 2008-10-22
History of my problem:

1. Installed XP on a hd on ide 1.

2. Installed Dapper on a new hd on ide 2 and used grub to dual boot.

3. Following an update I had a problem with grub and used a procedure (documented at these forums) to change over to use the XP boot loader to dual boot.

4. Installed Hardy on a new hd on sata 1 and now use grub to dual boot (Hardy and XP).

The problem is:

I would like to physically remove the Dapper hd but if I do, I get a message telling me that I don't have a bootable device.

I'm baffled.  I have the bios set to boot from the Hardy hd and everything works ok as long as the Dapper hd is in place.  It's as if the pc is checking on the Dapper hd before moving onto the Hardy hd.

Can anyone think of an explanation of why this is happening?

It's not an urgent problem but shows an obvious lack of knowledge on my part that I'd like to remedy.

Thanks in advance for any help you can give.

---

### Post by gn2 on 2008-10-22
When you did step 4, where did you write Grub to?

Which drive is first in the BIOS boot list?

You need to have the BIOS (or the Xp bootloader?) "looking at" the hard drive with Grub on it, if that was the drive that's been removed, the BIOS will not find it....

You could try re-installing Grub onto one of the remaining drives, there's a few ways of doing so, here's some more info:
[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

---

### Post by SpikeyB on 2008-10-22
Thank you very much gn2, that was a brilliant response.  You have got me started on the road to a solution.

I now realise I have grub installed on hd(1,0) and hd(2,0).  The menu.lst on both my ubuntu installations states that the root is hd(1,0).  I guess that's where the problem lies.

I will have a play now and let you know how I get on.

Thanks again.

---

### Post by Kellemora on 2008-10-22
Hi SB

Before you move or delete any of those, make sure you keep a copy of each of them so you can see which ones contain the most recent Kernel as well.

I'm always changing things, so my MBR is constantly getting overwritten by Inferior Programs!  Some completely wipe out the MBR and install their own and forget about anything else on the whole computer.
Ubuntu plays nice and locates all the other versions and installs them for you in the MBR.  It even fixes errors other loaders have caused!

If you do have the Doze on your computer, normally it wants to be King of the Hill and sit in place of God and everyone else at the left hand.

As a good rule of thumb, install the Doze first, then everything else, and then at the very end install Ubuntu and the Bootloader should work properly on all distro's.  Install the MBR on hda0,0 and keep a copy on hda0,1; hda0,2, etc.
EG:  If you installed Debian, I think you will find its bootloader on the partition you installed it, with ONLY it in the file.
CentOS, like the DOZE, thinks it's the ONLY OS on the machine, hi hi.....

So if I do have CentOS on a machine, it's loaded immediately after the Doze, then CentOS, then all other Distro's, finally Ubuntu to clean up all their messes and keep things humming along.

TTUL
Gary

---

### Post by SpikeyB on 2008-10-22
Thanks for the extra info Kellemora.

I have had a play around and now I am more confused than a confused man in confusionville.

Background:
All o/s's are on 1st partition of respective hd
hda is XP on ide master
hdb is Dapper on ide slave
sda is Hardy on sata

If I:
boot off hda I get the menu.lst located on hdb
boot off hdb I get "error loading operating system"
boot of sda I get menu.lst located on sda but the option for hardy gives "error 17: cannot mount selected partiton" and the option for XP gives "error 13: invalid or unsupported executable format"

My workaround is to boot off hda.  I have copied the o/s details for Hardy from the menu.lst located on sda into the menu.lst located on hdb.  This allows me to boot into Hardy, Dapper and XP.

Does anyone understand what is happening here?

---

### Post by Kellemora on 2008-10-22
Hi SB

I'm a Noob TOO, so my explanation might be wetter than a red hen.

Your bios will tell the computer WHERE to look for the MBR, usually this is hd0,0 = hda0 or sda0.
When it gets there it will look for the STAGE 1 boot message.
This information is used to tell Where the ROOT DEVICE is located.
So the stage 1 message on your computer may be redirecting the computer to look to hdb0 as the Root Device to boot from.

From a LIVE CD in Root Terminal you can
Sudo grub
in this new screen type
find/boot/grub/stage1
this output will tell you where the root device is.  EG root (hd0,1)
If you want to leave it there, you would type
root (hd0,1)
setup (hd0)
quit

That's as far as I've learned so far.
Don't know if changing root (hd0,0) would cause it to look there instead or not.  Or if that was what the setup command was used for.
Sorry, I couldn't be of more help!
But this info might help you learn more or be able to search what those commands mean and do.
These are the commands I use, each time a BREAK my MBR and need to FIX IT.

Hopefully someone more knowledgable than I will chime in.
Even if to say I'm wetter than a red hen, hi hi........

TTUL
Gary

---

### Post by SpikeyB on 2008-10-22
Thanks Kellemora, I tried what you suggested but it didn't change anything.

I found some extra info that might give a clue.  I changed the entry for Hardy in the menu.lst from hd2,0 to hd0,0 and now I can boot into Hardy when booting from sda.

That means that hdb reckons Hardy is located on hd2,0 and sda reckons Hardy is located on hd0,0.

Do Dapper and Hardy have different naming/numbering conventions for hd's?

---


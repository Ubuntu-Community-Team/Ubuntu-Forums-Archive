---
title: "[SOLVED] Shared SWAP! Swap on won't stay ON!"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-08-03
I've done a lot of playing since I discovered Ubuntu in about March of this year. I started with Freespire and gOS 1.0.1, then it was Kubuntu and I then discovered the absolute beauty and options of Gnome and Ubuntu in general!

So, in the process, I've done a lot of removing and installing different distros. Most recently I got ticked off because of flash problems with Hardy so I replaced a Linux Mint Elyssa partition with Gutsy. (Hey Gutsy is damn stable!)

Anyway, my problem is keeping my SWAP in Swap-on mode. I'm sharing swap between Hardy and Gutsy, which shouldn't be a problem and I've clicked "swap-on" in both systems but it doesn't stay "on"!

I've not seen this before, of course maybe I hadn't demanded enough from the system that I noticed it but editing videos certainly brings up the problem.

Here's a pic of my drive:

[ATTACH]80092[/ATTACH]

Yeah, bad math left nearly 1gb of space floating, but you'll notice that "swap is off". I click swap-on and the next time I restart the puter, in either Gutsy or Hardy, I go to partition editor and swap is off!

Why won't it stay in "Swap-on"?

---

### Post by Paqman on 2008-08-03
When you look at the resources tab of the system monitor, does it show your swap as being in use?

---

### Post by hansdown on 2008-08-03
Hi kansasnoob. If you install gnome system monitor from the repos, you can get a really good look at your system while it is running. Open system
 monitor, click on resources, and it will show how much swap is in use, and also track your cpu usage.

---

### Post by mcduck on 2008-08-04
If you have reformatted the swap partition it's UUID has changed, and you need to edit the /etc/fstab to use the new UUID. Otherwise Linux won't recognize the swap partition at boot time.

As you have installed multiple Linux versions that would be the most likely reason for your problems.

You can get the UUID's for your partitons with the "blkid"-command, and then just run "gksudo gedit /etc/fstab" (on _all_ Linux installs) and change the UUID to the correct one.

---

### Post by kansasnoob on 2008-08-04
> **Paqman said:**
> When you look at the resources tab of the system monitor, does it show your swap as being in use?

No, not until I open Gparted and click on the swap partition, then select swapon.But I must do it every time I restart in either Ubuntu system.

---

### Post by kansasnoob on 2008-08-04
> **mcduck said:**
> If you have reformatted the swap partition it's UUID has changed, and you need to edit the /etc/fstab to use the new UUID. Otherwise Linux won't recognize the swap partition at boot time.

As you have installed multiple Linux versions that would be the most likely reason for your problems.

You can get the UUID's for your partitons with the "blkid"-command, and then just run "gksudo gedit /etc/fstab" (on _all_ Linux installs) and change the UUID to the correct one.

OK! But I'm clueless how to do that.

BTW, I've never reformatted the swap partition but I've used the same swap with many, many installations, and it's been resized numerous times.

With 2GB of ram and a low end 2d graphics card I doubt I've needed swap until I started editing these videos. I do know that when I choose swapon all works well. It's just annoying to have to open Gparted and click swapon each time I start the computer.

Is sharing swap a problem?

Uh, I don't even know what UUID is and I'm clueless how to do what you're suggesting.

Time to sleep but I'd big-time appreciate a more detailed explanation.

Sorry to be a pain!

---

### Post by mcduck on 2008-08-04
> **kansasnoob said:**
> OK! But I'm clueless how to do that.

BTW, I've never reformatted the swap partition but I've used the same swap with many, many installations, and it's been resized numerous times.

With 2GB of ram and a low end 2d graphics card I doubt I've needed swap until I started editing these videos. I do know that when I choose swapon all works well. It's just annoying to have to open Gparted and click swapon each time I start the computer.

Is sharing swap a problem?

Uh, I don't even know what UUID is and I'm clueless how to do what you're suggesting.

Time to sleep but I'd big-time appreciate a more detailed explanation.

Sorry to be a pain!
Sharing swap is not a problem.

UUID is an unique identifier given to each partition, and if you edit the partiton in any way (recreate it, resize it or format it) the UUID will change. In the user's point of view, UUID is a long sequence of letters and numbers.

So, first run the 'blkid' command, it will list all your partitons,a nd their UUIDs.

Then open /etc/fstab for editing, by running the "gksudo gedit /etc/fstab"-command. Now find your swap partition from  the file, and change the UUID for it into the one that the "blkid" command gave you.

You'll need to edit the fstab in all your linux installs, as they all have their own fstab files. The UUID will be same.

After editing the fstab reboot and the swap should now work. If it doesn't, use the swapon command or the swapon feature from gParted, and the swap should be recognized automatically on following boots.

(The reason why UUID's are used is that as long as you don't edit the partitions, their UUID's will always be the same. This allows, for example, configuring removable drives in fstab. And also makes sure that each partition is detected correctly even if you change your drives to diifferent cables, or if your system detects the partitions on different order on different boots. So it's just a way to detect the actual partiton itself, instead of configuring drives based on the device and partiton numbers which might change in some cases)

(This is pretty much as detailed instruction as I'm available to write at the time, as I'm at work and using a Windows machine :/ )

---

### Post by kansasnoob on 2008-08-04
Awesome! I just finally had time to give this a try. It worked flawlessly!

Many thanks!

---


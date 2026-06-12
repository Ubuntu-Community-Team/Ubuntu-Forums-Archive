---
title: "Best Update practices"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by Deskjockey on 2011-11-27
I just built a computer, inserted the MS CD, thought a few moments and  removed it to go cold turkey with 11.10, so I'm a complete novice.

I'm  concerned about the 265 updates on a new release. What is the best way  to handle this? I notice some folks say never update anything that has  "kernel" to avoid trouble. Also don't upgrade Ubuntu versions but do a  clean install. I also notice some game updates that are of no interest.  I'm not familiar with Linux to have an idea what to update and what most  of the files relate to. 

My thinking is to limit updates to  avoid problems. Conversely my concern is that I may not be seeing  possible programs in the software ctr. that require prior updates to  see. For example I notice folks getting Firefox 8. I notice my software  ctr. doesn't show it so I assume it isn't available for approved upgrade  for 11.10. But then I wonder is it available but I'm not seeing it  because it requires me to do an update first or if not for this program  can that be the case with other programs?

Deskjockey

---

### Post by dniMretsaM on 2011-11-27
There isn't any best practice, just best for you. Personally, I always update programs immediately and have yet to run into any problems. Some people only update once a week, once a month, or less frequently. Some update only specific programs. It's all personal preference. And the people who say to never update the kernel are wrong, in my opinion. Especially since version 3.1+  (which isn't in Ubuntu yet but should be fairly soon) has big power usage improvements. And after you do a fresh install you should always update due to the (usually) fairly large amount of bug fixes that get released relatively soon after public release.

---

### Post by Rex Bouwense on 2011-11-27
Updates are issued for several reasons.  First are the security patches to correct problems.  Second are new releases of programs.  Third are releases of new kernels.  I'm sure there are others but you get the idea.  You can pick and choose, but if you don't know what you are choosing or omitting you might have a problem.  I download and install all updates and have never had a problem even with the release of new kernels.  I have had Ubuntu and now Lubuntu since 8.04 Hardy Herron.  I would recommend you do the same until you are comfortable with Ubuntu.

---

### Post by bluexrider on 2011-11-27
Congrats on a new computer. you really shouldn't be so concerned with the updates.

1. Newer hardware is usually supported as would it be with MS
2. You are able to choose those updates that you want to deal with. You don't have to update if you don't want too. Unlike MS
3. Think of updates as enhancements rather than issues. Now UPGRADES are different!
4. You are doing the right thing by NOT installing MS. Dual boots are a PITA.imho
5. Its always good to start out in small steps. Install, run, test, update. 

Good Luck

---

### Post by 3rdalbum on 2011-11-27
> **Deskjockey said:**
> I just built a computer, inserted the MS CD, thought a few moments and  removed it to go cold turkey with 11.10, so I'm a complete novice.

I'm  concerned about the 265 updates on a new release. What is the best way  to handle this? I notice some folks say never update anything that has  "kernel" to avoid trouble...
My thinking is to limit updates to  avoid problems.

If you've removed Windows, then you should install ALL the updates.

If you had installed Ubuntu alongside Windows using the "Wubi" tool (not the regular Ubuntu installer) then, and only then, would I recommend not getting the kernel updates.

So you know, the Ubuntu bugfix updates get tested on the developers' machines and the testing computers at Canonical. If there are no problems, then they get pushed to a repository called "proposed", where bleeding-edge users test them. If there are no problems reported after a few days, then they get pushed to the general public.

If there are any problems at any point, the changes get reverted and never reach the general public.

As a result, by the time the updates reach you, they have been very well tested indeed.

And also as a note, it's not actually 200-odd updates to install. One update might require several packages to be rebuilt. For instance, fixing a bug in the 'uno' library will cause the whole of Libreoffice to be rebuilt and pushed out. It looks like six or seven updates but it's actually one update. Windows reports the number of updates, Ubuntu reports the number of packages that need to be redownloaded to complete the update.

You tend to get a stream of updates toward the beginning of the distro's life as more people start using it and reporting bugs, and the stream thins out over time.

---

### Post by Deskjockey on 2011-11-27
When I loaded 11.10 I did a format and clean install and don't intend to load MS at all. So based on the responses it looks like I should have no trouble letting the updates run. Thanks for the encouragement.

---

### Post by grahammechanical on 2011-11-27
If you go to System Settings in the Power Cog menu and then click on Software Sources you will get a dialog box where you can set when the system checks for updates. Go to the updates tab. The longer you leave it the larger the update.

As you are not dual booting you will not have issues with kernel updates. When we dual boot we get a menu of operating systems to select which one to boot into. Each kernel update is treated like a new OS and gets added to the list and the older ones are not removed until you do a version upgrade.

I do not use Windows but I have more than one Ubuntu OS installed. I use Grub Customizer to keep the boot menu short. If you decide to try out different Linux distros you might like to check out Grub Customizer.

Regards.

---

### Post by Deskjockey on 2011-11-28
Graham,

I'm just starting with Linux so I'm not going to look at dual booting. 

I did the 265 updates, less 9. So far so good. I noticed a few days ago somebody mention a way to remove those 9 updates from the update list  but didn't write it down. Oh well.

---

### Post by jockyburns on 2011-11-28
I'm still running 11.04 Natty. The update manager does usually inform me when updates are available. Very rare that I look through the updates to see what they are though. So far I've resisted the major update to 11.10 Oneiric, although I have tried it off a bootable usb stick. ;);)

---


---
title: "Separate /home partition"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-06-07
Currently I only have one partition for / and one for swap. I have been reading about having a separate partition for /home and separate for /. 

Now here are my questions:
1. Currently whenever I want to do a complete backup I use partimage to simply backup the entire Installation, this is useful as it only takes about 15-20mins and then if I ever have errors I can restore everything again in about 15-20mins. Again this is perfect because if I ever do something to wreck the installation I can easily just restore the image. 

So, my question is if I were to have to partitions, one for /home and one for / how could I backup these two separate partitions with partimage? I am assuming the easiest thing to do would be to backup an image of the / folder and simply copy the /home folder to another hard drive. Or just create two images.

2. Ihave numerous things customised JUST the way I like, from programs, to hotkeys, to background images, to terminal colour schemes, and panels :P. Anyway my point is I can't even remember all the settings I have changed. however, I like my setup just the way it is. If I remove my / folder (and say upgrade and do a clean installation) and keep the /home folder backed up will my settings remain intact? 

Again this is important as I don't mind upgrading BUT, I would rather do a clean installation each time.

---

### Post by bumanie on 2008-06-07
If you find regularly backing up with partimage not to be bothersome there is no real reason to muck around creating a separate /home. However, if you were to reinstall form scratch at some time in the future, I think creating a separate / and /home is advantageous. Generally one will not get corruption within a /home partition, that will most often occur where the system files are, thus you only have to reinstall (or in your case copy an image back) to / - your partimage sessions would also be shorter as you would only have to image /. I have played around and destroyed / a few times and never had trouble with my separate /home - reinstall to / and everything fires again and /home data has always been untouched. Just my opinion, others may feel differently.

---

### Post by abhiroopb on 2008-06-07
Thanks, like I said I see the benefits in having two separate partitions. But like you say when you reinstall from scratch what all "settings", etc. do you lose? I mean I know I will have to reinstall all my programs, that is not such a big deal, I have scripts for that. But I'm more worried about all the tweaking I have done.

---

### Post by autocrosser on 2008-06-07
I work with the Testing Branch & find having a separate /home a "must have"--As long as the programs you use are reinstalled when you install on your /--everything will be there. If you have differences, there will be generic icons for things that are missing--easy to see & reinstall. 

I've reinstalled many times due to "blowups" & glitches--& having my /home off to the side makes it easy--I can be right back where I was before in most times within the hour.

All your settings "generally" are in your /home under a . file---.mozilla for example.

---

### Post by Paqman on 2008-06-07
> **abhiroopb said:**
> when you reinstall from scratch what all "settings", etc. do you lose?

You'll lose any tweaks you've made to files outside of /home. So if you've changed your /etc/fstab for example, you'd need to keep a copy of that too.

Otherwise all your customisations to the appearance of your system, all your settings in your aps, all your emails, etc will all be kept safe in /home.

---

### Post by abhiroopb on 2008-06-07
Wow ok. Thanks for that, I guess it takes away a lot of worries for me. My main concern while reinstalling the / partition was that all my settings (or at least some of them) would be toast. 

Are there any config files that I should backup? 

I have a cron job that backups up my xorg.conf, menu.lst, sources.list files at 59 minutes past the hour, and then every hour on the hour my entire hard drive is automatically backed upto an external hard drive. So, I make changes to these three files at times, especially sources, and so I know that these I should keep backed up. For example if I were to NOT backup menu.lst or xorg.conf, upon reinstallation of / my monitor would be at an odd resolution, and my windows partition would not show up in grub!

UPDATE: Just read Paqman's post, exactly what I meant I guess. I don't recall ever changing /etc/fstab/ any chance I would've?

---

### Post by bumanie on 2008-06-07
As I said, at this point I wouldn't be bothered seeing you don't seem to mind regularly backing up with partimage. In the future you may find you have to reinstall a fresh ubuntu i.e the upgrade to a new version may not work (or whatever), at that time (if it eventuates), I would then install with  a separate / and /home. Personally, I prefer a fresh install with each version, but I have read that sometimes the upgrade from one version to the next does not always work perfectly, so I guess I'd go with the old adage, "If in aint broke, don't fix it." But if it does break in the future, then do as above re / and /home.

---

### Post by autocrosser on 2008-06-07
Yes--system-wide conf settings--custom menu.lst, network settings--things that would be in /etc or /usr will be wiped clean. A copy of /boot, /etc & some stuff in /usr (/usr/local comes to mind) helps make a fast restore.

---

### Post by abhiroopb on 2008-06-07
I backup all those folders anyway, but naturally after a clean reinstall (especially if I upgrade), I don't want to simply copy and paste those old folders and use old settings that may be corrupt a new installation. I identified four key files I guess:
fstab, menu.lst, sources.list, xorg.conf.

Also my current Ubuntu is quite slow, I mean it isn't unusable, but boot-up is a LOT slower than when i first started. In fact just to test I created a dummy account, and logging into the dummy account took about a quarter of the time. I have tried disabling startup programs, to almost no effect. So, thats why I have thought about reinstalling. I haven't done a reinstall in about 1.5 years (in windows I could only go about 6 months). But with ubuntu I have not needed to. And I stopped myself since I was scared about settings getting messed up. Now, especially with 8.04 slowly getting its act together I may do a fresh install of that. So, that is why I am asking so many questions, just to make sure nothing goes wrong!

Other than those 4 files, are there any more files/folders that you think backing up and restoring would be a good idea. Like I said I want a relatively fresh isntallation, so if there are any garbage files/directories I want them to be deleted. But I want as much of my settings as possible intact.

---

### Post by bumanie on 2008-06-07
Thought others may have a different idea than I. It is sure that it can be done and there are tutorials around regarding how to make a separate /home (I think psychocats have one) from where you are now, ie splitting up / from /home files and changing /home to a new partition. Not worth the hassle IMO. With a range of opinions, you can more informed decision.
Here's the psychcats link [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) It's a few distro's old, but the principle is the same. Go for it if you wish.

---

### Post by abhiroopb on 2008-06-07
Yes I read the psychocats tutorial, it seems a bit convoluted, and difficult. I would rather erase everything and install 8.04 to a clean partition, and install /home to another partition, then copy my backed up files. if it achieves the same result as the tutorial then I think my option is better.

---

### Post by bumanie on 2008-06-07
Can't disagree with that. I think creating a separate /home  could easily go wrong. By the way, I have a friend with an older computer, 8.04 is much quicker on it than previous distro's were.

---

### Post by abhiroopb on 2008-06-07
> **bumanie said:**
> Can't disagree with that. I think creating a separate /home  could easily go wrong. By the way, I have a friend with an older computer, 8.04 is much quicker on it than previous distro's were.

When you say creating a separate /home could cause problems, you mean following the guide right? 

Yes I've heard its much faster. The problem I had with it was that my wireless card did not work as apparently Ubuntu was using some different drivers, so where before it was a simple job of me using restricted drivers manager to install, I now had to use other methods (see thread:[http://ubuntuforums.org/showthread.php?t=768515&page=2](http://ubuntuforums.org/showthread.php?t=768515&page=2))

So until wireless seems to be OK, I don't see myself upgrading, but once I have some time on my hands I would like to play around with it a bit.

What about my other questions? About which system files/directories are useful to keep backed up.

---

### Post by bumanie on 2008-06-07
> When you say creating a separate /home could cause problems, you mean following the guide right?  Yes. Sorry should have been clearer. As you said it looks rather convaluted, but creating a separate /home with a fresh install should go without issue. Remember you will need to choose 'manual' at the partitoning stage to set up as you propose.

---

### Post by abhiroopb on 2008-06-07
Yes thanks for that!

---


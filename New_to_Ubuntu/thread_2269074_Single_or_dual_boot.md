---
title: "Single or dual boot"
date: 2015-03-13
forum: New to Ubuntu
---

### Post by phillip_smith on 2015-03-13
I have an aging laptop that has windows vista on it and i have put ubuntu on it about 2 years ago.
This was the first time i used any linux distro.
The windows vista is dreadful and full of malware. I never use it.

I was thinking of formatting the hard drive and installing the most uptodate ubuntu on it without windows.

Would i see any advantages of doing this apart from freeing up hard drive space?

Would the speed increase because 
1. the hard drive is formatted and therefore not fragmented
and
2. there is more space available

Would i see no difference at all

or

Would it slow down my system because of the possibility that the newest Ubuntu needs a more powerful computer?

If i decide to go down the single boot option what is the best way to do it? Format and start again or is there some easy and clever way Ubuntu can get rid of windows when i update it to the newest version?

Thanks for your help

---

### Post by Irihapeti on 2015-03-13
We would need to know more about the hardware before we can say anything definite.

However, if standard Ubuntu is too heavy, you could probably still use one of the other variants, such as Lubuntu or Xubuntu.

---

### Post by Impavidus on 2015-03-13
Ubuntu doesn't really suffer from fragmentation until the drive is nearly full, so formatting the drive won't give you a significant speedup. Ubuntu does slow down when the drive gets full, but only once you get to 90% disk usage or so.

I don't think Ubuntu system requirements are much higher now than 2 years ago. Computers that came with Windows Vista should be able to handle Ubuntu.

It's easy to get rid of Windows from within Ubuntu. No need to reinstall or upgrade. Reusing the freed disk space in a sensable way without reinstalling is a different matter, but to give you any advice on that we need to know the way the hard drive is currently partitioned.

---

### Post by mastablasta on 2015-03-13
and even if Ubuntu doesn't run as fast there are other variations with lighter desktop (e.g. Xubuntu). or even something like ToriOS...

---

### Post by oldrocker99 on 2015-03-13
If you are going to wipe the disk and install Ubuntu (HIGHLY recommended), boot from the disk or USB, and tell it to install. Whe it comes to the screen where you can choose whether to wipe the disk or install it side-by-side with Windows, select "Something Else." Then divide your disk into two partitions. One will be / the root diectory, which can be small (I have found 64GB to be plenty, and 128GB to be far more than enough), and the rest of the disk should be devoted to /home. Your /home folder can never be too big. 

At the screen you get with "Something Else," make the partitions, and select ext4 as the file system for both. They will both be formatted. You can then reinstall Ubuntu, upgrade it, or install a completely different distro, and your /home folder will not be touched. You uncheck the "format" button in this scenario, and mount as ext4 (or whichever file system it is formatted to) and as /home.

This makes it a lot easier to use, especially with reinstallation. Some people (like myself) put /home on a separate disk drive, which helps the /home folder be as big as it needs to be.

---

### Post by Bucky Ball on 2015-03-13
Welcome. I've never used anything larger than 15Gb for the / root partition and have only ever gotten to about 12Gb full, but I use mini installs. 25Gb for / should be ample if you have a separate /home.

I'd go 25Gb for / and the rest of the disk for /home with 2Gb /swap at the end by using 'Something Else', as suggested, at the partitioning section of the install. If you never use Vista, who needs it? Good luck. ;)

---

### Post by newb85 on 2015-03-13
As has been said, fragmentation isn't an issue with Ubuntu.  The only reason you need to do this for performance reasons is if you're running out of space on your Ubuntu partition.  That said, if you're *never* going to use that Windows partition, there's no need to keep it.  And IMO, it's good to do a fresh install every few years.  I copy 
the files I want to keep to some external media/cloud space, do the fresh install, and then put my files back.  

Of course, you could simply do the upgrade without a fresh install.  It usually goes well, and the config files from your old system usually work fine on the new one, but sometimes that's not the optimal situation.  It depends on how much you're into customization and what kind of fancy things you've done with your system (and how easily you could replicate them on a fresh install).

If you're going to wipe and start over, I would suggest going with 14.04, because it's the latest LTS release.  Given that you haven't upgraded in 2 years, I'm guessing you're not interested in upgrading every 6 months.  I used to, but now that I have less time to tinker, I decided to start sticking with LTS releases beginning with 14.04.  (You know you're not supposed to keep running an unsupported release, right?

---

### Post by ansus on 2015-03-13
I was faced with the same dilemma with a model 2004 BENQ with XP. I opted for complete install of 14.04 and it works great. However on my old model 2005 year, PC I run Dual Boot, 14.04 with windows 8.1 because I have a couple of Windows programs I use from time to time especially ACRONIS for back up.

---

### Post by HermanAB on 2015-03-14
The disk space will be bigger, that's all.  However, if you also install Virtualbox and put Win7 in that, then you will have PC with Linux and Windows in a window at the same time, which makes for a very nice setup - much better than dual booting.

---

### Post by phillip_smith on 2015-03-14
Thanks for all the great advice.

currently running 12.04
My computer specs are as follows 80gb hd
2GB RAM
INTEL CORE DUO T2250 1.73GHZ X 2
AND 32BIT

So would you guys suggest the newest Ubuntu would work ok with this? and as my HD is quite small should i use 25GB for system files? or should i use more and get a usb memory stick for additional storage.

gonna start fresh to tidy things up and if i get no benefits at least i wont have to select Ubuntu at each boot.

---

### Post by Bucky Ball on 2015-03-14
I would suggest three partitions:

/ = 25Gb, root partition;
/home = rest of the disk, your personal data and settings, but leave room for;
/swap = 2Gb at the end of the drive.

14.04 LTS should run ok on those specs but maxing out the RAM never hurt! And chucking in a new 80Gb SSD. ;)

I actually did that with my old P4 desktop. I swapped the OS drive for a 120Gb SSD, maxed out the RAM from 1Gb to 4Gb and it is like a whole new machine.

If 14.04 LTS doesn't run smoothly, you can always go back to 12.04 LTS or try a lighter flavour (Xubuntu would run fine, or Lubuntu) or desktop environment (xfce4 or lxde). 



PS: You might want to look in Gparted (install from repos if not installed) at how much disk space your current install (/ partition) is using. If you're only intending to only surf the net, watch vids, play music and check emails, you won't need much more than that.

---

### Post by mörgæs on 2015-03-14
25 GB for system files is more than enough. 
Yes, Ubuntu 14.04.2 will probably run faster than 12.04.

---

### Post by Bucky Ball on 2015-03-14
> **mörgæs said:**
> 25 GB for system files is more than enough. 


+1. I've never used more that 15Gb, but run a fairly lean install.

---

### Post by phillip_smith on 2015-03-14
Am I correct in think that my laptop will support the 64bit version or am I best sticking to 32bit?

---

### Post by Bucky Ball on 2015-03-14
If you have a 64bit processor, 64bit you should go for. If you're not sure which you have, you can always try the 64bit release and if it doesn't run, you have a 32bit processor! ;)

---

### Post by sudodus on 2015-03-14
With 2 GB RAM I suggest that you use a 32-bit system. It will be almost as fast, and it will need less RAM for the same tasks. If you upgrade to 4 GB RAM, I suggest that you use a 64-bit system.

But I warn you about the 12.04 LTS versions of Lubuntu (way past end of life) and Xubuntu (end of life in April). If standard Ubuntu 12.04 LTS is too heavy, you should use a community re-spin with a light-weight desktop environment, for example LXLE, which promises support until April 2017 (until the end of life of that version of Ubuntu itself).

Lubuntu and Xubuntu 14.04 LTS are supported until April 2017, while standard Ubuntu and Kubuntu 14.04 LTS are supported until April 2019.

---

### Post by monkeybrain20122 on 2015-03-14
2 G of ram is enough for regular Ubuntu. For lighter option I would recommend xubuntu. There is no need to go for Lubuntu or LXLE resource wise unless you like them.

---

### Post by Bucky Ball on 2015-03-14
> **monkeybrain20122 said:**
> 2 G of ram is enough for regular Ubuntu. For lighter option I would recommend xubuntu. There is no need to go for Lubuntu or LXLE resource wise unless you like them.

Agreed. Xubuntu should run well on 2Gb. I was using 12.04 on a 1Gb machine and it was fine.

---

### Post by sudodus on 2015-03-15
Standard Ubuntu 32-bit might work well for you with 2 GB RAM. Your way to use the computer can make a big difference, so if you have an opportunity to download several iso files, [try them live (booted from DVD or USB drives) before you decide what to install]("http://ubuntuforums.org/showthread.php?t=2230389").

---


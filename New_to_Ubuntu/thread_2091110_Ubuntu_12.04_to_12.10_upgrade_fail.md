---
title: "Ubuntu 12.04 to 12.10 upgrade fail"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by Malt Frisky on 2012-12-04
I recently upgraded from 12.04 to 12.10. This was done at the software updater.

Everything seemed to go will and finally came to the last procedure to restart computer.

Restarted it, and stuck on a black screen with cursor flashing in the top left hand corner.

I tried restarting it with no luck, been in GNU GRUB screen and tried to use recovery mode with no luck either.

It's definitely not the hardware, I was running 12.04 without any problems and when I run my 12.04 disc and select the try Ubuntu 12.04 version there's no problems.

Normally I would do a simple reinstall of 12.04 but I have about 200GB of files on my which like the idiot I am didn't backup on a external.

So I'm left with a laptop that freezes all the time on the boot up screen.

The problem seems to fairly common but I can't find any answers.

Any help would be appreciated.

Jonny

---

### Post by verymadpip on 2012-12-04
Could be graphics.  I'd suggest running 12.10 from a CD or USB to check.
You should be able to retrieve your data from a live environment too, then do a fresh install perhaps...?

12.04 is LTS (supported for 5 years), you could stay with that. The big plus is that you know it works.

Personally I dislike the upgrade route as it takes too long for me; impatience.

---

### Post by Malt Frisky on 2012-12-04
I was thinking it may be a graphics card problem, I have NVIDIA on my laptop and I'm well aware of the problems Linux has with it. How do you retrieve the data? I'm not fully aware of the whole live environment retrieval but it would be a massive help.

---

### Post by verymadpip on 2012-12-04
Hey Malt.

I think I'm correct in saying that when you run your 12.04 Live CD you should be able to access the drive/partition you have your data stored on from either the launcher (left side "dock") or Nautilus (file manager).  Thereafter it's a case of copying the stuff to your external storage, pretty much like any other copy & paste.

If I'm way off here someone cleverer than me will help us out :)

---

### Post by monkeybrain2012 on 2012-12-04
If you use the Nvidia driver in 12.04 you need to remove it before  you run upgrade, ditto all third party applications and proprietary drivers.

Also, clean install is a lot faster and less problematic. I won't recommend "upgrading" through the update manager especially if you have made a lot of customizations.

---

### Post by krustenBrot on 2012-12-04
**+1** for the fresh installation vs. upgrade function.
I have encountered several bugs after I upgraded to 12.10. I do not know why, but it works faster and better using a fresh install. A few handy tips:
- Split your partition one root *"/"* partition and one *home folder* partition, this way you can just format *"/"*, install the next version, enter the **same username**, set your home folder mount point to your *home partition* and you'll have everything right there.
-all your configuration files are stored at your home folder, so you will open Firefox and everything will be as you are used to. Don't worry about that.
-If you want to dump a applications list open up a termrinal and type ```
dpkg --get-selections > package_list
```additionally you'll find your sources list at */etc/apt/sources.list *if you want to make a copy for comparison.

An optional plus for me is that i get a new clean system everytime there's a major upgrade. I still got my personal stuff and reinstall the few Apps i need.

---

### Post by NM5TF on 2012-12-04
> **Malt Frisky said:**
> I was thinking it may be a graphics card problem, I have NVIDIA on my laptop and I'm well aware of the problems Linux has with it. How do you retrieve the data? I'm not fully aware of the whole live environment retrieval but it would be a massive help.

there are several well known bugs associated with the newer kernels
and AMD based proc's and Nvidia graphics cards....I use 12.04.1 LTS
and had the same problems when I installed the newer 3.2.0-34 kernel

I have filed a bug report with launchpad & the kernel dev's are working
to resolve it...the report is here if you're interested...

[https://bugs.launchpad.net/bugs/1085548](https://bugs.launchpad.net/bugs/1085548)

Tommy

---

### Post by monkeybrain2012 on 2012-12-04
> **NM5TF said:**
> there are several well known bugs associated with the newer kernels
and AMD based proc's and Nvidia graphics cards....I use 12.04.1 LTS
and had the same problems when I installed the newer 3.2.0-34 kernel

I have filed a bug report with launchpad & the kernel dev's are working
to resolve it...the report is here if you're interested...

[https://bugs.launchpad.net/bugs/1085548](https://bugs.launchpad.net/bugs/1085548)

Tommy

So a fresh install without upgrading the kernel should work. After install I have upgraded my kernel to 3.5.0-17 (now 3.5.0-18) and I have never experienced a problem.

---

### Post by LuisGMarine on 2012-12-04
I had the same exact problem when I did a fresh install of 12.04 and 12.10.  You can give these troubleshooting steps a try, hopefully it is not too late.

The first step is to boot with "nomodeset" enabled in the kernel options.

Open the link below and scroll down to the section that reads, "How to temporarily set kernel boot options on an installed OS." Once all steps are completed and you should be able to boot into a functioning desktop.

[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

The next step requires you to install the respective nvidia driver.  To do so I recommend that you run the following commands:  

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

Next you can use one of the two following commands.  One is for nvidia-current and the other is for the nvidia-current-updates.  I don't know much about the difference betwen the drivers.  I do recollect reading that nvidia-current driver is more stable, while the nvidia-current-updates run on a more bleeding edge.
```

sudo apt-get install nvidia-current
```
or
```
sudo apt-get install nvidia-current-updates
```

Once you reboot (fingers crossed), you should be back up and running ...

---

### Post by Malt Frisky on 2012-12-08
I did manage to get back to 12.04 but I took the long way round.

I got my original 12.04 disc and clicked on try Ubuntu.

From there I went to file system and plugged in an external hard drive and drag dropped all my files that I needed.

After that it's simply a case of reinstalling from scratch and loading all software back on again.

I phoned a friend about this who is way more experienced at Linux than I am, so I will try to get the exact terminal commands that I used from him.  My brain is too fried after spending 3 hours on the phone trying possible routes to get this fixed.

Lesson here people is simple, ALWAYS BACK EVERYTHING UP!

However keep this forum alive I really want people to try these different options that have been suggested to see if they work for anyone else.  Nothing is more frustrating trying to ask a question and getting no answer. :confused:

Malt Frisky

---


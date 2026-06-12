---
title: "Can't get past &quot;Preparing to install&quot;"
date: 2012-11-17
forum: New to Ubuntu
---

### Post by AntLord on 2012-11-17
Hi,

I have installed and uninstalled Ubuntu and some of it's variants more than once, so maybe I'm not an absolute beginner, but I'm still pretty ignorant.

My issue is, when I boot Ubuntu/Kubuntu/Xubuntu (even Mint) from a USB stick and choose to install it, the installation window won't get past the "Preparing to install... " part, when it checks if I have enough disk space, internet connection and power source. I wouldn't say it gets stuck because I'm able to quit and everything works just fine, nothing crashes. It just won't go any further when I hit "Continue".

I've tried booting on another PC and managed to go beyond this part, so I'm sure the USB stick isn't the problem. Also, it happened with all distros mentioned, so something's definitely wrong with my laptop. I'm guessing it's  got something to do with my partitions.

My HDD is partitioned like so: Window's C: ( ~200 GB); D: ( ~8 GB) and one I made long ago, but isn't unallocated space ( 30 GB)

So should I erase that partition? Is having no unallocated space somehow causing the problem?
Can I fix/do everything I need to do while booted from the USB stick? (Presently with Kubuntu 12.10)

Thanks in advance for any response

---

### Post by d.atanasov on 2012-11-17
Hi, 
Your problem sound very weird. I had some problems while ago when the distro did not wanted to pass and it showed me some error message. You can try to investigate you RAM, which also could be a problem. By the way try different version like 32bit or 64bit. 

cheers

---

### Post by newb85 on 2012-11-17
Sometimes the Ubiquity slideshow can cause a problem like this.  Instead of choosing the install option at boot-up, select "Try Ubuntu".  Then, open a terminal and run

```
sudo apt-get remove ubiquity-slideshow-ubuntu
```

Then, proceed with the install.

---

### Post by AntLord on 2012-11-17
> **newb85 said:**
> Sometimes the Ubiquity slideshow can cause a problem like this.  Instead of choosing the install option at boot-up, select "Try Ubuntu".  Then, open a terminal and run

```
sudo apt-get remove ubiquity-slideshow-ubuntu
```

Then, proceed with the install.


Thanks, but that didn't work. I actually ran

```
sudo apt-get remove ubiquity-slideshow-kubuntu
```

and it was removed, but then I proceeded with the installation (I clicked "Install Kubuntu 12.10" on the desktop) and same thing happened. In fact, nothing seems to have changed. Did I do it wrong?

---

### Post by AntLord on 2012-11-17
> **d.atanasov said:**
>  
By the way try different version like 32bit or 64bit. 


I did

---

### Post by AntLord on 2012-11-17
Wow, actually it ended up working, all it took was waiting +30min. Weird.

 But now I click "Install now" after I chose the partition in which to do so and it says "No root file system is defined". What now?

---

### Post by Dennis N on 2012-11-17
This problem has been reported by a number of people: google "stuck at preparing to install Ubuntu". You can look through those - some are marked solved, but there does not seem to be a silver bullet.

I had this same problem with Lubuntu 12.10, and did not come across a solution among them, at least that worked in my case. Instead, I used the Lubuntu alternate installer and that worked. Unfortunately, there is no longer an alternate installer for Ubuntu 12.10.

A possible work around might be to install Ubuntu 12.04, and immediately upgrade.

Comments: Waiting an hour (which I tried) did not work for me. The same USB stick (standard installer) worked fine on two other installs, so it is something with that particular machine's components.

---

### Post by deadflowr on 2012-11-17
> **AntLord said:**
> Wow, actually it ended up working, all it took was waiting +30min. Weird.

 But now I click "Install now" after I chose the partition in which to do so and it says "No root file system is defined". What now?

When you choose a partition you have something like two dropdown thingys. One sets the filesystem type(ext4,ntfs,etc,etc
) and the other marks where things are going to install(/, /home, /usr, /boot, /etc,etc,etc)for a whole partition select /(root) and everything should be fine.

---

### Post by AntLord on 2012-11-18
> **Dennis N said:**
> This problem has been reported by a number of people: google "stuck at preparing to install Ubuntu". You can look through those - some are marked solved, but there does not seem to be a silver bullet.

I had this same problem with Lubuntu 12.10, and did not come across a solution among them, at least that worked in my case. Instead, I used the Lubuntu alternate installer and that worked. Unfortunately, there is no longer an alternate installer for Ubuntu 12.10.

A possible work around might be to install Ubuntu 12.04, and immediately upgrade.

Comments: Waiting an hour (which I tried) did not work for me. The same USB stick (standard installer) worked fine on two other installs, so it is something with that particular machine's components.


First of all, thanks everyone. Secondly, excuse me for bumping the thread, but I'd really like to get this fixed/worked around.

From googling my problem I found that this is indeed a common issue and also an overlooked one. No one solution will work for everyone, it seems. I don't fancy the idea of wasting hours or, god forbids, days until something works. What do you think is my best bet:

 - Trying Ubuntu 11.04 which [**supposedly**]("http://ubuntuforums.org/showpost.php?p=10595803&postcount=9") is successful when others failed

 - Removing the USB stick after booting into Ubuntu (tell me now if it's stupid, but I got the idea [**here**]("http://ubuntuforums.org/showpost.php?p=10296996&postcount=10"))

 - Using a live CD (I know I should've tried already, give me a break) 

 - "F**k this sh*t" and delete all partitions (including Window's)

---

### Post by Peripheral Visionary on 2012-11-18
I've never installed from a USB, only from LiveCDs because my computer has no option to boot from a USB.

Is the installer insisting that you manually partition the drive?  Are you dual-booting?

If you're just trying to install Ubuntu and it's all you want to use, you can either let it have the whole drive or define your partitions kinda like this:

"**Linux swap**" gets the first partition, twice the amount of your RAM.

Next partition is "**/**" and I always give it 10 to 20 GB of my 80 GB drive. All the rest is "/**home**."

If no root partition is defined, perhaps the installer is expecting you to define the partitions, and can't proceed until you do.  Just a guess, but I'm using Xubu 12.04 and only use the LiveCDs. But maybe this helps a little.

---

### Post by Dennis N on 2012-11-18
> **AntLord said:**
>  What do you think is my best bet:


Two best bets (in my opinion):

1) Use the Lubuntu 12.10 alternate installer. Requires keyboard navigation and careful reading, but worked when the standard installer did not:

[https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)

2) Install 12.04 with the standard installer, then upgrade with it's update manager. (The 12.04 standard Lubuntu installer previously worked for me on the same machine that didn't work with 12.10 installer.)

Choice #1 would be quicker.

Lubuntu 11.04 is not supported any longer, so you would get no updates after the install.

[COLOR="Red"]EDIT: Looking back at the posts, looks like you were trying Ubuntu, not Lubuntu, so option #1 would be off the table, since Ubuntu 12.10 has no Alternate Installer. Sorry about that. If it were me, and I wanted Ubuntu, I would install and stay with 12.04 which is good.[/COLOR]

---

### Post by AntLord on 2012-11-18
Nevermind guys, I chose my own last option. Because the hell with windows already, I'm fed up and no longer need to be enslaved by microsoft office, which was the only reason keeping me from at long last making the switch. So I'm off to lurk more, thanks everyone.

---


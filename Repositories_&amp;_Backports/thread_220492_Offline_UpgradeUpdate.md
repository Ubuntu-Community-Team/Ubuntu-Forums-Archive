---
title: "Offline Upgrade/Update"
date: 2006-07-21
forum: Repositories &amp; Backports
---

### Post by Ziox on 2006-07-21
first off, sorry if i'm posting in the wrong forum, i really have no idea where to post it.

Now to my main problem, does anyone know how to upgrade ubuntu without internet connection? I have a desktop that's connected to the net via broadband, but my laptop (the one i'm planning to install ubuntu on) can't connect via broadband, only dial-up.  So can i used the desktop to download the packages that i need to upgrade? 

I know that apt-get cache the recently downloaded packages on the computer, so I'm think of using that function.  However, I dont' know what packages to download to upgrade the laptop. Is there a way that i can make synaptic/apt-get to generate a list consisting of the versions of each package, so then I can use the desktop to check the versions against the newest version in the repositories, and then I'll download what i need?

---

### Post by aysiu on 2006-07-21
On your desktop, download the Dapper Alternate CD (do not get the Desktop CD).

Then on your laptop ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.breezy
sudo nano /etc/apt/sources.list
``` Control-X ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
```

For updates... well, you don't really need those unless you're connected to the internet, as most of the updates until Edgy will be security updates.

Nevertheless, you desktop should keep all the .deb files for updates in the /var/cache/apt/archives directory. Copy those over to the desktop of the laptop and then ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---


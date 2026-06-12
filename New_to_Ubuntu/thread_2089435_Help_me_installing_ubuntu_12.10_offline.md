---
title: "Help me installing ubuntu 12.10 offline"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by ANiK3T on 2012-11-29
Hi all
i m a windows user
i want to remove it and install a fresh ubuntu 12.10 version on it
so i'v got some questions regarding it

Q1.what is a step-by-step procedure for offline download?

i read it somewhere that i requires some stuff from net.

Q2.what if i download .iso file from official site n install it offline will it require some more OS's stuff(I MEAN THOSE 'UBUNTU'S RESTRICTED EXTRAS' ? If yes then proceed to Q3&Q4)?

Q3. Keryx or apt-offline-gui?which is better

Q4. Guides regarding keryx & apt-offline

thank you in advance

---

### Post by pkadeel on 2012-11-29
> **ANiK3T said:**
> 
Q1.what is a step-by-step procedure for offline download?

know your system i.e. 32bit or 64bit
Choose (32bit or 64bit) and Download the .iso
Check md5 hash using the guideline on following two links
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
burn the .iso to DVD or USB
Boot from DVD or USB and follow the instructions. (It is always better to choose "Try Ubuntu" from instructions before actual installing)

> **ANiK3T said:**
> Hi all
Q2.what if i download .iso file from official site n install it offline will it require some other OS's stuff?

No. you won't need internet connectivity during installation. However after install it is recommended to connect to internet and do an update.

---

### Post by audiomick on 2012-11-29
> **pkadeel said:**
> 
No. you won't need internet connectivity during installation. However after install it is recommended to connect to internet and do an update.

Yes, when you connect the machine to the internet the first time, it will likely want to do a huge update. If the machine never gets connected to the 'net, it will happily continue to work in the state it was installed in.

---

### Post by dolphin194 on 2012-11-29
> **ANiK3T said:**
> Q1.what is a step-by-step procedure for offline download?
There is no special download for installing Ubuntu offline. Simply download the .iso from the Ubuntu website.

Now either burn it to a DVD or put it on a USB drive. You can then reboot and install it normally

However, if you desire to use Wubi, I would recommend using an image mounting program such as SlySoft Virtual CloneDrive (freeware).

> Q2.what if i download .iso file from official site n install it offline will it require some other OS's stuff?If you downloaded the .iso from the official site and installed it offline, you will not need to install any other software or operating systems.

> Q3. Keryx or apt-offline-gui?which is betterI would recommend not using Keryx since it is not the one used by most Ubuntu users. I would say that apt-offline is better to use.

> Q4. Guides regarding keryx & apt-offlineInstall apt-offline with an internet connection or by downloading the packages from the repository yourself. Here is the manpage to using it: [http://manpages.ubuntu.com/manpages/lucid/man8/apt-offline.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-offline.8.html)

---

### Post by ANiK3T on 2012-11-29
> **dolphin194 said:**
> There is no special download for installing Ubuntu offline. Simply download the .iso from the Ubuntu website.

Now either burn it to a DVD or put it on a USB drive. You can then reboot and install it normally

However, if you desire to use Wubi, I would recommend using an image mounting program such as SlySoft Virtual CloneDrive (freeware).

If you downloaded the .iso from the official site and installed it offline, you will not need to install any other software or operating systems.

I would recommend not using Keryx since it is not the one used by most Ubuntu users. I would say that apt-offline is better to use.

Install apt-offline with an internet connection or by downloading the packages from the repository yourself. Here is the manpage to using it: [http://manpages.ubuntu.com/manpages/lucid/man8/apt-offline.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-offline.8.html)



but buddy what about those  'ubuntu restricted extras'

---

### Post by ANiK3T on 2012-11-29
> **dolphin194 said:**
> There is no special download for installing Ubuntu offline. Simply download the .iso from the Ubuntu website.

Now either burn it to a DVD or put it on a USB drive. You can then reboot and install it normally

However, if you desire to use Wubi, I would recommend using an image mounting program such as SlySoft Virtual CloneDrive (freeware).

If you downloaded the .iso from the official site and installed it offline, you will not need to install any other software or operating systems.

I would recommend not using Keryx since it is not the one used by most Ubuntu users. I would say that apt-offline is better to use.

Install apt-offline with an internet connection or by downloading the packages from the repository yourself. Here is the manpage to using it: [http://manpages.ubuntu.com/manpages/lucid/man8/apt-offline.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/apt-offline.8.html)



Regarding Q2: u saying dat i dont need xtra software but what about RESTRICTED EXTRAS?

---

### Post by VeloxNeb on 2012-11-29
the "restricted extras" is a package like any other: you can either  download and install it like dolphin described or connect your machine  to the net and let your package manager do it for you.

---

### Post by ashwinrao on 2012-11-29
It's better to install 12.04 LTS and install required software&#8217;s offline using the Repository DVD pack. Check this [link]("http://www.zyxware.com/shop/software/free-software/ubuntu-12-04-amd64-repository-11-dvd-pack") which should be useful for you. Suggested 12.04 since I was unable to find 12.10 Repository DVD pack in that website.

---

### Post by evilsoup on 2012-11-29
> **ANiK3T said:**
> Hi all
i m a windows user
i want to remove it and install a fresh ubuntu 12.10 version on it

I would strongly recommend against getting rid of Windows entirely, as you may find that you actually do need some program that is only available on Windows. I suggest trying Ubuntu out with [wubi](http://www.psychocats.net/ubuntu/wubi) for a few months before committing to anything irreversible.

---


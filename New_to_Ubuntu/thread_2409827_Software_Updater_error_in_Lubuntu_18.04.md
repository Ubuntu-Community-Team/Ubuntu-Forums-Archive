---
title: "Software Updater error in Lubuntu 18.04"
date: 2019-01-07
forum: New to Ubuntu
---

### Post by kesetyan on 2019-01-07
Hi,

When I run the Software Updater in Lubuntu I get the error message 'Failed to download repository information'.   If I click 'OK' another message appears stating 'No software updates are available'.  Sometimes I see a message stating 'The software on this computer is up to date' - that seems to appear after the cache is updated and follows another error message about the repository.

This is all very confusing and  I am somewhat out of my depth in trying to understand.

Thanks.

---

### Post by howefield on 2019-01-07
If you don't mind using the terminal, you could try the following ommand and then post back the output..

```
sudo apt update
```

---

### Post by kesetyan on 2019-01-07
Hi howefield;

Thanks for replying so quickly.

I've copied and pasted the following from the terminal after running the command you suggested:

Ign:1 [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu) bionic InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Err:4 [http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu](http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu) bionic Release    
  404  Not Found [IP: 91.189.95.83 80]
Hit:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) bionic-security InRelease
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/ravefinity-project/ppa/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

Hope this is useful.  Regards.

---

### Post by kesetyan on 2019-01-07
Hi howefield,

UPDATE:
Having run the command you suggested and seeing the error reported in the terminal (as included in my last post), I disabled the ravefinity-project item in the updater and I now no longer get the original error I reported.  I don't know what the Ravefinty Project is or whether or not I should delete it from the updater.  I await your advice with interest.

Thanks.

---

### Post by howefield on 2019-01-07
Basically, there is no ravefinity repository available for Bionic (Ubuntu 18.04) hence the error.

You have two choices, first and not recommended is to change the ravefinity ppa to point to the latest release that it supports, but not recommended as it may be looking for dependencies that have changed or are not even available.

Best to not use the repository and remove it from your sources.list file or /ect/apt/sources.list.d folder. Are you aware of how that is done ?

---

### Post by howefield on 2019-01-07
> **kesetyan said:**
> I don't know what the Ravefinty Project is or whether or not I should delete it from the updater.

We posted at the same time there. :)

The ravefinity project seems to be for themes and icons, it doesn't come as default so you must have enabled it at some point.

> The RAVEfinity Project's Official Theme PPA. Makes it easy to install RAVEfinity themes and icons. And get the "latest and greatest" artwork and themes right when they are released. (And often a few hours before they are even publicly announced! Like a true VIP.)

Now that you have removed it, you can use..

```
sudo apt update
```
```
sudo apt upgrade
```

to update your machine.

---

### Post by kesetyan on 2019-01-07
Hi howefield,

Thanks for your helpful reply.  I've run the commands you suggested in the terminal and no errors appeared.

Are those terminal commands an equivalent alternative to running the 'Software Updater' from 'System Tools' in the menu on the panel?

I can't remember enabling Ravefinity but I did recently investigate the possibility of adding alternative icon sets so must have enabled it - certainly I don't need it so am happy to delete it.

---

### Post by howefield on 2019-01-07
Hello kesetyan,

Yes, those two terminal commands are pretty much the same as running the Software Updater, I prefer using the terminal only because it shows better what is happening and gives a bit more information.

Just for info, I remove all packages responsible for updating and put an alias into ~/.bashrc as follows..

```
alias update='sudo apt update && sudo apt -y upgrade && sudo apt clean && sudo apt autoclean && sudo apt -y autoremove'
```

so by typing update in the terminal it automatically updates the package sources, performs any package upgrades and then cleans up. Wouldn't  necessarily recommend that for anyone else, it's just what I do to update the system.

---

### Post by kesetyan on 2019-01-07
Hi howefield,

What a great teacher you are for a newby like me.  Having access to this forum and the advice of experienced forum members like you, convinces me that deciding not to go to Windows 10 when Microsoft support for Windows 7 ceases next year, but to use Ubuntu and its derivatives on my two desktops instead, was my best option.  I'm using Lubuntu 18.04 LTS in a dual boot arrangement with Windows 7 (the latter will have the internet capability disabled next January) and using Ubuntu 18.04 LTS on a new desktop - in addition, I have several live Puppy Linux usb pendrives (I hope stating that is not a sin on this forum).

I might well try your script file suggestion, it sounds a good idea although I will see how it goes before actually removing the updating packages.

Thanks for your help and for building my confidence.  Cheers and regards.

---

### Post by kesetyan on 2019-01-07
Hi howefield,

UPDATE:

I typed your lines (actually copied and pasted) into .bashrc and saved.  Typed update into the terminal, gave my password and voila - it ran perfectly.

I've yet to delete the updater packages - I might bide my time on that until I'm absolutely sure which packages, where they are located and the best way to remove them safely.

Good progress today - thanks.

---

### Post by CatKiller on 2019-01-07
> **kesetyan said:**
> I've yet to delete the updater packages - I might bide my time on that until I'm absolutely sure which packages, where they are located and the best way to remove them safely.

A manual way to do it is to visit the PPA in a web browser to see which packages are made available, and remove those you no longer require.

An automatic way is to install the ppa-purge package, which will remove the specified PPA and all the installed packages from it.

---

### Post by kesetyan on 2019-01-08
Hi catkiller,

Thanks for your suggestion - I'll have go.

Cheers.

---


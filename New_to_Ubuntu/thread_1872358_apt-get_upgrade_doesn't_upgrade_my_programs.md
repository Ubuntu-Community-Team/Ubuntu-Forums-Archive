---
title: "apt-get upgrade doesn't upgrade my programs"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by moraxu on 2011-10-30
Hi there,

I'd like to know if 

```
apt-get upgrade
```

cmd ignores programs installed by means of Ubuntu Software Center ?

---

### Post by Paqman on 2011-10-30
It will upgrade anything you install using the package manager if an upgrade is available. So yes, it will update anything from Software Centre.

What are you trying to update, and what version are you running?

---

### Post by philinux on 2011-10-30
> **moraxu said:**
> Hi there,

I'd like to know if 

```
apt-get upgrade
```

cmd ignores programs installed by means of Ubuntu Software Center ?

Try this.

sudo apt-get update && sudo apt-get upgrade

---

### Post by moraxu on 2011-10-30
> **philinux said:**
> Try this.

sudo apt-get update && sudo apt-get upgrade

I already did.

> **Paqman said:**
> What are you trying to update, and what version are you running?

I was trying to update VirtualBox to 4.1.4 version from 4.1.2. I did it by typing this cmd:

```
sudo dpkg -i package_name.deb
```

I hope I'll can update it easily from now on.

---

### Post by Paqman on 2011-10-30
> **moraxu said:**
> 
I was trying to update VirtualBox to 4.1.4 version from 4.1.2. I did it by typing this cmd:

```
sudo dpkg -i package_name.deb
```

I hope I'll can update it easily from now on.

To get automatic updates you should add the Virtualbox repository, instructions for that are on the download page. Once you've add the repo you'll be able to update Virtualbox through Update Manager (or sudo apt-get upgrade). Virtualbox is a bit unusual in that it will also offer you a link to grab the .deb directly, but you can just ignore that if you want.

---

### Post by Silent Warrior on 2011-10-30
moraxu: If you install from Ubuntu's repositories using a package manager (Software Centre, Synaptic, PackageKit, Muon, WHATEVER - seriously, how many package managers do we have these days??), you will NEVER have ANY REASON AT ALL to use dpkg*. If you're sure there is an update in Ubuntu's repositories, you WILL find it there. You make it sound as if you've installed a package you downloaded yourself (VirtualBox from Oracle's website?), and those will NOT be updated through Update Manager/apt-get upgrade/Synaptic, for the simple reason that package updates have to be uploaded to the repositories first (which has a couple of hurdles, for stability and QA) - you will have to find and install updates to packages downloaded through your web browser by yourself.

* The exception being some sort of conflict, or some other breakage. Considering the question, however, I don't believe for a second either applies to you (which, I should probably hasten to say, is a good thing). Don't make a habit of using dpkg unless you really know what you're doing, AND have a reason do do that instead of using Gdebi or a proper package manager - it's probably the quickest way to break your system, or at least cause instabilities and warning/error messages.

[Edit]
... Yeah, or you can follow Paqman's suggestion. Pox on me for being a slow writer.

---

### Post by moraxu on 2011-11-02
Well, still, some of those things aren't clear for me.

1)

> **Silent Warrior said:**
> package updates have to be uploaded to the repositories first (which has a couple of hurdles, for stability and QA)

Yes, I've read in a book that ubuntu's programmers didn't get used to put new versions of software in Ubuntu stable versions since it could violate system's stability. But if it was a true, Synaptic wouldn't have a "Check for Updates" option. Isn't it an inconsistency ?

2) My 2nd quesiton is: is updating programs by Update Manager the same thing as doing it by the Synaptic ?

3)

> **Paqman said:**
> To get automatic updates you should add the Virtualbox repository, instructions for that are on the download page.

Well, maybe that's the reason why VirtualBox's version in Synaptic is still 4.1.2 instead of 4.1.4 (the newest one). Anyway, I should type this cmd, right ?

```
sudo add-apt-repository 'deb http://download.virtualbox.org/virtualbox/debian oneiric contrib'
```(I'd like to make sure whether I do this right, since I don't want to mess up in system).

---

### Post by Silent Warrior on 2011-11-03
1. It isn't inconsistent in the slightest. The packages are made from versions of software that are deemed stable enough - and then there are some criteriae for when an update should be uploaded. If the only real gain is a small version bump, I wouldn't be surprised if the packagers feel it's just more trouble than it's worth. If you want to know more about the updating policy, I, for one, am not the go-to guy.

2. In a nutshell, yes. They look through the same repositories, getting you the same packages; the only difference is the GUI.

3. I'm too lazy to go to their site and double check, but entering an incorrect PPA won't do anything worse than the update checking throwing an error message about not finding the package list. The important bit is installing packages for the correct version of Ubuntu - if you're using Oneiric (11.10), that command looks good to me. Just keep in mind that only the packages in the Ubuntu repositories are officially supported - if you have a problem with the new version, there's no guarantee we can come up with a solution HERE.

---


---
title: "packages held back in apt-get?"
date: 2017-08-01
forum: New to Ubuntu
---

### Post by blank-in-memory on 2017-08-01
Yesterday, I ran Software Updater and got a popup indicating not all packages could be installed and suggested a "partial upgrade" to install. I read some conflicting advice both here in the forums and at AskUbuntu suggesting that partial upgrades are a bad idea, but really I should be updating via the terminal rather than the GUI.

A little confused, I ran 'sudo apt-get update && sudo apt-get upgrade'. 58 packages updated, 0 removed, and 10 held back. And I guess I assumed this would resolve the problem and make the 10 held back packages ready for a proper download. But even after I ran the update with apt-get in terminal and rebooting, I'm still getting the GUI 'partial upgrade' popup and the following in terminal:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-headers-4.4.0-77
  linux-headers-4.4.0-77-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-image-4.4.0-72-generic
  linux-image-4.4.0-77-generic linux-image-4.4.0-79-generic
  linux-image-4.4.0-81-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-77-generic linux-image-extra-4.4.0-79-generic
  linux-image-extra-4.4.0-81-generic snap-confine
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  libegl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libgles2-mesa libinput10 libwayland-egl1-mesa libxatracker2
  ubuntu-mate-welcome
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```

Now, one of the held back packages -- 'ubuntu-mate-welcome' -- I deliberately put off installing when it first appeared a week ago (I just didn't want to run it at the time and it didn't seem to be a security update). But the other 9 I don't remember seeing before, and at least 8 of 9 appear to be necessary, security-related updates and all related to each other.

Can someone help me understand what is going on here and what to do?  Are these 10 packages being held back for a good reason (like problems with dependencies, etc.) that I can sort out by installing them via Synaptic?  Should I [follow this advice]("https://askubuntu.com/questions/58928/update-manager-says-not-all-updates-can-be-installed") to install each one individually in terminal with 

```
sudo apt-get install <package name>
```

 Or is this something I should just wait for the package devs to sort out?

---

### Post by deadflowr on 2017-08-01
It's simply a matter of the command in use
apt-get upgrade only installs updates for packages already installed.
If, as is the case here, the updates include new packages, then you need to run
```
sudo apt-get dist-upgrade
```
which will allow the installation of those new packages.

To Add:
Though the command seems like it would upgrade the Ubuntu release to a new release (like upgrading from 16.04 to 17.04) that is not what it does.
It only updates the packages for the release you are on.

---

### Post by Bucky Ball on 2017-08-01
As above, but I will add that before running that command, you should run this one (in your case, the Software Updater would have already run it):

```
sudo apt update
```

Instead of the command suggested by deadflowr, which I used to use, I now use this:

```
sudo apt full-upgrade
```

I *_think_* it does the same thing. deadflowr? Do you know if that's the case?

Again, my command WON'T upgrade you to a newer release, just upgrade what you already have.

---

### Post by vocx on 2017-08-01
> **blank-in-memory said:**
> ...
```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
...
Use 'sudo apt autoremove' to remove them.

```
...
Can someone help me understand what is going on here and what to do?  Are these 10 packages being held back for a good reason (like problems with dependencies, etc.) that I can sort out by installing them via Synaptic?  Should I [follow this advice]("https://askubuntu.com/questions/58928/update-manager-says-not-all-updates-can-be-installed") to install each one individually in terminal with 

```
sudo apt-get install <package name>
```

 Or is this something I should just wait for the package devs to sort out?
I think deadflowr and Bucky Ball have already given sound advice. Basically there is no problem installing the packages listed there. I honestly don't know why some packages turn out "held back" but in my experience it's never a problem, and you can install them manually to get everything done nicely.
```

sudo apt install libegl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa libinput10 libwayland-egl1-mesa libxatracker2 ubuntu-mate-welcome

```

I believe what deadflowr says is the key. Basically, most packages have "dependencies", which are packages that definitely need to be installed before that other package is installed. However, as software is always changing and improvements are being done, sometimes developers split their code into smaller packages that can be installed separately. Therefore, if a package A used to depend on package B, maybe now it may depend on C and D. So, package B becomes obsolete, and now you have to install C and D. I think this is what you are seeing in this case. As new dependencies are introduced, maybe the APT system is careful to not install the new packages immediately, giving you the option of keeping the old system intact. However, normally you would keep with the developers wishes and install the held packages. The packages are vetted by the developers and package maintainers, so you should probably trust that the new packages are okay.

By the way, your terminal also gives you the message that you have some old kernels, so you should probably remove these as well, just to save yourself some 1000 MB of kernel and header files.
```

sudo apt autoremove

```

---

### Post by blank-in-memory on 2017-08-02
> **deadflowr said:**
> It's simply a matter of the command in use
apt-get upgrade only installs updates for packages already installed.
If, as is the case here, the updates include new packages, then you need to run
```
sudo apt-get dist-upgrade
```
which will allow the installation of those new packages.

To Add:
Though the command seems like it would upgrade the Ubuntu release to a new release (like upgrading from 16.04 to 17.04) that is not what it does.
It only updates the packages for the release you are on.

Thanks so much, deadflowr! Your edit made all the difference; I was *sure* 'dist-upgrade' would mean an OS upgrade--really counterintuitive to me. Thanks for pointing this out. I ran your command and everything seems fine. Cheers! :D

Edited to add: Just to clarify, this was the first time I've seen packages held back, and though I feel like a noob even now I've run Ubuntu for close to 10 years!  So that really struck me funny / had me a bit worried. Anyway, thanks again everyone for reassuring me it's no big deal.

---


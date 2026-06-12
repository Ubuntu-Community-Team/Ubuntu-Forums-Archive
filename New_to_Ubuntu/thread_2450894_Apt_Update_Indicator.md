---
title: "Apt Update Indicator"
date: 2020-09-23
forum: New to Ubuntu
---

### Post by desertwalker1 on 2020-09-23
A quick question about the extension Apt Update Indicator.

I recently installed it and want to know what the following mean: 

New in repository 
Residual config files

What should I do about them?

[ATTACH=CONFIG]287010[/ATTACH]

---

### Post by ajgreeny on 2020-09-23
Residual config files are those from packages that you have probably removed but not purged, thus leaving configurations still in the system.
There is no necessity to remove them, and they may be useful if you decide to reinstall the package.

New in  repository means just what it says; the packages are new but if in the normal repos can still be trusted. I have never seen the extension you mention by that name; what version of Ubuntu are you using?

---

### Post by desertwalker1 on 2020-09-23
> **ajgreeny said:**
> Residual config files are those from packages that you have probably removed but not purged, thus leaving configurations still in the system.
There is no necessity to remove them, and they may be useful if you decide to reinstall the package.

New in  repository means just what it says; the packages are new but if in the normal repos can still be trusted. I have never seen the extension you mention by that name; what version of Ubuntu are you using?

Hey, thanks for the reply.

It's Ubuntu 20.04.

---

### Post by ActionParsnip on 2020-09-23
If you run:
```

sudo dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}`

```
This will remove residual config file for packages you uninstalled.

---

### Post by desertwalker1 on 2020-09-23
> **ActionParsnip said:**
> If you run:
```

sudo dpkg -P `dpkg -l | grep ^rc | awk {'print $2'}`

```
This will remove residual config file for packages you uninstalled.

Thanks for this. Appreciate it.

---

### Post by ActionParsnip on 2020-09-23
Did it clear the residual config message bit?

---

### Post by desertwalker1 on 2020-09-23
> **ActionParsnip said:**
> Did it clear the residual config message bit?

Yes it did. Just the 'New in repository' message left. Not sure how to address that.

---

### Post by deadflowr on 2020-09-23
I run this line for rc clearings
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y 
```
Note that rc is funny as it does not actually mean residual config, but it actually refers to two status states.
1) r (or the first letter) refers desired state of a package, in this case the desired state is for the package to be removed from the system. 
2) c (or the second letter) refers the actual states meaning the actual state is it still has configuration files installed.
But referring to rc as meaning residual configs fits it all too well, imo.
>  Just the 'New in repository' message left. Not sure how to address that.
Not sure either, but probably refers to either new versions of packages that have been added to a repository or packages which have new updates.
Most packages just get updates and not new packages with new version names. There are exceptions of course, like kernels.
Kernels actually get new versions with new names for each new kernel, ie, linux-image-5.4.0-48 is a different package than linux-image-5.4.0-47.

---

### Post by grahammechanical on 2020-09-23
It is a Gnome shell extension

[https://extensions.gnome.org/extension/1139/apt-update-indicator/](https://extensions.gnome.org/extension/1139/apt-update-indicator/)

Apparently it not only informs the user if there are updates available but also if a new package (application/program) has been added to the repositories. Just as we can have Editor's Picks and Featured Applications it seems we can also have What's New. 

I cannot wait for the Software Centre to inform me that I have new Facebook notifications and to nag me about having a Covid 19 test. Sometimes, clever is just too clever that it stops being nice.

Regards

---

### Post by desertwalker1 on 2020-09-23
> **deadflowr said:**
> I run this line for rc clearings
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo apt purge -y 
```
Note that rc is funny as it does not actually mean residual config, but it actually refers to two status states.
1) r (or the first letter) refers desired state of a package, in this case the desired state is for the package to be removed from the system. 
2) c (or the second letter) refers the actual states meaning the actual state is it still has configuration files installed.
But referring to rc as meaning residual configs fits it all too well, imo.

Not sure either, but probably refers to either new versions of packages that have been added to a repository or packages which have new updates.
Most packages just get updates and not new versions. There are exceptions of course, like kernels.
Kernels actually get new versions for each new kernel, ie, linux-image-5.4.0-48 is a different package than linux-image-5.4.0-47.

Appreciate the informative response! I clicked on the 'New in repository' message. It led to the following package: 'oem-somerville-caterpie-meta' 

Here's the screenshot:

[ATTACH=CONFIG]287012[/ATTACH]

---

### Post by #&amp;thj^% on 2020-09-23
Some information on that if interested.
[https://www.ubuntuupdates.org/package/core/focal/main/updates/oem-somerville-caterpie-meta](https://www.ubuntuupdates.org/package/core/focal/main/updates/oem-somerville-caterpie-meta)
Do you have Proposed enabled in your source.list?

---

### Post by desertwalker1 on 2020-09-23
> **grahammechanical said:**
> It is a Gnome shell extension

[https://extensions.gnome.org/extension/1139/apt-update-indicator/](https://extensions.gnome.org/extension/1139/apt-update-indicator/)

Apparently it not only informs the user if there are updates available but also if a new package (application/program) has been added to the repositories. Just as we can have Editor's Picks and Featured Applications it seems we can also have What's New. 

I cannot wait for the Software Centre to inform me that I have new Facebook notifications and to nag me about having a Covid 19 test. Sometimes, clever is just too clever that it stops being nice.

Regards

Thanks for the reply. Yep, just giving a couple of extensions a look. I'm not sure how useful this one is. How often do you need to address the things mentioned in this extension (updates, residual files, autoremovable files etc) as it is?

> **1fallen said:**
> Some information on that if interested.
[https://www.ubuntuupdates.org/package/core/focal/main/updates/oem-somerville-caterpie-meta](https://www.ubuntuupdates.org/package/core/focal/main/updates/oem-somerville-caterpie-meta)
Do you have Proposed enabled in your source.list?

Appreciate the link. Unfortunately I'm a complete newbie when it comes to linux. I'm not sure how I would check that. Is 'proposed' a repository? Does it by any chance have any thing to do with multimedia codecs? I have them enabled. 

I suppose what I'm really asking is; do I need to address the New in repository files? If so, with what command/action? :P

---

### Post by #&amp;thj^% on 2020-09-23
> **desertwalker1 said:**
> 
Appreciate the link. Unfortunately I'm a complete newbie when it comes to linux. I'm not sure how I would check that. Is 'proposed' a repository? Does it by any chance have any thing to do with multimedia codecs? I have them enabled. 

I suppose what I'm really asking is; do I need to address the New in repository files? If so, with what command/action? :P

A couple of ways to see.
```
cat /etc/apt/sources.list
```
Or  
```
sudo apt install inxi
```
then issue
```
inxi -r 
```
Inxi is a useful tool.
Forgot this one also to see where a package come from, (Repo wise)
```
apt policy oem-somerville-caterpie-meta
```

---

### Post by ActionParsnip on 2020-09-23
Possibly just run updates
```

sudo apt update 
sudo apt upgrade 

```

---

### Post by Impavidus on 2020-09-24
> **desertwalker1 said:**
> Thanks for the reply. Yep, just giving a couple of extensions a look. I'm not sure how useful this one is. How often do you need to address the things mentioned in this extension (updates, residual files, autoremovable files etc) as it is?
- Updates: When available, install. I install them daily, but others only weekly. Some people configure their system to install security updates automatically every day.
- Residual files: They will only appear when you remove a package without purging it. When you've done so and are sure you will no longer need those config files, you can remove those residual files.
- Autoremovable: They will only appear after you removed the packages that depended on them, or upgraded those dependent packages to a version with new dependencies. This typically happens with kernel upgrades. Unless you plan to install some package that depends on the autoremovable package, you can remove it. If you still need the autoremovable package (rarely happens), you can mark it manually installed.

> Appreciate the link. Unfortunately I'm a complete newbie when it comes to linux. I'm not sure how I would check that. Is 'proposed' a repository? Does it by any chance have any thing to do with multimedia codecs? I have them enabled.
"Proposed" is a repository for upgrades that are still being tested. When the developers think the update is ready, it's put in the "proposed" repository, where it can be used by people needing an urgent bugfix or people testing the upgrade. If this doesn't lead to a surge of bugreports, the upgrade is put in the regular repositories.

> I suppose what I'm really asking is; do I need to address the New in repository files? If so, with what command/action? :P
No need to do anything with packages new in the repository.

---

### Post by desertwalker1 on 2020-09-25
> **1fallen said:**
> A couple of ways to see.
```
cat /etc/apt/sources.list
```
Or  
```
sudo apt install inxi
```
then issue
```
inxi -r 
```
Inxi is a useful tool.
Forgot this one also to see where a package come from, (Repo wise)
```
apt policy oem-somerville-caterpie-meta
```

Apologies for the late update guys. Thanks for the codes. The sources.list did not include 'proposed' (used the inxi-r command). 

Edit: adding the command results: 

Repos:     Active apt repos in: /etc/apt/sources.list 
           1: deb focal main restricted
           2: deb focal-updates main restricted
           3: deb focal universe
           4: deb focal-updates universe
           5: deb focal multiverse
           6: deb focal-updates multiverse
           7: deb focal-backports main restricted universe multiverse
           8: deb focal partner
           9: deb focal-security main restricted
           10: deb focal-security universe
           11: deb focal-security multiverse


Also tried the apt policy command for that particular package: 
apt policy oem-somerville-caterpie-meta
oem-somerville-caterpie-meta:
  Installed: (none)
  Candidate: 20.04~ubuntu1
  Version table:
     20.04~ubuntu1 500
        500 focal-updates/main amd64 Packages
        500 focal-updates/main i386 Packages


> **ActionParsnip said:**
> Possibly just run updates
```

sudo apt update 
sudo apt upgrade 

```

Thanks for the suggestion. I've been running update + upgrade daily. 

> **Impavidus said:**
> - Updates: When available, install. I install them daily, but others only weekly. Some people configure their system to install security updates automatically every day.
- Residual files: They will only appear when you remove a package without purging it. When you've done so and are sure you will no longer need those config files, you can remove those residual files.
- Autoremovable: They will only appear after you removed the packages that depended on them, or upgraded those dependent packages to a version with new dependencies. This typically happens with kernel upgrades. Unless you plan to install some package that depends on the autoremovable package, you can remove it. If you still need the autoremovable package (rarely happens), you can mark it manually installed.


"Proposed" is a repository for upgrades that are still being tested. When the developers think the update is ready, it's put in the "proposed" repository, where it can be used by people needing an urgent bugfix or people testing the upgrade. If this doesn't lead to a surge of bugreports, the upgrade is put in the regular repositories.


No need to do anything with packages new in the repository.

Appreciate the info. I suppose just run updates and ignore the New in repository messages then? If that's the case this thread has reached its end. :P

---


---
title: "software installation problem"
date: 2017-02-04
forum: New to Ubuntu
---

### Post by laborant on 2017-02-04
Hallo,

I have Ubuntu 16.10 LTS installed. Since a few days software can not be installed or removed either with Synaptic or with apt-get 

With ```
sudo apt-get -f install
``` I got the following messages (last lines of the output)

```
Errors occurred while editing:
 /var/cache/apt/archives/python3-distupgrade_1%3a16.04.21_all.deb
 /var/cache/apt/archives/python3-update-manager_1%3a16.04.5_all.deb
 /var/cache/apt/archives/update-manager_1%3a16.04.5_all.deb
 /var/cache/apt/archives/software-properties-common_0.96.20.5_all.deb
 /var/cache/apt/archives/software-properties-kde_0.96.20.5_all.deb
 /var/cache/apt/archives/software-properties-gtk_0.96.20.5_all.deb
 /var/cache/apt/archives/python3-software-properties_0.96.20.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

with the command ```
sudo apt-get autoremove
```  get following output:

```
The following packages have unfulfilled dependencies:

kdenlive : Hängt ab von: kdenlive-data (= 4:16.08.2~ubuntu16.04.1) aber 4:16.12.1-2~ubuntu16.04.1 ist installiert
 libxine2 : Hängt ab von: libxine2-bin (= 1.2.6-1build5) aber 1:1.2.2-dmo3 ist installiert
 libxine2-ffmpeg : Hängt ab von: libxine2-bin (= 1.2.6-1build5) aber 1:1.2.2-dmo3 ist installiert
 libxine2-misc-plugins : Hängt ab von: libxine2-bin (= 1.2.6-1build5) aber 1:1.2.2-dmo3 ist installiert
 ubuntu-release-upgrader-core : Hängt ab von: python3-distupgrade (= 1:16.04.21) aber 1:16.04.18 ist installiert
 ubuntu-release-upgrader-gtk : Hängt ab von: python3-distupgrade (= 1:16.04.21) aber 1:16.04.18 ist installiert
 update-manager : Hängt ab von: update-manager-core (= 1:16.04.4) aber 1:16.04.5 ist installiert
 update-manager-core : Hängt ab von: python3-update-manager (= 1:16.04.5) aber 1:16.04.4 ist installiert

```
Synaptic Package Manager marks the same Packages as above  as broken:

but Synaptic is not able to repair the broken Packages.

I tried to install the missing dependies manually, but got stuck because the system comes always up with the same error messages. 


I appreciate any help to fix the problem.

---

### Post by Impavidus on 2017-02-04
16.10 is not an LTS release. So you have 16.10 or 16.04 LTS.

Try```
sudo apt update
sudo apt install -f
```and show the complete output. The first error mentioned usually gives the most important clue.

---

### Post by ian-weisser on 2017-02-04
Please show us the complete, unedited error output. Lots of helpful detail is above the summary.

Looks like you have a set of version conflicts. You added sources for the for the wrong release of Ubuntu, or you added non-Ubuntu sources like PPAs, or you downloaded .debs that were only marginally-compatible with your release of Ubuntu. That incompatible software from those incompatible sources are causing your problem.

Here's an example from your attempt to install kdenlive:
```
update-manager : Hängt ab von: update-manager-core (= **1:16.04.4**) aber **1:16.04.5** ist installiert
```
1:16.04.5, currently installed, is the version in xenal-updates (Ubuntu 16.04), **not 16.10**&#8203;. The current version in 16.10 is 1:16.10.7 (yakkety) and 1:16.10.8 (yakkety-proposed)
1:16.04.4, kdelive wants, is not in any repo of Ubuntu. You seem to be trying to install kdelive, with all it's dependencies, from an incompatible, non-Ubuntu source. That is most unwise, and will thoroughly break your system.

The solution to fix most systems is five steps. Do them in order. Do not skip any steps, or the problem may return:
First, delete all non-Ubuntu sources. Also delete all sources from a different release of Ubuntu.
Second, uninstall ALL non-Ubuntu software from those sources,
Third, delete all non-Ubuntu packages from your local apt cache (sudo apt autoclean)
Fourth, rebuild your package database (sudo apt update)
Finally, install compatible versions of the software from the Ubuntu repos (sudo apt install kdenlive)

The first two steps are hardest because only you know what sources and software you installed.

However, You are running 16.10 using 16.04 packages...which means you are not actually running 16.10 but some kind of [frankensystem]("https://wiki.debian.org/DontBreakDebian#Don.27t_make_a_FrankenDebian"). If you find untangling the threads too challenging, then preserve your data and reinstall.

---


---
title: "LUBUNTU How install &quot;obsolete&quot; software ?"
date: 2020-07-30
forum: New to Ubuntu
---

### Post by aug7744 on 2020-07-30
Using Lubuntu 20.04. Trying to install an deb package is displayed an message "an new version is available" and the install is blocked. How to install an deb package if is being blocked only because is "old" version ? Thanks for reply.

---

### Post by CelticWarrior on 2020-07-30
"A new version is available" message appears when the same but newer software is in the repository.
Why do you think you need to install an older version and not form the official repository?

---

### Post by GhX6GZMB on 2020-07-30
> **CelticWarrior said:**
> "A new version is available" message appears when the same but newer software is in the repository.
Why do you think you need to install an older version and not form the official repository?

I think I can answer that, I made the same mistake when starting with Ubuntu.

It's a mindset thing when coming from the MS world. Win users have over the years been brainwashed into accepting the "planned obsolesce" strategy of MS support for older hardware, which forces you to install older program versions if you have older hardware.
The Linux system of "once in the repository it stays in the repository" has to be learned and accepted first.

---

### Post by aug7744 on 2020-07-31
I wait have all packages downloaded saved in an folder to avoid download again. I had downloaded an software from debian repository and was the latest version, but had an new version unstable. Lubuntu wait to install the latest version unstable. I wait to avoid it.

---

### Post by ActionParsnip on 2020-07-31
Then you only have a snapshot of the version of the package in time. If the release of Ubuntu is still supported it will hit the repositories and see a newer version. Is your Web access limited or expensive per gigabyte or something like that?

---

### Post by aug7744 on 2020-07-31
Metered connection and slow. I wait avoid download all again if Lubuntu need to be reinstalled. I have an software that is last version, but Lubuntu not allow to install instead try to install latest unstable version :-( Not is possible to disable the block install for some softwares ?

---

### Post by Impavidus on 2020-07-31
Packages get cached in /var/cache/apt/archives/. This cache can be cleared automatically, so you may have to tweak some settings to prevent that.

Debian only calls something stable when it's really rock solid, therefore a bit old. Mixing Debian and Ubuntu may not work very well.

---

### Post by aug7744 on 2020-07-31
"Packages get cached in /var/cache/apt/archives/. This cache can be  cleared automatically, so you may have to tweak some settings to prevent  that."
That means if I configure to not clear that package cache is possible if copied that folder to an reinstalled system install package without download again ?

---

### Post by Impavidus on 2020-08-01
I think apt-get, update-manager and synaptic keep all downloaded packages in cache until it's cleared, but apt removes packages from cache after succesful installation. I guess that can be configured. You may have to dig deeply in the manuals.```
sudo apt-get autoclean
```removes packages from cache that are no longer available, like packages that have been replaced by upgraded versions. It would be OK for you to run that occasionally (like before backing up /var/cache/apt/archives/).```
sudo apt-get clean
```deletes all cache, so don't run that if downloads are more expensive to you than storage.

When you want to reinstall &#8211; and I don't know how often you're going to break your system &#8211; you can backup /var/cache/apt/archives/ to external storage. Then install Lubuntu (or any other flavour) without downloading and installing upgrades during the initial install. That's an option, so don't enable that. Then copy the .debs from your backup back to the new /var/cache/apt/archives/ and install upgrades and additional software. All packages that already have the latest version in your cache won't be downloaded again.

Note that I never tried this myself.

---

### Post by monkeybrain20122 on 2020-08-01
Strange. As long as the newer version is not already installed (or you can uninstall it first) you can just ignore the warning and install it anyway, then pin the package, that is assuming that you install the .deb with gdebi, with the command it may not let you, I haven't installed old packages with command (did it a few times with gdebi though since compiling tensorflow needs different versions of bazel, sometimes I have to downgrade)

---

### Post by monkeybrain20122 on 2020-08-02
> **Impavidus said:**
> 

Debian only calls something stable when it's really rock solid.

Or broken in a consistent and predictable way. I have tried Debian stable before, not only is the software old enough to go to the museum, some are also buggy since upstream bug fixes would never be backported unless it is security vulnerability. Speaking for myself I wouldn't care for "stability" in Debian speak, but that is just me, I am sure some would disagree.

---

### Post by aug7744 on 2020-08-02
@Impavidus
"I think apt-get, update-manager and synaptic keep all downloaded packages in cache until it's cleared, but apt removes packages from cache after succesful installation. I guess that can be configured. You may have to dig deeply in the manuals."
How configure to avoid the cache to be cleared after installation ? Where is information about it ?

"Packages get cached in /var/cache/apt/archives/. This cache can be cleared automatically, so you may have to tweak some settings to prevent that."
Is possible create an folder in second partition and create an symbolic link to /var/cache/apt/archives/ thus avoiding to copy all again to system partition ?

I had downloaded software in debian repository because not have the software in Ubuntu repository.
Another problem is an software that only is available in software site.

---

### Post by Impavidus on 2020-08-02
> **aug7744 said:**
> @Impavidus
"I think apt-get, update-manager and synaptic keep all downloaded packages in cache until it's cleared, but apt removes packages from cache after successful installation. I guess that can be configured. You may have to dig deeply in the manuals."
How configure to avoid the cache to be cleared after installation ? Where is information about it ?A lot of information can be found in the manuals. Use```
man [subject]
```to read the manual page about one subject, like a command or a system config file. They're not always easy to read, but it's a great way to learn about Linux systems. In this case, I suggest these:```
man apt
man apt-config
man apt.conf
```This all suggests that you can set```
Binary::apt::APT::Keep-Downloaded-Packages "1";
```in a config file where apt-config will read it, so that apt will no longer clear cache automatically after successful installation. For the other tools that was the default already.

> "Packages get cached in /var/cache/apt/archives/. This cache can be cleared automatically, so you may have to tweak some settings to prevent that."
Is possible create an folder in second partition and create an symbolic link to /var/cache/apt/archives/ thus avoiding to copy all again to system partition ?It may work if you create a directory for these cached .deb files on a different partition and replace your /var/cache/apt/archives/ with a symlink to this directory. Be careful though. It will cause weird problems if you attempt to use the package manager when that second partition isn't mounted or is mounted in an unexpected place. This will happen if you ever try to fix package management in recovery mode, when such partitions don't get mounted automatically. Also make sure this second partition has a native Linux filesystem and you give the cache directory there the same permissions and owner as the original. I never tried this myself, but most tools don't care about following some symlinks to get to the files they need. You can even make a dedicated partition for this apt cache and mount it at /var/cache/apt/archives, but you'll probably either make it too small (causing errors) or too big (wasting disk space) and will definitely make things opaque.

> I had downloaded software in debian repository because not have the software in Ubuntu repository.
Another problem is an software that only is available in software site.First choice is the Ubuntu repository, second choice is an alternative from the Ubuntu repository. You can install software from .debs from other sources, but keep track of them. Those packages may cause problems, so keep an eye on it and remove it when such problems arise.

---

### Post by aug7744 on 2020-08-03
" Binary::apt::APT::Keep-Downloaded-Packages "1"; "
The command need to be exaclt how is above to configure to not clear cache after installation ?

"You can install software from .debs from other sources, but keep track of them. Those packages may cause problems, so keep an eye on it and remove it when such problems arise."
Problems with wrong dependencies or virus ?

---

### Post by Impavidus on 2020-08-03
> **aug7744 said:**
> " Binary::apt::APT::Keep-Downloaded-Packages "1"; "
The command need to be exaclt how is above to configure to not clear cache after installation ?Have a look at the manual and the config files you find in /etc/apt/apt.conf.d/. You should be able to put the line in /etc/apt/apt.conf (create it if it doesn't exist). Actually, maybe you need the option Clean-Installed (and set it to 0) instead of Keep-Downloaded-Packages. I don't know, but the manual appears good.

> "You can install software from .debs from other sources, but keep track of them. Those packages may cause problems, so keep an eye on it and remove it when such problems arise."
Problems with wrong dependencies or virus ?
Problems with wrong dependencies. If there's malware in the .deb, it will be installed the moment you install the .deb, so don't install .debs from untrusted sources. If there's no malware in it, it won't appear later, unless you download a new version and install that.

---

### Post by aug7744 on 2020-08-13
Finnally I now understand the problem.
Thanks for all replies.

---


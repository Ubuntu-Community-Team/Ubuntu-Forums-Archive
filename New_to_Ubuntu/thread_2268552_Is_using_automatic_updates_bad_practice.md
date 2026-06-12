---
title: "Is using automatic updates bad practice?"
date: 2015-03-09
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-03-09
I currently have minimal Ubuntu with Synaptic installed. I want one application that is capable of doing all things package-related and it seems like Synaptic is pretty solid, but I cannot find a way for it to automatically detect package updates in the background (or at system startup) like Muon for Kubuntu can. In fact, because I was so used to entering a password whenever Muon prompted package updates on startup, I had forgotten I needed to constantly install security fixes and update packages. 

Since Synaptic seems to not have the function of automatically detecting package updates, I found "unattended-grades": [https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html).

Anyone used it? Is it safe to use and is it bad practice? Is it not advised to automatically install both regular packages and security-related packages?

Also, how do I know what to put in place of 
"Ubuntu trusty-security"
"Ubuntu trusty-updates"

if I'm using 14.10?

---

### Post by newb85 on 2015-03-09
Hmm... In a typical install, there's a way in Software & Updates to have security updates automatically installed.  But then, I imagine you don't have that dialog on a minimal install.  Perhaps you should have a look at /etc/apt/apt.conf.d/10periodic.

As to unattended-upgrades, I use it.  Everything from the main repos updates automatically in the background.  However, I haven't found a way to make it include PPA's.

I would imagine those two lines need to be changed to 
"ubuntu utopic-security"
"ubuntu utopic-updates"

But how did you end up with a source list that included those in Utopic?

---

### Post by ian-weisser on 2015-03-09
> **garycheng12 said:**
> Anyone used it? Is it safe to use and is it bad practice?
It's been quite safe for me for years.


> **garycheng12 said:**
> Also, how do I know what to put in place of 
"Ubuntu trusty-security"
"Ubuntu trusty-updates"

if I'm using 14.10?
Use the release name.
"Ubuntu utopic-security"
"Ubuntu utopic-updates"

Do note that auto-updates for those two repositories means normal, non-auto updates for -backports, PPAs, partner and non-Ubuntu repositories.
So check for those other updates using your Synaptic occasionally.

---

### Post by haplorrhine on 2015-03-09
I think the cronjob updates reset some apparmor profiles without notifying me, but I'll never know for sure.

---

### Post by ian-weisser on 2015-03-09
> **haplorrhine said:**
> I think the cronjob updates reset some apparmor profiles without notifying me, but I'll never know for sure.

If you can replicate the behavior, and show exactly which script is causing the problem, please file a bug report.
AppArmor profiles should not be 'reset', and your custom profiles should not be overridden.

---

### Post by deadflowr on 2015-03-10
> **newb85 said:**
> 
As to unattended-upgrades, I use it.  Everything from the main repos updates automatically in the background.  However, I haven't found a way to make it include PPA's.


You add the origin and suite from the ppa's Release file in /var/lib/apt/lists
in this section of the unattended-upgrades file in /etc/apt/apt/apt.conf.d/
```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}-security";
//    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";

```
add the ppa like this:
```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}-security";
//    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";
         "Whatever-it-says-in-the-origin-entry:whatever-it-says-in-the-suite-entry";

```
Save and run
```
sudo unattended-upgrades --debug
```

As a personal example I have firefox-trunk(nightly) installed and like to have it roll along on it's own.
So to add I look for the Release file, in this case /var/lib/apt/lists/ppa.launchpad.net_ubuntu-mozilla-daily_ppa_ubuntu_dists_precise_Release
Inside it looks like this:
```
Origin: LP-PPA-ubuntu-mozilla-daily
Label: Firefox and Thunderbird daily builds
Suite: precise
Version: 12.04
Codename: precise
Date: Fri, 06 Mar 2015 19:03:58 UTC
Architectures: amd64 armel armhf i386 powerpc
Components: main
Description: Ubuntu Precise 12.04
MD5Sum:
```
I then take the origin and the suite and add to the unattended-upgrades file like so:
```
// Automatically upgrade packages from these (origin:archive) pairs
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}-security";
//    "${distro_id}:${distro_codename}-updates";
//    "${distro_id}:${distro_codename}-proposed";
//    "${distro_id}:${distro_codename}-backports";
       "LP-PPA-ubuntu-mozilla-daily:precise";

```
then run the upgrade with debug to check. It will show if the line is correctly placed or not.
You can also set up mail to send you an email, or simply look over the unattended-upgrades logfiles in /var/log/unattended-upgrades.

Should work, hope this helps.

edit:adding: I should point out that if you have a ppa for something like gogle-chrome, then origin will be Google Inc, which has a space.
For these you need to add a \ after Google and before Inc, as Google's origins are google Inc. So in these cases and types like it do
Google\ Inc.
this way it'll know it is one entry and not two seperate entries, which can cause it not to work, for obvious reasons.

---

### Post by mastablasta on 2015-03-10
I have it setup on server. security only. which is a good thing as owncloud broke in last update and i had to manually fix it.

---

### Post by newb85 on 2015-03-10
> **deadflowr said:**
> You add the origin and suite from the ppa's Release file in /var/lib/apt/lists
in this section of the unattended-upgrades file in /etc/apt/apt/apt.conf.d/


You have too many /apt in there ;)

Thanks!  I had tried that before, but the instructions I was following weren't as good as yours.  I think I've had success this time.  Last time it just made unattended-upgrades crash.

---


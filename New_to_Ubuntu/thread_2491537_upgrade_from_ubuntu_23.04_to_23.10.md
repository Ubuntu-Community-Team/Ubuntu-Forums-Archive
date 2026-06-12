---
title: "upgrade from ubuntu 23.04 to 23.10"
date: 2023-10-12
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-10-12
first i did this
[LIST=1]
[*]sudo apt-get update
[*]sudo apt-get upgrade
[*]sudo apt-get dist-upgrade
[*]sudo do-release-upgrade
[*]sudo sed -i 's/lts/normal/g' /etc/update-manager/release-upgrades
[/LIST]
&#8203;Then it didn't upgrade

---

### Post by tuesdaybarrett on 2023-10-12
then it didn't upgrade

---

### Post by ian-weisser on 2023-10-12
Be patient. Not released yet. Try later.

---

### Post by Impavidus on 2023-10-12
The upgrade path is usually opened in the week after the live disk is released. But that's no hard rule.

---

### Post by Dennis N on 2023-10-12
At the moment, you can only install the new release as a new install with the 23.10 ISO. 

Checking availability with this:

```
dmn@Sydney-vm:~$ do-release-upgrade -c
Checking for a new Ubuntu release
No new release found.

```

Wait a few days and try again. Also, if you update your system with Software Updater, it will inform you of a new release when you do a regular update with it if that option is set in the Updates Tab of Software Updater settings.

---

### Post by tuesdaybarrett on 2023-10-12
i installed the beta version. It seem to work but  how can i change to full version and when can i do it
.

---

### Post by #&amp;thj^% on 2023-10-12
For my **:self:** I never wait, but just because you can doesn't make it a smart move, I'll always recommend an LTS version 20.04 22.04 
23.10 is a point release 9 month support.

I'll take no responsibility if your system crash's and burns: (Back Up's Back Up's Back Up's)
**[COLOR="#FF0000"]WARNING***[/COLOR]** I should have never posted the below code, meant for
Experienced Linux users, I'm a tester so I know the stakes involved.
```
sudo sed -i s/lunar/mantic/g /etc/apt/sources.list
```
***Warning use at your own peril.***
```
 Host: lvm-linux Kernel: 6.5.0-9-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Xfce 4.18.1 tk: Gtk 3.24.36 info: xfce4-panel wm: xfwm4 
  dm: LightDM 1.30.0 Distro: Linux Lite 6.6 LTS 
  base: Ubuntu 23.10 (Mantic Minotaur) 

```

---

### Post by Dennis N on 2023-10-12
> **tuesdaybarrett said:**
> i installed the beta version. It seem to work but  how can i change to full version and when can i do it
.
You installed the Ubuntu 23.10 beta release? In that case, by doing all the regular updates, you will have the final release version. Nothing more to do.

Note: The command I showed was done on 23.04. I assumed that is what you had.

---

### Post by guiverc on 2023-10-12
*This will mostly be repeated information from prior posts (with meta links)*.

Currently Ubuntu 23.10 is released as an ISO for new installs.

The *Ubuntu Release team* will decide when they deem it suitable for existing users of older releases (especially 23.04) to upgrade, and when they deem it suitable they'll make it suitable for upgrades. I've seen 4+ emails hit my inbox due to work being performed on that process in the last ~two hours.

If you attempt a *release-upgrade*, the following file is accessed, which if you open you'll note has no mention yet of Ubuntu 23.10 (*just view the bottom of the file*).

- [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release)

As 23.10 isn't in that file; no upgrade is seen by existing users.

You can *force* an upgrade early using the `-d` option (*development*) as using that will cause this file ([https://changelogs.ubuntu.com/meta-release-development](https://changelogs.ubuntu.com/meta-release-development)) to be used instead thus it'll be seen.

I would expect these two files to amended early next week, but it'll be done when the *Ubuntu Release team* have deemed it appropriate.

---

### Post by #&amp;thj^% on 2023-10-12
> **Dennis N said:**
> 
Note: The command I showed was done on 23.04. I assumed that is what you had.
Mark me as the same, The Topic of the Thread Reads 23.04 to 23.10

---

### Post by MAFoElffen on 2023-10-12
Well... Wait until the week after it is released. It releases on October 20th.

My littlest brother used to be mid-management at Microsoft, who used to say "a release comes with included bugs at no extra charge."

There is currently a problem with a filed bug report on the 'sources.list' and the format of files in /etc/apt/sources.list.d/. I am affected by that bug. I also cannot update the 'system-info' script for Mantic until all that sorts out, is STABLE, and the changes are static.

I my experience with testing for the DEV Cycles, is that usually 2 weeks before the release, they freeze the repos for that release, to put the real final versions of the packages into place.Then when the Release ISO comes out, there are changes in how the final product "really is". Why, because the DEV dailys have things they want us to test, so is not stable code. 

After the release, if you have it installed already, all you will have to do is to apply updates. It will go from beta, to the release version.

---

### Post by tuesdaybarrett on 2023-10-13
when it is released next week then to to upgrade to fully to ubuntu 23.10 is this the command from terminal
sudo apt-get full ugrade

---

### Post by ian-weisser on 2023-10-13
From 23.10 beta to 23.10 released:

```

sudo apt update
sudo apt upgrade

```

This is what @DennisN and @MAFoElffen meant by "apply updates" and "normal updates" earlier in this thread.

---

### Post by MAFoElffen on 2023-10-13
Thank you all for your patience.

I, myself, have to remind myself that this is the "New To Ubuntu" Section. Translations may be needed for the "Target Audience".

---

### Post by tuesdaybarrett on 2023-10-13
[SIZE=5][FONT=comic sans ms]I saw this [/FONT][/SIZE][COLOR=#000000][FONT=&quot]to update from beta to full version[/FONT][/COLOR][SIZE=2][FONT=comic sans ms]sudo apt update && sudo apt full-upgrade
 then this update-manager -d[/FONT][/SIZE]

---

### Post by MAFoElffen on 2023-10-13
> **tuesdaybarrett said:**
> [SIZE=5][FONT=comic sans ms]I saw this [/FONT][/SIZE][COLOR=#000000][FONT=&amp]to update from beta to full version[/FONT][/COLOR][SIZE=2][FONT=comic sans ms]sudo apt update && sudo apt full-upgrade
 then this update-manager -d[/FONT][/SIZE]
But NOT until "*it is available.*" It is not released (yet) until October 20th, 2023. Today is only October 13th, 2023.

I really do not know how many different ways we can explain the same thing.

Yes. That will work, when it is released and available. You have at least 7 days before that can happen.

Please do not be impatient with us. We are only the messengers, relaying the facts.

---

### Post by #&amp;thj^% on 2023-10-13
> **MAFoElffen said:**
> 
I really do not know how many different ways we can explain the same thing.
Please do not be impatient with us. We are only the messengers, relaying the facts.
+infinity ;)

---

### Post by MAFoElffen on 2023-10-13
@1fallen, check your PM's please.

---

### Post by #&amp;thj^% on 2023-10-13
> **MAFoElffen said:**
> @1fallen, check your PM's please.
i did and now tag your it...

---

### Post by guiverc on 2023-10-13
Ubuntu 23.10 was scheduled for release on 12 October 2023

[https://discourse.ubuntu.com/t/mantic-minotaur-release-schedule/34989](https://discourse.ubuntu.com/t/mantic-minotaur-release-schedule/34989)

The Ubuntu release team announced (on IRC) in their usual way that "it's out" after mirror sync etc. had occurred.. and announced to team members they could subsequently release as well.

A few hours later a problem was detected in a translation viewing to some users using a specific language in a region of the globe, and those ISOs using that translation were pulled offline. The status of that can be read here

[https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365](https://discourse.ubuntu.com/t/announcement-ubuntu-desktop-23-10-release-image-is-being-updated-to-resolve-a-malicious-translation-incident/39365)

Officially the Ubuntu 23.10 release is still *in progress* as per the tracker

[https://discourse.ubuntu.com/t/mantic-minotaur-23-10-release-status-tracking/37887](https://discourse.ubuntu.com/t/mantic-minotaur-23-10-release-status-tracking/37887)

with new images built & CI tested, before available for proper testing early next week. When they're confirmed as both *good *and *safe* (*of hate speech*) the Ubuntu 23.10 release will continue (*currently it's still in progress*).

@MAFoElffen do you have anywhere you can link me that says 20 October 2023, as I've been given no specific date by anyone from the Ubuntu Release team, and all sources I've read still say 12 October 2023 with release still *in progress*.

Ubuntu 23.10 is a released system as I see it (*alas **release in progress **still*). Normally I'd expect the *release-upgrade* 'taps' decision to be made early next week, I suspect it'll be rescheduled for later given the release hasn't officially yet completed.[URL="https://ubuntuforums.org/member.php?u=1044547"][B][COLOR=#DD4814][B]
[/B][/COLOR][/B][/URL]

---

### Post by MAFoElffen on 2023-10-13
@guiverc--

PM'ed you.

---

### Post by sayantan-ling on 2023-10-25
Upgrade path is still not open it seems. My 23.04 release is still not detecting any new versions.

---

### Post by montessori on 2023-10-26
Nobody can help us ?

---

### Post by guiverc on 2023-10-26
Nothing really has changed.

Status is as I outlined in my first comment, in particular 

- [https://discourse.ubuntu.com/t/mantic-minotaur-release-schedule/34989](https://discourse.ubuntu.com/t/mantic-minotaur-release-schedule/34989)

In my first reply; I mentioned the issues with release, required respin (*turned out being a few*) of new 22.10.1 ISOs for Ubuntu Desktop & Ubuntu Budgie; those were tested & have now been [ released]("https://fridge.ubuntu.com/2023/10/16/ubuntu-23-10-mantic-minotaur-released/") (*for new installs*).

The upgrade instructions for existing users have **not** changed, with the upgrade cycle still not open for those that want maximum stability, with some issues reported by those who *forced* it  etc. These issues are explored and work performed on the upgrades. If you'd like to *force upgrade*, the upgrade instructions provided were [https://help.ubuntu.com/community/ManticUpgrades](https://help.ubuntu.com/community/ManticUpgrades) which I mentioned before were found in announcements of Ubuntu 23.10.

As official upgrades are not yet open, the meta files haven't changed, ie. [https://changelogs.ubuntu.com/meta-release](https://changelogs.ubuntu.com/meta-release) is the same. That will change when the *Ubuntu Release Team* decide it's most *stable* for existing users, which is usually early in the week, so maybe next week; you can safely assume if it's not yet open, they have reasons for not opening it (esp. *early in the week*)

---


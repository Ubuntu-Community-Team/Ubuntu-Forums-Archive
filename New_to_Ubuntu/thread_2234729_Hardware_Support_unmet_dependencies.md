---
title: "Hardware Support unmet dependencies"
date: 2014-07-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-07-16
This OS is 12.04 LTS. I'm waiting for 14.04.1 LTS in a week.

On screen message after running Update Manager:

The following packages have unmet dependencies:

libgl1-mesa-glx-lts-trusty: Depends: libglapi-mesa-lts-trusty (= 10.1.3-0ubuntu0.1~precise1) but 10.1.3-0ubuntu0.1~precise1 is to be installed
                            Depends: libx11-6 (>= 2:1.4.99.1) but 2:1.4.99.1-0ubuntu2.2 is to be installed
                            Depends: libxdamage1 (>= 1:1.1) but 1:1.1.3-2build1 is to be installed
xserver-xorg-lts-trusty: Depends: xserver-xorg-core-lts-trusty (>= 2:1.11) but 2:1.15.1-0ubuntu2~precise1 is to be installed

I ran sudo apt-get install -f but that's not the way.

---

### Post by bapoumba on 2014-07-16
Would you happen to have the -proposed repos enabled ?

---

### Post by Mark_in_Hollywood on 2014-07-17
Not to my knowledge (memory) do I have other than stock or default OS, whether repos, or all other. I don't tinker with the workings. How would I check for "-proposed" repos?

---

### Post by kansasnoob on 2014-07-17
> **bapoumba said:**
> Would you happen to have the -proposed repos enabled ?

This hit the standard repos on the US archives this AM so it's no longer just a proposed problem :(

Of course it may have hit other mirrors much sooner, I found a few bug reports:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1328264)

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320)

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341324](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341324)

I personally think the smartest and safest thing to do is wait a few days for the devs to straighten things out, but that's just my *thimking* on the matter ;)

---

### Post by bapoumba on 2014-07-17
Thanks much kansasnoob for the follow up.

@Mark_in_Hollywood : you can have a look from Software Sources, but I guess my question is not the correct one any longer :)

---

### Post by Mark_in_Hollywood on 2014-07-17
I believe the dependencies are related to the video, as xorg.org etc. are mentioned. I'm an end user so I am guessing here, but *macht nix*.

I'm marking this as Solved but from a formal position it isn't. Here is why I'm marking as Solved:

I have both Wine and the Blizzard PC video game "Diablo II" installed. When I play the game, when the character is in the "sanctuary" or "at home" the screen erratically switches on/off every few seconds. The sound is garbage, too. Oddly if the character is in the field, there  is no video problem. Sound is still garbage.

But this isn't significant enough to take more of your time from people with more serious problems.

Thank you, Linux Community.

---

### Post by bapoumba on 2014-07-17
Well, have you tried to post in Gaming or in Hardware about that ?
Significant or not, you may get help with that. All it takes it to ask :)

---


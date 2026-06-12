---
title: "HOWTO: Switch to Banshee community PPA on 11.04"
date: 2011-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by adempewolff on 2011-06-04
I wasn't able to find any instructions for this process via googling, so I made a howto.

Banshee is the default music player in 11.04.  However, some users might want to use the version in the Banshee community PPA.  This version is both newer and has the original affiliate code for the amazon MP3 extension.  The original affiliate code donates 100% of revenues to the GNOME foundation (the modified version included in 11.04 sends 25% of revenues to the GNOME foundation and 75% to Canonical).

This howto does not seek to make any normative judgements over which revenue distribution is better.  Both Canonical and the GNOME foundation have made significant contributions to the open-source community.  I have made this howto simply because I believe one of the fundamental values of the open-source community is allowing users to make choices about the software they use; and, as such, I think users should be able to easily access instructions on how they can choose which version of Banshee they use.

Please do not use this thread to voice your opinion about the legality/morality/evilness of this whole row over revenue sharing between Canonical and the Banshee team.  There are plenty of other forums on the internet where you can do so.  (Moderators, please delete any posts that violate this request)

[SIZE="4"]How to switch to the Banshee community PPA[/SIZE]

Open a terminal and run the following commands:

```
sudo add-apt-repository ppa:banshee-team/ppa
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

And you are set.  Hope this makes instructions for this modification easier to find for interested users!

---


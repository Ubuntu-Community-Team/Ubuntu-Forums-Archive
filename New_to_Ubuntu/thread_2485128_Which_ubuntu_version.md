---
title: "Which ubuntu version"
date: 2023-03-20
forum: New to Ubuntu
---

### Post by skywalker007 on 2023-03-20
I am new to ubuntu and installed it only about 7 days ago. I installed 22.10 but still see most people use 22.04 now that I am on these page. Is there any significant difference between the two that would make people prefer 22.04 ?

---

### Post by Frogs Hair on 2023-03-20
22.04 is long term support release (LTS) supported for 5 years with exception of the [flavors]("https://ubuntu.com/desktop/flavours") which are supported for three years. These are stable releases while the interim releases are supported for only 6 months and will include newer packages being developed for the next LTS release. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by guiverc on 2023-03-20
Ubuntu 22.04 LTS is a *long term support* release, thus will receive security fixes, patches or updates for *five* years from it's initial release in 2022-April  (*life can also be extended via Ubuntu Pro or ESM*).

The two year *development* cycle on the next LTS started just after release; that *two year* development cycle includes 3 non-LTS releases; the first of which was Ubuntu 22.10, the next is due out next month being Ubuntu 23.04, and the final non-LTS is scheduled 7 months into the future (*one comes out every six months*), before the two year *development cycle* completes with the next LTS release of Ubuntu 24.04 LTS (2024-April release).

Your Ubuntu 22.10 has newer software than Ubuntu 22.04 LTS, however the big difference is the support life, as you'll need to *release-upgrade* to the next release (Ubuntu 23.04) within 4 months, as the non-LTS requires *release-upgrades* every 6-9 months...   The advantage of this is you'll always have the *recent* software, but its a regular upgrade cycle compared to a LTS release which is 2-5 years (*rather than 6-9 months*).

Ubuntu LTS releases have two kernel stack choices (the GA kernel, or HWE), the GA kernel stack is the 5.15 (for 22.04) that it originally released with & is seen as the more *stable* choice (*default for server installs* *& some flavor media*), or the HWE kernel stack which currently is 5.19 (*being the kernel stack from 22.10*), the HWE option usually prized by desktop users with recent hardware. 

More third party software is usually available for LTS releases (*it has more users*), but Ubuntu package all software they can for all releases.

ie.  in my opinion it's LATEST software versus less regular *release-upgrades* (*with slightly more  3rd party software options*).

Both are considered *STABLE*, but fewer chances are taken with a LTS release (ie.* 22.04 was actually rather like Ubuntu 21.10 if you look; few risks are taken at the end of the two year development cycle*).

---

### Post by skywalker007 on 2023-03-20
So... before I install too much applications ect, is it then better to install 22.04 ??
I would rather get one I can rely on and feel that I will even change now, just to be sure.Specifically for someone who is "just starting". 
As far as I understand from your reply 22.04 would be better if you are "just beginning".

---

### Post by BBQdave on 2023-03-20
> **skywalker007 said:**
> As far as I understand from your reply 22.04 would be better if you are "just beginning"

I would recommend 22.04 :)
Stable and longer support. And as mentioned, lots of applications available.

---

### Post by guiverc on 2023-03-20
I'll comment, but it'll be my thoughts & no answer.

If your purpose is to learn the OS, I'll suggest staying on 22.10 as we're approaching the release of Ubuntu 23.04's release, meaning your first *release-upgrade* can take place in a little over a month.  You'll learn a lot the OS during that upgrade; plus I'm of the opinion that *release-upgrades* from one release to the next are *easier* than the *release-upgrade *of one LTS to the next LTS (*which skips three release-upgrades*). Two reasons for this easier *release-upgrade* are 

(1) there is less change; only six months of development changes contrasted to two years of change with a LTS to next-LTS upgrade, and
(2) it's easier for us humans to remember what changes we made to our system (*the more tweaks, additional third party packages etc. we make/do, the more problems we can encounter during the release-upgrade*) over six-nine months, than trying to remember what changes we made in the prior 2-5 years...

If you want to restart on Ubuntu 22.04 LTS, I'd use it as a *learning* opportunity anyway; ie. make some  changes etc, add some packages etc, then try a non-destructive re-install of the 22.04 release & see if you can successfully change your release with *almost* no consequence!  We all learn & make mistakes, and need to re-install our system (*either because it's fast & easy & don't have the time for manually fix our mistake(s) manually, as re-install is just so quick/easy and we all make mistakes*), so Ubuntu Desktop systems allow a non-destructive re-install, and we can actually use that switch our release as well (*is better going to a later release than earlier as we're talking about here; and I'd normally suggest doing a load of homework to ensure you don't lose data that's valuable to you, but I gather you've a new system with minimal-data that can be lost; so use that to your advantage & learn how to re-install Ubuntu Desktop non-destructively being my suggestion; only you're using the earlier release instead of your existing release*).   This re-install is easier for *flavors* (*as they have 'universe' enabled by default; it needs to be manually enabled on Ubuntu Desktop/Server*), but I'd still use the chance to learn.

Of course; if you have data that's valuable to you, OR your system is dual boot; backup all data FIRST !  It's easy to make a mistake & erase everything during an install.

FYI:  The non-destructive install is triggered by re-using your existing partitions WITHOUT FORMAT!  (*we use it in Quality Assurance of Lubuntu; and I write about it [here]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") where it's the 'Upgrade using existing partition' testcase; but it works with ~all Ubuntu desktop systems)*

---


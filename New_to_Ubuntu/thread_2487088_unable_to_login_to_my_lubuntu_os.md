---
title: "unable to login to my lubuntu os"
date: 2023-05-22
forum: New to Ubuntu
---

### Post by mohitpain on 2023-05-22
i just installed lubuntu on my system which took nearly 3 hrs to install..i don't know why..
.
but after install and restart im not able to login
.
it is saying this:- 
[ 0.159689] x86/cpu: VMX (outside TXT) disabled by BIOS

You are in emergency mode. After logging in, type "journalct1 -xb" to view

system logs, "systemctl reboot" to reboot, "systemctl default" or "exit"

to boot into default mode.
.
.
when i reboot again i see this problem...
please help me I'm new to Linux

---

### Post by MAFoElffen on 2023-05-22
That message of "that" is a BIOS status message informing you that Virtual Machine Extensions (VMX) are disabled in your BIOS settings, and should probably be enabled...

But that will not prevent a system from booting Lubuntu nor any other flavor of Ubuntu.

Does your system not boot?

---

### Post by ne29914 on 2023-05-22
The BIOS message is totally harmless, I get it on every boot.
But 3 hrs. install time? Really?.
A full DVD install takes around 35 min., a USB install 15 min.
Which version of Lubuntu?

---

### Post by MAFoElffen on 2023-05-22
> **ne29914 said:**
> A full DVD install takes around 35 min.
There is a Launchpad Bug Report noting that current supported versions of (U)buntu flavors are built for USB and not optical formats, so there most likely will be a timeout error during the install process if installed from optical formats. Especially since that version, the first stage reads and verifies all the files on the image. It was also confirmed from members on this forum, that if you use the work-around to circumvent the timeout, that it sometimes took over 3 hours to install from a DVD. So that is not new nor unheard of.
RE: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1930880](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1930880)

What would be helpful here would for you to upload your installer log file from /etc/log/installer/syslog to pastebin.ubuntu.com for us to see what happened... That shows what happened , when in the installation process. That is the facts. Otherwise it would be just guesses and people's opinions. I go off the facts.

Another point would be to post the output of this within CODE Tags:
```

grep . /etc/log/installer/media-info

```
So we know what version of what media was used for the installation.

---

### Post by ne29914 on 2023-05-22
> **MAFoElffen said:**
> There is a Launchpad Bug Report noting that current supported versions of (U)buntu flavors are built for USB and not optical formats, so there most likely will be a timeout error during the install process if installed from optical formats.
As a Lubuntu user, I can say that the mentioned bug report is incorrect.
It may the true for other flavors, but for Lubuntu it's exactly the opposite.

The latest version I can install from USB is 20.04.1 LTS. After that (20.04.x up to 22.04.2), only DVD works. And it works perfectly.

---

### Post by MAFoElffen on 2023-05-22
> **ne29914 said:**
> As a Lubuntu user, I can say that the mentioned bug report is incorrect.
It may the true for other flavors, but for Lubuntu it's exactly the opposite.

The latest version I can install from USB is 20.04.1 LTS. After that  (20.04.x up to 22.04.2), only DVD works. And it works perfectly.
I PM'ed someone I know that is on the Lubuntu Team and does the QA for Ubuntu... I have tested some Dev Cycle Daily ISO's for him. He is *the person* who made 'me' aware of that Bug, and the methodology change for the installers. 

He is someone that should be made aware of this, if what you say is really true (to you)... I feel 'he' is the person who could authoritatively answer this for you... (As it relates to Lubuntu.)

I really feel that he is the authority and last word on things Lubuntu related. Hopefully he will see my PM and join in soon.

---

### Post by guiverc on 2023-05-23
> **ne29914 said:**
> As a Lubuntu user, I can say that the mentioned bug report is incorrect.
It may the true for other flavors, but for Lubuntu it's exactly the opposite.

I too am a Lubuntu user, and whilst I've *not* tick myself as *affected* by that [bug ]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1930880")that @MAFoElffen mentions, I know many Lubuntu users have complained about it.. and I've had DVD installs of 22.04 take longer than 60 minutes myself. We at Lubuntu tracked(##) the bug using a different bug ID (*that is likely the same cause; just results in different messages due to our using different packages & snapd being what we'd tend to see ourselves* *most*).

How long an install takes varies very much on hardware; I used some old 2005-2007 hardware for my DVD installs thus they took longer than what [Leó]("https://launchpad.net/~leok") used using [newer hardware]("https://discourse.lubuntu.me/t/bug-failed-snap-daemon-in-lubuntu-22-04-lts-no-firefox-help-please/3246/31"). I also had boxes that took >10 minutes to boot to the *plymouth* screen too due to a [different bug]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342") (*the bug is in the device firmware thus isn't a Ubuntu issue really anyway; Ubuntu ISOs just trigger it*) so install time can vary.

On a borrowed box I used for some QA tests though installs took well less than one minute (*not including boot time, as I time boots separately to installs; the install starting at final summary screen** of installer*), but hardware varies significantly.

Most of Lubuntu is identical to other Ubuntu products of the same release, as the differences are just we're installing different packages and using a different installer; but outside of that most of the install is done with common Ubuntu scripts (*identical to all*).  Clarification: we don't install 'packages' as I described, but a system is decompressed that achieves the same result.

##  Sorry I'd like to provide the link to the bug we tracked, alas it was long ago & on our issue tracker back then I deleted lines once addressed, instead of using <s></s> to have them show with strikeout.. I didn't find the bug report I was referring to, and will send this now (*incomplete*)

As for the original POST & Question from @Mohitpain

You've not provided release details (and for some like 22.04 I'd also want the *point* details as the version of `calamares` varies on *point* release too).. nor what media you installed from.

If it was DVD the slow speed in my opinion will meaning nothing... 

HOWEVER if you were install from *flash* media where faster is expected, I'd ignore the installer system & install again & if you have problems again (*which I'd expect*) I'd look at why; ie. you may have hardware issues (*ie. explore `dmesg` etc & check for squashfs **errors or problems with your install media; if there are you don't want to use the install - but release details are a starting point here & I don't know what you were using.. also if you have errors relating to the disk being installed to; again don't trust the install & instead move to SMART & explore hardware health etc... ie. I'd step back & look again at install process  and consider details in relation to your unstated media & release details we weren't provided*).

---

### Post by ne29914 on 2023-05-23
Just to be precise: the newer Lubuntu versions won't even boot to a live system from USB, The latest version that works is 20.04.1 LTS.
I'm sitting here with a pile of USB sticks and a stack of DVDs:
20.04.1, 20.04.2, 20.04.4, 20.04.5, 22.04.2
I can boot and install from _all_ DVDs. Also from the 20.04.1 USB.
All other USBs hang after pressing enter at the "Start Lubuntu" screen. After an hour per stick I gave up (the 20.04.1 proceeds to file check after 30...40 seconds).

My advice to @mohitpain: burn a DVD. It always works.

---


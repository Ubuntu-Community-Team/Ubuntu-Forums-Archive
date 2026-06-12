---
title: "Trouble after rejecting upgrade to 12.04"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by ask_ on 2012-04-27
Hello ,
I am using Lubuntu 11.10 on my system. As usual I started update manager today. It gave a notification of upgrading to 12.04.
At first I accepted. It then made some changes to repositories, I think.It also flashed the message that some 3-rd party software might be disabled.

 Then after a few minutes , I got the message that the download is 1 GB and will take 10 hours for installation.
Since I don't have that kind of data connection I rejected.:sad: Then the installation was cancelled and it rolled back the changes it had made to the system in past few minutes. But 2 problems have arisen after this :-
1) I am unable to use flash on chromium. I.e youtube videos don't load in chromium. It gives plug in missing error. I checked synaptic pachkage manager and found that flash-plugin was present. But in Chromium plugins list it is absent.
2) Update manager is taking forever to check if there are any updates for Ubuntu 11.10. Earlier it would take 2-5 seconds now it takes 10 minutes just to check with the software sources if there are any updates pending.


How to rectify these two problems without upgrading to 12.04 (I intend to do it in the future but not as of now.)

Thanks . :) :sad:

---

### Post by cryptotheslow on 2012-04-27
Hi,

1) Try removing and then reinstalling the flash-plugin package using Synaptic with Chromium closed. It was probably one of the 3rd party softwares disabled by the upgrade process.

2) The repositories are being absolutely hammered at the moment due to the 12.04 release. When I check for updates today it takes minutes reading the sources as opposed to a few seconds usually. It would also be worth checking that your sources list has been correctly reverted to the 11.10 selection.

If you post up the output to the below command here we can check for you if you are unsure:

```
cat /etc/apt/sources.list
```

---

### Post by Cavsfan on 2012-04-27
Don't mean to butt in here but, I never use update manager. A friend on here **ranch hand** calls it Update Mangler.

I always use these commands to get my updates:

```
sudo apt-get update 
sudo apt-get upgrade
```Then if it says a kernel or something else is being held back I enter these commands to get that kernel:

```
sudo apt-get update 
sudo apt-get dist-upgrade
```Right now I cannot get an update from Firefox version 12. So I just wait until I can.

You can even set these up as scripts by entering this:

**gksu gedit /home/(your login name)/.bashrc**
e.g. **gksu gedit /home/cavsfan/.bashrc**

and placing these 3 lines towards the bottom of that file where you see aliases.

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```Then you just have to enter "ud" in terminal to get updates and "ud2" if anything is held back.
You will have to logout and back in for these to take effect.

---

### Post by Cavsfan on 2012-04-27
**cryptotheslow** has a good idea to look at your sources though.

I am just providing a way to get future updates more visually.

---

### Post by ask_ on 2012-04-28
> **cryptotheslow said:**
> Hi,

1) Try removing and then reinstalling the flash-plugin package using Synaptic with Chromium closed. It was probably one of the 3rd party softwares disabled by the upgrade process.


Thanks. I did as you told and it is now working.


> **cryptotheslow said:**
> Hi,

If you post up the output to the below command here we can check for you if you are unsure:

```
cat /etc/apt/sources.list
```
```
# deb cdrom:[Lubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu oneiric partner
# deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

```


> **Cavsfan said:**
> Don't mean to butt in here but, I never use update manager. A friend on here **ranch hand** calls it Update Mangler.

I always use these commands to get my updates:

```
sudo apt-get update 
sudo apt-get upgrade
```Then if it says a kernel or something else is being held back I enter these commands to get that kernel:

```
sudo apt-get update 
sudo apt-get dist-upgrade
```Right now I cannot get an update from Firefox version 12. So I just wait until I can.

You can even set these up as scripts by entering this:

**gksu gedit /home/(your login name)/.bashrc**
e.g. **gksu gedit /home/cavsfan/.bashrc**

and placing these 3 lines towards the bottom of that file where you see aliases.

```
# update aliases
alias ud='sudo apt-get update && sudo apt-get upgrade && sudo apt-get clean'
alias ud2='sudo apt-get dist-upgrade'
```Then you just have to enter "ud" in terminal to get updates and "ud2" if anything is held back.
You will have to logout and back in for these to take effect.

Thanks I will remember these tips in the future.


Thanks everyone in this thread for helping me out.
:guitar:

---

### Post by cryptotheslow on 2012-04-28
Your sources file looks fine (no precise sources in there) so I can only attribute the slow updates to the massive load on the repositories right now.

Depending on your patience and desire to must have the latest / greatest I proffer options:

1. Wait a week or so and attempt the upgrade to the new release.
2. Download the latest release using bitorrent and burn it to a CD or DVD then use that as a source to upgrade from. Bitorrent links are available here: [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads) 
3. Ignore it and upgrade at some point in the future - maybe once we get to the first point release 12.04.1 in July. If everything works now, there is no rush to upgrade.

The choice is yours.

Glad you got your flash thing sorted :guitar:

---

### Post by ask_ on 2012-04-28
> **cryptotheslow said:**
> Your sources file looks fine (no precise sources in there) so I can only attribute the slow updates to the massive load on the repositories right now.



The updates are much faster today as compared to yesterday. The time has come down from 10 minutes to 2 minutes. So, all is well. I will upgrade it to 12.04 2-3 months later. :)

---


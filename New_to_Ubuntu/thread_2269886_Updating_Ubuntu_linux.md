---
title: "Updating Ubuntu linux"
date: 2015-03-18
forum: New to Ubuntu
---

### Post by justin45 on 2015-03-18
I have a dell inspiron 1720 laptop and I installed Ubuntu Linux 14.04 64 bit. During the installation process, I checked the option for
install this third party software
and I connected to my wireless router during the install.

Being new to Ubuntu Linux, the desktop boots up and I get a message saying that updates are available. The size is like 348MB. I'd like some update 101.
1) When updates are found for Linux, is there any chance that things can go wrong like getting a black screen during the install process?

Is there anything important that I should know for updating Linux in general?

---

### Post by buzzingrobot on 2015-03-18
> **justin45 said:**
> I have a dell inspiron 1720 laptop and I installed Ubuntu Linux 14.04 64 bit. During the installation process, I checked the option for
install this third party software
and I connected to my wireless router during the install.

Being new to Ubuntu Linux, the desktop boots up and I get a message saying that updates are available. The size is like 348MB. I'd like some update 101.
1) When updates are found for Linux, is there any chance that things can go wrong like getting a black screen during the install process?

Is there anything important that I should know for updating Linux in general?

That's not an unsual amount of updates for a release that's been out for some time.  The install images are not updated/remade after release.

Installing updates as they are available ensures your system receives security fixes, as well as bug fixes, etc. The chances of updates producing a Wndows-esque crash are much smaller than on that platform. 

You can reduce those odds even more by avoiding the installation of software from non-official sources. By default, your Ubuntu system is configured to allow you to find (and update) software in the official Ubuntu repositories.  When you add software from other, nonofficial and unsupported sources (you'll hear about PPA's) you increase the risk of introducing software components that are incompatible with software from the official sources, either at that time or later, after an update.

Software from nonofficial sources, including PPA's, can be very useful, but it's smart to avoid jumping in like a little kid in a candy store, at least until you've picked up a bit of experience.

---

### Post by Impavidus on 2015-03-18
I once had an update go wrong, giving me a black screen on reboot and making the computer unusable. Only once in 8 years of using Ubuntu, and it was quite easy to solve.

---

### Post by DuckHook on 2015-03-19
As both *buzzingrobot* and *Impavidus* say, problems are very rare. However, if you don't practice good data backup habits, then all bets are off. If you are concerned enough to ask on this forum, then you should do a full backup of all data prior to permitting the upgrade. That way, even in the unlikeliest of events, you will only be inconvenienced and not throwing your computer out the window. Make regular, scheduled backups your new religion and you will never regret it.

---

### Post by mastablasta on 2015-03-19
> **justin45 said:**
> 
1) When updates are found for Linux, is there any chance that things can go wrong like getting a black screen during the install process?

Is there anything important that I should know for updating Linux in general?

you can set only security updates in your update manager. they are safe. other updates include programs and drivers. they can sometimes make a mess. the most known one is if you use proprietary drivers for graphics card and then get a kernel update but the manufacturers drivers do not have this kernel included in their update 8so something like that) you could get a black screen or should I say command line only. 

however this can be resolved relatively easy - by removing the drivers and reinstalling them manually and provide sort of manual patch of kernel. it happened to me only once so far.

another think that can leave you with only CLI is bad updates or some power outage or similar during updates. it can be resolved by clearing cache and restarting the update process. I seriously think Ubuntu should come up with a windows like solution of some restore point or similar just for these cases. since you are using wi-fi connection beware that file can get corrupted in air more often that they do in copper wire. checks are in place ofcourse but still sometimes bad files are transmitted. so if possible might be good to use a wire for updates.

by the way CLI text only webbrowser is Lynx  - in case you get stuck in cli only and need to browse the web for solution. and you might also want to have something like Irssi or WeeChat installed to be able to get to ubuntu IRC channel from CLI and ask for help there.

---

### Post by King of Heart 4711 on 2015-03-19
Personally, I have never had an issue from the *official* repos. Just a "apt-get update ; apt-get dist-upgrade" and my system was updated. HOWEVER if you get like me and install an ungodly amount of PPAs things can go wrong. Now don't get me wrong, as long as those said PPAs are reliable and consistent you'll be fine. But if a PPA drops off the face of the planet never to be seen again (I'm Lookin at YOU Russo79!!), that can cause issues with packages. I ended up in dependency hell with my Desktop's install a number of weeks ago to the point after it's last reboot, X would no longer start. 

So moral of the story. If your new, stick with the official repos until you get your feet wet.

---

### Post by DuckHook on 2015-03-19
> **King of Heart 4711 said:**
> ...if you...install an ungodly amount of PPAs things can go wrong...
So moral of the story. If your new, stick with the official repos until you get your feet wet.I've been using Linux for the better part of two decades and I still lay off the PPAs, but for a different reason: they are big gaping security holes. I have only two non-repo sources attached: VirtualBox from Oracle and the ubuntu-wine PPA, and that's still enough to make me lose sleep at night. I've never liked the idea of counselling anyone to add PPAs. In my view, it's just begging for trouble, but I also understand the easy utility it provides. In security matters, it is generally true that each element of convenience is usually offset by an added exposure. So, a stable system is only one reason to avoid PPAs and it's not the most compelling reason at that.

---

### Post by King of Heart 4711 on 2015-03-21
> **DuckHook said:**
> I've been using Linux for the better part of two decades and I still lay off the PPAs, but for a different reason: they are big gaping security holes. I have only two non-repo sources attached: VirtualBox from Oracle and the ubuntu-wine PPA, and that's still enough to make me lose sleep at night. I've never liked the idea of counselling anyone to add PPAs. In my view, it's just begging for trouble, but I also understand the easy utility it provides. In security matters, it is generally true that each element of convenience is usually offset by an added exposure. So, a stable system is only one reason to avoid PPAs and it's not the most compelling reason at that.

I tottaly agree DarkHook, but I only run LTS releases of ubuntu, thus I have to stay on the old repos. PPAs bring the latest software to my system. If I could stay completey away from PPAs I would. However you are 100% correct about PPAs. If untrusted can be a gaping hole in security because the maintainer can place whatever they want in the PPA, OR if their PPA becomes compromised then bad software can be downloaded.

Basicly PPAs are ok if they come directly from the project. ie. Libreoffice/VirtualBox/ownCloud/etc. Those one offs (Russo) and others that "update" alot of software can be bad. Reason being they could update a package that is being keeped at an old version because another package depends on that package version, and if it updates it will break the dependant package. thus "dependancy hell". So they are not completely bad. Just don't add every PPA you see.... Like I used to do... Lesson Learned ;).

---


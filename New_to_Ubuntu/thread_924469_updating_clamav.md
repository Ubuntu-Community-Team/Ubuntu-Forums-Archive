---
title: "updating clamav"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by pranayama on 2008-09-19
sudo freshclam produces:
> ClamAV update process started at Fri Sep 19 20:13:48 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.94
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
main.inc is up to date (version: 48, sigs: 399264, f-level: 35, builder: sven)
daily.inc is up to date (version: 8287, sigs: 29596, f-level: 35, builder: arnaud)
i.e. I do not have the latest version. Following advice on the clamav wiki, I tried sudo apt-get install clamav, and got:
> Reading package lists... Done
Building dependency tree
Reading state information... Done
clamav is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
i.e. I do have the latest version, which must be wrong. Should I compile and install the latest version from source (not sure quite how) or is there an easier way?

---

### Post by roquefilipe on 2008-09-19
it seems that the clamav version in the repositories is 0.92 but the latest is 0.94 which will be in intrepid. 

[http://packages.ubuntu.com/hardy-updates/clamav](http://packages.ubuntu.com/hardy-updates/clamav)

---

### Post by pranayama on 2008-09-19
OK, but what if I want to use 0.94 before Intrepid comes out? 0.94 must have better protection surely?

---

### Post by terry_gardener on 2008-09-19
you can download the .deb from the intrepid packages link. 

[http://packages.ubuntu.com/intrepid/clamav](http://packages.ubuntu.com/intrepid/clamav)

---

### Post by daveu2008 on 2008-09-20
I have the same issue. I like using the synaptic package manager to update software and would rather stick to that than use a deb package.

I was wondering if/when the repository would get updated?

---

### Post by bhadotia on 2008-09-20
Actually you don't need clamav in ubuntu. But I also have it installed coz I dual boot with windoze.

You are good if you just have the latest signature updates.
Install the clamtk front end to clamav:
```
sudo apt-get install clamtk
```
Configure freshclam:
```
sudo dpkg-reconfigure clamav-freshclam
```
Then launch clamtk as root:
Press alt+f2 and in the run box :
gksu clamtk

In the clamtk window , click the help menu and then update signatures.

Hope that helps.:popcorn:

---

### Post by daveu2008 on 2008-09-20
I have it running and updating thanks (the out of date version). I am a pretty new user (3 days). My question really is to do with updating the system. I got a little arrow saying about updates and I downloaded them the other day. 

Will I get an update for this AV software at some point, how does the update process effect things?

Do the  repositories get updated with latest versions from time to time?

---

### Post by kamitsukai on 2008-09-20
> **daveu2008 said:**
> I have it running and updating thanks (the out of date version). I am a pretty new user (3 days). My question really is to do with updating the system. I got a little arrow saying about updates and I downloaded them the other day. 

Will I get an update for this AV software at some point, how does the update process effect things?

Do the  repositories get updated with latest versions from time to time?

I'm not sure about the av software but ubuntu stringently tests software before putting it into the general updates and major program updates are normally left until the new ubuntu release unless it, in some way compromises the security of ubuntu itself

---

### Post by sherts on 2008-09-25
**Thanks got it working =D>**

---

### Post by BrianV on 2009-04-10
I have added ClamAV using the Add/Remove Applications in Ubuntu 8.10 and am having similar difficulties: Following the suggested procedure, everything seemed to work up to launching clamtk, going to Help, then Update Signatures. This initiates a check, followed by a response "Your virus signatures are up to date", but clicking "Antivirus Information" displays:

Build: ClamAV 0.94.2
Signatures: 0
()
GUI Version: 3.11

Which seems to indicate there are no signatures to check. 

Is this correct?

---

### Post by wubrgamer on 2009-04-10
> **pranayama said:**
> OK, but what if I want to use 0.94 before Intrepid comes out? 0.94 must have better protection surely?


1) Your avatar is one freaky emoticon.

2) I doubt you'll have leaps and bounds of "better protection", I highly suggest just sticking with the ubuntu supported version for the moment.  it's more important that you keep the VIRUS SIGNATURES updated rather than the client software.

---

### Post by BrianV on 2009-04-14
How do you know if signatures are up to date? Please see my earlier query: does a Help > Antivirus Information display of

Build: ClamAV 0.94.2

Signatures: 0
()

GUI Version 3.11

mean there are no signatures loaded?

---

### Post by BrianV on 2009-05-09
I have updated to Ubuntu 8.10 with the latest (Ubuntu) version of ClamAV. The Virus Scanner screen shows:

Antivirus engine   0.95.1
GUI version        4.08
Virus definitions  not found
Last virus scan    09 May 2009
Last infected file Never

When I select Help > Update Signatures a window appears with two options selected: Check for antivirus signature updates, and Check for updates to the graphical interface. I deselect the second one, then click on Check for updates. A message appears "Update failed".

It seems I have never managed to load any virus definitions. I have followed all the suggestions in this thread. Are there any further suggestions to get ClamAV working?

Thanks, Brian

---

### Post by MrWES on 2009-05-09
> **BrianV said:**
> I have updated to Ubuntu 8.10 with the latest (Ubuntu) version of ClamAV. The Virus Scanner screen shows:

Antivirus engine   0.95.1
GUI version        4.08
Virus definitions  not found
Last virus scan    09 May 2009
Last infected file Never

When I select Help > Update Signatures a window appears with two options selected: Check for antivirus signature updates, and Check for updates to the graphical interface. I deselect the second one, then click on Check for updates. A message appears "Update failed".

It seems I have never managed to load any virus definitions. I have followed all the suggestions in this thread. Are there any further suggestions to get ClamAV working?

Thanks, Brian

Did you run:
```
sudo freshclam
```
from the terminal?

Bill

---

### Post by Sir Jasper on 2009-05-09
Hi,

Avast always performs significantly better than Clamav in independent tests but you can use any number of on-demand scanners. 

You could download the DEBIAN version to your desktop and then click it to install. It should then be listed under accessories. The link is:
[http://www.avast.com/eng/download-avast-for-linux-edition.html](http://www.avast.com/eng/download-avast-for-linux-edition.html)

Avast does an on-demand scan much faster than Clamav except for those on dial-up the daily updates are full (not incremental although there MAY be a way around that on the Avast Linux Forum).

Avast does not have a right-click context menu scan as can Clamav.

Avira's Antivir shews a very slight detection improvement over Avast in recent independent tests and it can provide active protection but its installation is (at least to me) complex.

I am almost sure that both Clamav and Avast can also give active protection with the addition of Dazuko.

My regards 

PS Clamav had a new Windows upgrade earlier this month  so look out for a Linux upgrade.

---

### Post by MrWES on 2009-05-09
> **BrianV said:**
> How do you know if signatures are up to date?

```
cat /var/log/clamav/freshclam.log | less
```

You should see something like this:
```
main.cvd is up to date (version: 50, sigs: 500667, f-level: 38, builder: sven)
daily.cld is up to date (version: 9349, sigs: 49144, f-level: 42, builder: mcichosz)

```

By default, freshclam is set to update 24 times a day.

Bill

---

### Post by BrianV on 2009-05-21
Thank you, MrWes.

Now how did you know that, to find the signature status in the log file? Is that published somewhere?

And what does the Virus Scanner Status mean:

Antivirus engine     0.95.1
GUI version           4.08
Virus definitions   None found
Last virus scan    21 May 2009
Last infected file   Never

and Scan

Scanning complet (0 signatures)
Files Scanned: 129   Viruses Found: 0   Ready

???

- still seems to indicate no signatures are being used?

Brian

---

### Post by MrWES on 2009-05-21
> **BrianV said:**
> Thank you, MrWes.

Now how did you know that, to find the signature status in the log file? Is that published somewhere?

And what does the Virus Scanner Status mean:

Antivirus engine     0.95.1
GUI version           4.08
Virus definitions   None found
Last virus scan    21 May 2009
Last infected file   Never

and Scan

Scanning complet (0 signatures)
Files Scanned: 129   Viruses Found: 0   Ready

???

- still seems to indicate no signatures are being used?

Brian

try #clamav on irc.freenode.net

---

### Post by jimmm on 2009-10-12
I am experiencing exactly the same issue, trying to set up a new PC. How did you resolve this?

---


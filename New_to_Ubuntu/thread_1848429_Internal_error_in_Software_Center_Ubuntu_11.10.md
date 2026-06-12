---
title: "Internal error in Software Center Ubuntu 11.10"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by vsr1312 on 2011-09-22
I downloaded Chrome 14, and when i tried to install chrome 14 on Ubuntu 11.10 Beta 1 from Software Center, i got the following error


Internal Error
The file "/home/vaibhav/Downloads/google-chrome-stable_current_i386.deb" could not be opened.

Is there any way to remove this bug and install chrome from software center?

---

### Post by Lisiano on 2011-09-22
I don't know why this happened but to install Chrome you could try this workaround.
Open a Terminal (Ctrl+Alt+T) and paste the following.
```
sudo dpkg -i /home/vaibhav/Downloads/google-chrome-stable_current_i386.deb
```

---

### Post by irv on 2011-09-22
> **vsr1312 said:**
> I downloaded Chrome 14, and when i tried to install chrome 14 on Ubuntu 11.10 Beta 1 from Software Center, i got the following error


Internal Error
The file "/home/vaibhav/Downloads/google-chrome-stable_current_i386.deb" could not be opened.

Is there any way to remove this bug and install chrome from software center?

I would delete the file /home/vaibhav/Downloads/google-chrome-stable_current_i386.deb and then try to download it again. Then try to install it again. There might have been a problem with the download and the file got corrupted. That's a good place to start.

---

### Post by MG&amp;TL on 2011-09-22
Try:

```
sudo apt-get install gdebi
```

then right-click on the chrome .deb and click "open with..." >> gdebi package installer.

Or:

```
cd <chromefolderhere> 
sudo dpkg -i chrome.deb
``` ...hey, lisiano got there first. ;)

Then file a bug on launchpad. :)

Does this help?

---

### Post by LukeMorrison on 2011-09-22
Do you already have Chrome installed on your machine?  If so, it should update automatically through the normal channels (i.e. apt-get update / apt-get upgrade; synaptic, Software Center).  If not, it may be in the repositories and you can install it the same way (apt-get install instead of apt-get update / apt-get upgrade).

---

### Post by MG&amp;TL on 2011-09-22
I don't think chrome is in the repositories.

There's chromium, which is identical, it seems. Just open-source.

Or:

Opera-from their site.
Firefox (repos)
rekonq(repos-I think)
Epiphany(repos-I think)
etc, etc.

---

### Post by LukeMorrison on 2011-09-22
Good call.  I tend to think of Chrome and chromium as one and the same, even though they aren't.

---

### Post by vsr1312 on 2011-09-22
> **irv said:**
> I would delete the file /home/vaibhav/Downloads/google-chrome-stable_current_i386.deb and then try to download it again. Then try to install it again. There might have been a problem with the download and the file got corrupted. That's a good place to start.

I had downloaded the same file twice but still the same problem

---

### Post by vsr1312 on 2011-09-22
Dependencies were broken so i executed command 
sudo apt-get install -f
and then installed it successfully

---

### Post by vsr1312 on 2011-09-22
how do i mark this thread as resolved??

---

### Post by MG&amp;TL on 2011-09-22
Thread tools:at the top.

---

### Post by josephp on 2011-09-24
I got the same problem. I even downloaded the beta and it still didn't work.

---

### Post by ingramproductions on 2011-10-14
Same problem here on a fresh install of 11.10
Any body know if it is only the chrome deb package this is happening on? or is it doing it on all of them?

---

### Post by ingramproductions on 2011-10-14
**Ugghh!** what the heck, this is a clean install...

sudo dpkg -i ./google-chrome-stable_current_i386.deb 
[sudo] password for user: 
Selecting previously deselected package google-chrome-stable.
(Reading database ... 127567 files and directories currently installed.)
Unpacking google-chrome-stable (from .../google-chrome-stable_current_i386.deb) ...
dpkg: dependency problems prevent configuration of google-chrome-stable:
 google-chrome-stable depends on libxss1; however:
  Package libxss1 is not installed.
 google-chrome-stable depends on libcurl3; however:
  Package libcurl3 is not installed.
dpkg: error processing google-chrome-stable (--install):
 dependency problems - leaving unconfigured
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for man-db ...
Errors were encountered while processing:
 google-chrome-stable

---

### Post by ingramproductions on 2011-10-14
Ok, now it works:

```
sudo apt-get -f install
sudo dpkg -i ./google-chrome-stable_current_i386.deb 
```

Couldn't get it to install through the software center though...

---

### Post by Hallic7 on 2011-10-14
> **ingramproductions said:**
> Ok, now it works:

```
sudo apt-get -f install
sudo dpkg -i ./google-chrome-stable_current_i386.deb 
```Couldn't get it to install through the software center though...

This worked for me!! Thanks a lot!!! :D

---

### Post by gigo625913 on 2011-10-15
Thank you!It work for me too.However i needed to type in code:
```
sudo dpkg -i google-chrome-stable_current_amd64.deb
```
without ./ before package name.
P.S. I am a begginer user.

---

### Post by Foxcow on 2011-10-21
Excellent!  This is a pretty annoying issue that will hopefully be squashed soon.

---

### Post by BlessedGeek on 2011-11-12
After downloading the chrome deb ...
First install chromium using software centre.
Then open the downloaded chrome deb using software centre, which will spell success in installing chrome.

There are apparently libs that both chrome and chromium depend on but that the chrome deb would not care to resolve, which are (apparently) resolved by our friendly ubuntu mates when they packaged the chromium deb.

If google chrome works, then uninstall chromium.

---

### Post by stokescj on 2011-12-08
I, am getting the same error. 

When running this command I am then getting a new error which says:

"E: Unable to locate package /home/christopher/downloads"

Before this it did ask for my password and did the following:

"Reading package lists...Done
Reading state information..Done"

Any ideas please?

---

### Post by nothingspecial on 2011-12-08
> **stokescj said:**
> I, am getting the same error. 

When running this command I am then getting a new error which says:

"E: Unable to locate package /home/christopher/downloads"

Before this it did ask for my password and did the following:

"Reading package lists...Done
Reading state information..Done"

Any ideas please?

That could be because the default Downloads folder starts with an upper case D not a lower case d

---

### Post by stokescj on 2011-12-08
Thank you.

I am a bit further now. It seems to install all the dependencies correctly and says the following:

After this operation, 758 kB of additional disk space will be used.
Do you want to continue [Y/n]?

Before it gives me a chance to do anything it then says abort.

I tried typing Y quickily, and it will responded with "abort" after.

Thanks in advance

---

### Post by benmarshall76 on 2012-02-10
If this error is coming up on a new install, then heres what helped me. After trying everything in this forum with no solution I was about to give up and when I went to power down I noticed the option for "Software Update" clicked on that and found I had plenty of things that needed updating. I updated all, and when done it ask to reboot. I rebooted, clicked the Chrome download file and was good to go. All worked correctly. I hope this helps someone new like me who just can't get chrome to install on a new install of Ubuntu.

---


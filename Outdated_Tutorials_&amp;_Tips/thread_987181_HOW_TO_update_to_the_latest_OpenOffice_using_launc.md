---
title: "HOW TO: update to the latest OpenOffice using launchpad repositories"
date: 2008-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by fooman on 2008-11-19
i see the question posted a lot in the forums and have not noticed a tutorial for it yet...so here is my first attempt at one:

we first need to add the repositories to the sources.list file.  so open a terminal and type or copy/paste the following:

```
gksudo gedit /etc/apt/sources.list
```when it opens, add (copy/paste) the following lines to the bottom of the file:

[COLOR=Red]for hardy[/COLOR]:

```
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu hardy main
```[COLOR=Red]for intrepid[/COLOR]:

```
##repo for open office3
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu intrepid main
```[COLOR=Red]for jaunty[/COLOR]:

```
##repo for open office3
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu]("http://ppa.launchpad.net/openoffice-pkgs/ubuntu") jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu]("http://ppa.launchpad.net/openoffice-pkgs/ubuntu") jaunty main
```[I]
save[/I] and then close the file.  

add the PGP key with this command:

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 247D1CFF
```now to upgrade openoffice to the latest version... just need to update the repos and upgrade the packages.  run (type or copy/paste) this command in a terminal:

```
sudo apt-get update && sudo apt-get dist-upgrade
```thats it...open office 3.1.* should be installed and in the menu: applications > office

or just start it up from the terminal:

```
openoffice
```**if you seem to be missing some items and would like the *entire* suite installed....open a terminal and type or copy/paste:
```
 sudo apt-get install openoffice.org
```hope that helps someone. :)

****************************************************************************************************************************

EDIT:  updated 5-13-09 to latest version.  ;)

---

### Post by RedRat on 2008-11-25
Just a question. Is Open Office 3 designed for Intrepid (8.10) or can it be installed also under Hardy (8.04). The reason I ask is that I have several programs from Debian (Pan 133 and Google Gadgets) that don't want to install under my current Hardy installation due to library dependencies (These library dependencies are referenced to libraries that I have installed, at least nominally they share the same names).

---

### Post by crjackson on 2008-11-25
> **RedRat said:**
> Just a question. Is Open Office 3 designed for Intrepid (8.10) or can it be installed also under Hardy (8.04). The reason I ask is that I have several programs from Debian (Pan 133 and Google Gadgets) that don't want to install under my current Hardy installation due to library dependencies (These library dependencies are referenced to libraries that I have installed, at least nominally they share the same names).

I tried adding the repo listed on my hardy install. It showed updates available but wouldn't install them. It wanted to do a partial upgrade, and I confirmed the upgrade, but it still wouldn't complete the install.

It worked fine in Intrepid however.

---

### Post by RequinB4 on 2008-11-25
> **RedRat said:**
> Just a question. Is Open Office 3 designed for Intrepid (8.10) or can it be installed also under Hardy (8.04). The reason I ask is that I have several programs from Debian (Pan 133 and Google Gadgets) that don't want to install under my current Hardy installation due to library dependencies (These library dependencies are referenced to libraries that I have installed, at least nominally they share the same names).

[http://ubuntuforums.org/showthread.php?t=982652](http://ubuntuforums.org/showthread.php?t=982652)

---

### Post by rjuhser on 2008-11-26
I followed all the steps above in fooman's description, but I don't get OpenOffice 3 installed. The response of the upgrade is ...

sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

... but when I start OpenOffice, I still got version 2.4.

Any ideas what might be wrong?

---

### Post by omns on 2008-11-26
> **rjuhser said:**
> 
Any ideas what might be wrong?
The packages seem to have disappeared from launchpad? The repo is now empty

---

### Post by frankleeee on 2008-11-26
> **GrantG said:**
> The packages seem to have disappeared from launchpad? The repo is now empty

In another thread the scoop is that due to bug issues the package was pulled to be worked on and will be back when fixed.

---

### Post by fooman on 2008-11-26
for anyone who updated using this guide and is getting errors when starting openoffice3 (eg..."[COLOR="Red"]Openoffice.org 3.0 Fatal Error - The application cannot be started[/COLOR]"),  this can be resolved by deleting the package "openoffice.org-gnome".  just run the following command:

```
sudo apt-get remove openoffice.org-gnome
```

should be working ok after that.

also...as stated above,  the repos are down atm while the bug is being fixed:

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

sorry,  hopefully it will be fixed soon.

---

### Post by frankleeee on 2008-11-26
> **fooman said:**
> for anyone who updated using this guide and is getting errors when starting openoffice3 (eg..."[COLOR="Red"]Openoffice.org 3.0 Fatal Error - The application cannot be started[/COLOR]"),  this can be resolved by deleting the package "openoffice.org-gnome".  just run the following command:

```
sudo apt-get remove openoffice.org-gnome
```

should be working ok after that.

also...as stated above,  the repos are down atm while the bug is being fixed:

[https://launchpad.net/~openoffice-pkgs/+archive](https://launchpad.net/~openoffice-pkgs/+archive)

sorry,  hopefully it will be fixed soon.

Thanks, the only problem I have had is the systray quickstarter disappearing on a reboot, but since I have to write a final paper for a class I am saving every thing on a thumbdrive in oog and doc just in case I have to rush to the college and use the windows computer. (shudder)

---

### Post by zika on 2008-11-27
Yesterday I've been usin OpenOfifice happily.

Today I've found today that my OpenOffice is missing from menu and that it won't open files anymore. I have upgraded openoffice to 3.0 from the one that came with Ibex (2.*) some time ago via:

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main
sudo apt-get update
sudo apt-get dist-upgrade


i've tried to do sudo apt-get install opennoffice.org but that gave me:
 
when I go through directories the files are there but how to re-activate them. When I click on OOfile (like .odt) openoffice is not mentioned. It all worked yesterday ... :sad:

sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
E: Broken packages

Is there any help?

I've tried just a minute ago to reinstall it using [ftp://ftp.ussg.iu.edu/pub/openoffice...-US_deb.tar.gz]("ftp://ftp.ussg.iu.edu/pub/openoffice/stable/3.0.0/OOo_3.0.0_LinuxX86-64_install_en-US_deb.tar.gz") and everything went well except menus could not be installed. But, the situation is the same, I can not start OpenOffice.

Where are the files that start writer etc?
 		                   		  		  		  		  		 		
I think I know what happened: after update yesterday Cruft Remover suggested to delete uno-libs3 package. So I did. It seems that it is needed for OO3.0.

Any ideas how to undo that operation?

I've done this on two machines, and today when I updated third machine I saw what is going on. I've saved that machine ... ;)

Should I reinstall (before uninstalling all of OO2.* originally from Ibex)?

I probably messed up now by trying to reinstall.

---

### Post by zika on 2008-11-27
when I try openoffice I get:

$ openoffice
/usr/lib/openoffice/program/soffice: 237: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 254: /usr/lib/openoffice/program/soffice.bin: not found

when I try sudo apt-get remove openoffice.org-gnome I get:

$ sudo apt-get remove openoffice.org-gnome
[sudo] password for viktor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package openoffice.org-gnome is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Yeti can't ski on 2008-11-27
But do you have open office installed or not? Can you use trough the terminal? Type "openoffice". Perhaps you simply have a problem of organizing the menu...

Sorry if you have already tried that and the comment is silly...

---

### Post by zika on 2008-11-27
I get:

:~$ openoffice
/usr/lib/openoffice/program/soffice: 237:
/usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 254:
/usr/lib/openoffice/program/soffice.bin: not found

yes I have tried this several times, but, no, no comment is silly, thak You.

---

### Post by moremix on 2008-11-29
I am having the exact same problem as you Zika - did the upgrade a couple days ago and my Openoffice 3.0 just disappeared from my Ubuntu 8.10 menu.  When I try to look at it using Synaptic, the packages are still installed.  When I try to run it from the command line I also get : 
/usr/lib/openoffice/program/soffice: 237: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 254: /usr/lib/openoffice/program/soffice.bin: not found

And I didn't have the openoffice.org-gnome package installed.

Does anyone have a fix or an idea when the repository will be back up?
Why did the menu get wiped as well????

Moremix

---

### Post by MeduZa on 2008-11-30
I updated open office to 3.0 time ago, today I try to open Base to made a work and IS NOT THERE :S
I go directly to synactic and found that there is no base 3.0 there only the 2.x

I'm using the repository posted here. ([http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main)

how to get Base 3.0?

---

### Post by Rotarychainsaw on 2008-11-30
This PPA crapped out for me too. Back to whatever the ibex default is for now. Subscribed.

---

### Post by woyzeckswoe on 2008-12-02
> **moremix said:**
> I am having the exact same problem as you Zika - did the upgrade a couple days ago and my Openoffice 3.0 just disappeared from my Ubuntu 8.10 menu.  When I try to look at it using Synaptic, the packages are still installed.  When I try to run it from the command line I also get : 
/usr/lib/openoffice/program/soffice: 237: /usr/lib/openoffice/program/../basis-link/program/pagein: not found
/usr/lib/openoffice/program/soffice: 254: /usr/lib/openoffice/program/soffice.bin: not found

And I didn't have the openoffice.org-gnome package installed.

Does anyone have a fix or an idea when the repository will be back up?
Why did the menu get wiped as well????

Moremix

Same here, it seems like the server's down someone knows better?

thanks

---

### Post by Skripka on 2008-12-02
> **woyzeckswoe said:**
> Same here, it seems like the server's down someone knows better?
 
thanks
 
 
They have been down for a _***full week***_.

---

### Post by Kow on 2008-12-02
If someone still has the source from the PPA then they could build it... but OO.org takes forever to compile. I'm guessing OO 3.0 was intentionally removed due to a program-stopping bug after the last update they did.

---

### Post by snowpine on 2008-12-02
Be patient... OO3 will be back soon once they release 3.0.1 which fixes some sort of gnome-related bug. 

Or you can download it from openoffice.org.

The worst part is by removing it from the ppa they broke a lot of tutorials posted on these forums and elsewhere. :(

---

### Post by kernelhaxor on 2008-12-04
Thanks for the howto.  Does this get rid of OO 2.4 or would we have both 2.4 and 3.0 side by side?

---

### Post by shaohu.xie on 2008-12-05
I'am using ubuntu 8.10 64bit.
The system language is Simplified Chinese.I can't upgrade OpenOffice to 3.0.

The [OpenOffice.org]("http://download.openoffice.org/other.html#zh") has not support Simplified Chinese version for Linux 64 deb now.

---

### Post by jetsaredim on 2008-12-05
I think there are just no amd64 builds at all, which is disappointing...  Anyone else looking for the amd64 builds and able to find them?

---

### Post by Skripka on 2008-12-06
> **jetsaredim said:**
> I think there are just no amd64 builds at all, which is disappointing...  Anyone else looking for the amd64 builds and able to find them?

They are there on the OOorg website.  I downloaded them and (re)installed them on my system yesterday.

---

### Post by fooman on 2008-12-09
repos are back up again!  \\:D/

version 3.0.0-6

---

### Post by andrewabc on 2008-12-09
> **fooman said:**
> repos are back up again!  \\:D/

version 3.0.0-6

It is asking me to do a partial upgrade. some openoffice 3.0 are selected, others are not.

I don't like partial upgrades, they usually mean trouble.

EDIT:
tried the partial upgrade (listed as distro upgrade!?). It failed saying some were not authenticated. So.. What do I do with calcs PPA? It's not working because of the partial upgrade.

Using ubuntu 8.10 and calcs 3.x PPA.

---

### Post by fire5nake on 2008-12-10
Installed sweet for me now that the repos are back up again.

---

### Post by zika on 2008-12-10
> **andrewabc said:**
> It is asking me to do a partial upgrade. some openoffice 3.0 are selected, others are not.

I don't like partial upgrades, they usually mean trouble.

EDIT:
tried the partial upgrade (listed as distro upgrade!?). It failed saying some were not authenticated. So.. What do I do with calcs PPA? It's not working because of the partial upgrade.

Using ubuntu 8.10 and calcs 3.x PPA.

ditto

I did not embark on partial upgrade, will wait for official update. Maybe something got mangled after breakdown of former installation of 3.0 and several ettempts of installation from OO official site ater breakdown and complete deinstall and reinstallation of Ubuntu official 2.4.

---

### Post by Drew Woodard on 2008-12-14
A note of warning to anyone thinking about using this who also uses NFS shares.
In the past openoffice had several bugs related to file locking on NFS shares, they seem to have been mostly resolved in the last year but this 3.0 release appears to bring some back.

I access my files over an NFS4 share and when opening these files with openoffice3 they would always be stuck in read-only mode.

I tried disabling openoffice file locking completely in /usr/lib/openoffice/program/soffice as indicated [here]("https://bugs.launchpad.net/openoffice/+bug/40537") which was a fix for the old bugs, but the problem persisted.
I also tried disabling locking completely via NFS mounting options but this didn't do anything either, so I went back to openoffice 2 and can now edit files once again.

---

### Post by hohlraum on 2008-12-17
Since everyone is having problems with the partial upgrade and this is the first thread that shows up on google i thought I'd post that the issue is (as someone mentioned above) that there are un-authenticated packages on PPA. 

The fix is to run system / administration / synaptic and do a mark all upgrades and apply.  That'll get you back up and running without the partial upgrade horking everything.

---

### Post by fooman on 2008-12-17
edited the original post and thread title to include the hardy repos.

sorry about the partial upgrade problem people are seeing.  i have now upgraded openoffice on 3 intrepid boxes and 2 hardy boxes with no such trouble....wish i could help,  but i have not seen this yet.

hopefully hohlraum's post above this one will help with that.

---

### Post by andrewabc on 2008-12-17
> **hohlraum said:**
> Since everyone is having problems with the partial upgrade and this is the first thread that shows up on google i thought I'd post that the issue is (as someone mentioned above) that there are un-authenticated packages on PPA. 

The fix is to run system / administration / synaptic and do a mark all upgrades and apply.  That'll get you back up and running without the partial upgrade horking everything.

Thank you that worked.

---

### Post by zika on 2008-12-24
Watch it! Again today, after weeks of empy list, Cruft remover offered to me to erase uno-libs3. That's how the problem described above started. Of course, I refused but beware ... :)

---

### Post by evertmantel on 2008-12-24
Worked like a charm in 8.04.
Thanks!

:-({|=

---

### Post by fastpakr on 2009-01-02
I had OpenOffice3 working fine on my parents 8.04 desktop.  After an in place update to 8.10, OpenOffice appeared to be uninstalled.  Looking at sources.list, the entry was commented out.  After fixing that, I reinstalled openoffice.org from the add/remove GUI.  Now, I have the icons back in the Office group, but get no response when launching.  From gnome-terminal, 'openoffice' hangs like a program has launched, but nothing appears on screen and there are no errors.

Can anybody point me in the right direction to troubleshoot?  Without an error message I'm at a loss.

---

### Post by fooman on 2009-01-02
> **fastpakr said:**
> I had OpenOffice3 working fine on my parents 8.04 desktop.  After an in place update to 8.10, OpenOffice appeared to be uninstalled.  Looking at sources.list, the entry was commented out.  After fixing that, I reinstalled openoffice.org from the add/remove GUI.  Now, I have the icons back in the Office group, but get no response when launching.  From gnome-terminal, 'openoffice' hangs like a program has launched, but nothing appears on screen and there are no errors.

Can anybody point me in the right direction to troubleshoot?  Without an error message I'm at a loss.

the repos are different for hardy (8.04) and intrepid (8.10)...when you fixed the sources.list, did you just *un*comment them?  or did you actually change them to the intrepid repos?

check your sources.list,  if you have upgraded to 8.10...then you should be using the intrepid repository.  open the sources.list file for editing:
```
gksudo gedit /etc/apt/sources.list
```if the openoffice section has the hardy repository listed....like this:
```
##repo for open office3
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]hardy[/COLOR] main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]hardy[/COLOR] main
```then change the 2 [COLOR=Red]hardy[/COLOR] lines...to [COLOR=Red]intrepid[/COLOR], so that it looks like this:
```
##repo for open office3
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]intrepid[/COLOR] main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]intrepid[/COLOR] main
```save and close the file.  run this command:
```
sudo apt-get update && sudo apt-get dist-upgrade
```the packages should upgrade to the intrepid versions.  hope that helps.

---

### Post by fastpakr on 2009-01-02
> **fooman said:**
> the repos are different for hardy (8.04) and intrepid (8.10)...when you fixed the sources.list, did you just *un*comment them?  or did you actually change them to the intrepid repos?

check your sources.list,  if you have upgraded to 8.10...then you should be using the intrepid repository.  open the sources.list file for editing:
```
gksudo gedit /etc/apt/sources.list
```if the openoffice section has the hardy repository listed....like this:
```
##repo for open office3
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]hardy[/COLOR] main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]hardy[/COLOR] main
```then change the 2 [COLOR=Red]hardy[/COLOR] lines...to [COLOR=Red]intrepid[/COLOR], so that it looks like this:
```
##repo for open office3
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]intrepid[/COLOR] main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) [COLOR=Red]intrepid[/COLOR] main
```save and close the file.  run this command:
```
sudo apt-get update && sudo apt-get dist-upgrade
```the packages should upgrade to the intrepid versions.  hope that helps.
I appreciate the suggestions, but they're already set to intrepid's repos.

---

### Post by celem on 2009-01-03
Solved, but I can't be sure why because I did several things at once.

I not only uninstalled OOo but I followed up by deleting the remaining /opt/openoffice.org3 AND I removed the /home/username/.openoffice.org/3/user directory. Then, I installed OOo via a different route. This time I used the method at [http://tinyurl.com/8obowd](http://tinyurl.com/8obowd)

Whichever fixed things, now the Templates dialog box works!
------------------------
I [twice] downloaded the deb from OpenOffice.org installed OpenOffice3 as described in [http://tinyurl.com/4pchvj](http://tinyurl.com/4pchvj)

I thought that all was well but the Templates and Documents dialog box in Writer is broken. 

Whenever I open File->New->Templates and Dialogs the resultant dialog is broken. The dialog pops up but cannot be successfully navigated. Sometimes the dialog is blank, other times it is populated but cannot be navigated. I downloaded a fresh copy from Sun and executed the update within but there was no improvement. I am using OpenOffice 3.0.0 OOO300M9 Build: 9358.

See also my post at the OpenOffice Community forum:
[http://tinyurl.com/8gt7so](http://tinyurl.com/8gt7so)

Is anyone else having this problem or am I all alone?

---

### Post by ithanium on 2009-01-03
Worked like a charm
Thank you! :D

---

### Post by MaddMatt on 2009-01-17
Thanks for the instructions - I had no problems installing on Intrepid 64bit. 

That being said, I'm not convinced OO3 is ready for the prime time. It has crashed on me about 5 times in the last week, which is not OK when working on a work-project. Luckily OO3 has improved recovery, so I haven't lost any data, but still... Some of the kinks need to get worked out. A word of caution.

---

### Post by Foaming Draught on 2009-01-25
Thank you very much, fooman.  Your clear instructions for Intrepid worked fine on Mint 6  :)

---

### Post by bj0 on 2009-02-11
I just tried this, but it didn't work.  The only 3.0 packages it seemed to make available to me were help/language files.  Nothing else upgrades, and I still have 2.4.

when I try a dist-upgrade, it gives me the following:

The following packages are BROKEN:
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-draw openoffice.org-filter-binfilter 
  openoffice.org-impress openoffice.org-math openoffice.org-officebean 
  openoffice.org-report-builder-bin openoffice.org-writer 
  openoffice.org-writer2latex python-uno 
The following packages will be REMOVED:
  openoffice.org-core{a} 
The following packages will be upgraded:
  openoffice.org-help-en-gb openoffice.org-help-en-us 
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
4 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/15.2MB of archives. After unpacking 107MB will be freed.
The following packages have unmet dependencies:
  openoffice.org-writer: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-impress: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-filter-binfilter: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-report-builder-bin: Depends: openoffice.org-core (> 1:2.3.0~oog680m1) but it is not installable
  openoffice.org-writer2latex: Depends: openoffice.org-core (>= 1:2.3.0~oog680m1) but it is not installable
  openoffice.org-math: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-common: Depends: openoffice.org-core (> 1:2.4.1) but it is not installable
  python-uno: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-officebean: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-base: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable
  openoffice.org-calc: Depends: openoffice.org-core (= 1:2.4.1-11ubuntu2.1) but it is not installable



This is on 8.10.

---

### Post by kcee on 2009-05-08
Thanks, fooman.  Don't recall what instructions I followed to upgrade to Oo3 on Intrepid - it ran fine but got the partial upgrade message on Update Manager.  Somehow I had only added deb line but not deb-src.  Added the line and followed the rest - partial upgrade problem solved!

---

### Post by fooman on 2009-05-13
updated today....sorry i have not checked on this in so long.

added jaunty and the PGP key...update should be to version 3.1[COLOR=Red]
[/COLOR]

---

### Post by zika on 2009-05-13
is it me or is it the launchpad but I do get offered only a sort of partial upgrade with all essential packages threatened to be removed and some general to be installed ...

calc, draw, impress, math, writer to be removed...

common, emailmerge, java-common, ttf-opensymbol, uno-libs3, ure to be installed ...

I'll pass ... :)

---

### Post by dgermann on 2009-05-13
Hi--

Running several 8.04 machines in a production environment. I have been using 3.0.1 obtained in the method in this thread.

About two days ago I got the update manager notice that 3.1.0 was ready for installation. I installed, and ended up with two issues (I tried just last night on another machine and still have these issues):

1. Tools > Customize > Keyboard was all blown to bits. For instance, destructive backspace would not backspace; F3 would give no auto text; and all my special key assignments were gone.

(As an aside, I had saved all those key assignments to a file using Tools > Customize > Keyboard > Save; however, using Load on the same page will not load up that file. How do you load these keyboard settings?)

2. There is no Help (F1) at all. It says the help file is not installed. Synaptic says it is installed. I'm presuming it just needs to be told where it is.... (I see the help-en-us file in Synaptic seems to be the 2.4 version, not 3.1.0).

Thanks for whatever help you can give me.

---

### Post by r_mano on 2009-05-20
Hi, 

thanks for the instruction. I have just a problem: since when updated to the new openoffice packages in Intrepid, I have lost the openoffice help... it say to install the package openoffice.org-help- locale (my locale is set to en_GB) but I can't find it. Any help on help :-) ?

---

### Post by Arup on 2009-05-20
copy paste this in terminal and you are all set.

echo -e 'echo "#PPA openoffice-pkgs
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/ppa.list

gpg --keyserver keyserver.ubuntu.com --recv 247d1cff
gpg --export --armor 247d1cff | sudo apt-key add -

sudo apt-get update

sudo aptitude -y safe-upgrade
sudo aptitude -y dist-upgrade
' > ./oooupgrade.sh
sudo sh ./oooupgrade.sh && rm ./oooupgrade.sh

---

### Post by f1r3br4nd on 2009-09-28
This does not work on Hardy. That repository does not appear to have the 3.1.* releases, and so no upgradeable packages show up if you're running Hardy and already have 2.4.*.

---

### Post by Skeletonix on 2009-09-28
The repository doesn't contains packages for Hardy. Anyone know any other repository with OO 3.x ? 

Thank you !

---

### Post by amaroKer on 2009-09-29
I'm having this problem too.  Would love to find another repo of anyone knows...

---

### Post by JanGerrit on 2009-12-07
Hello everybody,

for Ubuntu Hardy 8.04 you can use the BaWü (*1) repository from Itomig, which includes OpenOffice 3 for i386.
Have a look at:
[http://www.itomig.de/index.php?id=109](http://www.itomig.de/index.php?id=109)

Greetings,
Jan Gerrit

(*1) Bawü-Linux is an Ubuntu Hardy based standard desktop system for public administration.

---

### Post by calc on 2009-12-08
OpenOffice.org 1:3.1.1-5ubuntu1 for Hardy is back in the ppa. The test debs for the 3.2 series should be up for Karmic by sometime in January and will be in Lucid at the same time.

---


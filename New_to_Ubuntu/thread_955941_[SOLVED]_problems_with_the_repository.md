---
title: "[SOLVED] problems with the repository"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by plasmarox on 2008-10-22
Hello all
I have had ubuntu for a couple of days now, and have got on well so far, but i have been putting off a slight issue till now

I cannot use update manage to update
When i choose update, it gets to 43/70ish packages, it hangs and gives the following message:



```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  403 Forbidden
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz  403 Forbidden
Some index files failed to download, they have been ignored, or old ones used instead.
```

By the way, i do not have proxy settings specified and i definately have fine connectivity, as i post this now from ubuntu linux.

The main reason why i want to use this as i need to install codecs for rhythmbox so i can play music direct from my ipod or hard disk windows partition [im dual booting ubuntu and XP]

Thanks :P

EDIT:
When i change from UK updates to main server updates and try to update again, it can see about the indivudual packages, and they all seem to say that the cant download because of a   403 Forbidden error.

---

### Post by Pro-reason on 2008-10-22
Hmm, that's strange.  I can only suggest trying another nearby server, such as *fr* or *ie*.

---

### Post by plasmarox on 2008-10-23
hmm, possible - how do i specify what server to check for updates from?

---

### Post by Crandom on 2008-10-23
Go to System > Administration > Software Sources

There should be a drop down menu for servers. I use mirror.ox.ac.uk (Oxford University) and it has never given me any troubles as well as being fast (~2mbytes/s)

---

### Post by plasmarox on 2008-10-23
Hmm, ill try that when i get home (in about seven hours from now)

---

### Post by Kevbert on 2008-10-23
Welcome to Ubuntu. What version of Ubuntu are you using ? Please post your /etc/apt/sources.list file. When you update are you using 
```
sudo apt-get update
sudo apt-get upgrade
```
via Applications-Accessories-Terminal ?

---

### Post by plasmarox on 2008-10-23
Thanks :P
I am using hardy heron, downloaded from the ubuntu mirror only on monday, the version number runs something like 8.0xxx.

When i do upddate, i use system>admin>update manager

from there, i choose reload, or the option for loading the update index

---

### Post by Kevbert on 2008-10-23
It suggests that there may be problems with your software sources.  If you post the file, we may be able to see the error there. Attached is a copy of my sources.list file for Hardy.

---

### Post by plasmarox on 2008-10-23
um...
i couldnt do /etc/apt/sources.list, b/c of permission denied, even with sudo and sudo -i.

So i navigated to /etc/apt/sources.list in file manager and posted that.

Hope that means something to you =D

---

### Post by plasmarox on 2008-10-23
Update:
when i use ```
sudo apt-get update
sudo apt-get upgrade
```, im able to download fine; but i cant use update manager to install them :s

---

### Post by Kevbert on 2008-10-23
Your sources.list looks fine. You can't run /etc/apt/sources.list as it's not a program/script (only a text file). Hence the error when using sudo. If those commands work, you've looked at the sources.list files with the first command and the second one downloads and installs all of the updates. It looks like your update manager program is somehow corrupted. First try running
```
sudo apt-get install -f
```
to try to repair any damaged packages and then run Update Manager again. 
If you still get an error it might be worth trying a re-install via Synaptic Package Manager. Search for update-manager. The two things you want to reinstall are update-manager and update-manager-core. Right click on the green box next to them and select Mark for Reinstallation and then click on Apply.  If this doesn't work I'm not sure what to suggest.

---

### Post by plasmarox on 2008-10-23
hmm
i tried re-installing the update manager via synaptic package manager, but it still does it. Did you see that it always has a 403 forbidden error? do you know if thats like a http 404 error?

---

### Post by Pro-reason on 2008-10-23
The sources.lst file is fine.  The 403 error is coming from perfectly standard Ubuntu repositories that should just work (and which do work for the rest of us).

The first step is to try a couple of other servers and see whether it is possible to fix the problem thus.  Use the “Select best server” button, or manually select a nearby server in the UK, Ireland or France.

---

### Post by plasmarox on 2008-10-23
well, when i go to update manager and click check, it happens.
ive tried a few servers, and i tried best server, but it claimed that a server from thailand was the best for me.

---

### Post by Pro-reason on 2008-10-23
OK, let's see if this problem only occurs with APT, or is more general.

```

wget http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz
zless Packages.gz

```
That should display a long list of information about packages.  (Press “q” to exit.)

Does it work, or does it give you a 403 error?  Paste the output if it fails.

---

### Post by Kevbert on 2008-10-24
A http 404 error is web page not found. A 403 error occurs when you try to go to a private web page which you need special privileges (for example a login password and you've tried to access it without the password).
How are you accessing the web ? via a corporate lan/college/university ? If so you may need to speak to the system administrator in order to get additional user privileges.

---

### Post by plasmarox on 2008-10-24
hmm, that worked fine. Is that related to using ```
sudo apt-get update

sudo apt-get upgrade
```, which also worked fine.

---

### Post by plasmarox on 2008-10-24
> **Kevbert said:**
> A http 404 error is web page not found. A 403 error occurs when you try to go to a private web page which you need special privileges (for example a login password and you've tried to access it without the password).
How are you accessing the web ? via a corporate lan/college/university ? If so you may need to speak to the system administrator in order to get additional user privileges.

No, im using my home connection. The only thing that might stop it is im usign a BT HomeHub wireless router - would this changed anything, even though i disabled it's firewall?
even if it did, that would stop the terminal apt-get working as well, right?

---

### Post by Pro-reason on 2008-10-24
> **plasmarox said:**
> hmm, that worked fine. Is that related to using ```
sudo apt-get update

sudo apt-get upgrade
```, which also worked fine.

As far as I can tell, you're saying it's all fine now.

---

### Post by Pro-reason on 2008-10-24
> **plasmarox said:**
> hmm, that worked fine. Is that related to using ```
sudo apt-get update

sudo apt-get upgrade
```, which also worked fine.

As far as I can tell, you're saying it's all fine now.

---

### Post by Zalbor on 2008-10-24
No, he's saying that apt-get works when update-manager doesn't. Nothing seems to have changed.

---

### Post by Kevbert on 2008-10-24
OK, try this first (based on an old bug report).
```
sudo apt-get update
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```
Then try to use Update Manager again.
If you get an 403 error with Update Manager can you enter the address in your browser e.g. [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz) and see if you get an error (I've just checked it and it works fine for me).
If you don't get an error, please use Synaptic to completely remove update-manager and update-manager-core. Note all additional packages that are removed.  Reboot and then go back to Synaptic and Install all packages which have just been removed.
The only other thing I can suggest is that the install CD may have been corrupted. Did you burn it yourself ? Performed a checksum on the ISO that was downloaded ? Checked the CD via it's menu item prior to installing ?  It may be necessary to try a complete re-install from scratch.
I'm not aware of BT Home-hub problems when installing software (only setting up connections to the PC).
Good luck.

---

### Post by plasmarox on 2008-10-24
no no, i can only update using terminal - if i try to check for updated software using update manager, the 403 error comes up.
I can access the file ```
http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz
``` fine, and i can see that it contains text.

If i remove update manager, how do i get it back? i havn't got my live CD with me atm, a friend is using it. I did burn it myself, onto a re-writable dvd. That shouldn't cause a problem, right?

I have included two screenshots for clarity.
```

http://image.boswarez.org/image.php?id=3337_4901BA72
http://image.boswarez.org/image.php?id=33C5_4901BA72

```

---

### Post by Kevbert on 2008-10-24
Yes, I know it's frustrating, but I'd like to help.
What I've suggested is that you completely uninstall via Synaptic via the web and then re-install again with Synaptic via the web after a reboot (not using update-manager to do this).
 
Regarding installation CD/DVD. Yes it's possible to introduce problems via a bad disk.  When you download the ISO file the first thing to check is the downloaded file hasn't got corrupted data by performing a [[COLOR="Red"]hash check[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") (also known as checksum). If this is fine you can burn it to CD/DVD at a relatively slow speed (4x or less) to minimize burn errors. Burning software and information [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto"). Finally you should check the CD/DVD integrity from the grub boot menu that appears when you first run the CD/DVD. If you haven't done so a memory check using memtest (again in the grub boot menu) is a good idea as Windows, for example, can work with faulty memory (but you're likely to get random lockups and crashes).

---

### Post by plasmarox on 2008-10-24
> **Kevbert said:**
> Yes, I know it's frustrating, but I'd like to help.
What I've suggested is that you completely uninstall via Synaptic via the web and then re-install again with Synaptic via the web after a reboot (not using update-manager to do this).
 
Regarding installation CD/DVD. Yes it's possible to introduce problems via a bad disk.  When you download the ISO file the first thing to check is the downloaded file hasn't got corrupted data by performing a [[COLOR="Red"]hash check[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") (also known as checksum). If this is fine you can burn it to CD/DVD at a relatively slow speed (4x or less) to minimize burn errors. Burning software and information [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto"). Finally you should check the CD/DVD integrity from the grub boot menu that appears when you first run the CD/DVD. If you haven't done so a memory check using memtest (again in the grub boot menu) is a good idea as Windows, for example, can work with faulty memory (but you're likely to get random lockups and crashes).
i  will admit, i struggled to burn to the iso - i struggled to find a good program, and wasted a CD in the process :(

I didnt actually check the cd for errors, althoguh i guess i should have done.  Wouldnt the installer say it was corrupted when installing?

Also, where on the internet can i find the update manager *.deb? Or how cani find this out?

---

### Post by lswest on 2008-10-24
> **plasmarox said:**
> i  will admit, i struggled to burn to the iso - i struggled to find a good program, and wasted a CD in the process :(

I didnt actually check the cd for errors, althoguh i guess i should have done.  Wouldnt the installer say it was corrupted when installing?

Also, where on the internet can i find the update manager *.deb? Or how cani find this out?

you would install the update-manager program using Synaptic Package Manager.  Go to system-->administration-->Synaptic Package Manager, search for the update-manager packages, and remove them fully (click the checkbox and choose "mark for complete removal") then hit apply (after taking note of the other packages being removed) and after that is done, re-install using the same method but choosing "mark for installation" from the checkbox menu.

Hope that helps clarify things.

P.S. The installer wouldn't say it's corrupted if it installed fine nonetheless, the major errors are displayed for critical system files, which update-manager isn't.

---

### Post by Kevbert on 2008-10-24
When I suggested via the web, I meant as long as you have an active internet connection you can use Synaptic to get it for you.  For packages you can go also go [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/search?keywords=update-manager")(I've linked to where you can get the two files). Deb files you can just double click on.
Please also check your email.

---

### Post by plasmarox on 2008-10-24
> **lswest said:**
> you would install the update-manager program using Synaptic Package Manager.  Go to system-->administration-->Synaptic Package Manager, search for the update-manager packages, and remove them fully (click the checkbox and choose "mark for complete removal") then hit apply (after taking note of the other packages being removed) and after that is done, re-install using the same method but choosing "mark for installation" from the checkbox menu.

would i need to do a complete removal or just removal? whats the diffence?

---

### Post by Kevbert on 2008-10-24
Removal will only get rid of the packages that you ask, complete removal will get rid of all library files and support files for the package.

---

### Post by plasmarox on 2008-10-24
OK, this is frustrating!

ive uninstalled used synaptic file manager to tell me what file it is, copied into Firefox, downloaded, installed, and it STILL does exactly the same thing.

Maybe my IP range is banned on the server?

---

### Post by Pro-reason on 2008-10-24
Uninstall update-manager and leave it uninstalled.

If you really want automatic updates, install the Mint updater from Linux Mint.  Otherwise, just update manually from Synaptic.

---

### Post by Jammy4041 on 2008-10-29
Hi Plasmarox, welcome to the ubuntu forums.

First try a manual update of your system (launch a terminal >> sudo apt-get upgrade *)

If you get the same errors, you do still have a software sources problem.

If it does, you could try overwriting you /etc/apt/sources.list, just to be on the safe side.

open a terminal, and type
 
```
sudo -i
```to become root.

then type

```
gedit /etc/apt/sources.list
```In this file, clear everything, and paste

```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports restricted universe multiverse main
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security restricted main
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse
```and save.

A backup of the previous file is saved with the "~" suffix, so if anything goes wrong you have some sort of safety net to fall back on.

Then back at the terminal, type 

```
apt-get update
``` to reload your apt sources and then try launching update manager, or if your feeling brave, a sudo apt-get upgrade *

I hope this helps.

---

### Post by plasmarox on 2008-10-30
Hai James, how are you? By the way its me.

Well James, im sure this has already been said, but using the terminal (sudo apt-get upgrade) i can download fine, but using the UI update manager i cant.

Any ideas James?

Its Tim, your little ubuntu apprentice ^^

---

### Post by Earl_Maroon on 2008-10-30
I haven't used Ubuntu for a couple of months now, having not bothered to set up VPN on this side to use with my university network. I finally got around to it today and haven't been able to update my system. This could be for a few reasons: blocked ports and automatic proxy configuration URL not set up properly were what I initially thought it might be. I haven't ever tried to update under these circumstances, so I have no idea where the problem lies.

If I try to update from BASh I get 404s for everything; if I try to update using synaptic I get 403s all round.

---

### Post by Kevbert on 2008-11-01
Hi Tim. No luck with the CD then. It may be worth filling in a bug report on [[COLOR="Red"]launchpad[/COLOR]]("https://launchpad.net/").  you need to tell them what kernel you're running using Terminal
```
uname -a
```
link to this post and add that you've tried a re-install.
Cheers
Kev.

---

### Post by plasmarox on 2008-11-09
Hello Kevbert;
Sorry that i havnt replied, i havnt had anything to add until now when i tried it.

No, i had no luck with the CD you sent me - maybe hardy just didnt work for me.

However, ive since upgraded to Intrepid Ibex, which works flawlessly with the update manager.

Yay!

So ive marked this post as solved, and thanks for all your help.

=]

---


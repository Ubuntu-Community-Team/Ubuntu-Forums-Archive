---
title: "Ubuntu store issues in 20.04.1"
date: 2020-08-23
forum: New to Ubuntu
---

### Post by imon57 on 2020-08-23
I was a windows user, recently I have installed Ubuntu 20.04.1 LTS. But when I was trying to install apps using Ubuntu Store, Ubuntu store was just loading. I have not got any search result from it. There is only editor's picks option showing properly. Please help me to solve this issue.

---

### Post by CelticWarrior on 2020-08-23
Welcome.

Please assure the system is fully updated before attempting to install additional software.
Either open and run the Updates tool or, in terminal, just run
```
sudo apt update && sudo apt full-upgrade
```

---

### Post by imon57 on 2020-08-25
Thanks for your reply. I have run these commands in terminal, rebooted my laptop but the problem exists. Now what to do?

---

### Post by Impavidus on 2020-08-25
What was the output of those commands? You can run them again. That won't do any harm.

Maybe this is a snap-related problem. I don't use snap packages, but they're pushed somewhat on regular Ubuntu. Could you also show the output of```
snap list
dpkg --list gnome-software
```

---

### Post by Dennis N on 2020-08-25
> **imon57 said:**
> Thanks for your reply. I have run these commands in terminal, rebooted my laptop but the problem exists. Now what to do?

If you find applications are missing in Ubuntu Software, you can try the solution here:

[https://ubuntuforums.org/showthread.php?t=2443673&p=13958759#post13958759](https://ubuntuforums.org/showthread.php?t=2443673&p=13958759#post13958759)

---

### Post by imon57 on 2020-08-25
[**[COLOR=#000000]@Impavidus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721") How can I insert image screenshot of output here?

---

### Post by Impavidus on 2020-08-25
Don't use a screenshot. It's text, you can copy it to your post. Use code tags, like in multiple posts above, to preserve formatting in a grey code box.

---

### Post by imon57 on 2020-08-25
[COLOR=#DD4814][COLOR=#000000]@[Impavidus]("https://ubuntuforums.org/member.php?u=1417721") here is the output.[/COLOR][/COLOR]

```
imon@imon-hp-probook-4410s:~$ sudo apt update && sudo apt full-upgradeHit:1 [http://uk-mirrors.evowise.com/ubuntu](http://uk-mirrors.evowise.com/ubuntu) focal InRelease                                                                                     
Hit:2 [http://uk-mirrors.evowise.com/ubuntu](http://uk-mirrors.evowise.com/ubuntu) focal-updates InRelease                                                       
Hit:3 [http://uk-mirrors.evowise.com/ubuntu](http://uk-mirrors.evowise.com/ubuntu) focal-backports InRelease                        
Get:4 [https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) bionic InRelease [7,322 B] 
Hit:5 [http://uk-mirrors.evowise.com/ubuntu](http://uk-mirrors.evowise.com/ubuntu) focal-security InRelease           
Get:6 [https://deb.opera.com/opera-stable](https://deb.opera.com/opera-stable) stable InRelease [2,591 B]
Err:4 [https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) bionic InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D5AD3767530B91D0
Reading package lists... Done
W: GPG error: [https://repo.windscribe.com/ubuntu](https://repo.windscribe.com/ubuntu) bionic InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D5AD3767530B91D0
E: The repository 'https://repo.windscribe.com/ubuntu bionic InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
imon@imon-hp-probook-4410s:~$ snap list
Name               Version             Rev   Tracking         Publisher   Notes
core               16-2.45.3.1         9804  latest/stable    canonical&#10003;  core
core18             20200724            1885  latest/stable    canonical&#10003;  base
gnome-3-34-1804    0+git.3009fc7       36    latest/stable/&#8230;  canonical&#10003;  -
gtk-common-themes  0.1-36-gc75f853     1506  latest/stable/&#8230;  canonical&#10003;  -
snap-store         3.36.0-80-g208fd61  467   latest/stable/&#8230;  canonical&#10003;  -
snapd              2.45.3.1            8790  latest/stable    canonical&#10003;  snapd
vlc                3.0.11              1700  latest/stable    videolan&#10003;   -
imon@imon-hp-probook-4410s:~$ dpkg --list gnome-software
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version                 Architecture Description
+++-==============-=======================-============-=================================
ii  gnome-software 3.36.1-0ubuntu0.20.04.0 amd64        Software Center for GNOME



```

---

### Post by CelticWarrior on 2020-08-25
You have a problem in your software sources, the Windscribe repository. It has no content for 20.04. Remove it re-run the commands and you should be fine.

---

### Post by imon57 on 2020-08-25
[COLOR=#DD4814][COLOR=#000000]@[CelticWarrior]("https://ubuntuforums.org/member.php?u=1826209")[/COLOR][/COLOR][COLOR=#000000]
[/COLOR]How to remove windscribe repository?

---

### Post by CelticWarrior on 2020-08-25
The simplest way is:

Open Software & Updates > Other software.
Find the line about it, select it and remove (you'll be asked for the password).
Close Software & Updates and answer YES to the message that pops up.

---

### Post by coffeecat on 2020-08-25
@imon57, I've replaced the quote tags for code tags in your post. Note the improvement in columnar formatting. If you need to post terminal output or contents of config files, or similar, please always use code tags, not quote tags. There's a link in my sig if you need to know how. Use the advanced editor for code tags,.

---

### Post by Impavidus on 2020-08-25
> **imon57 said:**
> ... rebooted my laptop ...

FYI: Kernel and driver issues are the only problems where rebooting can be part of solving the problem. For some other issues you have to logout and login again, for most problems even that isn't necessary. But rebooting doesn't hurt either (unless the problem made your system unbootable and you've got no spare).

---

### Post by imon57 on 2020-08-26
[URL="https://ubuntuforums.org/member.php?u=1826209"][COLOR=#000000]@[/COLOR][B][COLOR=#000000]CelticWarrior
[/COLOR][/B][/URL][**[COLOR=#000000]@Impavidus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721")
After removing windscribe repositories, I have ran those commands again. It was successful. But ubuntu software is not working properly, same as before. Now what to do?

---

### Post by Dennis N on 2020-08-26
You have two software stores installed:

_package name --> Application Name_
snap-store --> Ubuntu Software
gnome-software --> Software

The second isn't in a fresh install of ubuntu 20.04. If you did a new install, you must have installed it. 
Try removing it and see if that affects how Ubuntu Software behaves.

```
sudo apt remove gnome-software
```

---

### Post by imon57 on 2020-08-26
[COLOR=#DD4814][COLOR=#000000]@[Dennis N]("https://ubuntuforums.org/member.php?u=321222")[/COLOR][/COLOR][COLOR=#000000] [/COLOR]
I have removed gnome software using this command, but ubuntu software is not working properly.

---

### Post by Dennis N on 2020-08-26
> **imon57 said:**
> [COLOR=#DD4814][COLOR=#000000]@[Dennis N]("https://ubuntuforums.org/member.php?u=321222")[/COLOR][/COLOR][COLOR=#000000] [/COLOR]
I have removed gnome software using this command, but ubuntu software is not working properly.
You did say you have the Editor's Picks showing. 
Do you see the categories? (see screen shot)
If so, realize that when you click on a category, it can take up to 30 seconds for the applications in that category to load. Did you wait long enough?

---

### Post by Impavidus on 2020-08-26
> **Dennis N said:**
> You have two software stores installed:

_package name --> Application Name_
snap-store --> Ubuntu Software
gnome-software --> Software

The second isn't in a fresh install of ubuntu 20.04. If you did a new install, you must have installed it. 
Try removing it and see if that affects how Ubuntu Software behaves.

```
sudo apt remove gnome-software
```

If I had to choose, I'd keep gnome-software and drop snap-store. But in fact, I have neither. Xubuntu comes with gnome-software, but without snap-store (or any other snaps). I removed gnome-software (and snapd).

---

### Post by imon57 on 2020-08-26
No. Only editors's picks is showing.
I have given enough time to load but the result is same. If I search anything it shows no software found or just loading for 5 minutes+. The problem is same like before it was...
Screenshot:

---

### Post by Dennis N on 2020-08-26
> **imon57 said:**
> No. Only editors's picks is showing.
I have given enough time to load but the result is same. If I search anything it shows no software found or just loading for 5 minutes+. The problem is same like before it was...
Screenshot:
Many users had problems with the snap-store back when Ubuntu 20.04 was first released back in April. Absent further ideas for fixing it, I suggest you just do what I and others did and use 'Software' instead of 'Ubuntu Software'. Follow these two steps (also given in the link provided in post #5):

First, remove 'Ubuntu Software' using your terminal:
```
snap remove snap-store
```
Then install 'Software' from the Ubuntu repository using your terminal:
```
sudo apt install gnome-software
```

The icon for the software store will now be labeled 'Software' instead of 'Ubuntu Software'.

---

### Post by imon57 on 2020-08-27
**[COLOR=#000000]@[/COLOR]**[**[COLOR=#000000]Dennis N[/COLOR]**]("https://ubuntuforums.org/member.php?u=321222")
Now Software app is working perfectly, after removing ubuntu software. Thank you. 
What about snap store? Is it better to use gnome store or snap store?

---

### Post by Dennis N on 2020-08-27
> **imon57 said:**
> **[COLOR=#000000]@[/COLOR]**[**[COLOR=#000000]Dennis N[/COLOR]**]("https://ubuntuforums.org/member.php?u=321222")
Now Software app is working perfectly, after removing ubuntu software. Thank you. 
What about snap store? Is it better to use gnome store or snap store?

If you did the two steps in post #20, you don't have snap-store installed anymore. 'Ubuntu Software' is the name that snap-store uses when you do a fresh install of Ubuntu 20.04. 

When working correctly, Ubuntu Software and Software are nearly the same. One difference is that the latter can also manage flatpak packages - that's the reason I use 'Software' myself. 

_Bonus information_:
snap-store is a confusing package, as there are two versions in use. One is for Ubuntu 20.04, currently revision 467, and there is another version (revision 415) that's usable by any distro, including non-Ubuntu distros. Revision 415 only handles snap packages.

---

### Post by imon57 on 2020-08-27
[URL="https://ubuntuforums.org/member.php?u=1826209"][B][COLOR=#000000]@CelticWarrior 
[/COLOR][/B][/URL]@[**[COLOR=#000000]Impavidus[/COLOR]**]("https://ubuntuforums.org/member.php?u=1417721")
@[**[COLOR=#000000]Dennis N[/COLOR]**]("https://ubuntuforums.org/member.php?u=321222") 
Thanks to everyone for helping me to solve this issue.

---


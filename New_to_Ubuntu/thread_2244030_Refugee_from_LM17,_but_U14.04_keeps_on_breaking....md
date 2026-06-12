---
title: "Refugee from LM17, but U14.04 keeps on breaking..."
date: 2014-09-13
forum: New to Ubuntu
---

### Post by SJLPHI on 2014-09-13
Hello, I think I could identify myself as a Linux Mint 17 Refugee. I have a Lenovo T410S, bought used and worked very well with LM17; but it had slight issues here and there which I was able to fix most over time. Yesterday after a systematic failure (second time in the past 2 weeks) I've decided to give Ubuntu 14.04 a go.

So far everything looks great and works well and fast... After a generic update, upgrade and dist-upgrade. The OS becomes broken. After upgrade and reboot, the network applet somehow disappears then after dist-upgrade I can't even use the terminal properly anymore because keyboard decides to work against me.

I am using Konsole for terminal and I have set it to my default, I've set google-chrome to be my default, and I am about to Re-install this distro for the third time today...

I'm suspecting that this is not a hardware issue because why else would the system work fine until the upgrade?

I have to ask, if there is a known bug that's been going around lately? From what I can read, during the dist-upgrade, there is a kernel upgrade..

In summary:

1. Network Applet disappears after update & upgrade
-It is evident that the startup applications are not being loaded because I tried to load different commands
-That applet is broken because I did try "nm-applet" in terminal and I get an error message

2. Will there be an issue for setting Konsole as my default terminal?
-Konsole is definitely heavier!

3.This laptop will be dedicated for scientific/programming purposes mostly. 
It is to have:
 VM-Windows7Pro 32 bit
Crossover13-MSOffice2013
ROOT-CERN
python-numpy, python-scipy
Maple13
Okular pdf editor

I have read some troubleshoots regarding these issues, one of them this:
[http://askubuntu.com/questions/449658/networkmanager-tray-nm-applet-is-gone-after-upgrade-to-14-04-trusty](http://askubuntu.com/questions/449658/networkmanager-tray-nm-applet-is-gone-after-upgrade-to-14-04-trusty)

except, the situations are different. I am currently applying a third fresh install and I am going to carefully go step-by-step on each package installation. I am not very optimistic at this point. Will someone please explain to me what I may be doing wrong or official known bugs and etc.?

//Edit, I am currently just beginning one of the toughest semesters I will be going through in school and I need this thing to be GOOD-TO-GO by Monday, if not I will have to return to semi-broken yet more familiar LM17

---

### Post by Tadaen_Sylvermane on 2014-09-13
Did you check the md5 of the iso you downloaded? Also what problems were you having with mint?

Another thing, while you can technically use virtually anything in the repos on any DE there are reasons that some are labelled for kde. If you want kde apps you may find that using Kubuntu may be the better choice. Better integration as well. I have found google-chrome lately to be a bit fishy. I use chromium now and the pepperflash plugin for it and haven't had a lick of trouble. I know people say they are identical but they aren't. Google adds a few things here and there then re-releases it as Chrome.

---

### Post by SJLPHI on 2014-09-13
I did not check the md5, but like I said, the problem starts after upgrade.
LM17 had hardware specific issue, i.e. during boot sometimes keyboard and touchpad didn't work. After a recent upgrade, it started slowing down for some reason then started freezing and started failing to boot. I used live dvd to copy as much important documents as I could then decided to do a fresh install on Ubuntu 14.04

I will check out Kubuntu if this time around doesn't work out. It's currently running update, upgrade and dist-upgrade. I am keeping my fingers crossed for now.

---

### Post by Rob Sayer on 2014-09-14
I have Konsole installed on my netbook running xubuntu 14.04.  That's just because I use dolphin as my file manager, and I installed it along with ark and rar so I could more easily run a terminal or extract files from within dolphin.  I've done this with several non kde DEs.  Never ever had a problem with it.

And running kubuntu rather than any other DE isn't going to solve underlying config issues.

Installing ubuntu to fix problems in mint isn't a very reliable strategy.  Mint is based on ubuntu,  but uses a slightly older kernel version.  A newer kernel may solve a problem and it may make things worse.

There are definitely times when I feel reinstalling is better than fixing a borked install.  Which is one of the reasons it's such a good idea to install with a separate /home partition.  But I don't think this is one of those cases.

You're going to have to post some hardware details beyond the computer make and model # ... which is actually not very useful in diagnosis ... and tackle the real configuration issue(s) you have.  Distro hopping isn't likely to help.  Ubuntu has hardware recognition as good or better than anyone else's.

---

### Post by grahammechanical on 2014-09-14
Do not run dist-upgrade. Why not use the Update Manager?

The use of apt-get dist-upgrade will upgrade the version of Ubuntu that we are using and it will pull in updated packages that are not yet ready to be installed by the usual apt-get upgrade command. If there is a conflict between library versions then dis-upgrade will remove conflicting libraries and that can break things. You could install Synaptic Package Manager and use that to update. Synaptic will tell us what packages are going to be upgraded, what are going to be installed and what are going to be removed. Then we have an opportunity to stop the thing from removing a package the user interface depends on.

If we use apt-get update followed by apt-get upgrade we may see a list of packages being held back. Well, dist-upgrade will bring in all those held back packages. It may not cause a problem but then again it may.

You should also think about having all your important documents on a separate partition. Then a re-install will not affect those documents.

Regards.

---

### Post by SJLPHI on 2014-09-14
Thank you for you input, I think your last reply was the most helpful and sound.

I think the biggest problem was that I installed packages before upgrading the system after a fresh install.
With the combination of not changing anything on the system, other than swappiness. I reserved the original terminal as the default terminal and just made a short cut to Konsole.

I am currently over 100% of where I was on LM17, running stable on U14.04. The boot time is a little slow but once the system is going. It seems to be working very well and fast. I even installed vbox Windows7 32 bit which is running stable.

---


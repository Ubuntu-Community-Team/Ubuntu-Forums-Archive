---
title: "This could b a BUG"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by fattyz on 2011-12-16
I've been working a few days on this, following some other threads same problem, and I've seen it b4.  Time to get this up in the big leagues, it could b a bug.  If not, its still a major headache.

I borrowed this material because my fellow sufferer catalogs the process nicely.

 I was trying to finish an installation of Ubuntu 10.04 (Lucid Lynx). It got interrupted partway through. When I tried to finish it, I got error messages. At the point where I decided to start blogging the situation, I had just tried the advice to enter these commands:

apt-get clean
apt-get autoclean
apt-get update
apt-get upgrade
apt-get dist-upgrade
(These required "sudo" before each command or "sudo -i" by itself first.)  The first three went OK, but after "apt-get upgrade," I got this:

You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  gnome-power-manager: Depends: devicekit-power (>= 011) but it is not installable
  indicator-session: Depends: devicekit-power but it is not installable
  initramfs-tools: Breaks: mountall (< 2.0~) but 1.0 is installed
  mountall: PreDepends: libc6 (< 2.11) but 2.11.1-0ubuntu7 is installed
  ubuntu-desktop: Depends: usplash but it is not installed
  usplash-theme-ubuntu: Depends: usplash (>= 0.5.30) but it is not installed
E: Unmet dependencies. Try using -f.
Running "apt-get -f install" generated a similar message, ending with these two lines:
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
Just before this, I had run into an error, "Could not resolve 'us.archive.ubuntu.com,'" to which one suggested solution was just to wait for a certain software repository to sort out a problem with its server.  In the present case, however, I had been having these dependency errors for weeks, each time I had booted up Ubuntu on this particular computer and had attempted to update it.  So I did not think the problem was with the repository in my case.

I ran a different search and got a new set of suggestions.  In at least one case, the suggestion to uninstall and reinstall the Gnome and KDE desktops did not seem to have solved the problem.  I tried the approach of going through the list of problem packages (quoted above) and attacking them one by one.  The error for initramfs-tools (above) looked simple enough:  I went into Synaptic, clicked on Edit > Fix Broken Packages, right-clicked on initramfs-tools, and marked it for reinstallation.  But when I clicked "Apply," it said, "Could not apply changes!  Fix broken packages first."  I tried again, this time selecting "Mark for removal."  It said it would have to "mark additional required changes."  I said OK.  It marked dozens of other packages, including some that Synaptic labeled as "(ESSENTIAL)."  I clicked Apply.  It said, "Essential packages will be removed.  This may render your system unusable!"  I cancelled that.  I tried marking a different package -- usplash-theme-ubuntu -- for reinstallation.  Again, it showed me a list of dozens of other packages that would be removed; and again, when I tried to go ahead with that, I got an indication that I was trying to remove essential packages.  I tried the suggestion to type "dpkg --purge (package name)," beginning with initramfs-tools.  I had to quit Symantec to make that go.  But it still just listed a dozen programs that depended on initramfs-tools.  I figured that trying to remove those would quickly lead to the same long list as before.

It seemed that the option, mentioned by many, of just reinstalling Ubuntu might turn out to be the fastest (if not the only) option left.  Facing that possibility, I went back and proceeded through the option of uninstalling initramfs-tools in Synaptic, including the essential packages.  This generated a new list of problems.

I had to call it quits for the time being.  I got back to this situation a few days later.  To see where things stood now, I went back into Symantec.  It said I had seven broken packages.  I marked the first on the list, gnome-power-manager, for updating, and clicked Apply.  It said this:
An error occurred
The following details are provided:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/fontconfig-config_2.8.0-2ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fontconfig/fontconfig-config_2.8.0-2ubuntu1_all.deb)
Undetermined error [IP: 91.189.92.166 80]
[It gave me a number of other error messages similar to this one.]
That made it look like us.archive was still definitely dysfunctional.  I killed Synaptic and went into System > Administration > Software Sources > Other Software.  I checked all of those us.archive.ubuntu.com/ubuntu/ sources and clicked Remove.  Then I clicked Close > Reload.  Not surprisingly, I got this:
Could not download all repository indexes
The repository may no longer be available . . . .
I closed that.  Now I got another message:
An error occurred
The following details are provided:
E: The package fontconfig-config needs to be reinstalled, but I can't find an archive for it.
I closed that too.  Software Sources closed.  I tried restarting Synaptic, but that last error message ("An error occurred") recurred.  I retried the sequence suggested at the start of this post:commands:

sudo -i
apt-get clean
apt-get autoclean
apt-get update
apt-get upgrade
apt-get dist-upgrade
The "apt-get update" line gave me a bunch of error messages along the lines of "Ign [http://security.ubuntu.com/](http://security.ubuntu.com/) lucid-security" and then another bunch along the lines of "W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security" errors, and closed with this:
E: Some index files failed to download, they have been ignored, or old one used instead.
I repeated the apt-get update command, but got the same thing.  I went ahead with "apt-get upgrade," but got this:  "E: The package fontconfig-config needs to be reinstalled, but I can't find an archive for it."  So Synaptic wouldn't start.  I tried "dpkg --purge fontconfig-config."  It said "dependency problems prevent removal of fontconfig-config."  Those problems were that "libfontconfig1 depends on fontconfig-config" and "fontconfig depends on fontconfig-config." I tried dpkg with libfontconfig1, but that gave me a list of about a hundred dependencies.

I had seen several other threads in which a complete reinstall seemed to be the only solution.  I had now reached that point myself.

---

### Post by philinux on 2011-12-16
> **fattyz said:**
> 

 I was trying to finish an installation of Ubuntu 10.04 (Lucid Lynx). It got interrupted partway through. When I tried to finish it, I got error messages. 

If any OS installation gets interrupted part way through, the best solution is to start again. This is a much quicker and painless path.

You don't mention what caused the interruption?

---

### Post by fattyz on 2011-12-16
Right, I just used that post because I got into a similar situation, exactly the same really.

All I did was add a couple repos, bigisi and pmecenry were the only ones.  Then I was trying to run a-desk, which I always install with ubuntu, and trying to get it to work I wanted to install mplayer.

That started all the fun.

---

### Post by Paqman on 2011-12-16
How did you add the new repos? Did you use add-apt-repository, Software Sources, or did you manually edit your /etc/apt/sources.list?

---

### Post by fattyz on 2011-12-16
I used software sources once and I think I used terminal on the other one.

---

### Post by Paqman on 2011-12-16
Can you post a copy of /etc/apt/sources.list? Something has got mangled.

If I understand you correctly the details in the OP are not the actual fault that you've got, but your problem is very similar. What error do you actually get when you try to update?

---

### Post by fattyz on 2011-12-17
sudo apt-get update produces no errors but watch this


mark@mark-laptop:~$ sudo apt-get install mplayer
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libavcodec52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libavformat52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavformat-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libcaca0 (>= 0.99.beta17-1) but 0.99.beta16-3 is to be installed
           Depends: libdirectfb-1.2-9 but it is not installable
           Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installable or
                    libjack-0.116 but it is not installable
           Depends: libncurses5 (>= 5.7+20100313) but 5.7+20090803-2ubuntu3 is to be installed
           Depends: libx264-98 but it is not installable
E: Broken packages


sources.list
# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick free non-free

---

### Post by fattyz on 2011-12-17
Here is another thread that goes into detail trying to fix this problem.  No dice unfortunately. 

[http://www.mydigitallife.info/ubuntu-unmet-dependencies-not-going-to-be-installed-or-try-apt-get-f-install-error/](http://www.mydigitallife.info/ubuntu-unmet-dependencies-not-going-to-be-installed-or-try-apt-get-f-install-error/)

---

### Post by Paqman on 2011-12-17
I notice from your sources.list that you're connecting to Medibuntu for Maverick, while the rest of your repos are lucid. Since a lot of the errors that got spat out were for multimedia packages it might be worth switching to the correct version of Medibuntu and trying again.

---

### Post by Frogs Hair on 2011-12-17
> **fattyz said:**
> Right, I just used that post because I got into a similar situation, exactly the same really.

All I did was add a couple repos, bigisi and pmecenry were the only ones.  Then I was trying to run a-desk, which I always install with ubuntu, and trying to get it to work I wanted to install mplayer.

That started all the fun.

Bigisi for Gnome 2 is a dead project and the themes will be ported to Gnome 3 for 12.04 .

If you have installed the themes on a Gnome 2 version of Ubuntu you may want to disable that source because it won't update .

---

### Post by fattyz on 2011-12-17
Thanks I'll try that and let you know.  I already unchecked the bigisi repo and stopped getting errors from apt-get update.  I did not notice the medibuntu repo was wrong, I'll fix it and post results.

---

### Post by amjjawad on 2011-12-17
> **philinux said:**
> If any OS installation gets interrupted part way through, the best solution is to start again. This is a much quicker and painless path.

+1

On a side note, in case you want to report a bug, please use Launchpad because developers don't look at forums.

Thanks!

---

### Post by fattyz on 2011-12-18
I checked the repo and reinstalled using this  [http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/11/add-medibuntu-repository-ubuntu-10-0410-10-maverick-meerkat/)

but I unchecked the maverick line in software sources and kept the lucid line.

The install did not go exactly like on the page but I see the repo in my software sources and nothing is changed.

---

### Post by fattyz on 2011-12-18
Here is the result of apt-get update, upgrade and dist-upgrade then trying to apt-get install mplayer.mark@mark-laptop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/blueman/ppa/ubuntu/](http://ppa.launchpad.net/blueman/ppa/ubuntu/) lucid/main Translation-en_US  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release.gpg                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [748B]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/free Translation-en_US             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) maverick/non-free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick Release        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/free Packages                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) maverick/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources                       
Fetched 2,293B in 13s (164B/s)
Reading package lists... Done
mark@mark-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:~$ sudo apt-get dist upgrade
E: Invalid operation dist
mark@mark-laptop:~$ sudo apt-get-dist upgrade
sudo: apt-get-dist: command not found
mark@mark-laptop:~$ sudo apt-get-dist-upgrade
sudo: apt-get-dist-upgrade: command not found
mark@mark-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mark@mark-laptop:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libavcodec52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavcodec-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libavformat52 (>= 4:0.6-1~) but it is not going to be installed or
                    libavformat-extra-52 (>= 4:0.6-1~) but it is not going to be installed
           Depends: libcaca0 (>= 0.99.beta17-1) but 0.99.beta16-3 is to be installed
           Depends: libdirectfb-1.2-9 but it is not installable
           Depends: libjack-jackd2-0 (>= 1.9.5~dfsg-14) but it is not installable or
                    libjack-0.116 but it is not installable
           Depends: libncurses5 (>= 5.7+20100313) but 5.7+20090803-2ubuntu3 is to be installed
           Depends: libx264-98 but it is not installable
E: Broken packages
mark@mark-laptop:~$

---

### Post by cryptotheslow on 2011-12-18
As witnessed in what you posted just above:

```
Hit http://packages.medibuntu.org maverick Release.gpg 
Ign http://packages.medibuntu.org/ maverick/free Translation-en_US 
Hit http://packages.medibuntu.org maverick Release 
Hit http://packages.medibuntu.org maverick/free Packages
Hit http://packages.medibuntu.org maverick/non-free Packages
```


You still have one or more Maverick (v10.10) Medibuntu repositories listed in your apt sources.

As most of the packages being complained about at the end of your log are audio-visual related - it looks like that is what (still) needs sorting out. :)

---

### Post by fattyz on 2011-12-18
Yep, so what did we learn today?  The repositories are version specific.

Thanks very very much.

---

### Post by amjjawad on 2011-12-21
Glad you managed to fix it :)

---


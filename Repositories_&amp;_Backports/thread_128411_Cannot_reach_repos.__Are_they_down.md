---
title: "Cannot reach repos.  Are they down?"
date: 2006-02-11
forum: Repositories &amp; Backports
---

### Post by nrwilk on 2006-02-11
I'm still trying to understand ubuntu's repository system, so some of my assumptions may be way off here.  My sources.list comes from this suggested one in the sticky thread:
[http://ubuntuforums.org/showthread.php?t=92672](http://ubuntuforums.org/showthread.php?t=92672)

This has always happened to me, and I figured that it was just normal operating procedure for the ubuntu repositories, but recently it's way worse.  I'd say that a```
sudo apt-get update
```only works every other time I do it.  In the times it doesn't work, it will work two minutes later.  Sometimes, though, it takes longer to get it to work.  I won't be able to reach the repositories for a couple hours sometimes.  Do they go down?  Is this normal?  Do other people have this problem?  It's daily for me.

Recently it's been even worse, though.  I haven't been able to connect to the repositories at all for about three days.  Am I the only one?

here's my sources.list:
```

deb http://archive.ubuntu.com/ubuntu breezy main restricted 
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted 
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team

deb http://archive.ubuntu.com/ubuntu breezy universe multiverse 
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse 

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted 
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted 

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse 
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse 

## official backports
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse 

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free 
deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free 

## plf secondary repo. Use if primary repo is offline.
## FTP mirror from http://free.fr (french ISP)
## deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
## deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## plf mirror. Use if primary and secondary are offline
## deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free

##
## Use the following repos only if you need them.
## To use one remove the "##"  from the line that starts with "## deb".
##

## wine
## deb http://wine.sourceforge.net/apt/ binary/

## opera web browser
## deb http://deb.opera.com/opera/ etch non-free

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
## deb http://people.ubuntu.com/~doko/OOo2 ./

## KDE 3.5.1
## deb http://kubuntu.org/packages/kde351 breezy main 

```

Here's what I get when I try to apt-get update:
```

Ign http://packages.freecontrib.org breezy Release.gpg
Ign http://packages.freecontrib.org breezy Release
Ign http://packages.freecontrib.org breezy/free Packages
Ign http://packages.freecontrib.org breezy/non-free Packages
Ign http://packages.freecontrib.org breezy/free Sources
Ign http://packages.freecontrib.org breezy/non-free Sources
Get:1 http://packages.freecontrib.org breezy/free Packages [545B]
Get:2 http://packages.freecontrib.org breezy/non-free Packages [2337B]
Get:3 http://packages.freecontrib.org breezy/free Sources [316B]
Get:4 http://packages.freecontrib.org breezy/non-free Sources [473B]
Err http://archive.ubuntu.com breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com breezy-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://archive.ubuntu.com breezy-backports Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Fetched 3671B in 6m0s (10B/s)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/breezy-backports/Release.gpg  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Are there more reliable mirrors that I could use?

---

### Post by aysiu on 2006-02-11
It seems to be working for me: ```
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:3 http://security.ubuntu.com breezy-security Release.gpg [189B]
Get:4 http://archive.ubuntu.com breezy-backports Release.gpg [189B]
Hit http://archive.ubuntu.com breezy Release
Get:5 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://archive.ubuntu.com breezy-updates Release
Hit http://archive.ubuntu.com breezy-backports Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Hit http://archive.ubuntu.com breezy/main Sources
Get:6 http://security.ubuntu.com breezy-security/main Packages [34.8kB]
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Hit http://archive.ubuntu.com breezy-updates/main Packages
Hit http://archive.ubuntu.com breezy-updates/restricted Packages
Hit http://archive.ubuntu.com breezy-updates/main Sources
Hit http://archive.ubuntu.com breezy-updates/restricted Sources
Hit http://archive.ubuntu.com breezy-backports/main Packages
Get:7 http://security.ubuntu.com breezy-security/restricted Packages [4458B]
Get:8 http://security.ubuntu.com breezy-security/main Sources [10.6kB]
Get:9 http://security.ubuntu.com breezy-security/restricted Sources [960B]
Hit http://archive.ubuntu.com breezy-backports/restricted Packages
Get:10 http://security.ubuntu.com breezy-security/universe Packages [27.9kB]
Hit http://archive.ubuntu.com breezy-backports/universe Packages
Get:11 http://security.ubuntu.com breezy-security/universe Sources [4747B]
Hit http://archive.ubuntu.com breezy-backports/multiverse Packages
Fetched 103kB in 3s (26.6kB/s)
Reading package lists... Done
``` I just did that on the sources based on the first link of my signature.

---

### Post by nrwilk on 2006-02-11
Is there anything else that I could have messed up?

Because using the ones from your sig, I get the exact same output as above.

This makes me think it's not the sources.list that's the problem.  What else could it be?

---

### Post by aysiu on 2006-02-11
[QUOTE=Fealos]Is there anything else that I could have messed up?

Because using the ones from your sig, I get the exact same output as above.

This makes me think it's not the sources.list that's the problem.  What else could it be?[/QUOTE] Okay. I took a second look. I've seen this before in other threads: ```
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
``` and it had something to do with using a proxy internet connection or having some weird firewall configuration. I don't know how to fix that, though.

**Edit** A quick search on your error message turned up [this solution](http://www.ubuntuforums.org/showpost.php?p=224019&postcount=9), but there may be others if that doesn't work for you.

---

### Post by nrwilk on 2006-02-11
Wow!  it worked!

Thanks so much, Aysiu!

Strange that the Automatic DHCP hadn't updated those nameservers automatically like it should have.  Or, at least Qwest's site said that they should be updated automatically in that case.  I guess it recently changed, that must have been when it started acting wierd for me.

The funny thing is, I'm not using a proxy OR a firewall.  I wonder why the problem affects me.

Thanks again!

---

### Post by nrwilk on 2006-02-12
Strange, I had to do it again.  Why is my automatic detection DHCP process detecting the wrong DNS IPs?

---

### Post by mmcmonster on 2006-02-14
For those of us that also have this problem, how can I figure out my ISP's DNS?  I am pretty sure I have DHCP or something like that. (I never had to manually enter a DNS to begin with).

---

### Post by nrwilk on 2006-02-16
I just googled for "qwest dns."  There was even a section on editing the DNS entries manually in linux.  Your ISP probably has a similar page.

---

### Post by nrwilk on 2006-02-17
I have to do this almost daily.  Can I find out why DHCP is detecting the wrong DNS IPs, and entering them into /etc/resolv.conf?

Is there any way I can make this permanent so I don't have to edit resolv.conf every day?

---


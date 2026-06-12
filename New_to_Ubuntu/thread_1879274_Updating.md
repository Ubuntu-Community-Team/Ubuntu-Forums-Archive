---
title: "Updating"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by llmunro on 2011-11-11
Hi all,

I can't seem to update Ubuntu 11.10, as the update manager continually tells me to check my internet connection for the following reasons:

W:Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

If I look at software sources > Other software, I see that this ppa has been disabled with the upgrade to Oneric, so I'm confused as to why this appears to be hanging up the update manager? 
Any suggestions?

Thanks to all.
Best,
Lisa

---

### Post by BillyBoa on 2011-11-11
Try to edit your sources.list file, seems corrupted

[http://www.howtoforge.com/generate_sources.list_with_source_o_matic](http://www.howtoforge.com/generate_sources.list_with_source_o_matic)

---

### Post by matt_symes on 2011-11-11
Hi

> [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources)This PPA does not exist for Oneiric.

Open a terminal and type

```
grep nautilus-elementary-ppa /etc/apt/sources.list.d/*
```Post the results back here if it's not in sources.list.

Kind regards

---

### Post by philinux on 2011-11-11
> **llmunro said:**
> Hi all,

I can't seem to update Ubuntu 11.10, as the update manager continually tells me to check my internet connection for the following reasons:

W:Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

If I look at software sources > Other software, I see that this ppa has been disabled with the upgrade to Oneric, so I'm confused as to why this appears to be hanging up the update manager? 
Any suggestions?

Thanks to all.
Best,
Lisa

Use ppa purge. You can restore the ppa after the upgrade.

 [http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html)

---

### Post by llmunro on 2011-11-11
Thanks for all of the advice!

I decided to try PPA purge first, as it seemed the simplest.

But...

lisa@lisa-Samsung:~$ sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
[sudo] password for lisa: 
PPA to be removed: am-monkeyd nautilus-elementary-ppa
Warning:  Could not find package list for PPA: am-monkeyd 
nautilus-elementary-ppa


Now what?

Thanks all.

Best,
Lisa

---

### Post by matt_symes on 2011-11-11
Hi

From /usr/bin/ppa-purge

```
# Make list of all packages in PPA
PPA_LIST=/var/lib/apt/lists/${PPAHOST}_${PPAOWNER}_${PPANAME}_*_Packages
for LIST in $PPA_LIST; do
        if [ -e $LIST ]; then
                grep "^Package: " $LIST | cut -d " " -f2 | sort >> $PPA_PKGS
        fi
done

if [ ! -s $PPA_PKGS ]; then
        warn "Could not find package list for PPA: $PPAOWNER $PPANAME"
        exit 1
fi
```I suspect you added the PPA but it was never able to download a package list because it does not exist for Oneiric.

You have done nothing wrong so far (that i can see). I would suggest following the steps in #1 and #2. 

It is a good little script - i have bookmarked it myself - however, in your case, it will not fix your issue.

Kind regards

---

### Post by llmunro on 2011-11-11
Hi,

Thanks for the help.

Here's what I got when I tried 

grep nautilus-elementary-ppa /etc/apt/sources.list.d/*

lisa@lisa-Samsung:~$ grep nautilus-elementary-ppa /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list.distUpgrade:deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) maverick main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list.distUpgrade:deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) maverick main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list.save:# deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main # disabled on upgrade to natty
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-maverick.list.save:# deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main # disabled on upgrade to natty
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.distUpgrade:deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.distUpgrade:deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.distUpgrade:deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.distUpgrade:deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.save:deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.save:deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.save:deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-natty.list.save:deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) natty main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-oneiric.list:deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) oneiric main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-oneiric.list:deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-oneiric.list.save:deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) oneiric main
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-oneiric.list.save:deb [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) oneiric main # disabled on upgrade to oneiric
/etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa-oneiric.list.save:# deb-src [http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu](http://ppa.launchpad.net/am-monkeyd/nautilus-elementary-ppa/ubuntu) oneiric main # disabled on upgrade to oneiric

Sorry to be asking the obvious, but what do I do with this now?

Thanks much for the help and patience.

Best,
Lisa

---

### Post by matt_symes on 2011-11-11
Hi

> Sorry to be asking the obvious, but what do I do with this now?Now we are going to delete them :) That command shows the files in which the references to the PPAs are stored

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/am-monkeyd-nautilus-elementary-ppa*
```Enter your password. It will not be echoed to the screen. Then type

```
sudo apt-get update
```

It was upgrading Ubuntu that caused the problems here.

Kind regards

---

### Post by llmunro on 2011-11-11
Huzzah!

This seems to have fixed *that* problem, but after running 

sudo apt-get update


I have this:

W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Ideas?

Thanks so much for the help and patience!

Best,
Lisa

---

### Post by matt_symes on 2011-11-11
Hi

Please post the output of

```
cat -n /etc/apt/sources.list
```

Kind regards

---

### Post by llmunro on 2011-11-11
Thank you!  Here it is! 


lisa@lisa-Samsung:~$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
     2    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3    # newer versions of the distribution.
     4    
     5    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
     6    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
    11    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
    17    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
    18    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
    19    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
    27    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
    28    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
    29    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
    30    
    31    ## Uncomment the following two lines to add software from the 'backports'
    32    ## repository.
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    39    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
    46    deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
    47    
    48    ## This software is not part of Ubuntu, but is offered by third-party
    49    ## developers who want to ship their latest software.
    50    deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
    51    deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
    52    
    53    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
    54    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security main restricted
    55    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security universe
    56    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security universe
    57    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security multiverse
    58    deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-security multiverse
    59    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-proposed restricted main multiverse universe
lisa@lisa-Samsung:~$ 

Best,
Lisa

---

### Post by matt_symes on 2011-11-11
Hi

Hmmm. I can see nothing wrong with your sources.list file so i don't think the problem is there.

Open a terminal and type

```
sudo rm -rf /var/lib/apt/lists/*
```

(This will clear your apt lists cache)

Then type

```
sudo mkdir /var/lib/apt/lists/partial
```

(this will recreate you partial directory)

Finally..

```
sudo apt-get update
```

(to refresh your apt lists cache again)

Post back any errors.

Kind regards

---

### Post by llmunro on 2011-11-11
Hello! 

If its not one thing, its another.

The last error appears to have been resolved and another has appeared:

sudo apt-get update

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I am sorry to have to keep asking for help, but these errors are leaving me lost!  Thanks again for all of the assistance!

Best,
Lisa

---

### Post by matt_symes on 2011-11-11
> **llmunro said:**
> Hello! 

If its not one thing, its another.

The last error appears to have been resolved and another has appeared:

sudo apt-get update

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I am sorry to have to keep asking for help, but these errors are leaving me lost!  Thanks again for all of the assistance!

Best,
Lisa

Don't worry :) We are getting there. 

Here is a tutorial that has been doing the rounds on the Internet in one form or another.

[http://www.hbyconsultancy.com/blog/ubuntu-howto-fix-repository-signature-verification-issues.html](http://www.hbyconsultancy.com/blog/ubuntu-howto-fix-repository-signature-verification-issues.html)

I have not used it as i have not had this problem. I'm not sure why so many apt-get cleans are needed either :confused: and i cannot test it as .... i have not had the problem.

Never the less, it is meant to work. Give it a go. Any questions the post back.

Kind regards

---

### Post by llmunro on 2011-11-11
Double huzzah!

Following the instructions in this tutorial seem to have worked and I just tried updating via sudo apt-get update without a single error!

Thanks to all for all the help!!! :D

Best,
Lisa

---

### Post by llmunro on 2011-11-12
Bah.

I thought I had this all figured out and then I get this:

W:Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/glasen/intel-driver/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I tried to fix this using the commands that I'd learned earlier in this thread, but I apparently keep doing it wrong, as I keep getting this error.

Suggestions?
Thanks.
Lisa

---

### Post by matt_symes on 2011-11-14
Hi

Open a terminal and type

```
grep glasen /etc/apt/sources.list.d/*
```

Post the results back here.

Kind regards

---

### Post by llmunro on 2011-11-14
matt_symes, you have the patience of a saint!


lisa@lisa-Samsung:~$ grep glasen /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/glasen-intel-driver-oneiric.list:deb [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) oneiric main
/etc/apt/sources.list.d/glasen-intel-driver-oneiric.list:deb-src [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) oneiric main
lisa@lisa-Samsung:~$ 

I promise, promise, promise that once I get this straightened out, I am no longer messing with PPAs! :)

Thanks much.
Lisa

---

### Post by matt_symes on 2011-11-14
Hi

> I promise, promise, promise that once I get this straightened out, I am no longer messing with PPAs! 

:P

```
sudo rm /etc/apt/sources.list.d/glasen-intel-driver*
```

Kind regards

---

### Post by llmunro on 2011-11-14
Okay, here's the latest!

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_oneiric-updates_restricted_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


As usual, I am lost! :)

---

### Post by matt_symes on 2011-11-14
Hi

Follow the instructions in the link in post #14 again.

Kind regards

---

### Post by llmunro on 2011-11-14
Hi matt_symes,

I may have really done it this time.

I went back to the tutorial that you linked to in post #14 and here's what I get:

lisa@lisa-Samsung:~$ sudo apt-get clean
[sudo] password for lisa: 
lisa@lisa-Samsung:~$ cd /var/lib/apt
lisa@lisa-Samsung:/var/lib/apt$ sudo mv lists lists.old
mv: cannot move `lists' to `lists.old/lists': Directory not empty
lisa@lisa-Samsung:/var/lib/apt$ ^C
lisa@lisa-Samsung:/var/lib/apt$ 

I don't really know what it means that the directory isn't empty.

Once again, your patience is mightily appreciated!

Lisa

---

### Post by matt_symes on 2011-11-15
Hi

You are getting that error because the directory lists.old already exists. It exists from the previous time you followedthe stepsin post 14.

Delete the directory.

```
sudo rm -rf /var/lib/apt/lists.old
```Then run the steps post #14 again.

Kind regards

---

### Post by llmunro on 2011-11-16
matt_symes,

I think I've got it all back together again! Updating without problems.

No more PPAs for me! :)

Thanks for your enduring patience and all the help,

Best,
Lisa

---


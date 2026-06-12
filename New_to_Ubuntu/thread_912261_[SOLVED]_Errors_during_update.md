---
title: "[SOLVED] Errors during update"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by Myros00 on 2008-09-06
Hello, guys.

I always get the following error during update:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ae.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://ae.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ae.archive.canonical.com'

W: Failed to fetch [http://ae.archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://ae.archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'ae.archive.canonical.com'

W: Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://ae.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


I must've done something wrong :(

Any ideas on what could be done?

Thanks!

---

### Post by kansasnoob on 2008-09-06
> **Myros00 said:**
> Hello, guys.

I always get the following error during update:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://ae.archive.ubuntu.com](http://ae.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://ae.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://ae.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ae.archive.canonical.com'

W: Failed to fetch [http://ae.archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://ae.archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'ae.archive.canonical.com'

W: Failed to fetch [http://ae.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://ae.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


I must've done something wrong :(

Any ideas on what could be done?

Thanks!

Let's begin by looking at Software Sources. Go to System > Administration > Software Sources:

[ATTACH]84309[/ATTACH]

[ATTACH]84310[/ATTACH]

NOTE: That only deals with the Ubuntu Software tab and the Updates tab. No need to worry about anything else just yet.

---

### Post by kansasnoob on 2008-09-06
Oh, also go to System > Administration > Synaptic Package Manager and click on "Reload"! I'd also click on "Mark All Upgrades", but I'd read what they are before continuing ........... just so you know in case something breaks.

---

### Post by Myros00 on 2008-09-06
thank you for the speedy reply, Kansasnoob.

The pictures are attached. I tried the synaptic manager, but I received the same error as listed above.

---

### Post by Myros00 on 2008-09-08
*Bump*?

---

### Post by Myros00 on 2008-09-10
*Bump....*

---

### Post by jemate18 on 2008-09-10
> **Myros00 said:**
> *Bump....*

This is what I do:
1. Open a terminal 
> Applications -> Accessories -> Terminal)
2. type 
```
sudo gksu gedit /etc/apt/sources.list
```
3. Uncomment the repositories by removing the "#"
> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
4. It will be
> ## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
5. Find all those #deb and #deb-src and remove/erase the # to be able to uncomment it, except for the entry
```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
``` If you uncomment this, the update will look for your CD Installer before connecting to the internet.

6. After editing it, click SAVE
7. Type
```
sudo apt-get update
```
8. Enjoy

---

### Post by Myros00 on 2008-09-10
Thank you for your reply, Jemate18.

The sources are already uncommented.

Maybe it would help if you take a look at my sources.list file

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy restricted multiverse universe main
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

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

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://ae.archive.canonical.com/ubuntu](http://ae.archive.canonical.com/ubuntu) hardy partner
deb-src [http://ae.archive.canonical.com/ubuntu](http://ae.archive.canonical.com/ubuntu) hardy partner

deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://ae.archive.ubuntu.com/ubuntu/](http://ae.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe

My main server was for the United Arab Emirates as well... However, running a google search said switching servers is a solution, that didnt work, I ended up getting Error 503.

So, since the United Arab Emirates server isn't in the drop-down list in "Software Sources", I edited the sources.list file links by making it "ae.archive" again...

I dunno where did I bomb, but the error is always caused by that accursed translation file!!!

> Reading package lists... Done
W: Failed to fetch [http://ae.archive.canonical.com/ubuntu/dists/hardy/Release.gpg](http://ae.archive.canonical.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ae.archive.canonical.com'

W: Failed to fetch [http://ae.archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2](http://ae.archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2)  Could not resolve 'ae.archive.canonical.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


---

### Post by jemate18 on 2008-09-10
> **Myros00 said:**
> Thank you for your reply, Jemate18.

The sources are already uncommented.

Maybe it would help if you take a look at my sources.list file



My main server was for the United Arab Emirates as well... However, running a google search said switching servers is a solution, that didnt work, I ended up getting Error 503.

So, since the United Arab Emirates server isn't in the drop-down list in "Software Sources", I edited the sources.list file links by making it "ae.archive" again...

I dunno where did I bomb, but the error is always caused by that accursed translation file!!!

Did you tried removing the "ae" in the [http://ae.archive?](http://ae.archive?) what happens?

---

### Post by Myros00 on 2008-09-13
Hello, Jemate.

Sorry for the very late reply... had to spend some time on windows.. (and I stress on the 'had to'). And thank you for your patience :KS

Anyway, I did remove the 'ae' from only two links, which are:

deb [http://ae.archive.canonical.com/ubuntu](http://ae.archive.canonical.com/ubuntu) hardy partner
deb-src [http://ae.archive.canonical.com/ubuntu](http://ae.archive.canonical.com/ubuntu) hardy partner

I do remember removing the ae from all the links, but I cant quite remember how it turned out, my guess is it wasn't good :P

And I think the updates are running fine now (just installed 8 new packages). However, I DO occasionally get the signature error message. But, the bright side is that its not as frequent. :)

---

### Post by Myros00 on 2008-09-16
Damn, I guess this is not really solved...

Running "sudo apt-get update" now, found 670 KB worth of security updates, but I'm receiving this error:

> "W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems"

Removing the "ae" in front of the links leads to the same results, it seems...

Can anyone help?

---

### Post by kiwidoc66 on 2008-09-29
Hmmm
Similarly, I was getting
 
GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

after running apt-get update

I have stopped it by commenting out the 

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

lines in /etc/apt/sources.list

#deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

---


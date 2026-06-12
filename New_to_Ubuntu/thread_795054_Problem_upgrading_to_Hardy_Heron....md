---
title: "Problem upgrading to Hardy Heron...?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by jwkungfu on 2008-05-15
Hi all,
I have tried a couple of times to upgrade to Hardy Heron and I keep getting the following error message...

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_AU.bz2](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_AU.bz2) 
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_AU.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_AU.bz2) 

I religiously update as soon as they show up, so I'm confused as to why I am having this problem...?

Thanks in advance for any help!

Cheers!

Ubuntu/Linux RULES!!

jw.

---

### Post by Cypher on 2008-05-15
Looks like the AU server is either slow or isn't up to date with all the latest Hardy files. The security server is missing the AU translations..so perhaps it takes a little longer for the new release to get to all the other servers?

You might find it easier to download the Alternate CD for Hardy Heron and update that way..

---

### Post by jwkungfu on 2008-05-15
Cheers! Thanks for that. I'll have a bash after downloading the CD as you suggest... wish me luck!

---

### Post by Cypher on 2008-05-15
Once you burn the Alternate CD, when you pop it into the CD the desktop will automatically pop up a dialog box asking if you want to upgrade. Say yes, go grab a Fosters and when you return the upgrade will be done. ;)

---

### Post by jwkungfu on 2008-05-15
I prefere a Coopers Sparkling Ale to Fosters (CUB beer is pants)....  ;o)

When you say the Alternate CD, do you mean there is a different CD to download than what Ubuntu offers on it's front page...?
I'm in the process of downloading a 699MB file ubuntu-8.04-desktop-i386.iso
 
Thanks for the help!

---

### Post by jwkungfu on 2008-05-15
> **Cypher said:**
> Once you burn the Alternate CD, when you pop it into the CD the desktop will automatically pop up a dialog box asking if you want to upgrade. Say yes, go grab a Fosters and when you return the upgrade will be done. ;)

I prefere a Coopers Sparkling Ale to Fosters (CUB beer is pants).... ;o)

When you say the Alternate CD, do you mean there is a different CD to download than what Ubuntu offers on it's front page...?
I'm in the process of downloading a 699MB file ubuntu-8.04-desktop-i386.iso

Thanks for the help!

---

### Post by Cypher on 2008-05-15
Fosters is the only Australian beer I know..;)

The Alternate CD can be downloaded from the same [Ubuntu page]("http://www.ubuntu.com/getubuntu/download") you are getting the Desktop CD from. After choosing the closest "Location near you", there is a checkbox and string that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer." So click on that checkbox and then start the download and you'll begin to download the file **ubuntu-8.04-alternate-i386.iso**.

The Desktop CD you are downloading right now is the LiveCD and it is meant for new-installation and will not upgrade your existing installation..

---

### Post by jwkungfu on 2008-05-15
> **Cypher said:**
> Fosters is the only Australian beer I know..;)

The Alternate CD can be downloaded from the same [Ubuntu page]("http://www.ubuntu.com/getubuntu/download") you are getting the Desktop CD from. After choosing the closest "Location near you", there is a checkbox and string that says "Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer." So click on that checkbox and then start the download and you'll begin to download the file **ubuntu-8.04-alternate-i386.iso**.

The Desktop CD you are downloading right now is the LiveCD and it is meant for new-installation and will not upgrade your existing installation..

Many thanks for that, I've stopped the original download and I've started the alternate one that you have suggested...
My internet connection is very slow, so I'm going to bed and let it download while I snooze....

Night night!

---


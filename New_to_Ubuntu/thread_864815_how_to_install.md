---
title: "how to install"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-07-20
hi all,

  i have downloaded clamav0.93.3 (.tar.gz) file from clam site. i dont know what i have to do to proceed the installation of clamav. i also dont know which one file has to click and proceed installation. I am 40 days old to ubuntu linux. before that i was a windows user. please reply and thanks in advance.

---

### Post by mgranet on 2008-07-20
Unless you are scanning Samba shares, there is no need for ClamAV. Without downloading and seeing for myself, you probably have to extract the archive to your home directory, and then execute the binary.

EDIT: Please post the contents of your extracted archive.

---

### Post by |{urse on 2008-07-20
that's not entirely true, there are a few (30 or so) linux viruses/malware/trojan/worms and clamav *Does* scan for them as well as windows virii. 

> sudo apt-get install clamav

that said, you will probably never see a linux virus. So depending on how paranoid you are, scan at will.

---

### Post by sharks on 2008-07-20
I think u should install it via synaptic(package manager)

---

### Post by sharks on 2008-07-20
if u have windows , then u should(not must) install a antivirus.

---

### Post by |{urse on 2008-07-20
sorry to double post but the other point of running a Linux AV is so when you pass along files and documents collected online to friends who are using windows, you aren't passing along any viruses in the process. Because that's just rude.

---

### Post by Canis familiaris on 2008-07-20
Applications->Add/Remove

Search for ClamAV.
Mark the checkbox and install.

For details about how to install programs in Ubuntu. Look at my signature.
Remember Linux is not Windows.

---

### Post by sharks on 2008-07-20
> Remember Linux is not Windows.

yes. Linux is better than Window$

---

### Post by Canis familiaris on 2008-07-20
> **sharks said:**
> yes. Linux is better than Window$

For us, and maybe most but not for everybody. ;)

---

### Post by mgranet on 2008-07-20
> **|{urse said:**
> sorry to double post but the other point of running a Linux AV is so when you pass along files and documents collected online to friends who are using windows, you aren't passing along any viruses in the process. Because that's just rude.

There may be 30 or so, but there are only a small handful actually in the wild. And all of those are virtually harmless. Yes, you could scan, but it's not even worth the RAM it uses. 
As for passing Windows viri  along to friends; yes. I didn't think of that one. Still a low chance of infection (Windows system probably has AV too).

---

### Post by |{urse on 2008-07-20
[http://en.wikipedia.org/wiki/OSF.8759](http://en.wikipedia.org/wiki/OSF.8759) <--- learn

Actually a bunch of them are just backdoors, then poof someone else is at the wheel. Trust me lol I've cleaned up many a fedora webserver left in shambles.

---

### Post by mailtwogopal on 2008-07-20
hi all,

 i installed clamav thru command prompt itself. when i try to check updates, in command prompt i typed "sudo freshclam" i get the following o/p:

```

sudo freshclam
ClamAV update process started at Sun Jul 20 12:42:09 2008
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.92.1 Recommended version: 0.93.3
DON'T PANIC! Read http://www.clamav.net/support/faq
main.inc is up to date (version: 47, sigs: 312304, f-level: 31, builder: sven)
daily.inc is up to date (version: 7760, sigs: 48697, f-level: 33, builder: ccordes)

```

what to do with this? i visited the  site mentioned in it and i found nothing. please help.

---

### Post by sharks on 2008-07-20
type sudo apt-get update and see whether u have got any updates for clamav.

---

### Post by mailtwogopal on 2008-07-20
hi,

 i tried the sudo apt-get update and i got following o/p:

```

Hit http://in.archive.ubuntu.com hardy Release.gpg                         
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN              
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN         
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN           
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN         
Hit http://in.archive.ubuntu.com hardy-updates Release.gpg                  
Ign http://in.archive.ubuntu.com hardy-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/restricted Translation-en_IN
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/universe Translation-en_IN
Ign http://in.archive.ubuntu.com hardy-updates/multiverse Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release 
Hit http://in.archive.ubuntu.com hardy-updates Release              
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN
Hit http://security.ubuntu.com hardy-security Release               
Hit http://in.archive.ubuntu.com hardy/main Packages
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://in.archive.ubuntu.com hardy/restricted Packages
Hit http://in.archive.ubuntu.com hardy/main Sources
Hit http://in.archive.ubuntu.com hardy/restricted Sources
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://in.archive.ubuntu.com hardy/universe Packages
Hit http://in.archive.ubuntu.com hardy/universe Sources
Hit http://in.archive.ubuntu.com hardy/multiverse Packages
Hit http://in.archive.ubuntu.com hardy/multiverse Sources
Hit http://in.archive.ubuntu.com hardy-updates/main Packages
Hit http://in.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://in.archive.ubuntu.com hardy-updates/main Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://in.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://in.archive.ubuntu.com hardy-updates/universe Packages
Hit http://in.archive.ubuntu.com hardy-updates/universe Sources
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://in.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done

```

i dont find any updates for clamav from here. what to do?

---

### Post by mgranet on 2008-07-20
> **|{urse said:**
> [http://en.wikipedia.org/wiki/OSF.8759](http://en.wikipedia.org/wiki/OSF.8759) <--- learn

Actually a bunch of them are just backdoors, then poof someone else is at the wheel. Trust me lol I've cleaned up many a fedora webserver left in shambles.

Which must be ran as root...And it only infects 200 files. And it more commonly affects servers. And it's still a very low threat. I don't have to "trust you lol". This stuff used to be my bread and butter. It's simply not a real threat.
EDIT:
Also, rootkits are a far larger threat to the modern Linux system than a 6 year old (and probably patched out) virus. To the OP: If you are truly concerned with the security of the system, also (in addition to Clam) install rkhunter, tripwire and Bastille. No sense in half-assing it.

---


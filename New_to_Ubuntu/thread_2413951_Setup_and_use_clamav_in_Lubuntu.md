---
title: "Setup and use clamav in Lubuntu"
date: 2019-03-04
forum: New to Ubuntu
---

### Post by sed_faster on 2019-03-04
Hello folks,

I am a newbie in this system :p I am trying scan my computer through clamav. I have this system/flavor:
```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.2 LTS
Release:    18.04
Codename:    bionic
$ uname -a
Linux user 4.15.0-22-generic #24-Ubuntu SMP Wed May 16 12:15:17 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

After install, trough apt-get, the clamav in my system I googled articles about this software on internet. I found many articles and I don know which recipe I should use. Through this article: [https://askubuntu.com/questions/909273/clamav-error-var-log-clamav-freshclam-log-is-locked-by-another-process](https://askubuntu.com/questions/909273/clamav-error-var-log-clamav-freshclam-log-is-locked-by-another-process)
I receive this result in my terminal:
```

$ sudo freshclam
Mon Mar  4 10:37:56 2019 -> ClamAV update process started at Mon Mar  4 10:37:56 2019
Mon Mar  4 10:37:56 2019 -> ^Your ClamAV installation is OUTDATED!
Mon Mar  4 10:37:56 2019 -> ^Local version: 0.100.2 Recommended version: 0.101.1
Mon Mar  4 10:37:56 2019 -> DON'T PANIC! Read https://www.clamav.net/documents/upgrading-clamav
Mon Mar  4 10:37:56 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Mon Mar  4 10:37:56 2019 -> daily.cvd is up to date (version: 25377, sigs: 2267948, f-level: 63, builder: raynman)
Mon Mar  4 10:37:56 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)

```
But when I goes to the page "https://www.clamav.net/documents/upgrading-clamav" I don't know which method and steps I should use.

The purpose of this search which use the clamav correctly.
Thanks

---

### Post by webaake on 2019-03-04
As an Ubuntu user I think you should "wait" as the linked instructions says. The other alternatives for upgrading the application (not the virus definitions) are too complicated and not worth the effort IMO. It involves compiling from source code and the learning curve is very steep.

Concerning using Clamav I think updating virus definitions periodically, as you have done already, is well enough. 

I trust the normal repos will be updated with Clamav when need be, and you'll get the update the normal way. So, no worries.

EDIT; found this; "Backports
The Ubuntu backports repository will contain the newest clamav version that has been at least lightly tested to work with that version. These packages can be installed by enabling the backports repository on your system."

So by enabling the Backport repos you'll get the latest app version. Source: [https://www.clamav.net/downloads#otherversions](https://www.clamav.net/downloads#otherversions)

---

### Post by sed_faster on 2019-03-04
I use this command:
```

$ sudo clamscan -ir /

```
But I didn't received only print infected files, through parameter -i, just like manual says. I received the same report which I use a normal command:
```

----------- SCAN SUMMARY -----------
Known viruses: 6826807
Engine version: 0.100.2
Scanned directories: 48097
Scanned files: 248496
Infected files: 2
Total errors: 50678
Data scanned: 43026.91 MB
Data read: 101529.64 MB (ratio 0.42:1)
Time: 5580.723 sec (93 m 0 s)

```
What am I doing wrong?
Thanks

I am trying following this page: [https://www.clamav.net/downloads#otherversions](https://www.clamav.net/downloads#otherversions) but I receive this message:
```

$ sudo apt-get install libclamunrar6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libclamunrar6

```

But when I ran again sudo freshclam, I get this:
```

$ sudo freshclam
Mon Mar  4 14:58:08 2019 -> ClamAV update process started at Mon Mar  4 14:58:08 2019
Mon Mar  4 14:58:08 2019 -> ^Your ClamAV installation is OUTDATED!
Mon Mar  4 14:58:08 2019 -> ^Local version: 0.100.2 Recommended version: 0.101.1
Mon Mar  4 14:58:08 2019 -> DON'T PANIC! Read https://www.clamav.net/documents/upgrading-clamav
Mon Mar  4 14:58:08 2019 -> main.cvd is up to date (version: 58, sigs: 4566249, f-level: 60, builder: sigmgr)
Mon Mar  4 14:58:09 2019 -> Downloading daily-25378.cdiff [100%]
Mon Mar  4 14:58:12 2019 -> daily.cld updated (version: 25378, sigs: 2269257, f-level: 63, builder: raynman)
Mon Mar  4 14:58:12 2019 -> *Can't query daily.25378.93.1.0.6810DB54.ping.clamav.net
Mon Mar  4 14:58:12 2019 -> bytecode.cvd is up to date (version: 328, sigs: 94, f-level: 63, builder: neo)
Mon Mar  4 14:58:14 2019 -> Database updated (6835600 signatures) from db.local.clamav.net (IP: 104.16.219.84)
Mon Mar  4 14:58:14 2019 -> Clamd successfully notified about the update.
$ clamscan -V
ClamAV 0.100.2/25378/Mon Mar  4 10:47:26 2019

```

---

### Post by webaake on 2019-03-04
libclamunrar7 try that instead of libclamunrar6

---

### Post by webaake on 2019-03-04
By the way here's how to activate the Backports repo:

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

Might be it's needed for that libclamunrar7

---

### Post by webaake on 2019-03-05
I suggest that you keep this thread for installation/upgrade and create another thread for usage of clamav.

(I can can give you a hint: clamav -h will show you all parameters for usage)

---

### Post by monkeybrain20122 on 2019-03-05
You don't need AV on linux , clamav detects Windows virus, and is garbage anyway so I won't waste my time.

---

### Post by oldrocker99 on 2019-03-05
> **monkeybrain20122 said:**
> You don't need AV on linux , clamav detects Windows virus, and is garbage anyway so I won't waste my time.

Exactly what I was going to say. It is useful, I suppose, for servers which handle Windows programs.

---


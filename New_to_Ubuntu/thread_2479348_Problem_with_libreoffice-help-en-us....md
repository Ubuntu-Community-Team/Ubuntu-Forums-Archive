---
title: "Problem with libreoffice-help-en-us..."
date: 2022-09-22
forum: New to Ubuntu
---

### Post by yatski on 2022-09-22
....While I tried to run Software Updater to install it, I got this error:
 ```
Package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f
Transaction failed: The package system is broken
 The following packages have unmet dependencies:

libreoffice-help-en-us: Depends: libreoffice-l10n-en-us but it is a virtual package
                        Depends: libreoffice-help-common (= 1:7.3.5-0ubuntu0.22.04.1) but 1:7.3.6-0ubuntu0.22.04.1 is installed
```

Next I ran "apt-get install -f"

```
sudo apt-get install -f
[sudo] password for heta: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool thermald
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libreoffice-help-en-us
Suggested packages:
  firefox | firefox-esr | epiphany-browser | konqueror | chromium-browser
  | chromium
The following packages will be upgraded:
  libreoffice-help-en-us
1 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
Need to get 0 B/1&#8239;646 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 310176 files and directories currently installed.)
Preparing to unpack .../libreoffice-help-en-us_1%3a7.3.6-0ubuntu0.22.04.1_all.deb ...
Unpacking libreoffice-help-en-us (1:7.3.6-0ubuntu0.22.04.1) over (1:7.3.5-0ubuntu0.22.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libreoffice-help-en-us_1%3a7.3.6-0ubuntu0.22.04.1_all.deb (--unpack):
 unable to open '/usr/share/libreoffice/help/en-US/text/swriter/main0220.html.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-help-en-us_1%3a7.3.6-0ubuntu0.22.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

.. Not that I would use help, but that "an error occured"-notification is bothering me a bit..
Also, it seems I can't download other updates because this error.

---

### Post by ActionParsnip on 2022-09-22
What is the output of
```

apt-cache policy libreoffice-l10n-en-us libreoffice-help-common

```

Thanks

---

### Post by yatski on 2022-09-22
> **ActionParsnip said:**
> What is the output of
```

apt-cache policy libreoffice-l10n-en-us libreoffice-help-common

```

Thanks

This:

```
heta@heta-vaio:~$ apt-cache policy libreoffice-l10n-en-us libreoffice-help-common
libreoffice-l10n-en-us:
  Installed: (none)
  Candidate: (none)
  Version table:
libreoffice-help-common:
  Installed: 1:7.3.6-0ubuntu0.22.04.1
  Candidate: 1:7.3.6-0ubuntu0.22.04.1
  Version table:
 *** 1:7.3.6-0ubuntu0.22.04.1 500
        500 http://fi.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://fi.archive.ubuntu.com/ubuntu jammy-updates/main i386 Packages
        100 /var/lib/dpkg/status
     1:7.3.2-0ubuntu2 500
        500 http://fi.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        500 http://fi.archive.ubuntu.com/ubuntu jammy/main i386 Packages
```

---

### Post by ActionParsnip on 2022-09-22
Are you using Sophos antivirus by any chance?

---

### Post by yatski on 2022-09-22
> **ActionParsnip said:**
> Are you using Sophos antivirus by any chance?

Yes, I still have it, but I have disabled on-access scanning.
Edit: Huh, it was "on" after all. I vividly remember turning it "off". :confused:

I'm not sure if "libreoffice-help-en-us" was installed in partial upgrade I ran.

---


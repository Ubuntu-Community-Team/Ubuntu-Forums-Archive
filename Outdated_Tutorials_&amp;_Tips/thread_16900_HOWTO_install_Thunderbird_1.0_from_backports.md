---
title: "HOWTO: install Thunderbird 1.0 from backports"
date: 2005-02-24
forum: Outdated Tutorials &amp; Tips
---

### Post by PaDV on 2005-02-24
1. ACTIVATE THE WARTY BACKPORTS REPOSITORY
[list]
[*]sudo gedit /etc/apt/sources.list
[*]Add the following line:
```
deb http://backports.ubuntuforums.org/backports warty-backports main
```
[*]sudo apt-get update
[/list]

2. sudo apt-get install mozilla-thunderbird

3. INSTALL A LANGUAGE PACK FOR YOUR LANGUAGE (SKIP FOR ENGLISH)
[list]
[*]The language pack for thunderbird 1.0 is not available from the backports project but can be downloaded from debian testing at the following url: [http://packages.debian.org/cgi-bin/search_packages.pl?keywords=mozilla-thunderbird-locale&searchon=names&subword=1&version=testing&release=all](http://packages.debian.org/cgi-bin/search_packages.pl?keywords=mozilla-thunderbird-locale&searchon=names&subword=1&version=testing&release=all)
[*]download the package "mozilla-thunderbird-locale-xx" to eg. your home directory (click the "all" button), xx is your language code.
[*]dpkg -i ~/mozilla-thunderbird-locale-xx_1.0.debian1-1_all.deb
[/list]

4. MAKE THUNDERBIRD YOUR DEFAULT MAIL CLIENT
To make sure thunderbird opens instead of evolution when clicking mailto urls in eg. firefox you have to make thunderbird the default mail client.
[list]
[*]Go to "Computer > Desktop Preferences > Default Applications" or similar in your language.
[*]Go to E-mail program and choose custom program.
[*]Enter the following command: mozilla-thunderbird -compose %s
[/list]

---


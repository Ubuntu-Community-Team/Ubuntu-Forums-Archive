---
title: "Installation Help - OpenAstro"
date: 2012-09-16
forum: New to Ubuntu
---

### Post by michaelas on 2012-09-16
Hi
I am a Linux Newbie. I just installed Ubuntu v 12.04.1, having tried out Suse Linux back in 2008. Currently using Windows 7, and wanting to get away from it.

I am trying to install **Open Astro v 1.1.25**  [http://www.openastro.org/?Download](http://www.openastro.org/?Download)
I have managed to download the software, as the file is in the Software Center, but am unclear about how to install it.
When I tried opening through the Ubuntu Software Center (double click on the file) I get a page describing the **openastro **features, with the following message:
[I][B]Dependency is not satisfiable: python 2.6
ERROR
[/B][/I]
I installed Oneiric I-386, because I wasn't sure which one, only that Oneiric represented the latest version on that download page. I have an AMD processor, but it is not 64 (32 I think). Anyway, I went to the Terminal and typed in the following commands listed at the bottom of the download page (see openastro link above):

[B]wget [https://launchpad.net/~pellesimon/+archive/+files/openastro.org_1.1.25.orig.tar.gz](https://launchpad.net/~pellesimon/+archive/+files/openastro.org_1.1.25.orig.tar.gz)

tar -xzf openastro.org_1.1.25.orig.tar.gz[/B] [B]

cd openastro.org-1.1.25.orig[/B] [B]

sudo ./setup.py install[/B] 

It seemed to download everything fine, and then I found the file on the software page when I searched for it, and it was also in my dash folder. But then I got the error message.

Is Python the problem?

Anyone know where I can go from here?
Thanks for your help.

M :confused:

---

### Post by apienk01 on 2012-11-14
The Oneiric package has broken dependencies that have to be corrected for the .deb to install.

1. Download the Oneiric installation package for your system architecture (32-bit or 64-bit) from [OpenAstro website]("http://www.openastro.org/?Download"). You can check the architecture of your system by typing in the terminal window:

```
uname -i
```

2. Unpack the file (right click, select unpack).

3. In the unpacked folder navigate to 'DEBIAN' and find the file 'control'. Double-click it to edit.

4. From the line beginning with 'Depends:' delete 'python2.6,'. Save and exit.

5. In the unpacked folder navigate to 'usr/bin' and find the file 'openastro.py'. Double-click and select edit.

6. In the first line change '/usr/bin/python2.6' to '/usr/bin/python'. Save and exit.

7. Re-pack the deb package by opening a terminal window, changing dir to where you saved the .deb (e.g. Desktop) and typing:

```
dpkg-deb -b openastro.org_1.1.25-0ubuntu1~oneiric_amd64
```

8. If everything went well just install the package by double-clicking on it.

Enjoy!

---


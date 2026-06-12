---
title: "What's the difference between apt-get and aptitude?"
date: 2008-05-17
forum: Philippine Team
---

### Post by SHENGTON on 2008-05-17
Hello again Ubuntu Experts!

As stated above:
1. What's the difference between apt-get and aptitude?

Thanks and God bless!

---

### Post by loell on 2008-05-17
before there was but not much now.  i personally prefer apt-get just because many old howto's still refer to it.

---

### Post by 505 on 2008-05-17
I believe aptitude can do a bit more. If you run it without arguments you get a graphic interface in the terminal. With the arguments "aptitude show package" or "aptitude search string" you can search packages. And most importantly, aptitude removes dependencies when no longer needed when that program was installed with aptitude.

"Both aptitude and apt-get will install kword and its dependencies (kspread, kword-data, and libwv2-1c2), but only aptitude will actually remove the dependencies when kword is removed (and only if no other packages depend on those dependencies)." [source](http://www.psychocats.net/ubuntu/aptitude)

For this reason I prefer aptitude

---

### Post by Saint Angeles on 2008-05-17
> **505 said:**
> I believe aptitude can do a bit more. If you run it without arguments you get a graphic interface in the terminal. With the arguments "aptitude show package" or "aptitude search string" you can search packages. And most importantly, aptitude removes dependencies when no longer needed when that program was installed with aptitude.

"Both aptitude and apt-get will install kword and its dependencies (kspread, kword-data, and libwv2-1c2), but only aptitude will actually remove the dependencies when kword is removed (and only if no other packages depend on those dependencies)." [source]("http://www.psychocats.net/ubuntu/aptitude")

For this reason I prefer aptitude
doesn't apt-get autoremove and autoclean take care of the dependency thing?

---

### Post by SHENGTON on 2008-05-17
What's kword?

---

### Post by pendletone on 2008-05-17
> **SHENGTON said:**
> What's kword?

KWord is a word processing and desktop publishing application. It is a package that is a part of the KDE Office Suite.

It has nothing to do with the difference between apt-get and aptitude. So you don't have to worry about it. :)

Nagkataon lang na na-mention nya (505) yung word na kword when he quoted it from [here]("http://www.psychocats.net/ubuntu/aptitude").

---

### Post by pmcastillo on 2008-05-17
^^

Kinuha nya kase yung explanation dito [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) (nakalimutan nya lang kumpletuhin). Ginamit lang nya yung kword as an explanation. Eto yung complete na gusto nyang sabihin:

> 
Below is the demonstrated difference, though, at least for Ubuntu 6.06 and earlier. The example displayed is the package kword, but it works the same for any package that has dependencies.


APTITUDE METHOD

> 
username@ubuntu:~$ sudo aptitude update && sudo aptitude install kword
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [27.0kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release [27.0kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [19.6kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [14.4kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [95.2kB]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [14B]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [3593B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [14B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [3762B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [14B]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [10.2kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [9006B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [14B]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [14B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [14B]
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Fetched 263kB in 2s (89.0kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
kspread kword-data libwv2-1c2
The following NEW packages will be installed:
kspread kword kword-data libwv2-1c2
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 6613kB of archives. After unpacking 18.9MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main kspread 1:1.5.0-0ubuntu9 [2276kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main libwv2-1c2 0.2.2-5 [225kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main kword-data 1:1.5.0-0ubuntu9 [1590kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main kword 1:1.5.0-0ubuntu9 [2522kB]
Fetched 6613kB in 45s (146kB/s)
Selecting previously deselected package kspread.
(Reading database ... 110852 files and directories currently installed.)
Unpacking kspread (from .../kspread_1%3a1.5.0-0ubuntu9_i386.deb) ...
Selecting previously deselected package libwv2-1c2.
Unpacking libwv2-1c2 (from .../libwv2-1c2_0.2.2-5_i386.deb) ...
Selecting previously deselected package kword-data.
Unpacking kword-data (from .../kword-data_1%3a1.5.0-0ubuntu9_all.deb) ...
Selecting previously deselected package kword.
Unpacking kword (from .../kword_1%3a1.5.0-0ubuntu9_i386.deb) ...
Setting up kspread (1.5.0-0ubuntu9) ...

Setting up libwv2-1c2 (0.2.2-5) ...

Setting up kword-data (1.5.0-0ubuntu9) ...

Setting up kword (1.5.0-0ubuntu9) ...

username@ubuntu:~$ sudo aptitude remove kword
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
kspread kword-data libwv2-1c2
The following packages will be REMOVED:
kword
0 packages upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 18.9MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 111678 files and directories currently installed.)
[b]Removing kword ...
Removing kspread ...
Removing kword-data ...
Removing libwv2-1c2 ...[/b]
username@ubuntu:~$



APT-GET METHOD

> 
username@ubuntu:~$ sudo apt-get update && sudo apt-get install kword
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Fetched 4B in 2s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
kspread kword-data libwv2-1c2
Suggested packages:
koffice-doc-html
The following NEW packages will be installed:
kspread kword kword-data libwv2-1c2
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/6613kB of archives.
After unpacking 18.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package kspread.
(Reading database ... 110852 files and directories currently installed.)
Unpacking kspread (from .../kspread_1%3a1.5.0-0ubuntu9_i386.deb) ...
Selecting previously deselected package libwv2-1c2.
Unpacking libwv2-1c2 (from .../libwv2-1c2_0.2.2-5_i386.deb) ...
Selecting previously deselected package kword-data.
Unpacking kword-data (from .../kword-data_1%3a1.5.0-0ubuntu9_all.deb) ...
Selecting previously deselected package kword.
Unpacking kword (from .../kword_1%3a1.5.0-0ubuntu9_i386.deb) ...
Setting up kspread (1.5.0-0ubuntu9) ...

Setting up libwv2-1c2 (0.2.2-5) ...

Setting up kword-data (1.5.0-0ubuntu9) ...

Setting up kword (1.5.0-0ubuntu9) ...

username@ubuntu:~$ sudo apt-get remove kword
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
kword
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 7000kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 111678 files and directories currently installed.)
**Removing kword ...**
username@ubuntu:~$ 



[SIZE="5"]Both aptitude and apt-get will install **kword** and its dependencies (kspread, kword-data, and libwv2-1c2), but only aptitude will actually remove the dependencies when **kword** is removed (and only if no other packages depend on those dependencies).[/SIZE]

---

### Post by loell on 2008-05-17
this could actually go into a long discussion, apt- tools * vs aptitude, in the end shengton might not be able to comprehend all this, its a newbie question which may only need a newbie answer

 we could just put it this way,    both apt-get and aptitude are front ends of **apt** and both of them can remove unneeded files when you uninstall programs.

now you may choose  from apt-get, aptitude , synaptic , etc   in installing and uninstalling programs.

---

### Post by pmcastillo on 2008-05-17
Yah, actually siguro ang isusunod nyang tanong ay... "Ano ang dependencies?" hehe...

---

### Post by SHENGTON on 2008-05-17
Ahh so both commands are the same but there's only one difference. Thanks sa lahat po!

@pmcastillo
ok itatanong ko nga Sir. Ano po yong "Dependencies"?

---

### Post by pmcastillo on 2008-05-17
Dependencies means Depend...

este....

Programs depend on other programs/components.... *phew! dinugo ako dun ah O_O *

Well kunwari, planong mong mag-install ng "AdBlock Plus". Well ang "AdBlock Plus" ay naka-depend sa Firefox... Ibig sabihin kailangan nakainstall muna yung Firefox bago mo mag-install yung "AdBlock Plus"... (malamang, paano mo magagamit ang "AdBlock Plus", kung wala ka ngang web browser)... and syempre ang Firefox naka-depend din sa ibang programs/components... and the cycle goes on...

Sinuper-simplified ko lang para ma-gets mo, actually pwede din naka-depend sa components hindi lang sa programs...


SA MUNDO NG CLOSED-SOURCE: "Akin eto! Hindi ko ipapahiram yung mga components ko sa kahit kaninong tao!" So ano ang result? Ang lalaki ng bawat programs kase COMPLETE package sila BAWAT ISANG PROGRAM.

SA MUNDO NG OPEN-SOURCE: "Ipapahiram ko etong mga components ko na eto, kung sino man ang may gusto sa components/programs ko sige lang gamitin nyo para lahat tayo nagbe-benefit?" So ano ang result? Maliliit ang mga sizes ng mga programs kase naghihiraman sila ng components... That's is where dependecies kicks in...


* kailangan na ata akong salinan ng dugo O_O *

---

### Post by pmcastillo on 2008-05-17
BTW, ang apt-get at aptitude at synaptic sila nag nagha-handle ng dependencies, kaya wala ka ng masyado pang i-intindihin...

---

### Post by yssida on 2008-05-17
> **pmcastillo said:**
> 
SA MUNDO NG CLOSED-SOURCE: "Akin eto! Hindi ko ipapahiram yung mga components ko sa kahit kaninong tao!" So ano ang result? Ang lalaki ng bawat programs kase COMPLETE package sila BAWAT ISANG PROGRAM.

SA MUNDO NG OPEN-SOURCE: "Ipapahiram ko etong mga components ko na eto, kung sino man ang may gusto sa components/programs ko sige lang gamitin nyo para lahat tayo nagbe-benefit?" So ano ang result? Maliliit ang mga sizes ng mga programs kase naghihiraman sila ng components... That's is where dependecies kicks in...


* kailangan na ata akong salinan ng dugo O_O *
Sa tingin ko po ay di ito entirely accurate. MAy mga applications na gumagamit ng Windows API, which means a lot of programs, that share resources. They do this through DLL. It is quite possible for a Windows user to go through a DLL Hell, just as in linux Dependency hell. I've never experienced it with my old XP install.

Just to clear things up a bit.:)

---

### Post by pmcastillo on 2008-05-17
Oo nga pala...

* dinudugo ako mag-explain LOL! *

---

### Post by SHENGTON on 2008-05-17
Thanks pm castillo and yssida!

---


---
title: "Ubuntu 12.04 Cant update or install"
date: 2014-01-12
forum: New to Ubuntu
---

### Post by larscvisser on 2014-01-12
Hi all,

I'm new to Ubuntu. I have installed Ubuntu 12.04 LTS but I'm encountering a lot of problems.

**First**, when I try to open the Ubuntu Software Center I get a error and the systems offers to repair the problem. Then a new error occurs reading:

Package Operation failed,

details:

installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'gir1.2-gtksource-3.0': Input/output error 
dpkg: dependency problems prevent configuration of ttf-unfonts-core: 
 ttf-unfonts-core depends on fonts-unfonts-core; however: 
  Package fonts-unfonts-core is not installed. 
dpkg: error processing ttf-unfonts-core (--configure): 
 dependency problems - leaving unconfigured

**Second**, Then I try to update my system in the Terminal by entering: apt-get upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 ttf-unfonts-core : Depends: fonts-unfonts-core but it is not installed
E: Unmet dependencies. Try using -f.

**Third**, I try apt-get -f install but then I get a new error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following package was automatically installed and is no longer required:
  libgrail1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fonts-unfonts-core
The following NEW packages will be installed:
  fonts-unfonts-core
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0 B/20.0 MB of archives.
After this operation, 34.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'gir1.2-gtksource-3.0': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)



It's driving me insane! It seems to me (correct me if I'm wrong...) that the problem is that fonts-unfonts-core, is not installed but I can't do anything about it since it&#347; not installed

---

### Post by joachim_altmann on 2014-01-12
Hi, 
I looked up the package information using synaptic package manager about fonts-unfonts-core and ttf-unfonts-core. fonts-unfonts-core is a set of korean TrueType fonts and tty-unfonts-core is a transitional package which can be safely removed (says the package information). Both do not seem to be really necessary to run your system if you do not need korean fonts.
Maybe you install via the software center the synaptic package manager and have a look for yourself. You can remove packages using this tool as well and its a bit simpler to use than pure command-line apt.
I have to admit that I do not know where the error comes from in the first place. Are there any other oddities?

---

### Post by deadflowr on 2014-01-12
As stated, try
```
sudo apt-get remove [COLOR=#000000]ttf-unfonts-core[/COLOR]
```
if you really need those fonts, then after you remove them try installing them again with
```
sudo apt-get install fonts-unfonts-core
```
or else if you don't need them, then don't reinstall them.

---

### Post by whitesmith on 2014-01-12
> **larscvisser said:**
> **Second**, Then I try to update my system in the Terminal by entering: apt-get upgradeYou are performing the operations in the wrong order. Try```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```See what this does for you.

[EDIT]Don't forget about **sudo**. These commands fail if used as an ordinary user. If you get a clean install -- that was your problem, wasn't it? -- then follow #deadflowr's advice about removing Korean fonts unless you need them.

---

### Post by larscvisser on 2014-01-13
Hi thank all for your replies. I still haven't made any progress.

Synaptic Package Manager can't be installed since the Software Center encounters a error.

I tried the suggested steps and ended with the sugested sudo apt-get remove ttf-unfonts-core, with the following result:

sudo apt-get remove ttf-unfonts-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libgrail1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  ttf-unfonts-core
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 27.6 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 50%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'gir1.2-gtksource-3.0': Input/output errorsudo apt-get remove ttf-unfonts-core

---

### Post by larscvisser on 2014-01-13
I had a clean install btw

---

### Post by deadflowr on 2014-01-13
This might help
[http://www.iasptk.com/ubuntu-debian/15825-ubuntu-fix-broken-package-best-solution](http://www.iasptk.com/ubuntu-debian/15825-ubuntu-fix-broken-package-best-solution)

It seems that the problem package is the [COLOR=#000000]gir1.2-gtksource-3.0 package.

[/COLOR]

---

### Post by larscvisser on 2014-01-13
Ok, I ran sudo nano var/lib/dpkg/status and located ttf-unfonts-core and it reads:

Status: deinstall ok unpacked
Priority: optional
Section: oldlibs
Installed-Size: 27
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecre: all
Source: fonts-unfonts-core
Version: 1.0.3.is.1.0.2-080608-5ubuntu1
Config-Version: 1.0.3.is.1.0.1-0ubuntu1
Depends: fonts-unfonts-core
Conffiles:
 /etc/defoma/hints/ttf-unfonts-core.hints cf6fed7c01b08fb46bb0a44e69481532 obsolete
Description: transitional dummy package
 This package is a dummy transitional package. It can be safely removed.
Homepage: [http://kldp.net/projects/unfonts](http://kldp.net/projects/unfonts)
Original-Maintainer: Debian Fonts Task Force <pkg-fonts-devel@lists.alioth.debian.org>


How do I remove it from the terminal?

---

### Post by deadflowr on 2014-01-13
The error problem is the [COLOR=#000000] [/COLOR][COLOR=#000000][COLOR=#000000]gir1.2-gtksource-3.0 package.
Open gedit as root or use the nano for terminal and remove the Entry for that package.

Besat practice would be to backup the status file first
[/COLOR][/COLOR]```
[COLOR=#000000]sudo cp /var/lib/dpkg/status /[/COLOR][COLOR=#000000]var/lib/dpkg/status.bak
``` 
I'd use gedit to edit the file.
```
gksu gedit /[/COLOR][COLOR=#000000]var/lib/dpkg/status [/COLOR][COLOR=#000000]
```
then use the search utility (it looks like a magnify glass/window thing)
locate the the Package entry for the [/COLOR][COLOR=#000000] [/COLOR][COLOR=#000000]gir1.2-gtksource-3.0 and delete the whole entry for that package.
(That would be everything fron it's PACKAGE: and stop before the next Packages PACKAGE:.
Then run the update command
```
sudo apt-get update
```
then the upgrade command
```
sudo apt-get upgrade
```
then see what happens, and if you can remove the ttf-unfonts package.

[/COLOR]

---

### Post by larscvisser on 2014-01-14
Thx deadflowr for your support,

I did the suggested steps and removed gir1.2-gtksource-3.0 and now I get

sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

Maybe the machine is just broken...

---

### Post by deadflowr on 2014-01-14
Try
```
sudo apt-get clean && sudo apt-get autoclean && sudo apt-get update
```
Then run the upgrade command.

Edit: if that doesn't work, maybe try uninstalling the gir1.2-gtksource-3-0 package.
```
sudo apt-get remove gir1.2-gtksource-3-0
```
or
```
sudo dpkg -r gir1.2-gtksource-3-0
```
then reinstall the package.

---

### Post by Impavidus on 2014-01-14
> **larscvisser said:**
> 
(...)
Do you want to continue [Y/n]? y
(Reading database ... 50%
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'gir1.2-gtksource-3.0': **[COLOR=#ff0000]Input/output error[/COLOR]**
sudo apt-get remove ttf-unfonts-core

> **larscvisser said:**
> 
Maybe the machine is just broken...

Something to keep in mind. Broken software can cause many errors, but rarely input/output errors. However, if you have a damaged hard drive the filesystem should be remounted read-only, which doesn't seem to happen.

---


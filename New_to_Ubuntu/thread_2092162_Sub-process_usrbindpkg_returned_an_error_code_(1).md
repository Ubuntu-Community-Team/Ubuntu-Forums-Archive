---
title: "Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by sangeetha821 on 2012-12-06
root@sang-desktop:/home/sang# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-mono (0.0.49) ...
/var/lib/dpkg/info/ubuntu-mono.postinst: 2: /var/lib/dpkg/info/ubuntu-mono.postinst: Syntax error: Unterminated quoted string
dpkg: error processing ubuntu-mono (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of light-themes:
 light-themes depends on ubuntu-mono; however:
  Package ubuntu-mono is not configured yet.

dpkg: error processing light-themes (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-artwork:
 ubuntu-artwork depends on light-themes; however:
  Package light-themes is not configured yet.

dpkg: error processing ubuntu-artwork (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 ubuntu-mono
 light-themes
 ubuntu-artwork
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ibjsb4 on 2012-12-07
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get -f install ; sudo dpkg --configure -a
```

See if that will fix it.  And welcome to the forum  :)

---

### Post by sangeetha821 on 2012-12-12
Still am getting same error only...

---

### Post by PinkFloyd102489 on 2012-12-12
```
sudo apt-get clean
```
```
sudo apt-get update
```

Looks like a package may have been broken and is still cached. This will clean out the apt cache and update.

---

### Post by sangeetha821 on 2012-12-12
I tried apt-get clean and update. But getting same error only.

---

### Post by Bashing-om on 2012-12-13
sangeetha821; Hi !

Let's delve a bit deeper and see if we can find out what is going on.
1. With the file manager inspect the status of ubuntu-mono in the file located:
 /var/lib/dpkg/status
2, Also with the file manager look at 
/var/lib/dpkg/info/ubuntu-mono.list  --it's a huge directory and will take a bit to load.

compare these listing to others similar, and if corrupted advise us, instructions pending for resolution.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by sangeetha821 on 2012-12-17
HI... 
I checked /var/lib/dpkg/status and  the status of ubuntu-mono 
Status: install ok half-configured

In  /var/lib/dpkg/info/ubuntu-mono.list ... i dunno what to check..

---

### Post by Bashing-om on 2012-12-17
sangeetha821;

/dpkg/status confirms there is a problem with the ubuntu-mono package.

OK, so what is the nature of the problem ? Open up the file "ubuntu-mono.list in a text editor ( I prefer gedit)
```
gksudo gedit /var/lib/dpkg/info/ubuntu-mono.list
```look over this file, looking for garbage (compared to another file in same directory), A single instance will corrupt the entire file.

 If the file is corrupt, delete it and reinstall "ubuntu-mono":
```
sudo apt-get install ubuntu-mono --reinstall
```[INDENT]what are you look'n like now ? <== BDQ

[/INDENT]

---

### Post by sangeetha821 on 2012-12-21
Hi...
Thanks a lot.. I reinstall ubuntu-mono. now  k..
ubuntu-mono status:
status install ok installed

---

### Post by Bashing-om on 2012-12-22
sangeetha821; Glad you got it working. Please mark this thread as solved.
Aides others seeking a solution
Aides us not having to look to solve a solved situation.

[INDENT]enjoy 'buntu <== BDQ

[/INDENT]

---


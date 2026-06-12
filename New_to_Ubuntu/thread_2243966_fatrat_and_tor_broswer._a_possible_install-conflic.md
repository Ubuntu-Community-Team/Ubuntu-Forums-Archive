---
title: "fatrat and tor broswer. a possible install-conflict?"
date: 2014-09-12
forum: New to Ubuntu
---

### Post by gnowair on 2014-09-12
i tried yesterday to install tor-browser and once apparently installed, i  clicked the "home" (ubuntu) symbol, typed into the "dash" to find the tor-browser, got it, tried to launch it, but it said something along the lines of "tor has unexpectedly exited, please retry... but it kept failing. (port forwarding needed? i'm not sure. googled for answers, but none were undersatandable to me, or the peoples queiries i read didnt provide a "solved".)

similarly, i did the same with fatrat later the same evening,it at first seemed it had installed fine,but it wouldnt appear when i looked for it in dash.

i tried with it a 2nd and 3rd time,and here is what happened:
 
```
"paul@paul-home:~$ apt-get install fatratE: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
paul@paul-home:~$ sudo su
[sudo] password for paul: 
root@paul-home:/home/paul#  apt-get install fatrat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 fatrat : Depends: libgloox11 but it is not going to be installed
          Depends: liblog4cpp5 but it is not going to be installed
          Depends: libpion-common-4.0 but it is not going to be installed
          Depends: libpion-net-4.0 but it is not going to be installed
          Depends: fatrat-data (= 1.2.0~beta2-0ubuntu8) but it is not going to be installed
 tor-geoipdb : Depends: tor (>= 0.2.4.23-2~trusty+1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@paul-home:/home/paul# E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
bash: syntax error near unexpected token `('
root@paul-home:/home/paul# E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
bash: syntax error near unexpected token `('
root@paul-home:/home/paul# paul@paul-home:~$ sudo su
paul@paul-home:~$: command not found
root@paul-home:/home/paul# [sudo] password for paul: 
[sudo]: command not found
root@paul-home:/home/paul# root@paul-home:/home/paul#  apt-get install fatrat
bash: root@paul-home:/home/paul#: No such file or directory
root@paul-home:/home/paul# Reading package lists... Done
Reading: command not found
root@paul-home:/home/paul# Building dependency tree       
Building: command not found
root@paul-home:/home/paul# Reading state information... Done
Reading: command not found
root@paul-home:/home/paul# You might want to run 'apt-get -f install' to correct these:
You: command not found
root@paul-home:/home/paul# The following packages have unmet dependencies.
No command 'The' found, did you mean:
 Command 'the' from package 'the' (universe)
The: command not found
root@paul-home:/home/paul#  fatrat : Depends: libgloox11 but it is not going to be installed
The program 'fatrat' is currently not installed. You can install it by typing:
apt-get install fatrat
root@paul-home:/home/paul#           Depends: liblog4cpp5 but it is not going to be installed
Depends:: command not found
root@paul-home:/home/paul#           Depends: libpion-common-4.0 but it is not going to be installed
Depends:: command not found
root@paul-home:/home/paul#           Depends: libpion-net-4.0 but it is not going to be installed
Depends:: command not found
root@paul-home:/home/paul#           Depends: fatrat-data (= 1.2.0~beta2-0ubuntu8) but it is not going to be installed
bash: syntax error near unexpected token `('
root@paul-home:/home/paul#  tor-geoipdb : Depends: tor (>= 0.2.4.23-2~trusty+1) but it is not going to be installed
bash: syntax error near unexpected token `('
root@paul-home:/home/paul# E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
bash: syntax error near unexpected token `('
root@paul-home:/home/paul# root@paul-home:/home/paul# E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
bash: syntax error near unexpected token `('
root@paul-home:/home/paul# bash: syntax error near unexpected token `('
> root@paul-home:/home/paul# E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
> bash: syntax error near unexpected token `('
bash: syntax error near unexpected token `('
root@paul-home:/home/paul# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libjreen1 libqtweetlib1.0 linux-image-3.13.0-32-lowlatency
  linux-image-3.13.0-34-generic linux-image-3.13.0-34-lowlatency
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-34-generic
  linux-image-extra-3.13.0-35-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tor
Suggested packages:
  mixmaster xul-ext-torbutton socat tor-arm apparmor-utils
The following NEW packages will be installed
  tor
0 to upgrade, 1 to newly install, 0 to remove and 34 not to upgrade.
3 not fully installed or removed.
Need to get 0 B/807 kB of archives.
After this operation, 2,573 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 559886 files and directories currently installed.)
Preparing to unpack .../tor_0.2.4.23-2~trusty+1_amd64.deb ...
Unpacking tor (0.2.4.23-2~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@paul-home:/home/paul# sudo apt-get remove tor-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 tor-geoipdb : Depends: tor (>= 0.2.4.23-2~trusty+1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@paul-home:/home/paul# rm -r ~/.tor-browser-en
rm: cannot remove &#8216;/root/.tor-browser-en&#8217;: No such file or directory
root@paul-home:/home/paul# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libjreen1 libqtweetlib1.0 linux-image-3.13.0-32-lowlatency
  linux-image-3.13.0-34-generic linux-image-3.13.0-34-lowlatency
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-34-generic
  linux-image-extra-3.13.0-35-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tor
Suggested packages:
  mixmaster xul-ext-torbutton socat tor-arm apparmor-utils
The following NEW packages will be installed
  tor
0 to upgrade, 1 to newly install, 0 to remove and 34 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/807 kB of archives.
After this operation, 2,573 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 559886 files and directories currently installed.)
Preparing to unpack .../tor_0.2.4.23-2~trusty+1_amd64.deb ...
Unpacking tor (0.2.4.23-2~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@paul-home:/home/paul# apt-get uninstall fatrat
E: Invalid operation uninstall
root@paul-home:/home/paul#  apt-get remove fatrat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'fatrat' is not installed, so not remo ved
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 tor-geoipdb : Depends: tor (>= 0.2.4.23-2~trusty+1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@paul-home:/home/paul# " 
```

it's just an uneducated guess,but perhaps some dependancies of tor stuff for the tor-browser have gotten some conflict with fatrat?
interestingly, when i go intosynaptic package manager tor-browser elements show there, but no fatrat things.

also,i i try to uninstall either, they cant be found.  for example:

```
"paul@paul-home:~$ sudo su
[sudo] password for paul: 
root@paul-home:/home/paul# apt-get remove fatrat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'fatrat' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 tor-geoipdb : Depends: tor (>= 0.2.4.23-2~trusty+1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@paul-home:/home/paul# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libjreen1 libqtweetlib1.0 linux-image-3.13.0-32-lowlatency
  linux-image-3.13.0-34-generic linux-image-3.13.0-34-lowlatency
  linux-image-3.13.0-35-generic linux-image-extra-3.13.0-34-generic
  linux-image-extra-3.13.0-35-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  tor
Suggested packages:
  mixmaster xul-ext-torbutton socat tor-arm apparmor-utils
The following NEW packages will be installed
  tor
0 to upgrade, 1 to newly install, 0 to remove and 34 not to upgrade.
1 not fully installed or removed.
Need to get 0 B/807 kB of archives.
After this operation, 2,573 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 559886 files and directories currently installed.)
Preparing to unpack .../tor_0.2.4.23-2~trusty+1_amd64.deb ...
Unpacking tor (0.2.4.23-2~trusty+1) ...
dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb (--unpack):
 trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db (2.6.7.1-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"
```

and for tor-browser:

```
"root@paul-home:/home/paul# sudo apt-get remove tor-browserE: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@paul-home:/home/paul# "
```

well, another process may be using it, but i really wouldnt know.
(the above tor-browser removal was todays attempt for showing here just what's been happening, but i thibk what showed up last night may have differed)


and i guess it might be worth noting, that as this was happening, i kept getting an update notification for not only flash, but for things that may have been essential to the two programs i'm having issues with here.
maybe they failed as i was still in terminal with those two install/uninstalls?
the updates failed and kept giving me the choice constantly,to retry.

it might be worth noting, as i'm really unsure if there's any connection/relevance, that many, or most of my updates fail.
i'll post about that seperately.

thanks, beforehand for anyone reading what will no doubt be gibberish to experienced users, but it is a real struggle for me to get my head around much of this. so thank you all in advance for your time and patience

---

### Post by gnowair on 2014-09-12
incase it may be of relevance, here is what happens when i try to fix whats up with the tor packages through synaptic package manager:
"E: Internal Error, No file name for tor-geoipdb:amd64"

---

### Post by gnowair on 2014-09-12
it may be worth adding this info here too.
when i try to re-install tor-geopdn via software centre i get a window popping up asking me to repair tor-geopdn, and when i click "repair" i get this notification:

"[COLOR=#000000]"nstallArchives() failed: (Reading database ... (Reading database ... 5%[/COLOR]
[COLOR=#000000](Reading database ... 10%[/COLOR]
[COLOR=#000000](Reading database ... 15%[/COLOR]
[COLOR=#000000](Reading database ... 20%[/COLOR]
[COLOR=#000000](Reading database ... 25%[/COLOR]
[COLOR=#000000](Reading database ... 30%[/COLOR]
[COLOR=#000000](Reading database ... 35%[/COLOR]
[COLOR=#000000](Reading database ... 40%[/COLOR]
[COLOR=#000000](Reading database ... 45%[/COLOR]
[COLOR=#000000](Reading database ... 50%[/COLOR]
[COLOR=#000000](Reading database ... 55%[/COLOR]
[COLOR=#000000](Reading database ... 60%[/COLOR]
[COLOR=#000000](Reading database ... 65%[/COLOR]
[COLOR=#000000](Reading database ... 70%[/COLOR]
[COLOR=#000000](Reading database ... 75%[/COLOR]
[COLOR=#000000](Reading database ... 80%[/COLOR]
[COLOR=#000000](Reading database ... 85%[/COLOR]
[COLOR=#000000](Reading database ... 90%[/COLOR]
[COLOR=#000000](Reading database ... 95%[/COLOR]
[COLOR=#000000](Reading database ... 100%[/COLOR]
[COLOR=#000000](Reading database ... 559886 files and directories currently installed.)[/COLOR]
[COLOR=#000000]Preparing to unpack .../tor_0.2.4.23-2~trusty+1_amd64.deb ...[/COLOR]
[COLOR=#000000]Unpacking tor (0.2.4.23-2~trusty+1) ...[/COLOR]
[COLOR=#000000]dpkg: error processing archive /var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb (--unpack):[/COLOR]
[COLOR=#000000]trying to overwrite '/usr/bin/tor', which is also in package tor-browser 3.5.4[/COLOR]
[COLOR=#000000]dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)[/COLOR]
[COLOR=#000000]Processing triggers for man-db (2.6.7.1-1) ...[/COLOR]
[COLOR=#000000]Errors were encountered while processing:[/COLOR]
[COLOR=#000000]/var/cache/apt/archives/tor_0.2.4.23-2~trusty+1_amd64.deb[/COLOR]
[COLOR=#000000]Error in function: [/COLOR]
[COLOR=#000000]dpkg: dependency problems prevent configuration of tor-geoipdb:[/COLOR]
[COLOR=#000000]tor-geoipdb depends on tor (>= 0.2.4.23-2~trusty+1); however:[/COLOR]
[COLOR=#000000]Package tor is not installed"

any ideas how to fix?[/COLOR]

---

### Post by gnowair on 2014-09-24
TOR ISSUE SOLVED.
 but any info at all on fatrat?

---


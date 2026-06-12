---
title: "Have I have been hacked?"
date: 2010-08-17
forum: Recurring Discussions
---

### Post by ontherooftop on 2010-08-17
OK in Firestarter firewall I saw in allow connections
from inbound policy host 2 ip addresses that I never 
allowed and checked and I don't see that they are part
of any site or servers 1 is from washington and another
from New York, How could this happen if I didn't allow
it?  Also my computer does strange things sometimes like
freeze. Is there a trojan, rootkit, backdoor or keylogger
on my Ubuntu 9.10. And what programs should I use and 
check to scan to make sure everything is fine? thanks.

---

### Post by DrMelon on 2010-08-17
Calm down. You sound like you have paranoia problems.

The connections listed are likely to be connections to either websites or mailservers. Possibly the ubuntu repositories so it can get updates.

It's is very, very unlikely you have malware on your system. Very few actually exist for Linux, and those that do are more often targeted towards businesses and high-ranking servers.

Unless you specifically installed *and* ran the software with admin rights (which is very unlikely) you don't have any.

Freezing indicates hardware problems or driver issues. I would make sure everything is up-to-date on your system.

---

### Post by ontherooftop on 2010-08-17
Dr melon I did a rootkit scan and here is what it says
on the terminal.

```
[ Rootkit Hunter version 1.3.4 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ Updated ]
  Checking file backdoorports.dat                            [ Updated ]
  Checking file suspscan.dat                                 [ Updated ]
  Checking file i18n/cn                                      [ No update ]
  Checking file i18n/de                                      [ Updated ]
  Checking file i18n/en                                      [ No update ]
  Checking file i18n/zh                                      [ No update ]
  Checking file i18n/zh.utf8                                 [ No update ]
noname@noname-laptop:~$ sudo rkhunter --check
[ Rootkit Hunter version 1.3.4 ]

Checking system commands...

  Performing 'strings' command checks
    Checking 'strings' command                               [ OK ]

  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preload file                                [ Not found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]

  Performing file properties checks
    Checking for prerequisites                               [ OK ]
    /bin/bash                                                [ OK ]
    /bin/cat                                                 [ OK ]
    /bin/chmod                                               [ OK ]
    /bin/chown                                               [ OK ]
    /bin/cp                                                  [ OK ]
    /bin/date                                                [ OK ]
    /bin/df                                                  [ OK ]
    /bin/dmesg                                               [ OK ]
    /bin/echo                                                [ OK ]
    /bin/ed                                                  [ OK ]
    /bin/egrep                                               [ OK ]
    /bin/fgrep                                               [ OK ]
    /bin/fuser                                               [ OK ]
    /bin/grep                                                [ OK ]
    /bin/ip                                                  [ OK ]
    /bin/kill                                                [ OK ]
    /bin/less                                                [ OK ]
    /bin/login                                               [ OK ]
    /bin/ls                                                  [ OK ]
    /bin/lsmod                                               [ OK ]
    /bin/mktemp                                              [ OK ]
    /bin/more                                                [ OK ]
    /bin/mount                                               [ OK ]
    /bin/mv                                                  [ OK ]
    /bin/netstat                                             [ OK ]
    /bin/ps                                                  [ OK ]
    /bin/pwd                                                 [ OK ]
    /bin/readlink                                            [ OK ]
    /bin/sed                                                 [ OK ]
    /bin/sh                                                  [ OK ]
    /bin/su                                                  [ OK ]
    /bin/touch                                               [ OK ]
    /bin/uname                                               [ OK ]
    /bin/which                                               [ OK ]
    /usr/bin/awk                                             [ OK ]
    /usr/bin/basename                                        [ OK ]
    /usr/bin/chattr                                          [ OK ]
    /usr/bin/curl                                            [ OK ]
    /usr/bin/cut                                             [ OK ]
    /usr/bin/diff                                            [ OK ]
    /usr/bin/dirname                                         [ OK ]
    /usr/bin/dpkg                                            [ OK ]
    /usr/bin/dpkg-query                                      [ OK ]
    /usr/bin/du                                              [ OK ]
    /usr/bin/env                                             [ OK ]
    /usr/bin/file                                            [ OK ]
    /usr/bin/find                                            [ OK ]
    /usr/bin/GET                                             [ OK ]
    /usr/bin/groups                                          [ OK ]
    /usr/bin/head                                            [ OK ]
    /usr/bin/id                                              [ OK ]
    /usr/bin/killall                                         [ OK ]
    /usr/bin/last                                            [ OK ]
    /usr/bin/lastlog                                         [ OK ]
    /usr/bin/ldd                                             [ OK ]
    /usr/bin/less                                            [ OK ]
    /usr/bin/locate                                          [ OK ]
    /usr/bin/logger                                          [ OK ]
    /usr/bin/lsattr                                          [ OK ]
    /usr/bin/lsof                                            [ OK ]
    /usr/bin/mail                                            [ OK ]
    /usr/bin/md5sum                                          [ OK ]
    /usr/bin/mlocate                                         [ OK ]
    /usr/bin/newgrp                                          [ OK ]
    /usr/bin/passwd                                          [ OK ]
    /usr/bin/perl                                            [ OK ]
    /usr/bin/pstree                                          [ OK ]
    /usr/bin/rkhunter                                        [ OK ]
    /usr/bin/runcon                                          [ OK ]
    /usr/bin/sha1sum                                         [ OK ]
    /usr/bin/size                                            [ OK ]
    /usr/bin/sort                                            [ OK ]
    /usr/bin/stat                                            [ OK ]
    /usr/bin/strace                                          [ OK ]
    /usr/bin/strings                                         [ OK ]
    /usr/bin/sudo                                            [ OK ]
    /usr/bin/tail                                            [ OK ]
    /usr/bin/test                                            [ OK ]
    /usr/bin/top                                             [ OK ]
    /usr/bin/touch                                           [ OK ]
    /usr/bin/tr                                              [ OK ]
    /usr/bin/uniq                                            [ OK ]
    /usr/bin/users                                           [ OK ]
    /usr/bin/vmstat                                          [ OK ]
    /usr/bin/w                                               [ OK ]
    /usr/bin/watch                                           [ OK ]
    /usr/bin/wc                                              [ OK ]
    /usr/bin/wget                                            [ OK ]
    /usr/bin/whatis                                          [ OK ]
    /usr/bin/whereis                                         [ OK ]
    /usr/bin/which                                           [ OK ]
    /usr/bin/who                                             [ OK ]
    /usr/bin/whoami                                          [ OK ]
    /usr/bin/gawk                                            [ OK ]
    /usr/bin/lwp-request                                     [ OK ]
    /usr/bin/bsd-mailx                                       [ OK ]
    /usr/bin/w.procps                                        [ OK ]
    /sbin/depmod                                             [ OK ]
    /sbin/ifconfig                                           [ OK ]
    /sbin/ifdown                                             [ OK ]
    /sbin/ifup                                               [ OK ]
    /sbin/init                                               [ OK ]
    /sbin/insmod                                             [ OK ]
    /sbin/ip                                                 [ OK ]
    /sbin/lsmod                                              [ OK ]
    /sbin/modinfo                                            [ OK ]
    /sbin/modprobe                                           [ OK ]
    /sbin/rmmod                                              [ OK ]
    /sbin/runlevel                                           [ OK ]
    /sbin/sulogin                                            [ OK ]
    /sbin/sysctl                                             [ OK ]
    /usr/sbin/adduser                                        [ OK ]
    /usr/sbin/chroot                                         [ OK ]
    /usr/sbin/cron                                           [ OK ]
    /usr/sbin/groupadd                                       [ OK ]
    /usr/sbin/groupdel                                       [ OK ]
    /usr/sbin/groupmod                                       [ OK ]
    /usr/sbin/grpck                                          [ OK ]
    /usr/sbin/nologin                                        [ OK ]
    /usr/sbin/pwck                                           [ OK ]
    /usr/sbin/rsyslogd                                       [ OK ]
    /usr/sbin/tcpd                                           [ OK ]
    /usr/sbin/unhide                                         [ Warning ]
    /usr/sbin/useradd                                        [ OK ]
    /usr/sbin/userdel                                        [ OK ]
    /usr/sbin/usermod                                        [ OK ]
    /usr/sbin/vipw                                           [ OK ]
    /usr/sbin/unhide-linux26                                 [ Warning ]

[Press <ENTER> to continue]


Checking for rootkits...

  Performing check of known rootkit files and directories
    55808 Trojan - Variant A                                 [ Not found ]
    ADM Worm                                                 [ Not found ]
    AjaKit Rootkit                                           [ Not found ]
    aPa Kit                                                  [ Not found ]
    Apache Worm                                              [ Not found ]
    Ambient (ark) Rootkit                                    [ Not found ]
    Balaur Rootkit                                           [ Not found ]
    BeastKit Rootkit                                         [ Not found ]
    beX2 Rootkit                                             [ Not found ]
    BOBKit Rootkit                                           [ Not found ]
    CiNIK Worm (Slapper.B variant)                           [ Not found ]
    Danny-Boy's Abuse Kit                                    [ Not found ]
    Devil RootKit                                            [ Not found ]
    Dica-Kit Rootkit                                         [ Not found ]
    Dreams Rootkit                                           [ Not found ]
    Duarawkz Rootkit                                         [ Not found ]
    Enye LKM                                                 [ Not found ]
    Flea Linux Rootkit                                       [ Not found ]
    FreeBSD Rootkit                                          [ Not found ]
    ****`it Rootkit                                          [ Not found ]
    GasKit Rootkit                                           [ Not found ]
    Heroin LKM                                               [ Not found ]
    HjC Kit                                                  [ Not found ]
    ignoKit Rootkit                                          [ Not found ]
    ImperalsS-FBRK Rootkit                                   [ Not found ]
    IntoXonia-NG Rootkit                                     [ Not found ]
    Irix Rootkit                                             [ Not found ]
    Kitko Rootkit                                            [ Not found ]
    Knark Rootkit                                            [ Not found ]
    Li0n Worm                                                [ Not found ]
    Lockit / LJK2 Rootkit                                    [ Not found ]
    Mood-NT Rootkit                                          [ Not found ]
    MRK Rootkit                                              [ Not found ]
    Ni0 Rootkit                                              [ Not found ]
    Ohhara Rootkit                                           [ Not found ]
    Optic Kit (Tux) Worm                                     [ Not found ]
    Oz Rootkit                                               [ Not found ]
    Phalanx Rootkit                                          [ Not found ]
    Phalanx Rootkit (strings)                                [ Not found ]
    Phalanx2 Rootkit                                         [ Not found ]
    Phalanx2 Rootkit (extended tests)                        [ Not found ]
    Portacelo Rootkit                                        [ Not found ]
    R3dstorm Toolkit                                         [ Not found ]
    RH-Sharpe's Rootkit                                      [ Not found ]
    RSHA's Rootkit                                           [ Not found ]
    Scalper Worm                                             [ Not found ]
    Sebek LKM                                                [ Not found ]
    Shutdown Rootkit                                         [ Not found ]
    SHV4 Rootkit                                             [ Not found ]
    SHV5 Rootkit                                             [ Not found ]
    Sin Rootkit                                              [ Not found ]
    Slapper Worm                                             [ Not found ]
    Sneakin Rootkit                                          [ Not found ]
    Suckit Rootkit                                           [ Not found ]
    SunOS Rootkit                                            [ Not found ]
    SunOS / NSDAP Rootkit                                    [ Not found ]
    Superkit Rootkit                                         [ Not found ]
    TBD (Telnet BackDoor)                                    [ Not found ]
    TeLeKiT Rootkit                                          [ Not found ]
    T0rn Rootkit                                             [ Not found ]
    Trojanit Kit                                             [ Not found ]
    Tuxtendo Rootkit                                         [ Not found ]
    URK Rootkit                                              [ Not found ]
    Vampire Rootkit                                          [ Not found ]
    VcKit Rootkit                                            [ Not found ]
    Volc Rootkit                                             [ Not found ]
    X-Org SunOS Rootkit                                      [ Not found ]
    zaRwT.KiT Rootkit                                        [ Not found ]

  Performing additional rootkit checks
    Suckit Rookit additional checks                          [ OK ]
    Checking for possible rootkit files and directories      [ None found ]
    Checking for possible rootkit strings                    [ None found ]

  Performing malware checks
    Checking running processes for suspicious files          [ None found ]
    Checking for login backdoors                             [ None found ]
    Checking for suspicious directories                      [ None found ]
    Checking for sniffer log files                           [ None found ]

  Performing trojan specific checks
    Checking for enabled inetd services                      [ OK ]

  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]

[Press <ENTER> to continue]


Checking the network...

  Performing check for backdoor ports
    Checking for TCP port 1524                               [ Not found ]
    Checking for TCP port 1984                               [ Not found ]
    Checking for UDP port 2001                               [ Not found ]
    Checking for TCP port 2006                               [ Not found ]
    Checking for TCP port 2128                               [ Not found ]
    Checking for TCP port 6666                               [ Not found ]
    Checking for TCP port 6667                               [ Not found ]
    Checking for TCP port 6668                               [ Not found ]
    Checking for TCP port 6669                               [ Not found ]
    Checking for TCP port 7000                               [ Not found ]
    Checking for TCP port 13000                              [ Not found ]
    Checking for TCP port 14856                              [ Not found ]
    Checking for TCP port 25000                              [ Not found ]
    Checking for TCP port 29812                              [ Not found ]
    Checking for TCP port 31337                              [ Not found ]
    Checking for TCP port 33369                              [ Not found ]
    Checking for TCP port 47107                              [ Not found ]
    Checking for TCP port 47018                              [ Not found ]
    Checking for TCP port 60922                              [ Not found ]
    Checking for TCP port 62883                              [ Not found ]
    Checking for TCP port 65535                              [ Not found ]

  Performing checks on the network interfaces
    Checking for promiscuous interfaces                      [ None found ]

[Press <ENTER> to continue]


Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ None found ]

  Performing system configuration file checks
    Checking for SSH configuration file                      [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]
    Checking if SSH protocol v1 is allowed                   [ Not allowed ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]

[Press <ENTER> to continue]


Checking application versions...

    Checking version of Exim MTA                             [ Warning ]
    Checking version of GnuPG                                [ Warning ]
    Checking version of OpenSSL                              [ Warning ]
    Checking version of OpenSSH                              [ Warning ]


System checks summary
=====================

File properties checks...
    Files checked: 128
    Suspect files: 2

Rootkit checks...
    Rootkits checked : 112
    Possible rootkits: 0

Applications checks...
    Applications checked: 4
    Suspect applications: 4

The system checks took: 2 minutes and 15 seconds

All results have been written to the logfile (/var/log/rkhunter.log)
```

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)


there are some warnings, now I think I am paranoid.

---

### Post by ontherooftop on 2010-08-17
I scanned with chkrootkit and all it found was this

Searching for anomalies in shell history files...           Warning: `//home/noname/.kino-history' is linked to another file


But rkhunter has 5 warnings or so but no rootkits 
found, what could be going on. I never did anything
stupid to even get me an infection.

in system monitor 

ssh-agent is running 

Am I running a server for christ sakes?

---

### Post by CharlesA on 2010-08-17
Have you used rkhunter before? That output looks normal, as it spits out false positives some of the time.

ssh-agent is part of Open-SSH (open-ssh client, which is the ssh client). If you don't have any services running that are accessible to the outside, you are fine.

It sounds like a hardware problem tbh.

Also: Firestarter is no longer being maintained, you GUFW or UFW if you want a firewall enabled.

---

### Post by Soul-Sing on 2010-08-17
imo it is hard to understand the outcome of rkhunter/chkrootkit "logs", I find it so difficult to understand them that I don't use them as security tools.
99,9 % of all threads on this forum with rkhunter or chkrootkit in it are ambiguous or even unnecessary alarming.

---

### Post by Rubi1200 on 2010-08-17
> **leoquant said:**
> imo it is hard to understand the outcome of rkhunter/chkrootkit "logs", I find it so difficult to understand them that I don't use them as security tools.
99,9 % of all threads on this forum with rkhunter or chkrootkit in it are ambiguous or even unnecessary alarming.

+1

Totally agree!

I am not even sure where people find out about using these tools. If they had read the sections in the security sticky by bodhi.zazen they would know that certain conditions apply to the use of such tools; namely, false positives can and do occur, the user needs to Google for results BEFORE posting to the forums, and that unless scans are done on a clean system and/or you know your system very well it is quite likely you will misinterpret the results.

---

### Post by CharlesA on 2010-08-17
> **Rubi1200 said:**
> +1

Totally agree!

I am not even sure where people find out about using these tools. If they had read the sections in the security sticky by bodhi.zazen they would know that certain conditions apply to the use of such tools; namely, false positives can and do occur, the user needs to Google for results BEFORE posting to the forums, and that unless scans are done on a clean system and/or you know your system very well it is quite likely you will misinterpret the results.
Indeed. I'm still surprised that people are still using firestarter, even though it's no longer under development.

[Insert obligatory link to security sticky here.]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by ontherooftop on 2010-08-17
I am using firestarter, it seems to be blocking lots
of things and I also have a router but some ports are 
open in the router and UPNP is enabled in router
(if that matters) whats wrong with Firestarter, I 
have been using it the whole time and I didn't know
nothing about it being not upgraded. It did show allow
incoming connections from 2 strange IP addresses that I
did not allow or configure but could this be normal? 
and wouldn't the router block the incoming source 
anyways? Seems like there is no rootkits on my Ubuntu
just 4 false positives.

---

### Post by cariboo on 2010-08-17
These threads pop up several times a week. A quick google search would have answered the op's question, these are the same false positives that come up time and time again. Moved to Recurring.

---

### Post by eveg on 2011-11-22
> **ontherooftop said:**
> I scanned with chkrootkit and all it found was this
 
Searching for anomalies in shell history files... Warning: `//home/noname/.kino-history' is linked to another file
 
 
But rkhunter has 5 warnings or so but no rootkits 
found, what could be going on. I never did anything
stupid to even get me an infection.
 
in system monitor 
 
ssh-agent is running 
 
Am I running a server for christ sakes?
 
yes, unfortunately you are indeed running a server, in your computer's opinion. [if you installed the system, for instance, it considers you the system administrator, one hopes! there are rootkits and possibly also other attacks which can result in your copmputer no longer accepting the fact that it *is* yours and locking you out of progressively more and more of it. do all computer repairs offline with modem etc unplugged. never install an operating system online. try to find a trustworthy computer professional to make a backup system for you, and hope s/he is competant and honest, &/or teach yourself as much as you can to keep your own system safe. anyone who offers you a computer fix that involves rebooting is probably trying to sneak something vicious indeed into your computer. possibly find a reliable linux book with an install os disc. that is by no means a guarantee of safety. however, it's a better bet than trying to download an os on an already compromised machine which may lead you to quite unreliable 'mirror' sites. i quite understand it's considered more polite to use them. they can however present serious vulnerabilities, as can getting your os from an online download at all.] and you almost certainly have a hacked machine. do you absolutely have to run a system other than the current lts for which there are security fixes? and anytime someone tells you you are being paranoid about computer security, please realize that the person telling you that is quite possibly a criminal hacker for fun and/or profit.
 
computers are dangerous toys and insanely dangerous tools. anyone who tries to tell you you're paranoid about computer security probably 'has an ax to grind'. ignore them and keep it out of your neck, metaphorically.

---

### Post by Dangertux on 2011-11-22
> **eveg said:**
> yes, unfortunately you are indeed running a server, in your computer's opinion. [if you installed the system, for instance, it considers you the system administrator, one hopes! there are rootkits and possibly also other attacks which can result in your copmputer no longer accepting the fact that it *is* yours and locking you out of progressively more and more of it. do all computer repairs offline with modem etc unplugged. never install an operating system online. try to find a trustworthy computer professional to make a backup system for you, and hope s/he is competant and honest, &/or teach yourself as much as you can to keep your own system safe. anyone who offers you a computer fix that involves rebooting is probably trying to sneak something vicious indeed into your computer. possibly find a reliable linux book with an install os disc. that is by no means a guarantee of safety. however, it's a better bet than trying to download an os on an already compromised machine which may lead you to quite unreliable 'mirror' sites. i quite understand it's considered more polite to use them. they can however present serious vulnerabilities, as can getting your os from an online download at all.] and you almost certainly have a hacked machine. do you absolutely have to run a system other than the current lts for which there are security fixes? and anytime someone tells you you are being paranoid about computer security, please realize that the person telling you that is quite possibly a criminal hacker for fun and/or profit.
 
computers are dangerous toys and insanely dangerous tools. anyone who tries to tell you you're paranoid about computer security probably 'has an ax to grind'. ignore them and keep it out of your neck, metaphorically.

While a lot of that advice is good. You're being paranoid. Forget the fact that this thread is over a year old for a moment. 

The rkhunter log posted gives no indication of a rootkit, at all. In fact it gives every indication of the typical false positives it throws on a normal Ubuntu install. Again, I usually am a security evangelist, but telling people their systems are owned without any real evidence is silly.

> 
and you almost certainly have a hacked machine. do you absolutely have  to run a system other than the current lts for which there are security  fixes?


All non end of lifed Ubuntu distros receive security updates, the distro in question probably wasn't EOL when this was posted (again a year ago)

A healthy sense of paranoia is good, however ranting and making a statement like "You almost certainly have a hacked system" based on a log file that is at best inconclusive is a little silly.

If you're interested in learning more about securing Ubuntu I recommend the following links.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)
[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)
[http://ubuntuforums.org/showthread.php?t=1477696](http://ubuntuforums.org/showthread.php?t=1477696)
[http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

Hope this helps.

---


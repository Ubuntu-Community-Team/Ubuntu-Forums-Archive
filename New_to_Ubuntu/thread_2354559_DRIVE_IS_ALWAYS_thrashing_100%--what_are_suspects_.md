---
title: "DRIVE IS *ALWAYS* thrashing 100%--what are suspects to look for&gt;??"
date: 2017-03-03
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2017-03-03
Hello,
I have a bad problem. My CPU (Xubuntu 14.04.05)---is *ALWAYS* thrashing at 100% CPU usage. However I can't isolate the problem. 

AKA--I thought maybe it's trying to outbound communicate--turning off Modem does nothing (even 30-mins later). 

Here's the *ODD* behavior. When I reinstall the OS---It's BLAZING FAST (as it should be). I do *NOTHING* installing programs,etc. To test it. Everything seems fine (so far without fail), 24-hours later my Drive will be Trashing again. 
(thus don't *THINK* it's a rogue app). 
HOWEVER (Paradoxically to me)---the "turning off"--even waiting for a malware phone home app--to time out---never does. A *FEW TIMES* I try and use Peer Guardian and Lock Down any outbound IP----I *SOMETIMES* get "expected" results. 
AKA--the "trashing stops"---I turn network back on-----it seems to stay that way as I work away. (BUT this solution does not work 100% of time---thus I've so far put as a false hit). 

I've tried *EVERYTHING*----including buying a brand new drive, etc. I have full, boat RAM (4GB) a "not bad" CPU (I'm a WindowsXP refugee to Linux and ROCK SOLID SOLD---never going back)_----but XP worked just fine on this box...so that's the "standard" compare. 

I've tried 
CLAMSCAN
CHKROOT
RKHUNTER
TIGER

```

Nothing looks "wrong" (course get the false hit of "SUCKIT"). 

HOWEVER I DID NOTICE THIS with RKHUNER
Checking for passwd file changes                         [ Warning ]
    Checking for group file changes                          [ Warning ]
    Checking root account shell history files                [ OK ]


  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]




```

Anything to be concerned about? 

Using "Glances" looks like nothing out of line------(no real process stealing much CPU, etc.). 
```

Using LYNIS (outdated/need to update). using 139 latest 240 (I just installed, not sure why not "latest release"?>??

However Errors I get with LYNIS

[+] Memory and processes
------------------------------------
  - Checking /proc/meminfo...                                 [ FOUND ]
  - Searching for dead/zombie processes...                    [ OK ]
  - Searching for IO waiting processes...                     [ WARNING ]


```

IO waiting process could be problem right? I/O is a read/write process correct????

also 

```

Networking
------------------------------------
  - Checking configured nameservers...
    - Testing nameservers...
        Nameserver: 209.222.18.222...                         [ OK ]
        Nameserver: 209.222.18.218...                         [ OK ]
    - Minimal of 2 responsive nameservers...                  [ OK ]
  - Checking default gateway...                               [ DONE ]
  - Getting listening ports (TCP/TCP)...                      [ DONE ]
      * Found 7 ports
  - Checking promiscuous interfaces...                        [ OK ]
  - Checking waiting connections...                           [ WARNING ]

```



and
```


[+] Banners and identification
------------------------------------
  - /etc/motd...                                              [ NOT FOUND ]
  - /etc/issue...                                             [ FOUND ]
    - /etc/issue contents...                                  [ WEAK ]
  - /etc/issue.net...                                         [ FOUND ]
    - /etc/issue.net contents...                              [ WEAK ]



```


and 
(I did tweak my sysconf.ctl file...thus these warnings from this? (from a trusted site regarding hardening). 
```


Kernel Hardening
------------------------------------
  - Comparing sysctl key pairs with scan profile...
    - kernel.core_uses_pid (exp: 1)                           [ DIFFERENT ]
    - kernel.ctrl-alt-del (exp: 0)                            [ OK ]
    - kernel.sysrq (exp: 0)                                   [ DIFFERENT ]
    - net.ipv4.conf.all.accept_redirects (exp: 0)             [ OK ]
    - net.ipv4.conf.all.accept_source_route (exp: 0)          [ OK ]
    - net.ipv4.conf.all.bootp_relay (exp: 0)                  [ OK ]
    - net.ipv4.conf.all.forwarding (exp: 0)                   [ OK ]
    - net.ipv4.conf.all.log_martians (exp: 1)                 [ OK ]
    - net.ipv4.conf.all.mc_forwarding (exp: 0)                [ OK ]
    - net.ipv4.conf.all.proxy_arp (exp: 0)                    [ OK ]
    - net.ipv4.conf.all.rp_filter (exp: 1)                    [ OK ]
    - net.ipv4.conf.all.send_redirects (exp: 0)               [ OK ]
    - net.ipv4.conf.default.accept_redirects (exp: 0)         [ DIFFERENT ]
    - net.ipv4.conf.default.accept_source_route (exp: 0)      [ DIFFERENT ]
    - net.ipv4.conf.default.log_martians (exp: 1)             [ DIFFERENT ]
    - net.ipv4.icmp_echo_ignore_broadcasts (exp: 1)           [ OK ]
    - net.ipv4.icmp_ignore_bogus_error_responses (exp: 1)     [ OK ]
    - net.ipv4.tcp_syncookies (exp: 1)                        [ OK ]
    - net.ipv4.tcp_timestamps (exp: 0)                        [ DIFFERENT ]
    - net.ipv6.conf.all.accept_redirects (exp: 0)             [ OK ]
    - net.ipv6.conf.all.accept_source_route (exp: 0)          [ OK ]
    - net.ipv6.conf.default.accept_redirects (exp: 0)         [ DIFFERENT ]
    - net.ipv6.conf.default.accept_source_route (exp: 0)      [ OK ]

```

and
```
-[ Lynis 1.3.9 Results ]-


  Tests performed: 150


  Warnings:
  ----------------------------
  - Version of Lynis very outdated [test:NONE]
  - Found too much connections in WAIT state (112) [test:NETW-3028]


  Suggestions:
  ----------------------------
  - update to the latest stable release.
  - Install a PAM module for password strength testing like pam_cracklib or pam_passwdqc [test:AUTH-9262]
  - Configure password aging limits to enforce password changing on a regular base [test:AUTH-9286]
  - Default umask in /etc/login.defs could be more strict like 027 [test:AUTH-9328]
  - Default umask in /etc/init.d/rc could be more strict like 027 [test:AUTH-9328]
  - Disable drivers like USB storage when not used, to prevent unauthorized storage or data theft [test:STRG-1840]
  - Purge old/removed packages (81 found) with aptitude purge or dpkg --purge command. This will cleanup old configuration files, cron jobs and startup scripts. [test:PKGS-7346]
  - Install package apt-show-versions for patch management purposes [test:PKGS-7394]
  - Configure a firewall/packet filter to filter incoming and outgoing traffic [test:FIRE-4590]
  - Check what deleted files are still in use and why. [test:LOGG-2190]
  - Add a legal banner to /etc/issue, to warn unauthorized users [test:BANN-7126]
  - Add legal banner to /etc/issue.net, to warn unauthorized users [test:BANN-7130]
  - Enable auditd to collect audit information [test:ACCT-9628]
  - One or more sysctl values differ from the scan profile and could be tweaked [test:KRNL-6000]
  - Harden the system by removing unneeded compilers. This can decrease the chance of customized trojans, backdoors and rootkits to be compiled and installed [test:HRDN-7220]
  - Harden compilers and restrict access to world [test:HRDN-7222]



```


Guess I'll take a look at LYNIS suggestions but others?

---

### Post by bearlake on 2017-03-04
Hi,

Have you checked your disk for failure yet?

This link may help.

[https://help.ubuntu.com/stable/ubuntu-help/disk-check.html](https://help.ubuntu.com/stable/ubuntu-help/disk-check.html)

---

### Post by HermanAB on 2017-03-04
$ top

---

### Post by Impavidus on 2017-03-04
It's not entirely clear from your first post what the problem is. Is something using too much CPU time or is it your hard drive?

In either case, use top to monitor your computer. It can tell you which processes use your cpu and your memory. Too much memory usage (or a memory leak) can cause swap usage.

---

### Post by whereismymindat2 on 2017-03-14
Thank you all for the time to reply. 
1st-Explain screen shots. 
Trying to show difference in VPN on/off (does it matter if client based?).
2nd-Always used glances prior to top. Why are the results so "different" (both were run inside "Root"). 
3rd-Also wanted to show "Terminal" view (of it in a GUI shows over 90% processor power). 

```

(To clarify on the drive)--I actually purchased a new drive about 6-8 months ago because of this. 
(It's been going on for about 2-years).The first attempt was "Duke Nuke" the drive--D.O.D. wiped and reinstalled a backup. 
The trashing quickly returned (in a day). 


Then purchased new drive--reinstalled "FRESH" (XUBUNTU 14.04.x) onto "new drive" 
Now, I simply use 2nd Drive as my "Folders" / storage drive. (aka--just left all data on "old drive1", 
"New_drive2"started the manual clean rebuild process (as if brand new CPU/Install)  on "New_drive2"
---thrashing quickly returned again. 

```


Since my Original Post I've gone back to make sure all the programs I'm using (to check malware/rootkit/etc/---up to date). Far as I know/believe they are . 


I just ran (running)
+++++++++++++++++++++++++++++++++++++
clamscan (clamav)--still running (every previous run is "OK"--all showing "OK" for now). 
rkhunter
lynis audit system --check-all
top-see screen shot


+++++++++++++++++++++++++++++++++++++
tiger--worthlesss (it's "Hanging" now)...never did before. Is this depricated?  
chkrootkit (only the "false positive" of suckit). 
+++++++++++++++++++++++++++++++++++++


```

Here's where I'm confused. (Think it might be something "rouge")

I use a VPN (Private Internet Access) aka "PIA". VPN. 
 
With VPN *TURNED ON*, I don't get much activity in PeerGuardian. 
A few programs try outbound on VPN.Usually port 123??? (or other "strange" ports.  
(PIA provides a built in Adware/Malware blocker "PIA MACE"--so guess it's doing it's job). 


When *NOT* connected to the VPN (using the 192.1.1.2 IP for desktop). 
Peer guardian goes *HAYWIRE* (Blocking outbound attempts on 192.168.1.2) 
THEN the drive will "trash"/run/etc. 

The extent to which it's "aggressive"----differs each time, but "normally" it's very aggressively thrashing (and/or) computer brought to it's knee's with processing,etc. 

VPN "ON" I get thrashing 70% of time. VPN "OFF" get "thrashing" 100% )(tends to be very aggressively thrashing

```

ABRIDGED RESULTS OF REST OF TESTS -------
+++++++++++++++++++++++++++++++++++++
tiger--worthlesss (it's "Hanging" now)...never did before. Is this depricated?  
chkrootkit (only the "false positive" of suckit). 
+++++++++++++++++++++++++++++++++++++

Here are the "actual" results of the Tests run 
+++++++++++++++++++++++++++++++++++++
clamscan (clamav)--still running (every previous run is "OK"
+++++++++++++++++++++++++++++++++++++

```

+++++++++++++++++++++++++++++++++++++
rkhunter (seems to me to give me most valuable info). Here's what it gave. 
+++++++++++++++++++++++++++++++++++++
[ Rootkit Hunter version 1.4.0 ]

*************ABRIDGED VERSION ONLY WITH "ERRORS" (WARNING,ETC. SHOWING) REST OF DATA SAID "OK"***********************
  Performing 'shared libraries' checks
    Checking for preloading variables                        [ None found ]
    Checking for preloaded libraries                         [ None found ]
    Checking LD_LIBRARY_PATH variable                        [ Not found ]


  Performing file properties checks
    /usr/sbin/adduser                                        [ Warning ]
    /usr/sbin/sestatus                                       [ Warning ]
    /usr/bin/awk                                             [ Warning ]
    /usr/bin/curl                                            [ Warning ]
    /usr/bin/unhide.rb                                       [ Warning ]
    /usr/bin/gawk                                            [ Warning ]
    /usr/bin/mawk                                            [ Warning ]


[Press <ENTER> to continue]




Checking for rootkits...


  Performing check of known rootkit files and directories
ALL SAY  ---------->                       [ Not found ]




[Press <ENTER> to continue]
 Performing additional rootkit checks
[ None found ]


 Performing malware checks
 [ None found ]


  Performing Linux specific checks
    Checking loaded kernel modules                           [ OK ]
    Checking kernel module names                             [ OK ]


[Press <ENTER> to continue]
Checking the network...
Checking for hidden ports                                [ Skipped ]


  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]


  Performing system configuration file checks
    Checking for SSH configuration file                      [ Not found ]
    Checking for running syslog daemon                       [ Found ]
    Checking for syslog configuration file                   [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]


  Performing filesystem checks
    Checking /dev for suspicious file types                  [ Warning ]
    Checking for hidden files and directories                [ Warning ]
+++++++++++++++++++++++++++++++++++++

```


+++++++++++++++++++++++++++++++++++++
LYNIS Results (copied from screen). 
+++++++++++++++++++++++++++++++++++++

```

[ Lynis 2.4.5 ]
  ---------------------------------------------------
  Program version:           2.4.5
  Operating system:          Linux
  Operating system name:     Ubuntu Linux
  Operating system version:  14.04
  Kernel version:            4.4.0
  Hardware platform:         i686
  ---------------------------------------------------

[+] System Tools
------------------------------------
  - Scanning available tools...
  - Checking system binaries...


[+] Program Details
------------------------------------
  - Verbose mode                                              [ YES ]
  - Debug mode                                                [ NO ]


[+] Plugins (phase 1)
------------------------------------
 Note: plugins have more extensive tests and may take several minutes to complete
  
  - Plugins enabled                                           [ NONE ]


[+] Boot and services
------------------------------------
  - Service Manager                                           [ SysV Init ]
  - Checking UEFI boot                                        [ DISABLED ]
  - Checking presence GRUB2                                   [ FOUND ]
    - Checking for password protection                        [ WARNING ]
  - Check services at startup (rc2.d)                         [ DONE ]
    Result: found 30 services
  - Check startup files (permissions)                         [ OK ]


[+] Kernel
------------------------------------
  - Checking default run level                                [ RUNLEVEL 2 ]
  - Checking CPU support (NX/PAE)
    CPU support: PAE and/or NoeXecute supported               [ FOUND ]
   - Checking Linux kernel configuration file                  [ FOUND ]
  - Checking default I/O kernel scheduler                     [ FOUND ]
  - Checking for available kernel update                      [ OK ]
  - Checking core dumps configuration                         [ DISABLED ]
    - Checking setuid core dumps configuration                [ DEFAULT ]
  - Check if reboot is needed                                 [ NO ]


[+] Memory and Processes
------------------------------------
  - Checking /proc/meminfo                                    [ FOUND ]
 
[+] Users, Groups and Authentication
------------------------------------
  - NIS+ authentication support                               [ NOT ENABLED ]
  - NIS authentication support                                [ NOT ENABLED ]
  - sudoers file                                              [ FOUND ]
    - Check sudoers file permissions                          [ OK ]
  - PAM password strength tools                               [ SUGGESTION ]
  - PAM configuration files (pam.conf)                        [ FOUND ]
  - PAM configuration files (pam.d)                           [ FOUND ]
  - PAM modules                                               [ FOUND ]

  - Checking user password aging (minimum)                    [ DISABLED ]
  - User password aging (maximum)                             [ DISABLED ]
    - umask (/etc/profile)                                    [ NOT FOUND ]
    - umask (/etc/login.defs)                                 [ SUGGESTION ]
    - umask (/etc/init.d/rc)                                  [ SUGGESTION ]
  - Logging failed login attempts                             [ ENABLED ]


[+] File systems
------------------------------------
  - Checking mount points
  - ACL support root file system                              [ ENABLED ]
  - Mount options of /                                        [ NON DEFAULT ]
  - Mount options of /boot                                    [ NON DEFAULT ]
  - Mount options of /home                                    [ NON DEFAULT ]
  - Mount options of /tmp                                     [ NON DEFAULT ]
  - Mount options of /var                                     [ NON DEFAULT ]
  - /var/tmp is not bound to /tmp                             [ INFO ]
  - Checking Locate database                                  [ FOUND ]
  - Disable kernel support of some filesystems
    - Discovered kernel modules: cramfs freevxfs hfs hfsplus jffs2 udf 


[+] Storage
------------------------------------
  - Checking usb-storage driver (modprobe config)             [ NOT DISABLED ]
  - Checking USB devices authorization                        [ ENABLED ]
  - Checking firewire ohci driver (modprobe config)           [ DISABLED ]


[+] Ports and packages
------------------------------------
  - Searching package managers
    - Searching dpkg package manager                          [ FOUND ]
      - Querying package manager
    - Query unpurged packages                                 [ FOUND ]
  - Checking security repository in sources.list file         [ OK ]
  - Checking APT package database                             [ OK ]
  - Checking vulnerable packages                              [ WARNING ]
  - Checking upgradeable packages                             [ FOUND ]
  - Checking package audit tool                               [ INSTALLED ]
    Found: apt-get

[+] Software: firewalls
------------------------------------
  - Checking iptables kernel module                           [ FOUND ]
    - Checking iptables policies of chains                    [ FOUND ]
      - Checking chain INPUT (table: filter) policy           [ DROP ]
    - Checking for empty ruleset                              [ OK ]
    - Checking for unused rules                               [ FOUND ]
  - Checking host based firewall                              [ ACTIVE ]


[+] PHP
------------------------------------
  - Checking PHP                                              [ FOUND ]
    - Checking PHP disabled functions                         [ FOUND ]
    - Checking expose_php option                              [ ON ]
    - Checking enable_dl option                               [ OFF ]
    - Checking allow_url_fopen option                         [ ON ]
    - Checking allow_url_include option                       [ OFF ]


[+] Logging and files
------------------------------------
  - Checking deleted files in use                             [ FILES FOUND ]

```



[ATTACH=CONFIG]274144[/ATTACH][ATTACH=CONFIG]274145[/ATTACH][ATTACH=CONFIG]274146[/ATTACH][ATTACH=CONFIG]274147[/ATTACH][ATTACH=CONFIG]274148[/ATTACH]

---


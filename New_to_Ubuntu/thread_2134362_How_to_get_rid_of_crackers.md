---
title: "How to get rid of crackers?"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by putStrLnNick on 2013-04-11
I've tried installing and reinstalling different versions of linux but I can't seem to get rid of what of one (or several) crackers. I've even used programs like dban and nwipe without success. I'm relatively new to linux, so I really don't know what to think or do. I've also tried HDDerase, but it doesn't seem to work (the hdderase command is not recognized and the version of the program is from 98'; similarly, when I try to install different versions of linux, I always start out with an outdated kernel). When I've been able to install chkrootkit, I've found one, and that's just the tip of the iceberg as far as weird behavior. I'll structure the rest of my post according to the suggestion here: [http://ubuntuforums.org/showthread.php?t=1897765](http://ubuntuforums.org/showthread.php?t=1897765).  1. My laptop came with windows 8, but I replaced it entirely with ubuntu (though, whenever I partition, there's /dev/sda (500GB disk space) and /dev/sdb (32GB disk space), and I normally partition the latter as FAT32: not really sure what purpose that serves, but that's what was recommended to me). I don't think my computer is networked with other computers, but again, I'm new to linux. Maybe the output of netstat -tulnp will help: > root@ubuntu:~# netstat -tulnp Active Internet connections (only servers) Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN      5715/vino-server tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      4375/dnsmasq     tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1711/cupsd       tcp6       0      0 :::5900                 :::*                    LISTEN      5715/vino-server tcp6       0      0 ::1:631                 :::*                    LISTEN      1711/cupsd       tcp6       0      0 :::5800                 :::*                    LISTEN      5715/vino-server udp        0      0 0.0.0.0:59360           0.0.0.0:*                           1412/avahi-daemon:  udp        0      0 127.0.0.1:53            0.0.0.0:*                           4375/dnsmasq     udp        0      0 0.0.0.0:68              0.0.0.0:*                           4371/dhclient    udp        0      0 0.0.0.0:5353            0.0.0.0:*                           1412/avahi-daemon:  udp6       0      0 :::58010                :::*                                1412/avahi-daemon:  udp6       0      0 :::5353                 :::*                                1412/avahi-daemon:    2. Well, there's the rootkit, the fact that my computer will only run so long after a fresh install before becoming non-functional (for any number of reasons: let me know if I should be more precise), and here's auth.log: >  Apr 11 02:42:34 ubuntu login[1952]: pam_unix(login:session): session opened for user ubuntu by (uid=0) Apr 11 02:42:34 ubuntu login[1948]: pam_unix(login:session): session opened for user ubuntu by (uid=0) Apr 11 02:42:34 ubuntu login[1963]: pam_unix(login:session): session opened for user ubuntu by (uid=0) Apr 11 02:42:34 ubuntu login[1960]: pam_unix(login:session): session opened for user ubuntu by (uid=0) Apr 11 02:42:34 ubuntu login[1961]: pam_unix(login:session): session opened for user ubuntu by (uid=0) Apr 11 02:42:44 ubuntu login[2553]: pam_unix(login:session): session opened for user ubuntu by (uid=0) Apr 11 02:42:46 ubuntu lightdm: pam_unix(lightdm-autologin:session): session opened for user ubuntu by (uid=0) Apr 11 02:42:46 ubuntu lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0 Apr 11 02:43:18 ubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session7 (system bus name :1.33 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) Apr 11 02:44:07 ubuntu dbus[1394]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.52" (uid=999 pid=3583 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=2244 comm="/usr/sbin/console-kit-daemon --no-daemon ") Apr 11 02:48:31 ubuntu dbus[1394]: [system] Rejected send message, 2 matched rules; type="method_return", sender=":1.2" (uid=0 pid=1406 comm="/usr/sbin/bluetoothd ") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.60" (uid=999 pid=3418 comm="bluetooth-applet ") Apr 11 02:48:46 ubuntu sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/usr/bin/apt-get remove --purge xserver-xorg-core-lts-quantal Apr 11 02:48:46 ubuntu sudo: pam_unix(sudo:session): session opened for user root by ubuntu(uid=999) Apr 11 02:49:13 ubuntu sudo: pam_unix(sudo:session): session closed for user root Apr 11 02:50:21 ubuntu sudo:   ubuntu : TTY=pts/0 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/bin/bash Apr 11 02:50:21 ubuntu sudo: pam_unix(sudo:session): session opened for user root by ubuntu(uid=999) Apr 11 03:17:01 ubuntu CRON[5730]: pam_unix(cron:session): session opened for user root by (uid=0) Apr 11 03:17:01 ubuntu CRON[5730]: pam_unix(cron:session): session closed for user root Apr 11 03:25:03 ubuntu sudo:   ubuntu : TTY=pts/2 ; PWD=/home/ubuntu ; USER=root ; COMMAND=/bin/bash   Here's boot.log: > stdin: error 0 Generating locales...   en_US.UTF-8... done Generation complete. pwconv: failed to change the mode of /etc/passwd- to 0600 /usr/lib/python2.7/dist-packages/LanguageSelector/LocaleInfo.py:256: UserWarning: Failed to connect to socket /var/run/dbus/system_bus_socket: No suc$   warnings.warn(msg.args[0].encode('UTF-8')) Using CD-ROM mount point /cdrom/ Identifying.. [d0c57d030ca18c0bb771d2916a23b3e7-2] Scanning disc for index files.. Found 4 package indexes, 0 source indexes, 0 translation indexes and 1 signatures Found label 'Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)' This disc is called: 'Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)' Copying package lists...gpgv: Signature made Wed Feb 13 22:21:17 2013 UTC using DSA key ID FBB75451 gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key "  Reading Package Indexes... 0%  Reading Package Indexes... 11%  Reading Package Indexes... Done  Writing new source list Source list entries for this disc are: deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/main/binary-i386/ deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ dists/precise/restricted/binary-i386/ deb cdrom:[Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)]/ precise main restricted Repeat this process for the rest of the CDs in your set. W: Skipping nonexistent file /cdrom/dists/precise/main/binary-amd64/Packages W: Skipping nonexistent file /cdrom/dists/precise/main/binary-i386/Packages W: Skipping nonexistent file /cdrom/dists/precise/restricted/binary-amd64/Packages W: Skipping nonexistent file /cdrom/dists/precise/restricted/binary-i386/Packages Adding 'diversion of /usr/bin/bluetooth-applet to /usr/bin/bluetooth-applet.orig by casper'  * Starting mDNS/DNS-SD daemon^[[164G[ OK ]  * Starting load fallback graphics devices^[[164G[ OK ]  * Stopping load fallback graphics devices^[[164G[ OK ]  * Starting configure network device security^[[164G[ OK ]  * Starting Uncomplicated firewall^[[164G[ OK ]  * Starting bluetooth daemon^[[164G[ OK ]  * Starting Mount network filesystems^[[164G[ OK ]  * Starting Failsafe Boot Delay^[[164G[ OK ]  * Stopping Mount network filesystems^[[164G[ OK ]  * Starting Bridge socket events into upstart^[[164G[ OK ]  * Starting CUPS printing spooler/server^[[164G[ OK ]  * Stopping Failsafe Boot Delay^[[164G[ OK ]  * Starting System V initialisation compatibility^[[164G[ OK ]  * Starting set sysctls from /etc/sysctl.conf^[[164G[ OK ]  * Starting configure network device security^[[164G[ OK ]  * Starting configure network device^[[164G[ OK ]  * Stopping set sysctls from /etc/sysctl.conf^[[164G[ OK ]  * Starting modem connection manager^[[164G[ OK ] * Stopping load fallback graphics devices^[[164G[ OK ]  * Starting configure network device security^[[164G[ OK ]  * Starting Uncomplicated firewall^[[164G[ OK ]  * Starting bluetooth daemon^[[164G[ OK ]  * Starting Mount network filesystems^[[164G[ OK ]  * Starting Failsafe Boot Delay^[[164G[ OK ]  * Stopping Mount network filesystems^[[164G[ OK ]  * Starting Bridge socket events into upstart^[[164G[ OK ]  * Starting CUPS printing spooler/server^[[164G[ OK ]  * Stopping Failsafe Boot Delay^[[164G[ OK ]  * Starting System V initialisation compatibility^[[164G[ OK ]  * Starting set sysctls from /etc/sysctl.conf^[[164G[ OK ]  * Starting configure network device security^[[164G[ OK ]  * Starting configure network device^[[164G[ OK ]  * Stopping set sysctls from /etc/sysctl.conf^[[164G[ OK ]  * Starting modem connection manager^[[164G[ OK ]  * Starting configure network device security^[[164G[ OK ]  * Starting configure network device^[[164G[ OK ]  * Starting network connection manager^[[164G[ OK ]  * Stopping System V initialisation compatibility^[[164G[ OK ]  * Starting System V runlevel compatibility^[[164G[ OK ]  * Starting restore sound card(s') mixer state(s)^[[164G[ OK ]  * Starting ACPI daemon^[[164G[ OK ]  * Starting save kernel messages^[[164G[ OK ]  * Starting Ubuntu live CD installer^[[164G[ OK ]  * Starting automatic crash report generation^[[164G[ OK ]  * Starting regular background program processing daemon^[[164G[ OK ]  * Starting deferred execution scheduler^[[164G[ OK ]  * Stopping Ubuntu live CD installer^[[164G[ OK ]  * Starting LightDM Display Manager^[[164G[ OK ]  * Starting CPU interrupts balancing daemon^[[164G[ OK ] speech-dispatcher disabled; edit /etc/default/speech-dispatcher  * Starting crash report submission daemon^[[164G[ OK ]  * Stopping save kernel messages^[[164G[ OK ]  * Starting network connection manager^[[164G[ OK ]  * Stopping System V initialisation compatibility^[[164G[ OK ]  * Starting System V runlevel compatibility^[[164G[ OK ]  * Starting restore sound card(s') mixer state(s)^[[164G[ OK ]  * Starting ACPI daemon^[[164G[ OK ]  * Starting save kernel messages^[[164G[ OK ]  * Starting Ubuntu live CD installer^[[164G[ OK ]  * Starting automatic crash report generation^[[164G[ OK ]  * Starting regular background program processing daemon^[[164G[ OK ]  * Starting deferred execution scheduler^[[164G[ OK ]  * Stopping Ubuntu live CD installer^[[164G[ OK ]  * Starting LightDM Display Manager^[[164G[ OK ]  * Starting CPU interrupts balancing daemon^[[164G[ OK ] speech-dispatcher disabled; edit /etc/default/speech-dispatcher  * Starting crash report submission daemon^[[164G[ OK ]  * Stopping save kernel messages^[[164G[ OK ] saned disabled; edit /etc/default/saned  I may have botched the ending, so just to be sure it terminates with:  > * Starting configure network device security^[[164G[ OK ]  * Starting configure network device^[[164G[ OK ]  * Starting network connection manager^[[164G[ OK ]  * Stopping System V initialisation compatibility^[[164G[ OK ]  * Starting System V runlevel compatibility^[[164G[ OK ]  * Starting restore sound card(s') mixer state(s)^[[164G[ OK ]  * Starting ACPI daemon^[[164G[ OK ]  * Starting save kernel messages^[[164G[ OK ]  * Starting Ubuntu live CD installer^[[164G[ OK ]  * Starting automatic crash report generation^[[164G[ OK ]  * Starting regular background program processing daemon^[[164G[ OK ]  * Starting deferred execution scheduler^[[164G[ OK ]  * Stopping Ubuntu live CD installer^[[164G[ OK ]  * Starting LightDM Display Manager^[[164G[ OK ]  * Starting CPU interrupts balancing daemon^[[164G[ OK ] speech-dispatcher disabled; edit /etc/default/speech-dispatcher  * Starting crash report submission daemon^[[164G[ OK ]  * Stopping save kernel messages^[[164G[ OK ] saned disabled; edit /etc/default/saned  3. There was some odd behavior on my mom's computer (we're sharing the same, password-protected wifi, but she has a mac): downloads such as hdderase wouldn't complete, the .Trashes folder that macs put on flashdrives contained a lot of strange files (sorry I can't name them: was a while ago), etc.  4. I'm the only user.  5. SSH, VNC, FTP, MySQL, Apache HTTP: all of these services seem to come preinstalled: though, I'm installing ubuntu desktop, not ubuntu server or cloud.  6. I think that my sources are trustworthy: just the standard sources.list fomat, no ppa.  7. Pretty sure it's WPA-protected wifi but will check in the morning.  8. I've been using ufw. Apparmor seems to come preinstalled, but maybe I should look into its configuration.  9. The computer is brand-new, always passes diagnostics tests.  10. The packages that come preinstalled, the presence of a rootkit, the faulty downloads (for instance, trying to install Debian, I get version 4 point something): all repeatable.  Happy to provide more info, and thanks!

---

### Post by stinkeye on 2013-04-11
Can you briefly summarize what your problem is?

---

### Post by mikewhatever on 2013-04-11
> **stinkeye said:**
> Can you briefly summarize what your problem is?

+1 That would have been nice.
Also post readable evidence instead of full log dumps with no spaces.

---

### Post by mastablasta on 2013-04-11
> **stinkeye said:**
> Can you briefly summarize what your problem is?


the OP thinks they have a rootkit installed and they do not know how to remove it.

the op also appears to have 2 disks in the maschine one of which is formatted in FAT32 for no known reason.

additionally they believe that various server services are installed despite using the desktop edition. which to them it is proof that malware is at work.

to the OP a.k.a. (putStrLnNick):
 use *CODE* tags to wrap your logs (icon # in forums post editor). 

Also the logs dont' seem to indicate anything unusual.

What do you mean by old kernels? Ubuntu doens't use the latest kernel. Arch linux might use it. they are usually for the more adventuorus users.

What image are you using to install the OS? Have you checked the md5sum after download?

---

### Post by putStrLnNick on 2013-04-11
Give me a break. I'm sorry for the poor formatting (it didn't look that way when I typed it out: though perhaps you expect me to know all the notational conventions in my first post); was in a hurry and didn't realize I was violating sacred laws.
In response to stinkeye, I'm sorry to say that I haven't been able to identify a single core problem. Maybe, it's just a rootkit, in which case I'd appreciate some suggestions about how I might get rid of it. Browsing the forums, I find only reinstallation as a suggested fix, but I've already tried that I'm not sure how many times, which leads me to worry that it's more than a rootkit.
I've been working on this for a while, and although I've found myself to be the source of some bugs, I simply don't know how to explain the various strange behaviors--all the more strange considered together--in terms of the relatively logical functioning I expect from a brand new computer (two, in fact). So, you want examples: I've tried working with different images (12.04, 12.10, linux mint, debian), and I always seem to get stuck with some kind of restraining packages at the outset. For one install, I'll start out with ubuntu-minimal, which seems to me harmless enough if it weren't that my attempts to install additional packages will very consistently setup replacements (update-alternatives pops up a lot during configuration) that don't always work as expected and tend to be identified as community-maintained by synaptic without me altering any default configurations; or, to take another example, I'll download the latest version of debian, and despite passing the md5 test, the live cd will give me version 4 point something and fail to detect my wifi each time; or, again, whenever I use chkrootkit, it will list users with names like "Suckit" and "FU." Though, I wouldn't use such strong labels as "proof," it's things like this that concern me. Unfortunately, my "belief" that the server services come preinstalled "despite using the desktop edition" appears more than some naive fancy, which strikes me as an odd thing: to mistakenly believe in the presence of something that isn't really there--unless you think I'm delusional. In any case, to the best of my ability, I've observed several samba packages that always seem to accompany fresh installations, and occasionally, I'll get some apache or mysql packages too. But please don't assume that I can't keep track of which packages I've downloaded against others that I take special care to avoid.
Was unaware that ubuntu doesn't use the latest kernel, thinking that kernels might be os-specific: good to know. I can't help but ask though whether 3.5.0-17, which is what I typically start out with, is normal for quantal?
I have been checking the md5sums, and mismatches have been rare.

---

### Post by squakie on 2013-04-11
Let's get this straight to the point:  you mention a rootkit - what are the SYMPTOMS that make you think you have one?  That's all people are asking - what are the SYMPTOMS?  If you're going by the logs which others have already reviewed - I'd trust what they said unless you already know the answer - if so, tell us.

---

### Post by lisati on 2013-04-11
> **putStrLnNick said:**
> I'm sorry for the poor formatting (it didn't look that way when I typed it out: though perhaps you expect me to know all the notational conventions in my first post); was in a hurry and didn't realize I was violating sacred laws.

Don't panic! It might seem a bit counter-intuitive at first, but sometimes using [noparse]```
 and 
``` tags instead of >  and [/noparse] helps preserve the formatting of quoted log files better.

---

### Post by deadflowr on 2013-04-11
You could run chkrootkit again and copy and paste the output ( using the code tags)
That way we'd have a better understanding of what it is your seeing from it.

I would at this point second and agree with earlier posts that remarked that there seems to be nothing extraordinary or wrong with the contents of the logfiles in post one.

---

### Post by DuckHook on 2013-04-11
No need to take offence. mastablasta is a regular on these forums and very helpful and welcoming to newcomers. He was not criticizing you but just offering info to better help you post--a "tip", if you will.

I don't see anything alarming in your logs either. They all look okay to me. If there is something in them that alarms you, please let us know what parts you find alarming. Perhaps we can then explain.

Having dealt with many newcomers to Linux, it is a common and natural misunderstanding to take some log entries or behaviours for malware. Windows and its accompanying anti-virus industry has so conditioned people to see threats around every corner that many will jump to the conclusion that every behaviour they are unused to or cannot explain is due to a rootkit, a Trojan or a virus. In the case of your examples:

1. I'm not sure what you mean by restraining packages, but Linux is designed to prevent you from installing things, changing system files or launching certain programs without first expressly elevating your privilege. This restraint is the way the OS is supposed to work and is not the manifestation of a rootkit.

2. Installing packages into a minimal install will drag in many dependencies because the nature of a minimal install is to initially leave everything out by default. Is this what you mean by "update-alternatives"? Since the phrase "update-alternatives" does not appear in any installation process, please provide actual samples of the output instead of paraphrasing (which we cannot work with).

3. Linux is not Windows, so most apps will not work like they do in Windows. Is this what you mean by "doesn't work as expected"? If not, please give very specific examples of unexpected behaviours that you are concerned about. That will allow us to either explain them or confirm your fears.

4. Are these precisely the info that chkrootkit returns? If so, are they part of a larger label? SU is to be expected in Linux distros. And FU or Foo is also a common occurrence.

@deadflowr is correct. It is always necessary to attach actual output. I would also refer you to [this]("http://ubuntuforums.org/showthread.php?t=1454147&page=3") thread which illustrates some common misconceptions about Linux security.

Most importantly, the following are excellent resources on basic Linux security and well worth the read:

[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://sites.google.com/site/easylinuxtipsproject/security](https://sites.google.com/site/easylinuxtipsproject/security)

---

### Post by stinkeye on 2013-04-12
I think you are being overly paranoid caused mainly by a lack of proper understanding.
chkrootkit and virus checkers often return false positives.
eg when chkrootkit is run here...
```
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED
```

...and other things like samba being installed.
Some samba packages are in the default install.... not sure why, possibly for printer sharing.

---

### Post by oldfred on 2013-04-12
Are you sure you do not have a feature - Intel SRT?
You mention Windows 8 and a small drive. That usually is a SSD used as cache for Windows. And is configured from Windows &  UEFI as Intel SRT. It may have RAID meta data still on drive. Many that use Ubuntu primarily, just install / (root) to the SSD and put data or /home on the rotating drive. 

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by putStrLnNick on 2013-04-13
Here's just the output of chkrootkit:
```
  chkrootkit
ROOTDIR is `/'
Checking `amd'...                                           not found
Checking `basename'...                                      not infected
Checking `biff'...                                          not found
Checking `chfn'...                                          not infected
Checking `chsh'...                                          not infected
Checking `cron'...                                          not infected
Checking `crontab'...                                       not infected
Checking `date'...                                          not infected
Checking `du'...                                            not infected
Checking `dirname'...                                       not infected
Checking `echo'...                                          not infected
Checking `egrep'...                                         not infected
Checking `env'...                                           not infected
Checking `find'...                                          not infected
Checking `fingerd'...                                       not found
Checking `gpm'...                                           not found
Checking `grep'...                                          not infected
Checking `hdparm'...                                        not infected
Checking `su'...                                            not infected
Checking `ifconfig'...                                      not infected
Checking `inetd'...                                         not infected
Checking `inetdconf'...                                     not found
Checking `identd'...                                        not found
Checking `init'...                                          not infected
Checking `killall'...                                       not infected
Checking `ldsopreload'...                                   not infected
Checking `login'...                                         not infected
Checking `ls'...                                            not infected
Checking `lsof'...                                          not infected
Checking `mail'...                                          not found
Checking `mingetty'...                                      not found
Checking `netstat'...                                       not infected
Checking `named'...                                         not found
Checking `passwd'...                                        not infected
Checking `pidof'...                                         not infected
Checking `pop2'...                                          not found
Checking `pop3'...                                          not found
Checking `ps'...                                            not infected
Checking `pstree'...                                        not infected
Checking `rpcinfo'...                                       not found
Checking `rlogind'...                                       not found
Checking `rshd'...                                          not found
Checking `slogin'...                                        not infected
Checking `sendmail'...                                      not infected
Checking `sshd'...                                          not found
Checking `syslogd'...                                       not tested
Checking `tar'...                                           not infected
Checking `tcpd'...                                          not infected
Checking `tcpdump'...                                       not infected
Checking `top'...                                           not infected
Checking `telnetd'...                                       not found
Checking `timed'...                                         not found
Checking `traceroute'...                                    not found
Checking `vdir'...                                          not infected
Checking `w'...                                             not infected
Checking `write'...                                         not infected
Checking `aliens'...                                        no suspect files
Searching for sniffer's logs, it may take a while...        nothing found
Searching for rootkit HiDrootkit's default files...         nothing found
Searching for rootkit t0rn's default files...               nothing found
Searching for t0rn's v8 defaults...                         nothing found
Searching for rootkit Lion's default files...               nothing found
Searching for rootkit RSHA's default files...               nothing found
Searching for rootkit RH-Sharpe's default files...          nothing found
Searching for Ambient's rootkit (ark) default files and dirs... nothing found
Searching for suspicious files and dirs, it may take a while... The following suspicious files and directories were found:  
/usr/lib/debug/.build-id /usr/lib/python2.7/dist-packages/PyQt4/uic/widget-plugins/.noinit /usr/lib/jvm/.java-1.7.0-openjdk-amd64.jinfo /usr/lib/pymodules/python2.7/.path
/usr/lib/debug/.build-id
Searching for LPD Worm files and dirs...                    nothing found
Searching for Ramen Worm files and dirs...                  nothing found
Searching for Maniac files and dirs...                      nothing found
Searching for RK17 files and dirs...                        nothing found
Searching for Ducoci rootkit...                             nothing found
Searching for Adore Worm...                                 nothing found
Searching for ShitC Worm...                                 nothing found
Searching for Omega Worm...                                 nothing found
Searching for Sadmind/IIS Worm...                           nothing found
Searching for MonKit...                                     nothing found
Searching for Showtee...                                    nothing found
Searching for OpticKit...                                   nothing found
Searching for T.R.K...                                      nothing found
Searching for Mithra...                                     nothing found
Searching for LOC rootkit...                                nothing found
Searching for Romanian rootkit...                           nothing found
Searching for Suckit rootkit...                             nothing found
Searching for Volc rootkit...                               nothing found
Searching for Gold2 rootkit...                              nothing found
Searching for TC2 Worm default files and dirs...            nothing found
Searching for Anonoying rootkit default files and dirs...   nothing found
Searching for ZK rootkit default files and dirs...          nothing found
Searching for ShKit rootkit default files and dirs...       nothing found
Searching for AjaKit rootkit default files and dirs...      nothing found
Searching for zaRwT rootkit default files and dirs...       nothing found
Searching for Madalin rootkit default files...              nothing found
Searching for Fu rootkit default files...                   nothing found
Searching for ESRK rootkit default files...                 nothing found
Searching for rootedoor...                                  nothing found
Searching for ENYELKM rootkit default files...              nothing found
Searching for common ssh-scanners default files...          nothing found
Searching for suspect PHP files...                          nothing found
Searching for anomalies in shell history files...           nothing found
Checking `asp'...                                           not infected
Checking `bindshell'...                                     not infected
Checking `lkm'...                                           You have     2 process hidden for readdir command
You have     2 process hidden for ps command
chkproc: Warning: Possible LKM Trojan installed
chkdirs: nothing detected
Checking `rexedcs'...                                       not found
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[1222], /sbin/dhclient (deleted)[14094])
Checking `w55808'...                                        not infected
Checking `wted'...                                          chkwtmp: nothing deleted
Checking `scalper'...                                       not infected
Checking `slapper'...                                       not infected
Checking `z2'...                                            user nick deleted or never logged from lastlog!
Checking `chkutmp'...                                        The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! root        20972 pts/5  synaptic
! root        21984 pts/7  /usr/bin/dpkg --status-fd 82 --configure libyaml-0-2:amd64 rkhunter:all chkrootkit:amd64 libruby1.9.1:amd64 postfix:amd64 ruby1.9.1:amd64 ruby:all unhide.rb:all
! root        29763 pts/7  /bin/sh /var/lib/dpkg/info/menu.postinst triggered /usr/share/menu
! root        29764 pts/7  update-menus --trigger
! root        29794 pts/7  /usr/bin/install-menu /etc/menu-methods/xdg-desktop-entry-spec-apps
chkutmp: nothing deleted
Checking `OSX_RSPLUG'...                                    not infected

```

---

### Post by 3rdalbum on 2013-04-13
I don't think the hidden files are anything to worry about. Hidden processes are a bit more irregular, but I think it's highly unlikely you have a rootkit, especially if you get the same warning messages from a live CD.

Anti-rootkit programs turn up a lot of false positives. They are only avenues for investigation, not definite identification.

Also, it is normal to have Samba and SSH installed by default. They are only the client software though, not the servers. If you are not running servers, it is almost impossible for you to get a rootkit.

---

### Post by DuckHook on 2013-04-13
> **3rdalbum said:**
> Anti-rootkit programs turn up a lot of false positives. They are only avenues for investigation, not definite identification.

+1
Ergo, to use a rootkit checker properly, the user should have a specific issue or occurrence in mind. Did we do something stupid recently, like install an unknown app from i-own-you.com? Do we suspect someone of physically accessing our system and installing something nasty while we weren't around? Did we run our system for a time with all ports open? Have we neglected to update our system for months? Did we visit questionable web sites with all scripts enabled and clicked "yes" to whatever it was the site asked us to do?

> If you are not running servers, it is almost impossible for you to get a rootkit.

I think I understand what @3rdalbum is trying to say here, but this is not quite accurate. Ubuntu/Linux is not a magic wand. It cannot protect people from their own foolishness or stupidity. New users on these forums constantly ask for instructions on how to:

1. nerf password challenge at login.
2. nerf authentication altogether.
3. activate root account.
4. run as root by default.
5. install every scripting language in creation on their browser, including stuff they've never heard of.
6. install the I-swear-I'm-not-a-trojan package that they downloaded from gotcha-now.ru
7. disable apparmor
8. disable Linux file and system privileges because they are "too complicated" to learn.

A user who does all of the above will have successfully turned Linux into Windows and would then be fully justified in worrying about malware.

@putStrLnNick

If there is a theme to what I'm trying to say, it is this:

Learning about chkrootkit, snort, or tripwire is all very good when the time comes, but is definitely secondary to learning about good primary practices like firewall and apparmor configuration; hardening your browser with noscript, adblock, better privacy and a cookie manager; encrypting sensitive data; and most of all, changing our security mindset from the Windows "install anti-virus and forget about it" to the far more secure "be knowledgeable and act responsibly" mindset of Linux. My advice would be to put chkrootkit aside for a time, until you are more familiar with the workings of Linux and can differentiate the false positives from the real threats. Instead, start implementing the primary security practices I've linked to in post #9. If you execute what is contained in them, I suspect that you will then greatly diminish your concerns about rootkits at all.

---

### Post by putStrLnNick on 2013-04-13
Thanks to all for the advice. Will apply it as best I can.

---

### Post by DuckHook on 2013-04-13
In all of the back-and-forth, forgot to welcome you to the forums and to Ubuntu/Linux--a place where you can forget about anti-virus and enjoy computing again.

Good luck and Happy Ubuntuing!

---


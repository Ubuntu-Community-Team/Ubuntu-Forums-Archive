---
title: "slow respond when using sudo command"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by k66473 on 2008-05-06
Hi, 
Ubuntu 8.04 of mine responds very slow when I type:
```
sudo gedit /etc/fstab
```
or
```
sudo gedit /usr/lib/vmware/share/st.txt
```
or```

sudo gnome-commander
```
System takes several minutes before window of gedit (or gnome-commander) pops up.
When that applications pop up, it acts slow too and often turn to gray color (halt or something like that)

---

### Post by subzero316 on 2008-05-06
try doing it after su command

```
su passwd
or
sudo passwd
<enter your password>

su
gedit /etc/fstab

```

---

### Post by subzero316 on 2008-05-06
try those commands  after su command

```
su passwd
```
or
```
sudo passwd
```
<enter your  password>
then, 
```

su
gedit /etc/fstabor
gedit /usr/lib/vmware/share/st.txtor
sudo gnome-commander
```

---

### Post by k66473 on 2008-05-06
I tried and it is still slow as usual

---

### Post by davidsrsb on 2008-05-06
Very delayed response sounds like a dns lookup is going on, so this may be related to the following thread:
[http://ubuntuforums.org/showthread.php?t=782567&highlight=hosts](http://ubuntuforums.org/showthread.php?t=782567&highlight=hosts)

Several users had problems with sudo and a missing /etc/hosts file entry during the beta phase.

---

### Post by k66473 on 2008-05-06
> **davidsrsb said:**
> Very delayed response sounds like a dns lookup is going on, so this may be related to the following thread:
[http://ubuntuforums.org/showthread.php?t=782567&highlight=hosts](http://ubuntuforums.org/showthread.php?t=782567&highlight=hosts)

Several users had problems with sudo and a missing /etc/hosts file entry during the beta phase.

no, this is not my trouble.
I checked the hosts file and nothing wrong there.
> 127.0.0.1 localhost
127.0.1.1 aspire

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
Above lines is the content of my /etc/hosts

---

### Post by SupaSonic on 2008-05-06
What if you use gksudo instead of sudo?

---

### Post by brian_p on 2008-05-06
> **k66473 said:**
> Hi, 
Ubuntu 8.04 of mine responds very slow when I type:
```
sudo gedit /etc/fstab
```
or
```
sudo gedit /usr/lib/vmware/share/st.txt
```
or```

sudo gnome-commander
```
System takes several minutes before window of gedit (or gnome-commander) pops up.
When that applications pop up, it acts slow too and often turn to gray color (halt or something like that)

Use top (or htop) to see what the load average is and what is using the cpu most.

---

### Post by subzero316 on 2008-05-06
Press 'CTRL+ALT+F1'....It ll enter the console mode try the same n see.

---

### Post by k66473 on 2008-05-06
in console mode, it refuses to open graphic mode

---

### Post by philinux on 2008-05-06
Look in System>Admin>System Log in particular the Auth log and others see if there are any useful entries to track this down.

---

### Post by k66473 on 2008-05-06
I find out this: When my system is offline, everything is fine. It only happens when system connects to the internet.

---

### Post by brian_p on 2008-05-06
> **k66473 said:**
> I find out this: When my system is offline, everything is fine. It only happens when system connects to the internet.

You are providing so little information that this has to a pure guess: a combination of browser and flash is using most of the cpu.

Now posting the first 10 lines or so of the output of top would help in making a judgement.

In a terminal:

```
top
```

---

### Post by k66473 on 2008-05-06
```
5607 root      20   0  225m  67m  19m S    5  3.8   0:09.04 Xorg               
 5628 root      20   0 16216 4596 1588 S    1  0.3   0:01.30 daemon.py          
 6101 minhtdvn  20   0 22480  15m 5852 S    1  0.8   0:03.42 compiz.real        
 6121 minhtdvn  20   0 22292  12m 7628 S    1  0.7   0:00.56 tray.py            
 6239 minhtdvn  20   0 75412  21m  11m S    1  1.2   0:01.68 gnome-terminal     
 6526 minhtdvn  20   0  2308 1120  852 R    1  0.1   0:00.14 top                
 6024 minhtdvn  20   0 52908  20m  13m S    0  1.1   0:02.44 gnome-panel        
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.32 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1
```

Hi, I tested this:
1. Restart the computer.
2. When log in completed, I try "sudo gedit /etc/fstab" and system run very fast.
3. I use wicd and connect to the internet, problem happens immediately, above command takes long time to respond (no firefox, no application loaded..)

Please help me. Just tell me if you need more information.

My system detail : Acer 5100, x2 Turion 1.8GHz, 2G Ram, ATi Radeon 1100

---

### Post by k66473 on 2008-05-06
> **philinux said:**
> Look in System>Admin>System Log in particular the Auth log and others see if there are any useful entries to track this down.

May  3 08:17:01 aspire CRON[12844]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 08:17:01 aspire CRON[12844]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 08:17:01 aspire CRON[12844]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 08:17:01 aspire CRON[12844]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 08:17:01 aspire CRON[12844]: pam_unix(cron:session): session closed for user root
May  3 09:17:01 aspire CRON[28542]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 09:17:01 aspire CRON[28542]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 09:17:01 aspire CRON[28542]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 09:17:01 aspire CRON[28542]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 09:17:01 aspire CRON[28542]: pam_unix(cron:session): session closed for user root
May  3 10:04:45 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 10:04:45 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 10:04:45 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 10:04:53 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  3 10:17:01 aspire CRON[12204]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 10:17:01 aspire CRON[12204]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 10:17:01 aspire CRON[12204]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 10:17:01 aspire CRON[12204]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 10:17:01 aspire CRON[12204]: pam_unix(cron:session): session closed for user root
May  3 11:17:01 aspire CRON[28652]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 11:17:01 aspire CRON[28652]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 11:17:01 aspire CRON[28652]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 11:17:01 aspire CRON[28652]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 11:17:01 aspire CRON[28652]: pam_unix(cron:session): session closed for user root
May  3 12:17:01 aspire CRON[12338]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 12:17:01 aspire CRON[12338]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 12:17:01 aspire CRON[12338]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 12:17:01 aspire CRON[12338]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 12:17:01 aspire CRON[12338]: pam_unix(cron:session): session closed for user root
May  3 13:10:56 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 13:10:56 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 13:10:56 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 13:11:00 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  3 13:17:01 aspire CRON[28521]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 13:17:01 aspire CRON[28521]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 13:17:01 aspire CRON[28521]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 13:17:01 aspire CRON[28521]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 13:17:01 aspire CRON[28521]: pam_unix(cron:session): session closed for user root
May  3 14:17:01 aspire CRON[12316]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 14:17:01 aspire CRON[12316]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 14:17:01 aspire CRON[12316]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 14:17:01 aspire CRON[12316]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 14:17:01 aspire CRON[12316]: pam_unix(cron:session): session closed for user root
May  3 15:17:01 aspire CRON[28402]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 15:17:01 aspire CRON[28402]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 15:17:01 aspire CRON[28402]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 15:17:01 aspire CRON[28402]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 15:17:01 aspire CRON[28402]: pam_unix(cron:session): session closed for user root
May  3 16:17:01 aspire CRON[12122]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 16:17:01 aspire CRON[12122]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 16:17:01 aspire CRON[12122]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 16:17:01 aspire CRON[12122]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 16:17:01 aspire CRON[12122]: pam_unix(cron:session): session closed for user root
May  3 17:17:01 aspire CRON[27929]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 17:17:01 aspire CRON[27929]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 17:17:01 aspire CRON[27929]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 17:17:01 aspire CRON[27929]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 17:17:01 aspire CRON[27929]: pam_unix(cron:session): session closed for user root
May  3 18:17:01 aspire CRON[11497]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 18:17:01 aspire CRON[11497]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 18:17:01 aspire CRON[11497]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 18:17:01 aspire CRON[11497]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 18:17:01 aspire CRON[11497]: pam_unix(cron:session): session closed for user root
May  3 19:17:01 aspire CRON[27289]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 19:17:01 aspire CRON[27289]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 19:17:01 aspire CRON[27289]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 19:17:01 aspire CRON[27289]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 19:17:01 aspire CRON[27289]: pam_unix(cron:session): session closed for user root
May  3 20:17:01 aspire CRON[10713]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 20:17:01 aspire CRON[10713]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 20:17:01 aspire CRON[10713]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 20:17:01 aspire CRON[10713]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 20:17:01 aspire CRON[10713]: pam_unix(cron:session): session closed for user root
May  3 21:17:01 aspire CRON[26484]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 21:17:01 aspire CRON[26484]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 21:17:01 aspire CRON[26484]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 21:17:01 aspire CRON[26484]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 21:17:01 aspire CRON[26484]: pam_unix(cron:session): session closed for user root
May  3 21:24:24 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 21:24:24 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 21:24:24 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 21:24:27 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  3 21:48:37 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 21:48:37 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 21:48:37 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 21:48:39 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  3 22:17:01 aspire CRON[10494]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 22:17:01 aspire CRON[10494]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 22:17:01 aspire CRON[10494]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 22:17:01 aspire CRON[10494]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 22:17:01 aspire CRON[10494]: pam_unix(cron:session): session closed for user root
May  3 23:17:01 aspire CRON[26846]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  3 23:17:01 aspire CRON[26846]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  3 23:17:01 aspire CRON[26846]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  3 23:17:01 aspire CRON[26846]: pam_unix(cron:session): session opened for user root by (uid=0)
May  3 23:17:01 aspire CRON[26846]: pam_unix(cron:session): session closed for user root
May  4 00:17:01 aspire CRON[10830]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 00:17:01 aspire CRON[10830]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 00:17:01 aspire CRON[10830]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 00:17:01 aspire CRON[10830]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 00:17:01 aspire CRON[10830]: pam_unix(cron:session): session closed for user root
May  4 01:17:01 aspire CRON[27168]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 01:17:01 aspire CRON[27168]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 01:17:01 aspire CRON[27168]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 01:17:01 aspire CRON[27168]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 01:17:01 aspire CRON[27168]: pam_unix(cron:session): session closed for user root
May  4 02:17:01 aspire CRON[11084]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 02:17:01 aspire CRON[11084]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 02:17:01 aspire CRON[11084]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 02:17:01 aspire CRON[11084]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 02:17:01 aspire CRON[11084]: pam_unix(cron:session): session closed for user root
May  4 03:17:01 aspire CRON[27249]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 03:17:01 aspire CRON[27249]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 03:17:02 aspire CRON[27249]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 03:17:02 aspire CRON[27249]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 03:17:02 aspire CRON[27249]: pam_unix(cron:session): session closed for user root
May  4 04:17:01 aspire CRON[11237]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 04:17:01 aspire CRON[11237]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 04:17:01 aspire CRON[11237]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 04:17:01 aspire CRON[11237]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 04:17:01 aspire CRON[11237]: pam_unix(cron:session): session closed for user root
May  4 05:17:01 aspire CRON[27480]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 05:17:01 aspire CRON[27480]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 05:17:01 aspire CRON[27480]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 05:17:01 aspire CRON[27480]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 05:17:01 aspire CRON[27480]: pam_unix(cron:session): session closed for user root
May  4 05:39:51 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 05:39:51 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 05:39:51 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 05:39:54 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 06:17:01 aspire CRON[11506]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 06:17:01 aspire CRON[11506]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 06:17:01 aspire CRON[11506]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 06:17:01 aspire CRON[11506]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 06:17:01 aspire CRON[11506]: pam_unix(cron:session): session closed for user root
May  4 06:25:01 aspire CRON[13736]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 06:25:02 aspire CRON[13736]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 06:25:02 aspire CRON[13736]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 06:25:02 aspire CRON[13736]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 06:25:02 aspire CRON[13736]: pam_unix(cron:session): session closed for user root
May  4 06:47:01 aspire CRON[19653]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 06:47:01 aspire CRON[19653]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 06:47:01 aspire CRON[19653]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 06:47:01 aspire CRON[19653]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 06:47:01 aspire CRON[19653]: pam_unix(cron:session): session closed for user root
May  4 07:17:01 aspire CRON[27761]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 07:17:01 aspire CRON[27761]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 07:17:01 aspire CRON[27761]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 07:17:01 aspire CRON[27761]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 07:17:01 aspire CRON[27761]: pam_unix(cron:session): session closed for user root
May  4 07:30:01 aspire CRON[31235]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 07:30:01 aspire CRON[31235]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 07:30:01 aspire CRON[31235]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 07:30:01 aspire CRON[31235]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 07:30:01 aspire CRON[31235]: pam_unix(cron:session): session closed for user root
May  4 07:35:07 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
May  4 07:35:07 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 07:35:07 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 07:35:07 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 07:35:07 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  4 07:35:07 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  4 07:35:07 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
May  4 07:35:07 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 07:35:07 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 07:35:07 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 07:35:07 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  4 07:35:07 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  4 07:35:07 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
May  4 07:35:07 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 07:35:07 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 07:35:07 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 07:35:07 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  4 07:35:07 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  4 08:17:01 aspire CRON[11737]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 08:17:01 aspire CRON[11737]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 08:17:01 aspire CRON[11737]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 08:17:01 aspire CRON[11737]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 08:17:01 aspire CRON[11737]: pam_unix(cron:session): session closed for user root
May  4 08:43:03 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 08:43:03 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 08:43:03 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 08:43:11 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 09:17:01 aspire CRON[28084]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 09:17:01 aspire CRON[28084]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 09:17:01 aspire CRON[28084]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 09:17:01 aspire CRON[28084]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 09:17:01 aspire CRON[28084]: pam_unix(cron:session): session closed for user root
May  4 10:17:01 aspire CRON[11552]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 10:17:01 aspire CRON[11552]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 10:17:01 aspire CRON[11552]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 10:17:01 aspire CRON[11552]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 10:17:01 aspire CRON[11552]: pam_unix(cron:session): session closed for user root
May  4 10:30:31 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 10:30:31 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 10:30:31 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 10:30:33 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 11:17:01 aspire CRON[27479]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 11:17:02 aspire CRON[27479]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 11:17:02 aspire CRON[27479]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 11:17:02 aspire CRON[27479]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 11:17:02 aspire CRON[27479]: pam_unix(cron:session): session closed for user root
May  4 11:43:16 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 11:43:16 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 11:43:16 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 11:43:57 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 12:17:01 aspire CRON[11331]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 12:17:01 aspire CRON[11331]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 12:17:01 aspire CRON[11331]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 12:17:01 aspire CRON[11331]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 12:17:01 aspire CRON[11331]: pam_unix(cron:session): session closed for user root
May  4 13:17:01 aspire CRON[27516]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 13:17:01 aspire CRON[27516]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 13:17:01 aspire CRON[27516]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 13:17:01 aspire CRON[27516]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 13:17:01 aspire CRON[27516]: pam_unix(cron:session): session closed for user root
May  4 14:01:30 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 14:01:30 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 14:01:30 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 14:01:33 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 14:17:01 aspire CRON[11304]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 14:17:01 aspire CRON[11304]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 14:17:01 aspire CRON[11304]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 14:17:01 aspire CRON[11304]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 14:17:01 aspire CRON[11304]: pam_unix(cron:session): session closed for user root
May  4 15:03:02 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 15:03:02 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 15:03:02 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 15:03:05 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive -o Synaptic::closeZvt=true --parent-window-id 65011715 --set-selections-file /tmp/tmp4vrB8I
May  4 15:03:05 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  4 15:03:05 aspire sudo: pam_unix(sudo:session): session closed for user root
May  4 15:14:11 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 15:14:11 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 15:14:11 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 15:14:27 aspire unix_chkpwd[27439]: password check failed for user (minhtdvn)
May  4 15:14:27 aspire gnome-screensaver-dialog: pam_unix(gnome-screensaver:auth): authentication failure; logname= uid=1000 euid=1000 tty=:0.0 ruser= rhost=  user=minhtdvn
May  4 15:14:29 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 15:14:29 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 15:14:29 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 15:14:34 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 15:17:01 aspire CRON[28155]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 15:17:01 aspire CRON[28155]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 15:17:01 aspire CRON[28155]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 15:17:01 aspire CRON[28155]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 15:17:01 aspire CRON[28155]: pam_unix(cron:session): session closed for user root
May  4 16:17:01 aspire CRON[12029]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 16:17:01 aspire CRON[12029]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 16:17:01 aspire CRON[12029]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 16:17:01 aspire CRON[12029]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 16:17:01 aspire CRON[12029]: pam_unix(cron:session): session closed for user root
May  4 16:19:02 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 16:19:02 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 16:19:02 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 17:17:01 aspire CRON[28399]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 17:17:01 aspire CRON[28399]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 17:17:01 aspire CRON[28399]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 17:17:01 aspire CRON[28399]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 17:17:01 aspire CRON[28399]: pam_unix(cron:session): session closed for user root
May  4 17:25:19 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 17:25:19 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 17:25:19 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 17:25:21 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 17:25:44 aspire gdm[5388]: pam_unix(gdm:session): session closed for user minhtdvn
May  4 17:51:39 aspire gdm[5481]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 17:51:39 aspire gdm[5481]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 17:51:39 aspire gdm[5481]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 17:51:47 aspire gdm[5481]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  4 18:15:39 aspire gdm[5481]: pam_unix(gdm:session): session closed for user minhtdvn
May  4 18:55:44 aspire gdm[5490]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 18:55:44 aspire gdm[5490]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 18:55:44 aspire gdm[5490]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 18:56:21 aspire gdm[5490]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  4 19:17:01 aspire CRON[10613]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:17:01 aspire CRON[10613]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:17:01 aspire CRON[10613]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:17:01 aspire CRON[10613]: pam_unix(cron:session): session opened for user root by (uid=0)
May  4 19:17:01 aspire CRON[10613]: pam_unix(cron:session): session closed for user root
May  4 19:18:59 aspire gnome-screensaver-dialog: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:18:59 aspire gnome-screensaver-dialog: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:18:59 aspire gnome-screensaver-dialog: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:19:02 aspire gnome-screensaver-dialog: gkr-pam: unlocked 'login' keyring
May  4 19:21:09 aspire gdm[5490]: pam_unix(gdm:session): session closed for user minhtdvn
May  4 19:21:16 aspire gdm[5490]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:21:17 aspire gdm[5490]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:21:17 aspire gdm[5490]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:21:20 aspire gdm[5490]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  4 19:23:23 aspire gdm[5490]: pam_unix(gdm:session): session closed for user minhtdvn
May  4 19:23:30 aspire gdm[14731]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:23:30 aspire gdm[14731]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:23:30 aspire gdm[14731]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:23:33 aspire gdm[14731]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  4 19:24:48 aspire gdm[14731]: pam_unix(gdm:session): session closed for user minhtdvn
May  4 19:24:55 aspire gdm[14850]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:24:55 aspire gdm[14850]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:24:55 aspire gdm[14850]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:25:02 aspire gdm[14850]: pam_nologin(gdm:auth): cannot determine username
May  4 19:26:15 aspire gdm[5523]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 19:26:15 aspire gdm[5523]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 19:26:15 aspire gdm[5523]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 19:26:19 aspire gdm[5523]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  4 19:33:20 aspire gdm[5523]: pam_unix(gdm:session): session closed for user minhtdvn
May  4 20:55:49 aspire gdm[5389]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  4 20:55:49 aspire gdm[5389]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  4 20:55:49 aspire gdm[5389]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  4 20:55:52 aspire gdm[5389]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  4 20:58:54 aspire gdm[5389]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 08:07:52 aspire gdm[5356]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 08:07:52 aspire gdm[5356]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 08:07:52 aspire gdm[5356]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 08:07:57 aspire gdm[5356]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 08:17:01 aspire CRON[18309]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 08:17:10 aspire CRON[18309]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 08:17:45 aspire CRON[18309]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 08:17:50 aspire CRON[18309]: pam_unix(cron:session): session opened for user root by (uid=0)
May  5 08:17:58 aspire CRON[18309]: pam_unix(cron:session): session closed for user root
May  5 08:43:10 aspire gdm[5356]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 08:44:14 aspire gdm[5351]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 08:44:14 aspire gdm[5351]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 08:44:14 aspire gdm[5351]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 08:44:17 aspire gdm[5351]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 08:52:22 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 08:52:22 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 08:52:22 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 08:52:23 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  5 08:52:23 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 08:52:23 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 08:55:50 aspire gdm[5351]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 08:56:55 aspire gdm[5417]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 08:56:55 aspire gdm[5417]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 08:56:55 aspire gdm[5417]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 08:56:58 aspire gdm[5417]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 09:02:03 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 09:02:03 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 09:02:03 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 09:02:05 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  5 09:02:05 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 09:02:05 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 09:04:55 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit
May  5 09:04:55 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 09:04:55 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 09:04:55 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 09:04:55 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 09:04:55 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 09:05:55 aspire gdm[5417]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 09:06:03 aspire gdm[19996]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 09:06:03 aspire gdm[19996]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 09:06:03 aspire gdm[19996]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 09:24:42 aspire gdm[5449]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 09:24:42 aspire gdm[5449]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 09:24:42 aspire gdm[5449]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 09:24:44 aspire gdm[5449]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 09:24:57 aspire gnome-keyring-daemon[5667]: adding removable location: volume_uuid_0453_8E04 at /media/SISS
May  5 09:28:44 aspire gnome-keyring-daemon[5667]: removing removable location: volume_uuid_0453_8E04
May  5 09:29:02 aspire gdm[5449]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 16:15:53 aspire gdm[5396]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:15:53 aspire gdm[5396]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:15:53 aspire gdm[5396]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:15:56 aspire gdm[5396]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 16:17:01 aspire CRON[6435]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:17:01 aspire CRON[6435]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:17:01 aspire CRON[6435]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:17:01 aspire CRON[6435]: pam_unix(cron:session): session opened for user root by (uid=0)
May  5 16:17:01 aspire CRON[6435]: pam_unix(cron:session): session closed for user root
May  5 16:20:45 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
May  5 16:20:45 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:20:45 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:20:45 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:20:45 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  5 16:20:45 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  5 16:20:45 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
May  5 16:20:45 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:20:45 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:20:45 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:20:45 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  5 16:20:45 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  5 16:20:45 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
May  5 16:20:45 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:20:45 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:20:45 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:20:45 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  5 16:20:45 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  5 16:31:21 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:31:21 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:31:21 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:31:24 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 62914563 --update-at-startup
May  5 16:31:24 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  5 16:31:24 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 16:33:11 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 62914563 --update-at-startup
May  5 16:33:11 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:33:11 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:33:11 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:33:11 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  5 16:33:11 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 16:35:02 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:35:02 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:35:02 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:35:04 aspire sudo: pam_unix(sudo:auth): authentication failure; logname=minhtdvn uid=0 euid=0 tty=/dev/pts/1 ruser= rhost=  user=minhtdvn
May  5 16:35:10 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  5 16:35:10 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 16:35:10 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 16:37:58 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/bin/mount /dev/hda /media/cdrom
May  5 16:37:58 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:37:58 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:37:58 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:37:58 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 16:37:58 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 16:39:08 aspire gdm[5396]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 16:40:12 aspire gdm[5497]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:40:12 aspire gdm[5497]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:40:12 aspire gdm[5497]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:40:15 aspire gdm[5497]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 16:56:02 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:56:02 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:56:02 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:56:03 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  5 16:56:04 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 16:56:04 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 16:58:16 aspire gdm[5497]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 16:59:21 aspire gdm[5504]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 16:59:21 aspire gdm[5504]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 16:59:21 aspire gdm[5504]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 16:59:24 aspire gdm[5504]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 17:00:47 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 17:00:47 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 17:00:47 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 17:00:50 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/jockey-gtk
May  5 17:00:50 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  5 17:00:50 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 17:03:49 aspire gdm[5504]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 17:53:54 aspire gdm[5478]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 17:53:54 aspire gdm[5478]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 17:53:54 aspire gdm[5478]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 17:53:58 aspire gdm[5478]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 18:01:25 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 18:01:25 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 18:01:25 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 18:01:27 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  5 18:01:27 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 18:01:27 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 18:04:11 aspire gdm[5478]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 18:05:14 aspire gdm[5379]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 18:05:14 aspire gdm[5379]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 18:05:14 aspire gdm[5379]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 18:05:22 aspire gdm[5379]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 18:07:53 aspire gdm[5379]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 18:43:57 aspire gdm[5437]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 18:43:57 aspire gdm[5437]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 18:43:57 aspire gdm[5437]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 18:44:03 aspire gdm[5437]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 18:44:15 aspire gnome-keyring-daemon[5657]: adding removable location: volume_uuid_4440_4B01 at /media/disk
May  5 19:02:27 aspire gnome-keyring-daemon[5657]: removing removable location: volume_uuid_4440_4B01
May  5 19:03:04 aspire gdm[5437]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 19:04:07 aspire gdm[5380]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 19:04:07 aspire gdm[5380]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 19:04:07 aspire gdm[5380]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 19:04:24 aspire gdm[5380]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 19:05:48 aspire gdm[5380]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 21:16:06 aspire gdm[5472]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 21:16:06 aspire gdm[5472]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 21:16:06 aspire gdm[5472]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 21:16:10 aspire gdm[5472]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 21:17:01 aspire CRON[6466]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 21:17:01 aspire CRON[6466]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 21:17:01 aspire CRON[6466]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 21:17:01 aspire CRON[6466]: pam_unix(cron:session): session opened for user root by (uid=0)
May  5 21:17:01 aspire CRON[6466]: pam_unix(cron:session): session closed for user root
May  5 21:30:58 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 21:30:58 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 21:30:58 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 21:31:00 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/nero
May  5 21:31:00 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 21:31:00 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 21:32:05 aspire gdm[5472]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 22:19:44 aspire gdm[5516]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 22:19:44 aspire gdm[5516]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 22:19:44 aspire gdm[5516]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 22:19:52 aspire gdm[5516]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 22:20:55 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 22:20:55 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 22:20:55 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 22:20:55 aspire sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=minhtdvn
May  5 22:25:37 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 22:25:37 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 22:25:37 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 22:28:12 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/dev ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  5 22:28:12 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 22:28:12 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 22:28:12 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 22:28:12 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  5 22:28:12 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 23:17:01 aspire CRON[16867]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 23:17:01 aspire CRON[16867]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 23:17:01 aspire CRON[16867]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 23:17:01 aspire CRON[16867]: pam_unix(cron:session): session opened for user root by (uid=0)
May  5 23:17:01 aspire CRON[16867]: pam_unix(cron:session): session closed for user root
May  5 23:19:32 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 23:19:32 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 23:19:32 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 23:19:36 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/sbin/gdmsetup
May  5 23:19:36 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  5 23:19:36 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 23:20:31 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/sbin/gdmsetup
May  5 23:20:31 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 23:20:31 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 23:20:31 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 23:20:31 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  5 23:20:31 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 23:21:03 aspire gdm[5516]: pam_unix(gdm:session): session closed for user minhtdvn
May  5 23:21:17 aspire gdm[5516]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 23:21:18 aspire gdm[5516]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 23:21:18 aspire gdm[5516]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 23:21:20 aspire gdm[5516]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  5 23:22:14 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/sbin/gdmsetup
May  5 23:22:14 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  5 23:22:14 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  5 23:22:14 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  5 23:22:14 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  5 23:22:14 aspire sudo: pam_unix(sudo:session): session closed for user root
May  5 23:34:50 aspire gdm[5516]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 07:56:22 aspire gdm[5413]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 07:56:22 aspire gdm[5413]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 07:56:22 aspire gdm[5413]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 07:56:31 aspire gdm[5413]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 08:01:14 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
May  6 08:01:14 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:01:14 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:01:14 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:01:14 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  6 08:01:14 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  6 08:01:14 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
May  6 08:01:14 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:01:14 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:01:14 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:01:14 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  6 08:01:14 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  6 08:01:14 aspire sudo:     root : TTY=unknown ; PWD=/ ; USER=minhtdvn ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
May  6 08:01:14 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:01:14 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:01:14 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:01:14 aspire sudo: pam_unix(sudo:session): session opened for user minhtdvn by (uid=0)
May  6 08:01:14 aspire sudo: pam_unix(sudo:session): session closed for user minhtdvn
May  6 08:16:22 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:16:22 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:16:22 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:16:25 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 08:16:25 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 08:16:25 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 08:17:01 aspire CRON[11017]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:17:01 aspire CRON[11017]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:17:01 aspire CRON[11017]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:17:01 aspire CRON[11017]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 08:17:01 aspire CRON[11017]: pam_unix(cron:session): session closed for user root
May  6 08:17:05 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:17:05 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:17:05 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:17:09 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; ENV=http_proxy=http://proxy.ch.alstom.com:8080/ ; COMMAND=/usr/sbin/synaptic
May  6 08:17:09 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  6 08:17:09 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 08:24:55 aspire polkit-grant-helper-pam[12066]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:24:55 aspire polkit-grant-helper-pam[12066]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:24:55 aspire polkit-grant-helper-pam[12066]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:25:01 aspire polkit-grant-helper[12063]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 11908 [uid=1000] [auth=minhtdvn]
May  6 08:46:46 aspire login[5610]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 08:46:46 aspire login[5610]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 08:46:46 aspire login[5610]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 08:46:49 aspire login[5610]: pam_unix(login:auth): check pass; user unknown
May  6 08:46:49 aspire login[5610]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=tty1 ruser= rhost= 
May  6 08:46:51 aspire login[5610]: FAILED LOGIN (1) on 'tty1' FOR `UNKNOWN', User not known to the underlying authentication module
May  6 08:46:55 aspire login[5610]: pam_unix(login:session): session opened for user minhtdvn by LOGIN(uid=0)
May  6 09:17:01 aspire CRON[18623]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 09:17:01 aspire CRON[18623]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 09:17:01 aspire CRON[18623]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 09:17:01 aspire CRON[18623]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 09:17:01 aspire CRON[18623]: pam_unix(cron:session): session closed for user root
May  6 09:18:48 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 09:18:48 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 09:18:48 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 09:18:52 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; ENV=http_proxy=http://proxy.ch.alstom.com:8080/ ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive --parent-window-id 54525955 --update-at-startup
May  6 09:18:52 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  6 09:18:52 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 09:39:04 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 09:39:04 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 09:39:04 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 09:39:06 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/nero
May  6 09:39:06 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 09:39:06 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 10:17:01 aspire CRON[26090]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 10:17:01 aspire CRON[26090]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 10:17:01 aspire CRON[26090]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 10:17:01 aspire CRON[26090]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 10:17:01 aspire CRON[26090]: pam_unix(cron:session): session closed for user root
May  6 10:56:39 aspire gdm[5413]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 10:57:45 aspire gdm[5556]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 10:57:45 aspire gdm[5556]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 10:57:45 aspire gdm[5556]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 10:57:48 aspire gdm[5556]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 11:17:01 aspire CRON[8651]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 11:17:01 aspire CRON[8651]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 11:17:01 aspire CRON[8651]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 11:17:01 aspire CRON[8651]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 11:17:01 aspire CRON[8651]: pam_unix(cron:session): session closed for user root
May  6 11:48:23 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 11:48:23 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 11:48:23 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 11:48:25 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/apt-get install build-essential
May  6 11:48:25 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 11:48:25 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 11:53:11 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 11:53:11 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 11:53:11 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 11:53:13 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/vmware-config.pl
May  6 11:53:13 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 11:53:13 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 11:55:37 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/home/minhtdvn/Desktop/vmware-any-any-update116/runme.pl
May  6 11:55:37 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 11:55:37 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 11:55:37 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 11:55:37 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 11:55:37 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 11:57:54 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn/Desktop/vmware-any-any-update116 ; USER=root ; COMMAND=./runme.pl
May  6 11:57:54 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 11:57:54 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 11:57:54 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 11:57:54 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 11:57:54 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:02:10 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/apt/sources.list
May  6 12:02:10 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:02:10 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:02:10 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:02:10 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:02:10 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:02:55 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit
May  6 12:02:55 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:02:55 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:02:55 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:02:55 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:02:55 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:05:44 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /usr/lib/vmware/share/EULA.txt
May  6 12:05:44 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:05:44 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:05:44 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:05:44 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:05:44 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:06:02 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 12:06:02 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:06:02 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:06:02 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:06:02 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:06:02 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:15:37 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/nautilus
May  6 12:15:37 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:15:37 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:15:37 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:15:37 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:15:37 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:16:11 aspire gdm[5556]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 12:17:18 aspire gdm[5425]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:17:18 aspire gdm[5425]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:17:18 aspire gdm[5425]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:17:23 aspire gdm[5425]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 12:18:02 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:18:02 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:18:02 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:18:11 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit
May  6 12:18:11 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:18:11 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:18:11 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:18:11 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:18:11 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:19:28 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 12:19:28 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:19:28 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:19:28 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:19:28 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:19:28 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:56:32 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:56:32 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:56:32 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:56:54 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/passwd
May  6 12:56:54 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:56:54 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:56:54 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:56:54 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 12:56:54 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 12:56:54 aspire passwd[11045]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:56:54 aspire passwd[11045]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:56:54 aspire passwd[11045]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 12:57:01 aspire passwd[11045]: pam_unix(passwd:chauthtok): password changed for root
May  6 12:57:54 aspire su[11230]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 12:57:54 aspire su[11230]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 12:57:54 aspire su[11230]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:00:46 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 13:00:46 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:00:46 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:00:46 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:00:46 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 13:00:46 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 13:01:38 aspire su[11694]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:01:38 aspire su[11694]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:01:38 aspire su[11694]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:01:40 aspire su[11694]: Successful su for root by minhtdvn
May  6 13:01:40 aspire su[11694]: + pts/0 minhtdvn:root
May  6 13:01:40 aspire su[11694]: pam_unix(su:session): session opened for user root by minhtdvn(uid=1000)
May  6 13:01:51 aspire sudo:     root : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 13:01:51 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:01:51 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:01:51 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:01:51 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 13:01:51 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 13:02:56 aspire su[11694]: pam_unix(su:session): session closed for user root
May  6 13:03:24 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/nautilus
May  6 13:03:24 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:03:24 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:03:24 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:03:24 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 13:03:24 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 13:15:56 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gconf-editor
May  6 13:15:56 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:15:56 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:15:56 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:15:56 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 13:15:56 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 13:17:01 aspire CRON[13707]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:17:01 aspire CRON[13707]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:17:01 aspire CRON[13707]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:17:01 aspire CRON[13707]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 13:17:01 aspire CRON[13707]: pam_unix(cron:session): session closed for user root
May  6 13:23:52 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:23:52 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:23:52 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:23:52 aspire sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=minhtdvn
May  6 13:26:45 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:26:45 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:26:45 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:26:47 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/nautilus
May  6 13:26:47 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 13:26:47 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 13:32:26 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:32:26 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:32:26 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:32:28 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/bin/rm /usr/lib/vmware/share/EULA.txt
May  6 13:32:28 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 13:32:28 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 13:32:50 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /usr/lib/vmware/share/EULA.txt
May  6 13:32:50 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 13:32:50 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 13:32:50 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 13:32:50 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 13:32:50 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 14:15:09 aspire gdm[5425]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 14:19:39 aspire gdm[5399]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:19:39 aspire gdm[5399]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:19:39 aspire gdm[5399]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:19:43 aspire gdm[5399]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 14:20:13 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:20:13 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:20:13 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:20:15 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 14:20:15 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 14:20:15 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 14:21:32 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:21:32 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:21:32 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:21:34 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit
May  6 14:21:34 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 14:21:34 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 14:22:33 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/hosts
May  6 14:22:33 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:22:33 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:22:33 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:22:33 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 14:22:33 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 14:23:23 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; ENV=http_proxy=http://proxy.ch.alstom.com:8080/ ; COMMAND=/usr/bin/gedit /etc/hosts
May  6 14:23:23 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:23:23 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:23:23 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:23:23 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 14:23:23 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 14:23:42 aspire gdm[5399]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 14:26:54 aspire gdm[5539]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:26:54 aspire gdm[5539]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:26:54 aspire gdm[5539]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:27:00 aspire gdm[5539]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 14:36:27 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:36:27 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:36:27 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:36:29 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/vmware
May  6 14:36:29 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 14:36:29 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 14:38:44 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:38:44 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:38:44 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:38:46 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/nero
May  6 14:38:46 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 14:38:46 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 14:49:03 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 14:49:03 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 14:49:03 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 14:49:07 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; ENV=http_proxy=http://proxy.ch.alstom.com:8080/ ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive -o Synaptic::closeZvt=true --parent-window-id 54525955 --set-selections-file /tmp/tmpdSOfT9
May  6 14:49:07 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  6 14:49:07 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 15:01:58 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:01:58 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:01:58 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:01:59 aspire sudo: minhtdvn : TTY=pts/2 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 15:01:59 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 15:01:59 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 15:02:23 aspire sudo: minhtdvn : TTY=pts/2 ; PWD=/home/minhtdvn ; USER=root ; ENV=http_proxy=http://proxy.ch.alstom.com:8080/ ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 15:02:23 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:02:23 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:02:23 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:02:23 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 15:02:23 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 15:02:46 aspire sudo: minhtdvn : TTY=pts/2 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 15:02:46 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:02:47 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:02:47 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:02:47 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 15:02:47 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 15:17:01 aspire CRON[1360]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:17:01 aspire CRON[1360]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:17:01 aspire CRON[1360]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:17:01 aspire CRON[1360]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 15:17:02 aspire CRON[1360]: pam_unix(cron:session): session closed for user root
May  6 15:17:23 aspire groupadd[1473]: new group: name=vboxusers, GID=124
May  6 15:37:01 aspire login[5835]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:37:01 aspire login[5835]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:37:01 aspire login[5835]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:37:02 aspire login[5835]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=tty1 ruser= rhost=  user=minhtdvn
May  6 15:37:04 aspire login[5835]: FAILED LOGIN (1) on 'tty1' FOR `minhtdvn', Authentication failure
May  6 15:37:08 aspire login[5835]: pam_unix(login:session): session opened for user minhtdvn by LOGIN(uid=0)
May  6 15:37:22 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:37:22 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:37:22 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:37:24 aspire sudo: minhtdvn : TTY=tty1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 15:37:24 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 15:37:24 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 15:37:36 aspire login[5835]: pam_unix(login:session): session closed for user minhtdvn
May  6 15:37:54 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:37:55 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:37:55 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:37:55 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 15:37:55 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 15:37:55 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 15:48:55 aspire gdm[5539]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 15:50:05 aspire gdm[5585]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 15:50:05 aspire gdm[5585]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 15:50:05 aspire gdm[5585]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 15:50:13 aspire gdm[5585]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 16:15:11 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 16:15:11 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 16:15:11 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 16:15:14 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 16:15:14 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 16:15:14 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 16:17:01 aspire CRON[12448]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 16:17:01 aspire CRON[12448]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 16:17:01 aspire CRON[12448]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 16:17:01 aspire CRON[12448]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 16:17:01 aspire CRON[12448]: pam_unix(cron:session): session closed for user root
May  6 16:19:24 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; ENV=http_proxy=http://proxy.ch.alstom.com:8080/ ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 16:19:24 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 16:19:24 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 16:19:24 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 16:19:24 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 16:19:24 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 17:17:01 aspire CRON[20185]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 17:17:01 aspire CRON[20185]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 17:17:01 aspire CRON[20185]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 17:17:01 aspire CRON[20185]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 17:17:01 aspire CRON[20185]: pam_unix(cron:session): session closed for user root
May  6 17:18:28 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 17:18:28 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 17:18:28 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 17:18:29 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 17:18:29 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 17:18:29 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 17:20:45 aspire gdm[5585]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 18:53:36 aspire gdm[5533]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 18:53:36 aspire gdm[5533]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 18:53:36 aspire gdm[5533]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 18:53:38 aspire gdm[5533]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 18:57:57 aspire gdm[5533]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 18:57:58 aspire seahorse-agent[5944]: Failed to send buffer
May  6 18:57:58 aspire seahorse-agent[5944]: Failed to send buffer
May  6 18:59:05 aspire gdm[5518]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 18:59:05 aspire gdm[5518]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 18:59:05 aspire gdm[5518]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 18:59:09 aspire gdm[5518]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 19:00:10 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:00:10 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:00:10 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:00:13 aspire sudo: minhtdvn : TTY=unknown ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/sbin/synaptic --hide-main-window --non-interactive -o Synaptic::closeZvt=true --parent-window-id 50331651 --set-selections-file /tmp/tmpaupe5a
May  6 19:00:13 aspire sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
May  6 19:00:13 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:03:53 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:03:53 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:03:53 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:03:55 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 19:03:55 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:03:55 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:04:15 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gnome-commander
May  6 19:04:15 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:04:15 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:04:15 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:04:15 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:04:15 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:04:54 aspire gdm[5518]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 19:16:54 aspire gdm[5526]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:16:54 aspire gdm[5526]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:16:54 aspire gdm[5526]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:17:01 aspire CRON[5842]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:17:01 aspire CRON[5842]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:17:01 aspire CRON[5842]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:17:01 aspire CRON[5842]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 19:17:01 aspire CRON[5842]: pam_unix(cron:session): session closed for user root
May  6 19:17:07 aspire gdm[5526]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 19:18:49 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:18:49 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:18:49 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:18:51 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn/Desktop/madwifi-ng-r2756+ar5007 ; USER=root ; COMMAND=/usr/bin/make install
May  6 19:18:51 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:18:51 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:20:05 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn/Desktop/madwifi-ng-r2756+ar5007 ; USER=root ; COMMAND=/sbin/reboot
May  6 19:20:05 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:20:05 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:20:05 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:20:05 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:20:05 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:20:06 aspire gdm[5526]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 19:21:13 aspire gdm[5580]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:21:13 aspire gdm[5580]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:21:13 aspire gdm[5580]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:21:15 aspire gdm[5580]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 19:23:08 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:23:08 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:23:08 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:23:10 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 19:23:10 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:23:10 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:49:08 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:49:08 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:49:08 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:49:09 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 19:49:09 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:49:09 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:51:36 aspire gdm[5580]: pam_unix(gdm:session): session closed for user minhtdvn
May  6 19:52:47 aspire gdm[5598]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:52:47 aspire gdm[5598]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:52:47 aspire gdm[5598]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:52:50 aspire gdm[5598]: pam_unix(gdm:session): session opened for user minhtdvn by (uid=0)
May  6 19:53:25 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:53:25 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:53:25 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:53:26 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 19:53:26 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:53:26 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:53:43 aspire sudo: minhtdvn : TTY=pts/0 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 19:53:43 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:53:43 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:53:43 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:53:43 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:53:43 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 19:54:26 aspire sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 19:54:26 aspire sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 19:54:26 aspire sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 19:54:27 aspire sudo: minhtdvn : TTY=pts/1 ; PWD=/home/minhtdvn ; USER=root ; COMMAND=/usr/bin/gedit /etc/fstab
May  6 19:54:27 aspire sudo: pam_unix(sudo:session): session opened for user root by minhtdvn(uid=0)
May  6 19:54:27 aspire sudo: pam_unix(sudo:session): session closed for user root
May  6 20:17:01 aspire CRON[12932]: PAM unable to dlopen(/lib/security/pam_smbpass.so)
May  6 20:17:01 aspire CRON[12932]: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
May  6 20:17:01 aspire CRON[12932]: PAM adding faulty module: /lib/security/pam_smbpass.so
May  6 20:17:01 aspire CRON[12932]: pam_unix(cron:session): session opened for user root by (uid=0)
May  6 20:17:01 aspire CRON[12932]: pam_unix(cron:session): session closed for user root

---

### Post by brian_p on 2008-05-06
> **k66473 said:**
> ```
5607 root      20   0  225m  67m  19m S    5  3.8   0:09.04 Xorg               
 5628 root      20   0 16216 4596 1588 S    1  0.3   0:01.30 daemon.py          
 6101 minhtdvn  20   0 22480  15m 5852 S    1  0.8   0:03.42 compiz.real        
 6121 minhtdvn  20   0 22292  12m 7628 S    1  0.7   0:00.56 tray.py            
 6239 minhtdvn  20   0 75412  21m  11m S    1  1.2   0:01.68 gnome-terminal     
 6526 minhtdvn  20   0  2308 1120  852 R    1  0.1   0:00.14 top                
 6024 minhtdvn  20   0 52908  20m  13m S    0  1.1   0:02.44 gnome-panel        
    1 root      20   0  2844 1688  544 S    0  0.1   0:01.32 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1
```

Hi, I tested this:
1. Restart the computer.
2. When log in completed, I try "sudo gedit /etc/fstab" and system run very fast.
3. I use wicd and connect to the internet, problem happens immediately, above command takes long time to respond (no firefox, no application loaded..)

Please help me. Just tell me if you need more information.

My system detail : Acer 5100, x2 Turion 1.8GHz, 2G Ram, ATi Radeon 1100

The %CPU column looks ok but there are some lines at above the ones you have given which give the load average amongst other things. What are they? What you could do is keep an eye on what top shows before and after connecting to the internet. The symptoms you describe are associated with high cpu usage by something.

Thr auth.log shows some issue with a samba password module. I don't think it is connected to your problem.

---


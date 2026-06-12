---
title: "slow login"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Stefanie on 2008-06-26
after i enter my username and password, it takes a while before my computer is fully functional (loading the panel etc). it takes about 3 minutes, not that i'm very impatient but i read on the forums that it takes only a few secs for most people :-? is this normal or is there something wrong?

---

### Post by sydbat on 2008-06-26
Can you supply the specs for your computer (processor, ram, etc)?

---

### Post by sonicskywalker on 2008-06-26
That probably is not the problem. i'm running a 500 MHz Pentium III and 448 MB of RAM with login times faster than that!

---

### Post by WRDN on 2008-06-26
Could you post a list of the processes that are running after you've logged on, and the memory they are using please. (To do this, type "top" in the terminal)

---

### Post by alienexplorers on 2008-06-26
Ihave the same problem.  It takes forever for the computer to fully load once the login and password are entered.  I timed a normal load and it takes 2 min 15 sec.  My computer data is in the signature line and note the IDE drive is a type 33.


```
tterminator@terminator-desktop:~$ top

top - 15:02:45 up 19:45,  2 users,  load average: 0.89, 0.51, 0.28
Tasks: 101 total,   2 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.9%us,  2.6%sy,  0.0%ni, 90.1%id,  0.0%wa,  0.0%hi,  1.3%si,  0.0%st
Mem:    385532k total,   314756k used,    70776k free,     7836k buffers
Swap:   987988k total,    42784k used,   945204k free,   129540k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5390 root      20   0 56888  29m 8780 R  5.0  7.8  16:36.62 Xorg               
 5878 terminat  20   0 50468  26m 8968 S  1.3  7.1   8:51.21 compiz.real        
 5727 terminat  20   0 35420  18m  12m S  0.7  5.0   7:03.36 gnome-panel        
 5737 terminat  20   0 41228 8372 6900 S  0.7  2.2   3:39.18 gnome-cups-icon    
22095 terminat  20   0 72072  18m  10m S  0.7  5.0   0:01.84 gnome-terminal     
22117 terminat  20   0  2208 1072  824 R  0.7  0.3   0:00.14 top                
 5054 root      20   0  5920 2520 1884 S  0.3  0.7   2:15.00 cupsd              
    1 root      20   0  2752 1668  524 S  0.0  0.4   0:04.06 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.18 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 khelper            
   39 root      15  -5     0    0    0 S  0.0  0.0   0:00.98 kblockd/0          
   42 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   43 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
```

---

### Post by Stefanie on 2008-06-26
output of top:

```
top - 21:14:15 up 2 min,  2 users,  load average: 3.00, 1.90, 0.75
Tasks: 102 total,   3 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.2%us,  5.1%sy,  1.5%ni,  0.0%id, 88.5%wa,  0.2%hi,  0.4%si,  0.0%st
Mem:   1027128k total,   677644k used,   349484k free,    64748k buffers
Swap:  1895660k total,        0k used,  1895660k free,   326684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6590 stefanie  39  19 29608 8356 2320 S  4.0  0.8   0:00.28 trackerd           
 5962 root      20   0  369m  44m 8944 R  3.1  4.5   0:05.52 Xorg               
 6739 stefanie  20   0  101m  19m  11m R  1.3  1.9   0:00.58 gnome-terminal     
 6459 stefanie  20   0 13476 4596 3768 S  0.9  0.4   0:00.30 at-spi-registry    
 6478 stefanie  20   0 28476 5624 3184 S  0.4  0.5   0:00.14 pulseaudio         
 6562 stefanie  20   0 19340  11m 5456 S  0.4  1.2   0:01.78 compiz.real        
 6566 stefanie  20   0 35776  23m  12m S  0.4  2.4   0:01.76 rainlendar2        
    1 root      20   0  2844 1692  544 S  0.0  0.2   0:01.56 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify   
```

I have 1GB RAM and my processor is an Intel Celeron 1.40 GHz.
there aren't a lot of programs in my startup list, i already disabled cairo-dock to see if this has an effect on the login time, but it doesn't. for the moment i'm using a background changer script and the rainlendar applet, but logging in wasn't any faster before i installed those. 

i noticed that logging in is only slow after a (re)boot. when i log out and back in it only takes 2 secs.

---

### Post by Stefanie on 2008-06-28
bump...

---

### Post by markbuntu on 2008-06-28
Tracker can really slow things down. Try turning it off in System/Preferences/Sessions.

---

### Post by Stefanie on 2008-06-28
thanks, but it didn't work.

---

### Post by markbuntu on 2008-06-28
You can try looking in your kern.log and messages and sys.log to see what is taking so long. You can find the logs in System/Administration/System Log. If one of those is not visible in the list you can use file/open to get it from the var/log directory.

The boot begins with a line: 

blah blah blah start or restart

These are all time stamped so it is easy to find gaps where something is hung up, syslog has more info but can be harder to look at since it updates all the time and you can lose your place. So look in messages or kern.log for time gaps and then in the sys.log for more info about what is using up that time.

For example I have a debugger running on gdm that I forgot to turn off and it slows down the boot by about 8-10 seconds. I found it by perusing the logs using the method above.

You can also get bum (Boot Up Manager) and stop all the stuff you don't need from loading at boot. Though you seem to have a pretty slim operation going on there some other items may be trying to load at boot unsuccessfully which will slow the process down.

---

### Post by ibbill on 2008-06-28
You may want to take a look [HERE]("http://ubuntutip.googlepages.com/bugsinubuntu")

scroll down to #3

---

### Post by Stefanie on 2008-06-29
> **markbuntu said:**
> You can try looking in your kern.log and messages and sys.log to see what is taking so long. You can find the logs in System/Administration/System Log. If one of those is not visible in the list you can use file/open to get it from the var/log directory.

The boot begins with a line: 

blah blah blah start or restart

These are all time stamped so it is easy to find gaps where something is hung up, syslog has more info but can be harder to look at since it updates all the time and you can lose your place. So look in messages or kern.log for time gaps and then in the sys.log for more info about what is using up that time.

For example I have a debugger running on gdm that I forgot to turn off and it slows down the boot by about 8-10 seconds. I found it by perusing the logs using the method above.

You can also get bum (Boot Up Manager) and stop all the stuff you don't need from loading at boot. Though you seem to have a pretty slim operation going on there some other items may be trying to load at boot unsuccessfully which will slow the process down.

thanks for your suggestion. I checked kern.log, my computer booted at 11:34:05 this morning and this is the last part of the list:
```
Jun 29 11:34:05 Stefanie kernel: [   33.739807] ACPI: \_SB_.PCI0.IDE0.SEC0.MAST: Adding notify handler
Jun 29 11:34:05 Stefanie kernel: [   33.739855] ACPI: Error installing bay notify handler
Jun 29 11:34:05 Stefanie kernel: [   33.739860] ACPI: Bay [\_SB_.PCI0.IDE0.SEC0.MAST] Added
Jun 29 11:34:06 Stefanie kernel: [   34.749579] ppdev: user-space parallel port driver
Jun 29 11:34:06 Stefanie kernel: [   34.795705] audit(1214732046.761:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5140 profile="/usr/sbin/cupsd" namespace="default"
Jun 29 11:34:13 Stefanie kernel: [   37.293311] NET: Registered protocol family 10
Jun 29 11:34:13 Stefanie kernel: [   37.293896] lo: Disabled Privacy Extensions
Jun 29 11:34:13 Stefanie kernel: [   37.295544] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 29 11:34:14 Stefanie kernel: [   37.295975] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 29 11:34:16 Stefanie kernel: [   38.955254] [drm] Initialized drm 1.1.0 20060810
Jun 29 11:34:16 Stefanie kernel: [   38.959086] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 18
Jun 29 11:34:16 Stefanie kernel: [   38.959096] PCI: Setting latency timer of device 0000:00:02.0 to 64
Jun 29 11:34:16 Stefanie kernel: [   38.959181] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jun 29 11:34:42 Stefanie kernel: [   45.336926] usb 5-6: new high speed USB device using ehci_hcd and address 2
Jun 29 11:34:42 Stefanie kernel: [   45.386624] usb 5-6: configuration #1 chosen from 1 choice
Jun 29 11:34:42 Stefanie kernel: [   45.712885] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x04A9 pid 0x1714
Jun 29 11:34:42 Stefanie kernel: [   45.712905] usbcore: registered new interface driver usblp
Jun 29 11:35:04 Stefanie kernel: [   50.827404] NET: Registered protocol family 17
Jun 29 11:35:06 Stefanie kernel: [   51.059245] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun 29 11:35:06 Stefanie kernel: [   51.098328] ieee80211_crypt: registered algorithm 'TKIP'
Jun 29 11:35:17 Stefanie kernel: [   53.581286] eth1: no IPv6 routers present
Jun 29 11:35:32 Stefanie kernel: [   63.642596] eth1: no IPv6 routers present
```

i guess there's a problem with eth1 (no IPv6 routers???) but i don't know what to do with this. eth1 is my wireless connection, i'm using it al the time and there doesn't seem to be a problem.

---

### Post by Stefanie on 2008-06-29
i checked syslog now and it seems that there is indeed a problem with my wireless card/connection. the relevant part of the log is attached.

---

### Post by markbuntu on 2008-06-29
It looks like NetworkManager is doing its thing OK. It just seems to be taking a long time figuring stuff out between  wired ethernet and wireless and which one to use and the handshaking etc, which it eventually does. Meantime the kernel is probing for stuff too like pci cards and usb stuff like your printer and talking to them and waiting for them to wake up and initialize and reply and then telling hal to use the right driver and then talking to Network Manager. 

Meantime Network Manager is trying to figure out which connection to use and trying the old key which is no longer valid and so it needs to get a new one blah blah blah, etc, etc, etc.

These things take time.

Do not worry about those dhcdbd redhat messages, they are just some leftover low priority code that no one has bothered to get rid of yet.

No IPv6 routers is not a problem, you are on IPv4.

I really don't see any problems there. You are booting up in less than 30 seconds which is pretty good actually.

But all that happens before you log in.

Are there any errors/problems in your auth.log?
gdm could be a little confused. That is the login manager.

Try logging in in gnome or gnome safe mode and see of that is quicker.

---

### Post by Stefanie on 2008-06-30
thanks! the big delay is when i log in, so i'll have a look at the other logs and post them here. it's possible that it will take a while though, i'm abroad and there doesn't seem to be a wireless network to connect to.

---

### Post by markbuntu on 2008-06-30
You may be having a problem with gdm, that is the graphical login manager, or pam may be looking for non-existent files or authorizations. look in the auth.log.

---

### Post by glennric on 2008-06-30
I suspect your problem is that you are using compiz.  Compiz slows down login a lot.  If your computer is fast enough, the slow down is not that much, but still noticeable.  If you have a slower computer you will have a long wait until it is loaded.  The more plugins and effects you activate the longer it will take to load.  The reason that it is quicker to load if you log out and log back in is that compiz is still in memory and then doesn't have to completely reload.  

In combination with the tracker daemon running, things can really get bogged down.

---

### Post by Stefanie on 2008-07-01
this is auth.log:
```
Jul  1 08:54:46 Stefanie gdm[5710]: pam_unix(gdm:session): session opened for user stefanie by (uid=0)
Jul  1 09:00:21 Stefanie sudo:     root : TTY=unknown ; PWD=/ ; USER=stefanie ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy
Jul  1 09:00:21 Stefanie sudo: pam_unix(sudo:session): session opened for user stefanie by (uid=0)
Jul  1 09:00:21 Stefanie sudo: pam_unix(sudo:session): session closed for user stefanie
Jul  1 09:00:21 Stefanie sudo:     root : TTY=unknown ; PWD=/ ; USER=stefanie ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host
Jul  1 09:00:21 Stefanie sudo: pam_unix(sudo:session): session opened for user stefanie by (uid=0)
Jul  1 09:00:21 Stefanie sudo: pam_unix(sudo:session): session closed for user stefanie
Jul  1 09:00:21 Stefanie sudo:     root : TTY=unknown ; PWD=/ ; USER=stefanie ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port
Jul  1 09:00:21 Stefanie sudo: pam_unix(sudo:session): session opened for user stefanie by (uid=0)
Jul  1 09:00:21 Stefanie sudo: pam_unix(sudo:session): session closed for user stefanie

```

i didn't know that compiz might cause a slowdown. i'm using the desktop cube, wobbly windows, minimize effects, reflection and emerald.

---


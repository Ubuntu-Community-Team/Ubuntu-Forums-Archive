---
title: "Merging partitions, Faster Boot, GRUB"
date: 2016-10-07
forum: New to Ubuntu
---

### Post by roi1207 on 2016-10-07
Hello,
Iv'e installed a fresh copy of Ubuntu 16.04LTS and I'm very happy with it.
I have a few questions though:

1. Boot up time takes forever. from the moment GRUB appears, it takes a good 2 minutes till I get to the lock screen. My computer is quite good - equipped with 8GB of ram and 500GB SSD so that isn't normal. How can I speed things up?

2. I have a backup drive (not SSD) that I accidently got split into 2 partitions. One contains my backup files, and the other is just free unallocated space. I tried merging them using GPARTED but with no avail. How can I merge them without losing my data?

3. I have an entry of Windows 7 in the GRUB loader when booting up even though the system has been deleted (result of trying a couple different linux distro's) - how can I get rid of it?

Thanks in advance :).

---

### Post by veddox on 2016-10-07
1. Sorry, don't know what might cause that. My only advice would be to reinstall from scratch, if that is a viable option. You might want to post this again as a separate question. (In general, each thread should center on one question only.)

2. How did you try to merge them? Staying with GParted, I would delete the empty partition, then expand the backup partition to fill the available space. Ought to work fine. (Don't forget to backup any vital data first, just in case...)

3. Make sure there are no Windows partitions left, then run ```
sudo update-grub
```

Hope that helps :-)

---

### Post by Bucky Ball on 2016-10-07
No idea about what the cause of 1 is, but as per veddox's remarks re. 2 and 3, with the proviso that for 2 you need to have the partition unmounted to resize them. Right click the partition in Gparted, unmount. 

Be warned: If you have any part of the system running on the partition you are unmounting this is not going to work (for instance if your /home partition is the one in question).

It is best to resize from a live session: Ubuntu install media> Try Ubuntu> launch Gparted at the desktop. That way all partitions can be unmounted (including / so be careful and just leave that alone.)

---

### Post by yancek on 2016-10-07
Are you using GParted from the installed system?  You should use it on a CD or flash drive and verify that the partition containing your backups is unmounted and you should then be able to increase its size.  The GParted Manual is at the link below and explains its use.  Scroll down to Advanced Partition Actions for info on resizing.


[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

### Post by Bucky Ball on 2016-10-07
Snap! :)

---

### Post by pfeiffep on 2016-10-07
[COLOR=#0000cd][SIZE=1]"1. Boot up time takes forever. from the moment GRUB appears, it takes a  good 2 minutes till I get to the lock screen. My computer is quite good -  equipped with 8GB of ram and 500GB SSD so that isn't normal. How can I  speed things up?"[/SIZE][/COLOR]

You might have already tried this, apologies if so.In a terminal execute```
systemd-analyze critical-chain
```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

a more complete listing is obtained with ```
systemd-analyze blame
```

Here's a [systemd cheat sheet]("https://access.redhat.com/articles/systemd-cheat-sheet")

---

### Post by roi1207 on 2016-10-08
> **pfeiffep said:**
> [COLOR=#0000cd][SIZE=1]"1. Boot up time takes forever. from the moment GRUB appears, it takes a  good 2 minutes till I get to the lock screen. My computer is quite good -  equipped with 8GB of ram and 500GB SSD so that isn't normal. How can I  speed things up?"[/SIZE][/COLOR]

You might have already tried this, apologies if so.In a terminal execute```
systemd-analyze critical-chain
```
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

a more complete listing is obtained with ```
systemd-analyze blame
```

Here's a [systemd cheat sheet]("https://access.redhat.com/articles/systemd-cheat-sheet")
What should I do with that list?
That's what I get :
```
graphical.target @1min 30.436s
&#9492;&#9472;multi-user.target @1min 30.436s
  &#9492;&#9472;getty.target @1min 30.436s
    &#9492;&#9472;getty@tty1.service @1min 30.436s
      &#9492;&#9472;rc-local.service @1min 30.412s +1ms
        &#9492;&#9472;network.target @1min 30.411s
          &#9492;&#9472;NetworkManager.service @1min 30.255s +111ms
            &#9492;&#9472;dbus.service @1min 30.231s
              &#9492;&#9472;basic.target @1min 30.217s
                &#9492;&#9472;sockets.target @1min 30.217s
                  &#9492;&#9472;snapd.socket @1min 30.215s +1ms
                    &#9492;&#9472;sysinit.target @1min 30.213s
                      &#9492;&#9472;systemd-udevd.service @6min 31.535s +21ms
                        &#9492;&#9472;systemd-tmpfiles-setup-dev.service @167ms +6ms
                          &#9492;&#9472;kmod-static-nodes.service @122ms +9ms
                            &#9492;&#9472;system.slice @105ms
                              &#9492;&#9472;-.slice @103ms


```

```
 6min 26.522s apt-daily.service
           874ms udisks2.service
           605ms dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
           568ms lvm2-monitor.service
           196ms ModemManager.service
           191ms snapd.refresh.service
           167ms accounts-daemon.service
           132ms systemd-modules-load.service
           118ms systemd-localed.service
           111ms NetworkManager.service
            97ms console-setup.service
            97ms apparmor.service
            88ms keyboard-setup.service
            87ms grub-common.service
            86ms gpu-manager.service
            85ms upower.service
            81ms apport.service
            79ms lightdm.service
            72ms systemd-logind.service
            72ms systemd-journald.service
            71ms thermald.service
            69ms irqbalance.service
            64ms avahi-daemon.service
            62ms ondemand.service
            59ms systemd-hostnamed.service
            58ms systemd-udev-trigger.service
            50ms speech-dispatcher.service
            45ms systemd-timesyncd.service
            41ms pppd-dns.service
            40ms networking.service
            38ms systemd-update-utmp.service
            31ms polkitd.service
            31ms user@1000.service
            26ms systemd-fsck@dev-disk-by\x2duuid-96868f2f\x2da00a\x2d4e10\x2d8c
            26ms plymouth-start.service
            23ms user@108.service
            22ms systemd-tmpfiles-setup.service
            22ms alsa-restore.service
            21ms systemd-tmpfiles-clean.service
            21ms plymouth-read-write.service
            21ms systemd-udevd.service
            19ms rsyslog.service
            16ms dev-mqueue.mount
            16ms systemd-journal-flush.service
            15ms plymouth-quit-wait.service
            14ms colord.service
            12ms sys-kernel-debug.mount
            12ms dev-hugepages.mount
             9ms ufw.service
             9ms rtkit-daemon.service
             9ms kmod-static-nodes.service
             8ms dns-clean.service
             7ms boot.mount
             6ms systemd-update-utmp-runlevel.service
             6ms systemd-tmpfiles-setup-dev.service
             6ms resolvconf.service
             5ms systemd-remount-fs.service
             5ms systemd-user-sessions.service
             5ms dev-mapper-ubuntu\x2d\x2dvg\x2dswap_1.swap
             4ms systemd-sysctl.service
             4ms ureadahead-stop.service
             3ms setvtrgb.service
             2ms systemd-random-seed.service
             1ms sys-fs-fuse-connections.mount
             1ms rc-local.service
             1ms snapd.socket


```

---

### Post by pfeiffep on 2016-10-08
There might be other methods for you to evaluate your system's timing; perhaps others here have ideas that will possibly help.

The cheat sheet link I provided is a list of commands that will help you discover dependencies that one service might have on another.

It's not going to be fast and maybe extremely boring but you'll be able to decide on an action plan.

The first step will be to identify which of the listed items is not required for your system ... for example do you need [COLOR=#ff0000]speech-dispatcher.service[/COLOR], or[COLOR=#ff0000] ModemManager.service
[/COLOR]
Once you've identified the items no longer required you can use the commands provided in the cheat sheet to manipulate the services.

Here's a list of commands that you can try ... _**example only - you need networking service**_

The first 4 will have no permanent affect, after a reboot the service will be in the original state 
```
systemctl list-dependencies networking.service
```

```
systemctl status networking.service
```

```
systemctl stop networking.service
```

```
systemctl start networking.service
```

These two survive a reboot
```
systemctl disable networking.service
```

```
systemctl enable networking.service
```

---

### Post by oldfred on 2016-10-08
First entry says graphical issues.
What video card/chip do you have?

---


---
title: "Fresh Kubuntu instalation, take more than 5 mins to boot in."
date: 2017-01-17
forum: New to Ubuntu
---

### Post by anishsrosevilla on 2017-01-17
I recently installed Kubuntu 16.10 on a Lenevo G50 laptop which used to run windows10 (its not duel boot now, i formated the harddisk).  It load into boot menu with out any problem. But ones I select to boot into ubuntu it takes about 5 to 8 mins to load into the login screen. The screen shows lots of activity like a terminal window, but I am unable to read it as it moves so fast and blinks. 

After it loads everything seems to run smoothly. I am using the same laptop to type this right now :-) Please help. Thanks

~~add: I dont know if this will help. 

systemd-analyze blame command and here's the result:

```
jeedhu@jeedhu--G50-30:~$ systemd-analyze blame
    6min 16.667s keyboard-setup.service
         35.976s plymouth-start.service
         34.844s apparmor.service
         34.647s plymouth-read-write.service
         33.638s apt-daily.service
          9.829s dev-mapper-kubuntu\x2d\x2dvg\x2droot.device
          7.537s lvm2-monitor.service
          6.236s systemd-udevd.service
          3.187s ModemManager.service
          3.172s accounts-daemon.service
          3.037s NetworkManager.service
          2.713s thermald.service
          2.508s irqbalance.service
          2.430s avahi-daemon.service
          1.236s grub-common.service
          1.200s systemd-fsck@dev-disk-by\x2duuid-1394d70d\x2ddd8b\x2d408f\x2d9cfc\x2d6c
          1.195s resolvconf.service
          1.096s dev-hugepages.mount
          1.082s sys-kernel-debug.mount
           990ms gpu-manager.service
           954ms dev-mqueue.mount
           950ms networking.service
           914ms systemd-modules-load.service
           837ms rsyslog.service
           830ms bluetooth.service
           775ms polkitd.service
           736ms systemd-tmpfiles-setup-dev.service
           561ms upower.service
           411ms apport.service
           407ms systemd-journald.service
           404ms udisks2.service
           347ms systemd-resolved.service
           346ms wpa_supplicant.service
           282ms kmod-static-nodes.service
lines 1-34

```

---

### Post by DuckHook on 2017-01-17
Welcome to the forums, anishsrosevilla
> **anishsrosevilla said:**
> …ones I select to boot into ubuntu it takes about 5 to 8 mins to load into the login screen.…I dont know if this will help.
It helps a lot. It is telling you that keyboard services is taking over 6.5 minutes to load. This is a long time and is highly unusual. Please post the results of:```
dmesg | egrep -i 'keyboard|error|warn'
```If this returns nothing, you will have to parse through the whole log yourself looking for anything that seems wrong. Consider using:```
dmesg | less
```Also, please post output of:```
lsusb
``````
xinput list
``````
sudo lshw -C input
```

[LIST=1]
[*]Do you have an external keyboard hooked up when you boot?
[*]If so, try disconnecting keyboard.
[*]Also, if present, is it connected to a KVM switch?
[*]If so, take out KVM and try connecting directly.
[*]If so, what make/model is external keyboard?
[/LIST]
If none of the above, then conversely, try plugging in an external USB keyboard to your computer before booting to see if that helps.

---

### Post by oldfred on 2017-01-17
This older thread mentions slow boot and keyboard issues.
[http://forums.debian.net/viewtopic.php?f=5&t=117440](http://forums.debian.net/viewtopic.php?f=5&t=117440)
But solution was mismatch on UUIDs??

Just to confirm include these in addition to DuckHook's request:
       sudo blkid -c /dev/null -o list 

            lsblk -o NAME,LABEL,SIZE,UUID,MOUNTPOINT 
cat /etc/fstab

---


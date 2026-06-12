---
title: "Ubuntu base ARMhf 16.04 boot/systemd issues"
date: 2016-06-02
forum: Programming Talk
---

### Post by iztok.jeras on 2016-06-02
Hi,

I have trouble porting Ubuntu Base 16.04 to a Xilinx Zynq board (FPGA + ARM A9). There are some issues in the boot process which are not present with Debian Jessie, and I tested with the same kernel.

First I get the next during the boot process:
```

[ TIME ] Timed out waiting for device dev-mmcblk0p1.device.
[DEPEND] Dependency failed for /opt/redpitaya.
[DEPEND] Dependency failed for Local File Systems.
[DEPEND] Dependency failed for /boot.
[DEPEND] Dependency failed for File System Check on /dev/mmcblk0p1.
[ TIME ] Timed out waiting for device dev-ttyPS0.device.

```

I tried to fix the TTY issue by following this post, there was a change but it did not help:
[http://askubuntu.com/questions/763631/console-login-on-ubuntu-core-16-04-core-armhf-tar-gz/766444](http://askubuntu.com/questions/763631/console-login-on-ubuntu-core-16-04-core-armhf-tar-gz/766444)
```

ln -s /lib/systemd/system/getty@.service /etc/systemd/system/getty.target.wants/getty@ttyPS0.service

```

Then I enabled verbosity for systemd, and copied logs to the SD card using:
```

dmesg > dmesg.log
journalctl -xb > journalctl.log

```
And this are the relevant lines from the log:
```

$ grep ttyPS0 dmesg.log 
[    0.000000] Kernel command line: console=ttyPS0,115200 root=/dev/mmcblk0p2 ro rootfstype=ext4 earlyprintk rootwait uio_pdrv_genirq.of_id=generic-uio loglevel=7 dyndbg=file axidmatest.c +p systemd.log_level=debug systemd.log_target=kmsg log_buf_len=1M
[    0.314167] xuartps e0000000.serial: ttyPS0 at MMIO 0xe0000000 (irq = 59, base_baud = 6249999) is a xuartps
[    0.775803] console [ttyPS0] enabled
[    2.400282] systemd-getty-generator[659]: Automatically adding serial getty for /dev/ttyPS0.
[    2.777643] systemd[1]: [email]serial-getty@ttyPS0.servic[/email]e: Installed new job [email]serial-getty@ttyPS0.servic[/email]e/start as 63
[    2.778090] systemd[1]: [email]getty@ttyPS0.servic[/email]e: Installed new job [email]getty@ttyPS0.servic[/email]e/start as 59
[    2.778560] systemd[1]: dev-ttyPS0.device: Installed new job dev-ttyPS0.device/start as 65
[   92.876625] systemd[1]: dev-ttyPS0.device: Job dev-ttyPS0.device/start timed out.
[   92.876655] systemd[1]: dev-ttyPS0.device: Job dev-ttyPS0.device/start finished, result=timeout
[   92.876716] systemd[1]: Timed out waiting for device dev-ttyPS0.device.
[   92.906612] systemd[1]: [email]serial-getty@ttyPS0.servic[/email]e: Job [email]serial-getty@ttyPS0.servic[/email]e/start finished, result=dependency
[   92.906672] systemd[1]: Dependency failed for Serial Getty on ttyPS0.
[   92.926620] systemd[1]: [email]serial-getty@ttyPS0.servic[/email]e: Job [email]serial-getty@ttyPS0.servic[/email]e/start failed with result 'dependency'.
[   92.926682] systemd[1]: dev-ttyPS0.device: Job dev-ttyPS0.device/start failed with result 'timeout'.
[   93.017933] systemd[1]: [email]getty@ttyPS0.servic[/email]e: Job [email]getty@ttyPS0.servic[/email]e/start finished, result=canceled
[   93.017997] systemd[1]: [email]getty@ttyPS0.servic[/email]e: Installed new job [email]getty@ttyPS0.servic[/email]e/stop as 99
[   93.336617] systemd[1]: [email]getty@ttyPS0.servic[/email]e: Job [email]getty@ttyPS0.servic[/email]e/stop finished, result=done
[   93.336674] systemd[1]: Stopped Getty on ttyPS0.

```
```

$ grep mmcblk0p1 dmesg.log 
[    2.433762] systemd-fstab-generator[658]: Found entry what=/dev/mmcblk0p1 where=/boot type=vfat nofail=no noauto=no
[    2.434063] systemd-fstab-generator[658]: Found entry what=/dev/mmcblk0p1 where=/opt/redpitaya type=vfat nofail=no noauto=no
[    2.694773] systemd[1]: dev-mmcblk0p1.mount: Failed to load configuration: No such file or directory
[    2.776662] systemd[1]: [email]systemd-fsck@dev-mmcblk0p1.servic[/email]e: Installed new job [email]systemd-fsck@dev-mmcblk0p1.servic[/email]e/start as 12
[    2.777822] systemd[1]: dev-mmcblk0p1.device: Installed new job dev-mmcblk0p1.device/start as 15
[    2.778987] systemd[1]: dev-mmcblk0p1.mount: Collecting.
[   92.926830] systemd[1]: dev-mmcblk0p1.device: Job dev-mmcblk0p1.device/start timed out.
[   92.926857] systemd[1]: dev-mmcblk0p1.device: Job dev-mmcblk0p1.device/start finished, result=timeout
[   92.926910] systemd[1]: Timed out waiting for device dev-mmcblk0p1.device.
[   92.956600] systemd[1]: [email]systemd-fsck@dev-mmcblk0p1.servic[/email]e: Job [email]systemd-fsck@dev-mmcblk0p1.servic[/email]e/start finished, result=dependency
[   92.956658] systemd[1]: Dependency failed for File System Check on /dev/mmcblk0p1.
[   93.019633] systemd[1]: [email]systemd-fsck@dev-mmcblk0p1.servic[/email]e: Job [email]systemd-fsck@dev-mmcblk0p1.servic[/email]e/start failed with result 'dependency'.
[   93.036666] systemd[1]: dev-mmcblk0p1.device: Job dev-mmcblk0p1.device/start failed with result 'timeout'.

```

I can manually get network up with:
```

ip link set eth0 up
ip addr add 192.168.178.77/24 broadcast 192.168.178.255 dev eth0
ip route add default via 192.168.178.0

```

I can mount the SD card FAT partition, as the device exists:
```

# ls -la /dev/mmcblk0p1
brw------- 1 root root 179, 1 Jan  1  1970 /dev/mmcblk0p1

```
```

mount -t vfat -o umask=000 /dev/mmcblk0p1 /boot

```

And the serial console device also exists:
```

# ls -la /dev/ttyPS0
crw------- 1 root root 248, 0 Feb 11 17:27 /dev/ttyPS0

```

I can debug this further, but without help will probably stop soon. 

Regards,
Iztok Jeras

---

### Post by iztok.jeras on 2016-06-03
for now it seems the issue was the Systemd translation of fstab into units, in fstab VFAT was mounted with options "ro,default" and it seems this created broken *.mount units, it also seems the same issue propagated to the ttyPS0 unit

I now wrote mount options as "default,ro" and it seems to work now, I also had to remove the ttyPS0 symbolic link fix, since it caused console instability (repeated text, logouts)

---


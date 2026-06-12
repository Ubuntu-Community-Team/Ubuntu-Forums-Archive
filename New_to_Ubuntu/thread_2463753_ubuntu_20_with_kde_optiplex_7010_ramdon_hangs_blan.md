---
title: "ubuntu 20 with kde optiplex 7010 ramdon hangs blank screen"
date: 2021-06-17
forum: New to Ubuntu
---

### Post by nvx0270 on 2021-06-17
Good day everyone,

Apologize if this is nothe proper subforum to post this, I've searched all forums for a similar issue without success.

While working it random hangs screen goes blank, keyboard unresponsive and cpu seems to be on.  then I force turn off with the power button and then turn on again. At the begining the issue happended from time to time, now it happens many times (5 or more) in a day. 

Any help would be appreciated .   regards.

---

### Post by oldfred on 2021-06-17
Do you have latest UEFI from Dell?
Older Haswell may not have very new UEFI, but often had several updates from when originally released.
Also is SSD using latest firmware?

If possible do not power down with power switch.
Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

Default setting now does not include all commands.
Here is a method to enable the process by editing a file:-
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = 244

REISUB - Cautions on use
[https://unix.stackexchange.com/questions/609442/whats-the-difference-between-reisub-and-a-regular-reboot](https://unix.stackexchange.com/questions/609442/whats-the-difference-between-reisub-and-a-regular-reboot)
[https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes](https://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes)
[https://ubuntuforums.org/showthread.php?t=617349](https://ubuntuforums.org/showthread.php?t=617349)

---

### Post by nvx0270 on 2021-06-17
hi oldfred, thanks for reply

not sure about the UEFI and if has latest driver, will check it today.  this a desktop pc and when hangs the keyboard turns unresponsive but will try those keypress combinations. 

will post any update. 

regards.

---

### Post by nvx0270 on 2021-06-18
yesterday updated BIOS and UEFI, worked fine .  just now about middle day crashed again. no keypress worked neither.  

is there any log file on ubuntu I could look at to search for hints this issue.

thanks

---

### Post by oldfred on 2021-06-18
Just posted this:
I get two screenfuls of warnings, but system works.
Review log files
sudo egrep -i 'warn|error' /var/log/*g

[https://ubuntuforums.org/showthread.php?t=2460294&p=14044216#post14044216](https://ubuntuforums.org/showthread.php?t=2460294&p=14044216#post14044216)

---

### Post by nvx0270 on 2021-06-18
filtered todays records and crash was about 12:40

```
cwrk01@win10std01:~$ sudo egrep -i 'warn|error' /var/log/*g | grep "Jun 18"
/var/log/kern.log:Jun 18 07:59:37 win10std01 kernel: [    0.497299] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Jun 18 07:59:37 win10std01 kernel: [    0.792484] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 07:59:37 win10std01 kernel: [    0.792495] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 07:59:37 win10std01 kernel: [    0.792499] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 07:59:37 win10std01 kernel: [    0.792502] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 07:59:37 win10std01 kernel: [    2.169632] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Jun 18 09:52:07 win10std01 kernel: [ 6756.871278] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
/var/log/kern.log:Jun 18 12:43:02 win10std01 kernel: [17012.452104] #PF: error_code(0x0000) - not-present page
/var/log/kern.log:Jun 18 12:47:32 win10std01 kernel: [    0.495284] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Jun 18 12:47:32 win10std01 kernel: [    0.783444] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 12:47:32 win10std01 kernel: [    0.783453] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 12:47:32 win10std01 kernel: [    0.783455] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 12:47:32 win10std01 kernel: [    0.783458] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20200528/utaddress-204)
/var/log/kern.log:Jun 18 12:47:32 win10std01 kernel: [    5.173444] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Jun 18 14:05:48 win10std01 kernel: [ 4704.890121] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
/var/log/syslog:Jun 18 07:59:42 win10std01 dockerd[1292]: time="2021-06-18T07:59:42.708227712-06:00" level=warning msg="Your kernel does not support CPU realtime scheduler"
/var/log/syslog:Jun 18 07:59:42 win10std01 dockerd[1292]: time="2021-06-18T07:59:42.708261490-06:00" level=warning msg="Your kernel does not support cgroup blkio weight"
/var/log/syslog:Jun 18 07:59:42 win10std01 dockerd[1292]: time="2021-06-18T07:59:42.708276413-06:00" level=warning msg="Your kernel does not support cgroup blkio weight_device"
/var/log/syslog:Jun 18 07:59:43 win10std01 VMware[init]: /usr/sbin/vmware-authdlauncher: error while loading shared libraries: libssl.so.1.0.2: cannot open shared object file: No such file or directory
/var/log/syslog:Jun 18 08:00:05 win10std01 pulseaudio[1168]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/var/log/syslog:Jun 18 08:00:05 win10std01 sddm[979]: Authentication error: "Authentication failure"
/var/log/syslog:Jun 18 08:00:08 win10std01 org.kde.KScreen[1885]: kscreen.xcb.helper: Event Error:  147
/var/log/syslog:Jun 18 08:00:18 win10std01 tracker-miner-f[1170]: Error while sending AddMatch() message: The connection is closed
/var/log/syslog:Jun 18 08:00:18 win10std01 tracker-miner-f[1170]: message repeated 2 times: [ Error while sending AddMatch() message: The connection is closed]
/var/log/syslog:Jun 18 08:00:33 win10std01 pulseaudio[1650]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/var/log/syslog:Jun 18 08:00:39 win10std01 xdg-desktop-por[1971]: Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list
/var/log/syslog:Jun 18 09:52:07 win10std01 kernel: [ 6756.871278] [drm:btc_dpm_set_power_state [radeon]] *ERROR* rv770_restrict_performance_levels_before_switch failed
dcwrk01@win10std01:~$
```

---

### Post by oldfred on 2021-06-18
Please use code tags for longer terminal output.
Easy to add with Forum's advanced Editor and # icon.  I just did that. 

Last error seems to be related to Radeon.
I do not know AMD/Radeon issues.

Found this with google on error.
[https://www.google.com/search?channel=fs&client=ubuntu&q=rv770_restrict_performance_levels_before_switch+failed](https://www.google.com/search?channel=fs&client=ubuntu&q=rv770_restrict_performance_levels_before_switch+failed)

Changed settings:
switching from "performance" to "battery" (and vice versa) did not reproduce this bug. What did reproduce the bug was switching from "balanced" and "battery" (and vice versa).

[https://bugs.freedesktop.org/show_bug.cgi?id=102511](https://bugs.freedesktop.org/show_bug.cgi?id=102511)

[https://dri-devel.freedesktop.narkive.com/FXTledTD/bug-89987-slow-vdpau-rv770-restrict-performance-levels-before-switch-failed](https://dri-devel.freedesktop.narkive.com/FXTledTD/bug-89987-slow-vdpau-rv770-restrict-performance-levels-before-switch-failed)

---

### Post by nvx0270 on 2021-06-19
Sorry for pasting the log wrong way.

But last error on log output has timestamp of 09:52  , i guess the output is not sorted by time.

/var/log/syslog:Jun 18 09:52:07 win10std01 kernel: [ 6756.871278] [drm:btc_dpm_set_power_state [radeon]] *ERROR*.

If timestamps are the same as local time, then the first message around the time it crashed would be :

/var/log/kern.log:Jun 18 12:43:02 win10std01 kernel: [17012.452104] #PF: error_code(0x0000) - not-present page

about the battery suggestion, this is a desktop pc it has no baterry at all.

---


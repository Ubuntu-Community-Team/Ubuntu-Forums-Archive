---
title: "Need help interpreting Dmesg to fix boot problem"
date: 2020-06-01
forum: New to Ubuntu
---

### Post by bradlivingstone1 on 2020-06-01
I recently added Arch to my bootable OS's and ever since then Ubuntu has been taking forever to load. 

dmesg:
> [    2.947899] logitech-hidpp-device 0003:046D:4069.0006: input,hidraw1: USB HID v1.11 Keyboard [Logitech MX Master 2S] on usb-0000:00:14.0-3.3/input2:1
[   34.038563] fbcon: Taking over console

> 
[   35.665360] audit: type=1400 audit(1591040723.289:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="libreoffice-senddoc" pid=984 comm="apparmor_parser"
[  124.374212] Bluetooth: BNEP (Ethernet Emulation) ver 1.3

I assume the large change in timestamp is what Im looking for. I'm not sure what this means or how to fix it. Any advise is welcome. 

Thanks.

---

### Post by DuckHook on 2020-06-01
Welcome to the forums bradlivingstone1,

You have good instincts. Timestamps are a good indicator and there are a number of ways to examine them.

Sometimes dmesg does not give a complete picture of the situation.

[LIST=1]
[*]I am perplexed by the fact that the trouble arose after an Arch install. Is Arch part of a multiboot? What else is being multibooted?
[*]Please post the results of: ```
sudo systemd-analyze blame
```&#8230;you need only post the first dozen or so lines.
[*]While you are at it, it wouldn't hurt to also post (in its entirety) the results of: ```
sudo systemd-analyze critical-chain
```
[*]Lets have a look at your GRUB: ```
cat /etc/default/grub
```
[*]Last but not least: ```
sudo journalctl -b -p err
```
[/LIST]
It's hard to fathom why something as simple as a keyboard device driver would hang for so long. Apparmor is a more likely culprit. The big mystery is why after an Arch install? Could this be just a coincidence? Was there a routine system update that happened around the same time?

---

### Post by bradlivingstone1 on 2020-06-01
> **DuckHook said:**
> Welcome to the forums bradlivingstone1,

You have good instincts. Timestamps are a good indicator and there are a number of ways to examine them.

Sometimes dmesg does not give a complete picture of the situation.

[LIST=1]
[*]I am perplexed by the fact that the trouble arose after an Arch install. Is Arch part of a multiboot? What else is being multibooted? 
[*]Please post the results of: ```
sudo systemd-analyze blame
```&#8230;you need only post the first dozen or so lines. 
[*]While you are at it, it wouldn't hurt to also post (in its entirety) the results of: ```
sudo systemd-analyze critical-chain
``` 
[*]Lets have a look at your GRUB: ```
cat /etc/default/grub
``` 
[*]Last but not least: ```
sudo journalctl -b -p err
``` 
[/LIST]
It's hard to fathom why something as simple as a keyboard device driver would hang for so long. Apparmor is a more likely culprit. The big mystery is why after an Arch install? Could this be just a coincidence? Was there a routine system update that happened around the same time?

I have Arch and Windows 10 also installed. 

     ```
     6.232s NetworkManager-wait-online.service
          5.024s bolt.service
          1.234s snap-clion-111.mount
          1.209s snap-clion-112.mount
          1.186s snap-gnome\x2dcalculator-730.mount
          1.176s snap-spotify-36.mount
          1.172s snap-gnome\x2dsystem\x2dmonitor-135.mount
          1.168s snap-discord-109.mount
          1.161s snap-ngrok-26.mount
          1.152s snap-code-33.mount
          1.150s snap-postman-109.mount
          1.094s snap-gnome\x2dcharacters-539.mount
          1.062s snap-heroku-3907.mount
          1.051s snap-chromium-1143.mount
          1.043s snap-gtk\x2dcommon\x2dthemes-1502.mount
          1.017s FAHClient.service
          1.013s snap-spotify-41.mount
           983ms snap-gnome\x2d3\x2d34\x2d1804-33.mount
           944ms snap-eclipse-40.mount
           941ms snap-eclipse-48.mount
           927ms snap-core-9066.mount
           920ms snap-pycharm\x2dcommunity-194.mount
           909ms snap-gnome\x2dlogs-100.mount
           909ms snap-gnome\x2d3\x2d34\x2d1804-27.mount
           905ms snap-gnome\x2dlogs-93.mount
           876ms snap-gnome\x2dsystem\x2dmonitor-145.mount
           872ms dev-loop9.device
           869ms motd-news.service
           858ms dev-loop1.device
           808ms snap-intellij\x2didea\x2dcommunity-226.mount
           770ms snap-pycharm\x2dcommunity-192.mount
           767ms dev-loop8.device
           766ms snap-core18-1754.mount
           762ms dev-loop7.device
           751ms snap-ngrok-21.mount
           678ms dev-loop13.device
           648ms dev-loop14.device
           646ms dev-loop5.device
           636ms dev-loop11.device
           606ms dev-loop0.device
           604ms snap-chromium-1165.mount
           604ms dev-sdc1.device
           589ms snap-core-8935.mount
           583ms snapd.service
           564ms snap-gnome\x2dcalculator-748.mount
           555ms dev-loop6.device
           554ms dev-loop2.device
           539ms dev-loop12.device
           529ms snap-gnome\x2d3\x2d28\x2d1804-110.mount
           527ms snap-intellij\x2didea\x2dcommunity-221.mount
           525ms dev-loop3.device
           522ms snap-gtk\x2dcommon\x2dthemes-1506.mount
           516ms systemd-fsck@dev-disk-by\x2duuid-F5A4\x2d442D.service
           514ms dev-loop16.device
           497ms dev-loop10.device
           482ms dev-loop4.device
           444ms systemd-journal-flush.service
           380ms dev-loop17.device
           374ms mysql.service
           333ms dev-loop22.device
           324ms dev-loop15.device
           323ms snap-code-32.mount
           319ms dev-loop19.device
           313ms dev-loop24.device
           311ms dev-loop23.device
           310ms systemd-resolved.service
           309ms systemd-timesyncd.service
           305ms systemd-logind.service
           268ms snapd.seeded.service
           263ms dev-loop21.device
           250ms lightdm.service
           249ms plymouth-quit-wait.service
           212ms dev-loop28.device
           208ms snap-postman-110.mount
           199ms dev-loop18.device
           192ms dev-loop33.device
           187ms dev-loop25.device
           186ms dev-loop20.device
           183ms dev-loop30.device
           177ms snap-core18-1705.mount
           173ms snap-gnome\x2d3\x2d28\x2d1804-116.mount
           165ms systemd-rfkill.service
           164ms snap-brackets-138.mount
           148ms dev-loop32.device
           144ms dev-loop34.device
           136ms apparmor.service
           136ms systemd-udev-trigger.service
           135ms snap-heroku-3929.mount
           128ms udisks2.service
           128ms snap-valgrind-46.mount
           123ms dev-loop35.device
           122ms systemd-udevd.service
           115ms snap-gnome\x2dcharacters-495.mount
           111ms systemd-tmpfiles-setup.service
           108ms dev-loop31.device
           107ms boot-efi.mount
           103ms dev-loop36.device
           103ms dev-loop29.device
            98ms networkd-dispatcher.service
            93ms dns-clean.service
            93ms dev-loop38.device
            91ms dev-loop26.device
            91ms dev-loop27.device
            83ms upower.service
            74ms ModemManager.service
            68ms virtualbox.service
            64ms NetworkManager.service
            62ms dev-loop37.device
            49ms accounts-daemon.service
            46ms grub-common.service
            38ms keyboard-setup.service
            35ms wpa_supplicant.service
            35ms systemd-journald.service
            32ms apport.service
            31ms gpu-manager.service
            25ms colord.service
            25ms dev-loop40.device
            25ms user@1000.service
            24ms plymouth-start.service
            23ms speech-dispatcher.service
            23ms systemd-tmpfiles-setup-dev.service
            20ms systemd-modules-load.service
            19ms lm-sensors.service
            18ms rsyslog.service
            18ms polkit.service
            17ms bluetooth.service
            17ms packagekit.service
            17ms plymouth-read-write.service
            17ms console-setup.service
            16ms thermald.service
            16ms nvidia-persistenced.service
            15ms networking.service
            14ms avahi-daemon.service
            13ms alsa-restore.service
            13ms systemd-sysctl.service
            10ms pppd-dns.service
             9ms rtkit-daemon.service
             8ms systemd-tmpfiles-clean.service
             7ms ureadahead-stop.service
             6ms ssh.service
             6ms ufw.service
             5ms systemd-random-seed.service
             5ms kerneloops.service
             5ms kmod-static-nodes.service
             4ms systemd-update-utmp.service
             4ms sys-kernel-debug.mount
             4ms dev-hugepages.mount
             4ms dev-loop39.device
             3ms systemd-remount-fs.service
             3ms systemd-user-sessions.service
             2ms systemd-update-utmp-runlevel.service
             2ms dev-mqueue.mount
             1ms sys-fs-fuse-connections.mount
             1ms sys-kernel-config.mount
             1ms setvtrgb.service
           425us snapd.socket
```

```
graphical.target @1min 37.568s
&#9492;&#9472;multi-user.target @1min 37.568s
  &#9492;&#9472;FAHClient.service @1min 36.550s +1.017s
    &#9492;&#9472;network-online.target @1min 36.549s
      &#9492;&#9472;NetworkManager-wait-online.service @1min 30.316s +6.232s
        &#9492;&#9472;NetworkManager.service @1min 30.250s +64ms
          &#9492;&#9472;dbus.service @1min 30.242s
            &#9492;&#9472;basic.target @1min 30.229s
              &#9492;&#9472;sockets.target @1min 30.229s
                &#9492;&#9472;snapd.socket @1min 30.229s +425us
                  &#9492;&#9472;sysinit.target @1min 30.225s
                    &#9492;&#9472;systemd-timesyncd.service @1.552s +309ms
                      &#9492;&#9472;systemd-tmpfiles-setup.service @1.439s +111ms
                        &#9492;&#9472;local-fs.target @1.437s
                          &#9492;&#9472;run-user-1000-gvfs.mount @1min 39.443s
                            &#9492;&#9472;run-user-1000.mount @1min 39.312s
                              &#9492;&#9472;local-fs-pre.target @237ms
                                &#9492;&#9472;keyboard-setup.service @198ms +38ms
                                  &#9492;&#9472;systemd-journald.socket @192ms
                                    &#9492;&#9472;system.slice @192ms
                                      &#9492;&#9472;-.slice @191ms


```

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

```
-- Logs begin at Sat 2020-01-11 07:26:20 PST, end at Mon 2020-06-01 17:41:23 PDT. --
Jun 01 12:46:51 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 12:46:52 Mark-Ubuntu wpa_supplicant[1167]: dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
Jun 01 12:46:52 Mark-Ubuntu wpa_supplicant[1167]: dbus: Failed to construct signal
Jun 01 12:46:54 Mark-Ubuntu lightdm[1439]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jun 01 12:46:54 Mark-Ubuntu lightdm[1439]: PAM adding faulty module: pam_kwallet.so
Jun 01 12:46:54 Mark-Ubuntu lightdm[1439]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Jun 01 12:46:54 Mark-Ubuntu lightdm[1439]: PAM adding faulty module: pam_kwallet5.so
Jun 01 12:46:54 Mark-Ubuntu wpa_supplicant[1167]: bgscan simple: Failed to enable signal strength monitoring
Jun 01 12:46:54 Mark-Ubuntu lightdm[1607]: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jun 01 12:46:54 Mark-Ubuntu lightdm[1607]: PAM adding faulty module: pam_kwallet.so
Jun 01 12:46:54 Mark-Ubuntu lightdm[1607]: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Jun 01 12:46:54 Mark-Ubuntu lightdm[1607]: PAM adding faulty module: pam_kwallet5.so
Jun 01 12:46:59 Mark-Ubuntu pulseaudio[1550]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Jun 01 12:46:59 Mark-Ubuntu pulseaudio[1775]: [pulseaudio] pid.c: Daemon already running.
Jun 01 12:47:06 Mark-Ubuntu pulseaudio[1975]: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
Jun 01 12:47:07 Mark-Ubuntu spice-vdagent[2068]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
Jun 01 12:48:22 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 12:50:23 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 13:02:35 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 14:02:23 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 14:20:28 Mark-Ubuntu kernel: Bluetooth: hci0: SCO packet for unknown connection handle 71
Jun 01 14:20:28 Mark-Ubuntu kernel: Bluetooth: hci0: SCO packet for unknown connection handle 71
Jun 01 14:20:28 Mark-Ubuntu kernel: Bluetooth: hci0: SCO packet for unknown connection handle 71
Jun 01 14:30:24 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 14:32:19 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 14:35:45 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 15:02:41 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 15:09:46 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 15:20:59 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 16:05:23 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
Jun 01 17:04:58 Mark-Ubuntu systemd[1]: Timed out waiting for device dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca.device.
```

---

### Post by DuckHook on 2020-06-01
If you change the following line in GRUB from: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```…to: ```
GRUB_CMDLINE_LINUX_DEFAULT=""
```…then: ```
sudo update-grub
```…it will eliminate the masking splash screen from your boot process and give you verbose output. Though the results are not as "pretty", seeing all of the processes as they are being loaded is far more informative. It gives you the chance to see which process is holding everything up before timing out.

In doing so, I suspect you will find that your boot process is stalling at trying to find the disk device that systemd identifies as: ```
dev-disk-by\x2duuid-49c99646\x2d86ab\x2d4723\x2da8e3\x2d169eb3e787ca
```As one completely wild guess, this may be a disk partition that you initially set up for some purpose in Ubuntu, but was then either deleted or co&#8209;opted and assigned a different ID by Arch. Ubuntu can no longer find this device and waits for it during the boot process. The usual countdown timer is 90 seconds for disk devices, but it may occur multiple times through a boot process depending on what the original device was used for.

You can either change Ubuntu's settings to point to the new ID number of the missing device, recreate the device, or delete the Ubuntu setting if that won't destabilize your system.

It is also possible that you've defined a network drive in fstab that the installation of Arch has somehow nerfed. If a network drive cannot be accessed, the same problem may show up.

Sorry I can't be more specific, but I really have no idea what the details are in your case based on the info posted. Every system is different and I've never multi-booted with Arch before so I have nothing to experiment on.

---

### Post by bradlivingstone1 on 2020-06-01
Googled the lines that were hanging, Found them [here]("https://askubuntu.com/questions/711016/slow-boot-a-start-job-is-running-for-dev-disk-by") and [here]("https://askubuntu.com/questions/1034359/boot-hangs-for-30-seconds-at-begin-running-scripts-local-premount"). I solved the first however the second eludes me. I still think the problem is with my swap partition since Im using the same swap partition for my arch installation, (is that oK?) . Ive set the UUID in /etc/fstab and lsblk identifies the partition as swap. Is there anything else I could check?

---

### Post by DuckHook on 2020-06-02
> **bradlivingstone1 said:**
> …I still think the problem is with my swap partition since Im using the same swap partition for my arch installation, (is that oK?) . Ive set the UUID in /etc/fstab and lsblk identifies the partition as swap. Is there anything else I could check?
Ah!

That's an awfully good showing of detective work and self-reliance. So you did share the swap between Ubuntu and Arch. That is more than likely the culprit right there.

I use the same swap between my three multiboots. It's not a problem so long as you don't hibernate. It becomes a *big* problem if you do. Many of the gurus on this forum will advise against it for that reason alone. There are other reasons such as a marginally increased security risk. For general info, it is not necessary to even define a swap partition for Ubuntu these days. The OS will automatically create a swap file if needed.

But the biggest problem with sharing swap is the one you just experienced: by pointing Arch to that existing partition, the Arch install process automatically assigned it a new ID. When your existing Ubuntu install then tried to access it using its old ID, it was no longer there. Based on your description, you have already corrected your mistake by changing the partition ID in *fstab* to the new one. This should now correct the problem and you should be good to go.

If you implement the GRUB change that I posted earlier, it will allow you to see if any other processes are holding you up at boot. Personally, I far prefer knowing what is going on at boot than being blithely blind to anything that is going on under the hood.

If this problem is solved, please remember to mark it so by using the "Thread Tools" pull-down at the top of the thread.

---

### Post by bradlivingstone1 on 2020-06-02
The way that I figured out which lines were hanging was by following your advice to show the processes. Do you have any experience with > Begin: Running /scripts/local-premount hanging?

---

### Post by DuckHook on 2020-06-02
Try:```
cat /etc/initramfs-tools/conf.d/resume
```If the UUID after: ```
RESUME=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```…is still your old swap UUID, then edit with: ```
sudo nano /etc/initramfs-tools/conf.d/resume
```…and replace it with your new proper UUID.

This file is used to set the proper partition for resume from hibernation. If you never use hibernate, you can just edit it to read: ```
RESUME=none
```
You may need to rebuild your initramfs: ```
sudo update-initramfs -u
reboot
```

---


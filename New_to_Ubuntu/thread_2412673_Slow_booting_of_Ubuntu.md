---
title: "Slow booting of Ubuntu?"
date: 2019-02-15
forum: New to Ubuntu
---

### Post by cdnhermit on 2019-02-15
Hello, How long should it take for Ubuntu 18.04.01 to load?  From the end of  bios screen delay to my password entry screen it takes 2 ½ minutes. Is it normal?
I am not using VM or anything similar.

Ubuntu 18.04.01
external ssd samsung 860 pro in a NexStar GX usb 3.1 Gen 2 tpe C with corresponding usb cable.
intel i7 8700k
Asus Prime Z370-A
64 Gb RAM

---

### Post by Autodave on 2019-02-15
Booting from an external HD is going to be longer than an internal unit.  What graphics card are you using?  Did you install any drivers for it?  If so, what one and where did you get it from?

Keep in mind that Win10 doesn't boot anywhere near that quickly.  It appears to, but it doesn't really shut down: it hibernates.

---

### Post by cdnhermit on 2019-02-15
Booting from an external ssd should not take that long in my opinion. I tried that with Win10 a while back (doing a disk copy) and I did not notice any appreciable difference. The graphic card used by Ubuntu I don't know. I have an integrated Intel graphic card that comes with my Asus prime z370-A motherboard. I also have   installed Asus geoforce gtx1060 but nothing is plug on it at the moment. NVidea drivers appear to have been installed. Also, I noticed that it took about 30 sec to lrun; the following command:
> daniel@daniel-pc:~$ systemd-analyze blame
Bootup is not yet finished. Please try again later.

Il ran 2 commands one that redirect to a file and the following and I am perplexe.

According to that comnand, it looks like part of the booting process is done twice.
> daniel@daniel-pc:~$ systemd-analyze blame
          5.081s bolt.service
          4.136s plymouth-quit-wait.service
          2.104s dev-sda2.device
          1.770s NetworkManager-wait-online.service
           846ms fwupd.service
           699ms alsa-restore.service
           694ms snapd.service
           675ms keyboard-setup.service
           664ms systemd-journald.service
           656ms systemd-modules-load.service
           633ms systemd-tmpfiles-setup-dev.service
           588ms plymouth-start.service
           549ms systemd-journal-flush.service
           537ms systemd-logind.service
           407ms dev-loop23.device
[B]           5.081s bolt.service
          4.136s plymouth-quit-wait.service
          2.104s dev-sda2.device
          1.770s NetworkManager-wait-online.service
           846ms fwupd.service
           699ms alsa-restore.service
           694ms snapd.service
           675ms keyboard-setup.service
           664ms systemd-journald.service
           656ms systemd-modules-load.service
           633ms systemd-tmpfiles-setup-dev.service
           588ms plymouth-start.service
           549ms systemd-journal-flush.service
           537ms systemd-logind.service
           407ms dev-loop23.device
           [/B]406ms dev-loop6.device
           403ms dev-loop15.device
           400ms dev-loop24.device
           393ms dev-loop17.device
           392ms snap-core18-719.mount
           392ms snap-gimp-113.mount
           390ms dev-loop25.device
           381ms dev-loop26.device
           378ms dev-loop19.device
           376ms dev-loop21.device
           374ms dev-loop27.device
           369ms dev-loop8.device
           366ms dev-loop28.device
           360ms dev-loop29.device
           360ms dev-loop16.device
           360ms dev-loop20.device
           357ms dev-loop22.device
           356ms dev-loop13.device
           355ms dev-loop18.device
           354ms dev-loop34.device
           354ms dev-loop30.device
           352ms snap-core18-677.mount
           352ms NetworkManager.service
           348ms dev-loop31.device
           346ms snap-gnome\x2d3\x2d26\x2d1604-78.mount
           338ms dev-loop32.device
           335ms dev-loop7.device
           316ms snap-core-6350.mount
           314ms dev-loop11.device
           312ms udisks2.service
           304ms dev-loop10.device
           302ms snap-gnome\x2dcalculator-180.mount
           301ms dev-loop33.device
           300ms dev-loop9.device


However I redirected the output to a file and I got the following:
>           5.081s bolt.service
          4.136s plymouth-quit-wait.service
          2.104s dev-sda2.device
          1.770s NetworkManager-wait-online.service
           846ms fwupd.service
           699ms alsa-restore.service
           694ms snapd.service
           675ms keyboard-setup.service
           664ms systemd-journald.service
           656ms systemd-modules-load.service
           633ms systemd-tmpfiles-setup-dev.service
           588ms plymouth-start.service
           549ms systemd-journal-flush.service
           537ms systemd-logind.service
           407ms dev-loop23.device
           406ms dev-loop6.device
           403ms dev-loop15.device
           400ms dev-loop24.device
           393ms dev-loop17.device
           392ms snap-core18-719.mount
           392ms snap-gimp-113.mount
           390ms dev-loop25.device
           381ms dev-loop26.device
           378ms dev-loop19.device
           376ms dev-loop21.device
           374ms dev-loop27.device
           369ms dev-loop8.device
           366ms dev-loop28.device
           360ms dev-loop29.device
           360ms dev-loop16.device
           360ms dev-loop20.device
           357ms dev-loop22.device
           356ms dev-loop13.device
           355ms dev-loop18.device
           354ms dev-loop34.device
           354ms dev-loop30.device
           352ms snap-core18-677.mount
           352ms NetworkManager.service
           348ms dev-loop31.device
           346ms snap-gnome\x2d3\x2d26\x2d1604-78.mount
           338ms dev-loop32.device
           335ms dev-loop7.device
           316ms snap-core-6350.mount
           314ms dev-loop11.device
           312ms udisks2.service
           304ms dev-loop10.device
           302ms snap-gnome\x2dcalculator-180.mount
           301ms dev-loop33.device
           300ms dev-loop9.device
           294ms snap-core18-594.mount
           284ms dev-loop14.device
           284ms dev-loop0.device
           282ms snap-gtk\x2dcommon\x2dthemes-818.mount
           278ms snap-gnome\x2dcharacters-139.mount
           266ms snap-p7zip\x2ddesktop-163.mount
           265ms gpu-manager.service
           258ms snap-notepad\x2dplus\x2dplus-185.mount
           251ms snap-chromium-595.mount
           246ms dev-loop3.device
           240ms snap-notepad\x2dplus\x2dplus-184.mount
           240ms snap-chromium-566.mount
           238ms dev-loop2.device
           235ms dev-loop1.device
           234ms dev-loop4.device
           223ms snap-gnome\x2dlogs-45.mount
           212ms dev-loop5.device
           211ms dev-loop12.device
           208ms snap-core-6405.mount
           207ms snap-gtk\x2dcommon\x2dthemes-1122.mount
           192ms snap-wine\x2dplatform-58.mount
           190ms snap-gimp-105.mount
           189ms systemd-resolved.service
           186ms snap-core-6259.mount
           173ms snap-inkscape-4693.mount
           168ms systemd-timesyncd.service
           167ms snap-inkscape-4690.mount
           165ms snap-gnome\x2d3\x2d26\x2d1604-70.mount
           158ms grub-common.service
           152ms snap-notepad\x2dplus\x2dplus-173.mount
           147ms snap-gnome\x2dcalculator-260.mount
           144ms snap-gnome\x2dsystem\x2dmonitor-57.mount
           124ms snap-wine\x2dplatform-74.mount
           124ms snap-skype-66.mount
           123ms speech-dispatcher.service
           120ms snap-gnome\x2dsystem\x2dmonitor-51.mount
           119ms systemd-remount-fs.service
           119ms sys-kernel-debug.mount
           118ms dev-hugepages.mount
           117ms dev-mqueue.mount
           110ms ModemManager.service
           108ms snap-gimp-110.mount
           106ms snap-gnome\x2d3\x2d26\x2d1604-74.mount
           103ms colord.service
           100ms gdm.service
            99ms snap-gtk\x2dcommon\x2dthemes-319.mount
            94ms accounts-daemon.service
            91ms snap-gnome\x2dcharacters-103.mount
            87ms snap-gnome\x2dlogs-37.mount
            80ms apparmor.service
            77ms apport.service
            75ms networkd-dispatcher.service
            74ms avahi-daemon.service
            72ms upower.service
            70ms lm-sensors.service
            67ms mono-xsp4.service
            65ms snap-vlc-770.mount
            63ms pppd-dns.service
            48ms [email]user@121.servic[/email]e
            48ms home.mount
            45ms systemd-udevd.service
            43ms [email]systemd-fsck@dev-disk-by\x2duuid-99089c4e\x2d76d6\x2d4387\x2d9687\x2dc362ccf2a1ff.servic[/email]e
            37ms systemd-udev-trigger.service
            36ms [email]user@1000.servic[/email]e
            28ms wpa_supplicant.service
            27ms thermald.service
            25ms rsyslog.service
            23ms kmod-static-nodes.service
            22ms boot-efi.mount
            19ms plymouth-read-write.service
            18ms systemd-update-utmp.service
            18ms packagekit.service
            17ms snapd.seeded.service
            14ms networking.service
            14ms binfmt-support.service
            12ms ufw.service
            11ms [email]systemd-fsck@dev-disk-by\x2duuid-FCCE\x2d7900.servic[/email]e
            11ms systemd-sysctl.service
             7ms ureadahead-stop.service
             6ms systemd-tmpfiles-setup.service
             5ms polkit.service
             5ms kerneloops.service
             4ms proc-sys-fs-binfmt_misc.mount
             3ms dns-clean.service
             2ms systemd-update-utmp-runlevel.service
             2ms snapd.socket
             2ms systemd-random-seed.service
             2ms systemd-user-sessions.service
             2ms rtkit-daemon.service
             1ms console-setup.service
             1ms sys-fs-fuse-connections.mount
             1ms nvidia-persistenced.service
             1ms sys-kernel-config.mount
             1ms setvtrgb.service

---

### Post by oldfred on 2019-02-16
My system went slow for a bit. Back in 2017 which would have been 16.04, it was 10 or 11 sec
Then it went to 23 sec to desktop but said it took 9 minutes to fully boot. I had that same note that system was not done booting.
Then it now has settled down, but still over 20 sec.

I found I had installed apache & mysql from old list of apps, but have never used them, so uninstalled them. I also uninstalled all snaps. but those changes were not the main issue which just went away with updates & reboots.

       May 25th 2017
fred@Z170N:~$ systemd-analyze 
Startup finished in 2.435s (kernel) + 8.703s (userspace) = 11.139s
Removed apache & mysql
fred@Z170N:~$ systemd-analyze 
Startup finished in 2.510s (kernel) + 7.536s (userspace) = 10.047s
fred@Bionic-Z170N:~$ systemd-analyze
Startup finished in 9min 10.611s (firmware) + 2.221s (loader) + 2.853s (kernel) + 23.190s (userspace) = 9min 38.877s
graphical.target reached after 23.185s in userspace
fred@Bionic-Z170N:~$  systemd-analyze
Startup finished in 2.932s (kernel) + 23.132s (userspace) = 26.064s

---


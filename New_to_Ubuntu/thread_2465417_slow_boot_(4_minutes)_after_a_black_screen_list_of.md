---
title: "slow boot (4 minutes) after a black screen list of problems."
date: 2021-08-01
forum: New to Ubuntu
---

### Post by renekert on 2021-08-01
Surely the details of the boot.repair utility will be better than any thing that I cuold write.
[http://paste.ubuntu.com/p/g6jKWsz7rk/](http://paste.ubuntu.com/p/g6jKWsz7rk/)
Thank you for any guidance you could give me
Enrique.

---

### Post by oldfred on 2021-08-01
Your 4 minutes does seem high.
Your report does not show any issues, standard older BIOS boot with MBR partitions.

Post these
 systemd-analyze
#only post first page, control C to exit
systemd-analyze blame

Some things to review:
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

---

### Post by renekert on 2021-08-02
Many thanks, oldfred, 
. . . If I understood your sugestion:
My terminal answers,
On "systemd-analyse", only this:
Startup finished in 6.032s (kernel) + 3min 20.364s (userspace) = 3min 26.396s
graphical.target reached after 3min 12.113s in userspace
. . . . I do not know what it means, but "userspace" sounds as my fault.

On "systemd-analyze blame" the answer is:
    1min 42.239s apt-daily.service
    1min 35.106s teamviewerd.service
    1min 22.616s snapd.service
         59.179s NetworkManager-wait-online.service
         31.040s dev-sda1.device
         24.301s [email]user@1000.servic[/email]e
         20.230s dev-loop1.device
         20.213s dev-loop3.device
         20.093s dev-loop6.device
         20.090s dev-loop4.device
         20.075s dev-loop8.device
         20.030s dev-loop10.device
         20.012s dev-loop9.device
         20.010s dev-loop0.device
         20.004s dev-loop13.device
         19.972s dev-loop2.device
         19.953s dev-loop11.device
         19.930s dev-loop7.device
         19.914s dev-loop12.device
         19.899s dev-loop14.device
         19.723s dev-loop5.device
         13.746s networking.service
         13.590s thermald.service
lines 1-23...skipping...
    1min 42.239s apt-daily.service
    1min 35.106s teamviewerd.service
    1min 22.616s snapd.service
         59.179s NetworkManager-wait-online.service
         31.040s dev-sda1.device
         24.301s [email]user@1000.servic[/email]e
         20.230s dev-loop1.device
         20.213s dev-loop3.device
         20.093s dev-loop6.device
         20.090s dev-loop4.device
         20.075s dev-loop8.device
         20.030s dev-loop10.device
         20.012s dev-loop9.device
         20.010s dev-loop0.device
         20.004s dev-loop13.device
         19.972s dev-loop2.device
         19.953s dev-loop11.device
         19.930s dev-loop7.device
         19.914s dev-loop12.device
         19.899s dev-loop14.device
         19.723s dev-loop5.device
         13.746s networking.service
         13.590s thermald.service
         11.816s ua-messaging.service
         10.752s networkd-dispatcher.service
         10.289s NetworkManager.service
          7.791s ModemManager.service
          7.414s plymouth-read-write.service
          6.710s apparmor.service
          6.552s gpu-manager.service
          6.464s udisks2.service
          6.446s systemd-journal-flush.service
          6.189s systemd-udevd.service
          4.336s loadcpufreq.service
          3.896s accounts-daemon.service
          3.840s wpa_supplicant.service
          3.419s avahi-daemon.service
          2.980s systemd-sysctl.service
          2.933s lightdm.service
          2.929s plymouth-quit-wait.service
          2.090s systemd-logind.service
          1.955s grub-common.service
          1.800s polkit.service
          1.612s systemd-tmpfiles-setup-dev.service
          1.285s rsyslog.service
          1.200s systemd-tmpfiles-setup.service
          1.132s colord.service
          1.124s apt-daily-upgrade.service
          1.105s systemd-modules-load.service

---

### Post by oldfred on 2021-08-02
It says it boots in 4 minutes. Or actually 3 & half. 

Are you using snaps? The loopmount devices?
I immediately uninstall all snaps, and install standard apt package or live without. (So nothing essential to me is a snap.)
boot time cut in half by removing snap, they since have improved boot somewhat
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)

I change the apt-daily and do my own updates after booting or first thing in morning.
If issues connecting to Internet that can hang for a while.
[https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297](https://ubuntu-mate.community/t/shorten-boot-time-apt-daily-service/12297)
This is Debian bug #844453. apt-daily.service shouldn't be run during boot
[https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service](https://askubuntu.com/questions/800479/ubuntu-16-04-slow-boot-apt-daily-service)

Some other things to review.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

But if you want faster system, add or change to a SSD. I added a tiny 60GB for boot SSD about ten years ago and it improved my old BIOS system so much I put off upgrade to new system for 3 years.

---

### Post by renekert on 2021-08-03
I removed all snaps, the snapd and its eventual reload. The result was that the line "[COLOR=#000000]1min 42.239s apt-daily.service" disappeared and the boot went down to:
[/COLOR]systemd-analyze
Startup finished in 6.190s (kernel) + 2min 33.968s (userspace) = 2min 40.159s    (a 22% decrease).

I am grateful for your help. However, I must tell that what really worries me is that the slow boot and the list of errors and problems listed at startup keep on increasing to a full system failure.
Can I send you the initial listing of errors? and, if this is possible, how can I capture them?
Best regards!

---

### Post by oldfred on 2021-08-03
Post these:
Errors/Warnings:
sudo journalctl -b -p err
sudo egrep -i 'warn|error' /var/log/*g

---

### Post by renekert on 2021-08-04
I am astonished.
Error and warnings dissappeared, boot time was 1'27" and I do not know why. The only thing I could think of, was that I accepted a standard Ubuntu base update invitation.

But your suggestions produced a lot of text. Thanks a lot for your time! I will wait for your comments.
Here follows the result of the first terminal command. The second command produced such a huge amount of text that this page did not let me send it. If there is an alternative way, please tell me.
enrique@enrique-PC:~$ sudo journalctl -b -p err
[sudo] contraseña para enrique: 
-- Logs begin at Tue 2021-06-22 07:19:33 -03, end at Wed 2021-08-04 13:28:02 -03
ago 04 12:58:50 enrique-PC kernel: sd 7:0:0:0: [sdc] No Caching mode page found
ago 04 12:58:50 enrique-PC kernel: sd 7:0:0:0: [sdc] Assuming drive cache: write
ago 04 12:58:50 enrique-PC kernel: ACPI BIOS Error (bug): Could not resolve symb
ago 04 12:58:50 enrique-PC kernel: ACPI Error: Aborting method \_SB.PCI0.VGA.ATC
ago 04 12:58:50 enrique-PC kernel: ACPI Error: Aborting method \_SB.PCI0.VGA.ATC
ago 04 12:58:50 enrique-PC kernel: sd 8:0:0:0: [sdd] No Caching mode page found
ago 04 12:58:50 enrique-PC kernel: sd 8:0:0:0: [sdd] Assuming drive cache: write
ago 04 12:59:27 enrique-PC spice-vdagent[1219]: Cannot access vdagent virtio cha
ago 04 12:59:53 enrique-PC pulseaudio[1129]: [pulseaudio] bluez5-util.c: GetMana
lines 1-10/10 (END)

---

### Post by oldfred on 2021-08-04
A lot of time ACPI errors can be ignored.
Sometimes an UEFI/BIOS update can improve things.
But after a few years vendors rarely offer new updates. Dell did come out with updates for a major security issue for many systems.

I then use Google and add ubuntu to error and see if others have fixes.
For example/
The no caching mode had several suggestions, but most then were reported as not solving issue.
Most just say it is a comment that your drive does not have RAM to store/cache info. Or drive is slower.

Were there errors from the log file?

If no Bluetooth, and older BIOS, you can turn off bluetooth & fwupdate as posted in some of the links.

---

### Post by renekert on 2021-08-05
Yes, there such a number of errors in the output of "[COLOR=#000000]sudo egrep -i 'warn|error' /var/log/*g[/COLOR] " that I was no allowed to post the output (too long).
[COLOR=#000000]If there is an alternative method to send it to you, and if your experience tells you that they might be important, I'll use it. Otherwise, if the system keeps working we might better not disturb it. What do you think?

[/COLOR]

---

### Post by oldfred on 2021-08-05
Try just the error without the warn part. 
And use code tags to post.

How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

---

### Post by renekert on 2021-08-05
Excuse my ignorance. I have just noted that the outputs for the "[COLOR=#000000]egrep -i 'warn|error' /var/log/*g"  were dated. in August 3, 4 and 5. 

[/COLOR]I am posting the part dated today

/var/log/kern.log:Aug  5 07:11:37 enrique-PC kernel: [    0.033018] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Length but zero Address: 0x0000000000000000/0x1 (20190816/tbfadt-624)/var/log/kern.log:Aug  5 07:11:37 enrique-PC kernel: [    1.458077] RAS: Correctable Errors collector initialized.
/var/log/kern.log:Aug  5 07:11:37 enrique-PC kernel: [    3.788916] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.ALIB], AE_NOT_FOUND (20190816/psargs-330)
/var/log/kern.log:Aug  5 07:11:37 enrique-PC kernel: [    3.788934] ACPI Error: Aborting method \_SB.PCI0.VGA.ATC0 due to previous error (AE_NOT_FOUND) (20190816/psparse-531)
/var/log/kern.log:Aug  5 07:11:37 enrique-PC kernel: [    3.788943] ACPI Error: Aborting method \_SB.PCI0.VGA.ATCS due to previous error (AE_NOT_FOUND) (20190816/psparse-531)
/var/log/kern.log:Aug  5 07:11:37 enrique-PC kernel: [    7.956525] random: 7 urandom warning(s) missed due to ratelimiting
/var/log/kern.log:Aug  5 07:11:37 enrique-PC kernel: [   12.248402] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/Xorg.0.log:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown

---

### Post by oldfred on 2021-08-05
I have a lot more errors than that. :)

Most of the ACPI errors can be ignored.
The remount is a setting for mounting of /.

Google seems to say that the ratelimiting is just not posting 7 copies of same error.

---

### Post by renekert on 2021-08-06
Well, let's call it "solved", and thank you for all the things I learned through this exchange!
Enrique.

---


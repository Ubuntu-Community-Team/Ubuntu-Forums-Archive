---
title: "Slow boot after installing ubuntu 24.10"
date: 2024-11-25
forum: New to Ubuntu
---

### Post by trancos93 on 2024-11-25
Good morning, 

Yesterday I successfully installed ubuntu 24,10 on my desktop PC to dual boot with windows 10,

The issue i'm experiencing is that it boots so slowly in comparison with windows 10. It doesnt make sense, taking into account it's a lighter OS,

I've ran some commands to check what was happening but i'm having some trouble interpreting them: 

systemd-analyze critical-chain:

graphical.target @9.208s
&#9492;&#9472;power-profiles-daemon.service @9.155s +52ms
  &#9492;&#9472;multi-user.target @9.154s
    &#9492;&#9472;cups-browsed.service @9.153s
      &#9492;&#9472;network-online.target @9.152s
        &#9492;&#9472;NetworkManager-wait-online.service @3.405s +5.747s
          &#9492;&#9472;NetworkManager.service @2.987s +417ms
            &#9492;&#9472;dbus.service @2.953s +31ms
              &#9492;&#9472;basic.target @2.949s
                &#9492;&#9472;sockets.target @2.949s
                  &#9492;&#9472;snapd.socket @2.931s +17ms
                    &#9492;&#9472;sysinit.target @2.927s
                      &#9492;&#9472;systemd-resolved.service @1.922s +1.004s
                        &#9492;&#9472;run-credentials-systemd\x2dresolved.service.mount @2.

systemd-analyze blame:

5.747s NetworkManager-wait-online.service
3.320s plymouth-quit-wait.service
1.049s kdump-tools.service
1.007s systemd-oomd.service
1.004s systemd-resolved.service
1.002s systemd-timesyncd.service
 797ms fwupd-refresh.service
 728ms fwupd.service
 637ms boot-efi.mount
 636ms snap-bare-5.mount
 635ms snap-core20-2434.mount
 520ms snapd.seeded.service
 417ms NetworkManager.service
 412ms snapd.service
 408ms gpu-manager.service
 193ms nvidia-persistenced.service
 180ms dev-nvme0n1p5.device
 170ms apport.service
 137ms systemd-udev-trigger.service
 135ms [EMAIL="user@1000.servic"]user@1000.servic[/EMAIL]e
 105ms udisks2.service
  89ms upower.service
  71ms update-notifier-download.service


My system is pretty powerful so I dont understand this boot times, 

Any help would be apreciated,

Thanks in advance.

---

### Post by yancek on 2024-11-25
I don't know if this is the reason for the difference but the default on windows 10 is hibernation on so it is not actually doing a full boot/reboot so it seems faster.

---

### Post by oldfred on 2024-11-25
My laptop, this Dell with 11th gen Intel comes up about 10 sec after grub menu, but this says it sill is booting.
> [FONT=monospace][COLOR=#54ff54]**fred@m2-noble**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$  systemd-analyze [/COLOR]
Startup finished in 11.975s (firmware) + 5.611s (loader) + 2.956s (kernel) + 9.717s (userspace) = 30.260s  
graphical.target reached after 9.710s in userspace.
[/FONT]

My desktop is similar, but I remove a few more settings as it does not have hardware for that.

I typically change some settings & remove all snaps. 
My older desktop does not have UEFI update, so fwupdate not required.  So I do vary settings a bit depending on which system. 

[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456](https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

I also turn off in UEFI settings network boot, so UEFI is not trying to connect to network.

Advanced changes:
[https://wiki.archlinux.org/title/Improving_performance/Boot_process](https://wiki.archlinux.org/title/Improving_performance/Boot_process)

---

### Post by him610 on 2024-11-25
@trancos93
Go back and look at the top two lines...
```
$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.
... 
```

---


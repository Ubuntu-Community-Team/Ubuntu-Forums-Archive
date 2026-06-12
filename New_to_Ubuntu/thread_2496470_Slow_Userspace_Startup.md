---
title: "Slow Userspace Startup"
date: 2024-03-29
forum: New to Ubuntu
---

### Post by djunna on 2024-03-29
For the past couple months I've had an unusually slow startup time. Windows is actually faster for me right now. I'm a little out of my depth on this. 
The results of my systemd-analyze are as follows:

```
tartup finished in 13.544s (firmware) + 13.901s (loader) + 4.031s (kernel) + 59.183s (userspace) = 1min 30.661s 
graphical.target reached after 47.670s in userspace
```

A list of my snaps:
```
bare                                  1.0                         5      latest/stable    canonical&#10003;     base
core18                                20231027                    2812   latest/stable    canonical&#10003;     base
core20                                20240111                    2182   latest/stable    canonical&#10003;     base
core22                                20240111                    1122   latest/stable    canonical&#10003;     base
cups                                  2.4.7-3                     1024   latest/stable    openprinting&#10003;  -
flutter                               0+git.2149a81               145    latest/stable    flutter-team&#10003;  classic
gnome-3-28-1804                       3.28.0-19-g98f9e67.98f9e67  198    latest/stable    canonical&#10003;     -
gnome-3-38-2004                       0+git.efb213a               143    latest/stable    canonical&#10003;     -
gnome-42-2204                         0+git.510a601               172    latest/stable    canonical&#10003;     -
gtk-common-themes                     0.1-81-g442e511             1535   latest/stable    canonical&#10003;     -
kde-frameworks-5-96-qt-5-15-5-core20  5.96.0                      7      latest/stable    kde&#10003;           -
kde-frameworks-5-core18               5.67.0                      35     latest/stable    kde&#10003;           -
kf5-5-104-qt-5-15-8-core22            5.104                       9      latest/stable    kde&#10003;           -
kf5-5-108-qt-5-15-10-core22           5.108                       5      latest/stable    kde&#10003;           -
kf5-5-111-qt-5-15-11-core22           5.111                       7      latest/stable    kde&#10003;           -
kf5-5-113-qt-5-15-11-core22           5.113                       1      latest/stable    kde&#10003;           -
krita                                 5.2.2                       100    latest/stable    krita&#10003;         -
nightmayr-kf5-qt-5-15-2-core20        5.85.0                      30     latest/stable    nightmayr      -
snapd                                 2.61.2                      21184  latest/stable    canonical&#10003;     snapd
software-boutique                     0+git.0fdcecc               57     latest/stable/&#8230;  flexiondotorg  classic
ubuntu-mate-welcome                   22.04.0-d3d4bb1a            726    latest/stable/&#8230;  flexiondotorg  classic

```


I'm running Ubuntu 20.04.6. CPU is Intel i5-4430 and GPU is NVIDIA GeForce GTX 1060 (I know these are a bit old, but I am skeptical that it's a hardware issue given how well Windows 10 is running.) 

Apologies for any ignorance of this forum's etiqutte.

---

### Post by deadflowr on 2024-03-29
You can dig a little deeper into the analyze output by running with blame and/or critical-chain
```
systemd-analyze blame
systemd-analyze critical-chain
```
press down to scroll (or enter key)
press q to exit

---

### Post by djunna on 2024-03-29
Thank you for your reply! The top results from blame are:

```

7min 3.622s dev-loop36.device                                                 
    52.445s apt-daily.service                                                 
    31.254s man-db.service                                                    
    25.144s snapd.seeded.service                                               
    23.995s snapd.service                                                      
    17.121s dev-sda2.device 
```

The result from systemd-analyze critical-chain

```
 
graphical.target @47.670s
&#9492;&#9472;multi-user.target @47.670s
  &#9492;&#9472;snapd.seeded.service @22.525s +25.144s
    &#9492;&#9472;basic.target @22.254s
      &#9492;&#9472;sockets.target @22.254s
        &#9492;&#9472;snapd.socket @22.253s +852us
          &#9492;&#9472;sysinit.target @22.225s
            &#9492;&#9472;snapd.apparmor.service @21.319s +905ms
              &#9492;&#9472;apparmor.service @20.537s +780ms
                &#9492;&#9472;local-fs.target @20.536s
                  &#9492;&#9472;run-snapd-ns-cups.mnt.mount @38.691s
                    &#9492;&#9472;run-snapd-ns.mount @32.561s
                      &#9492;&#9472;local-fs-pre.target @4.896s
                        &#9492;&#9472;systemd-tmpfiles-setup-dev.service @4.413s +482ms
                          &#9492;&#9472;systemd-sysusers.service @3.588s +823ms
                            &#9492;&#9472;systemd-remount-fs.service @3.473s +102ms
                              &#9492;&#9472;systemd-journald.socket @3.262s
                                &#9492;&#9472;-.mount @3.259s
                                  &#9492;&#9472;system.slice @3.259s
                                    &#9492;&#9472;-.slice @3.259s 
```

---

### Post by oldfred on 2024-03-29
I use Kubuntu which is a bit more lightweight that standard Ubuntu.
And do not install any snaps. And bit older system, that had early M.2 support now has NVMe type SSD. Not really noticeably faster than previous M.2 SSD, but main issue for slow system is between keyboard & chair. :)

[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.150s (kernel) + 5.574s (userspace) = 9.724s  
graphical.target reached after 5.529s in userspace

Some settings to review, I started changes with 20.04, in 22.04 and still using changes in 24.04 test install:
[/FONT]https://ubuntuforums.org/showthread.php?t=2450783
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456](https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 

[FONT=monospace]

[/FONT]

---

### Post by VMC on 2024-03-31
> **oldfred said:**
> I use Kubuntu which is a bit more lightweight that standard Ubuntu.
And do not install any snaps. And bit older system, that had early M.2 support now has NVMe type SSD. Not really noticeably faster than previous M.2 SSD, but main issue for slow system is between keyboard & chair. :)

[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ systemd-analyze [/COLOR]
Startup finished in 4.150s (kernel) + 5.574s (userspace) = 9.724s  
graphical.target reached after 5.529s in userspace

Some settings to review, I started changes with 20.04, in 22.04 and still using changes in 24.04 test install:
[/FONT]https://ubuntuforums.org/showthread.php?t=2450783
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456](https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[FONT=monospace]Thanks oldfred! I applied the  *systemctl* disables on must of them, and shocking how much seconds were  removed. I'm guessing most are started after the desktop is up. It  doesn't feel as though I'm gaining several seconds, as my desktop  appears almost instantly anyway with nvme's that I have.
[/FONT]

---


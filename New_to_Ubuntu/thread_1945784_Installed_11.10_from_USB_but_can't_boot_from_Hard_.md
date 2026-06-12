---
title: "Installed 11.10 from USB but can't boot from Hard Drive with Radeon graphics card"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by WipRace on 2012-03-23
I'm trying to run Windows 7 and Ubuntu on my machine, but Ubuntu doesn't seem to like my graphics card. When booting to Ubuntu from my hard drive, i get a corrupted purple screen. However, when booting from the USB, it works just fine. Also when i switched out my normal graphics card(Radeon HD 6670) for a generic "S3" card, booting from the hard drive worked fine. I have tried using the nomodeset command at boot, but that didn't seem to do anything helpful.

I'm out of ideas and not finding any others on the fourms, any help would be appreciated. Thanks.


Boot log:
```
fsck from util-linux 2.19.1
/dev/sda6: clean, 164232/2531328 files, 852248/10110208 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles                                            [ OK ] 
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades: 
initctl: Event failed
 * Stopping Failsafe Boot Delay                                          [ OK ]
 * Stopping System V initialisation compatibility                        [ OK ]
 * Starting load fallback graphics devices                               [fail]
 * Starting System V runlevel compatibility                              [ OK ]
 * Stopping automatic crash report generation                            [fail]
 * Starting ACPI daemon                                                  [ OK ]
 * Starting save kernel messages                                         [ OK ]
 * Starting CPU interrupts balancing daemon                              [ OK ]
 * Starting anac(h)ronistic cron                                         [ OK ]
 * Starting regular background program processing daemon                 [ OK ]
 * Starting deferred execution scheduler                                 [ OK ]
 * Starting LightDM Display Manager                                      [ OK ]
 * Starting Userspace bootsplash                                         [ OK ]
 * Stopping save kernel messages                                         [ OK ]

```

---

### Post by Mark Phelps on 2012-03-24
Did you manually install the Radeon restricted drivers? 

Asking because 11.10 should work fine with that card without your having to install any drivers.

---

### Post by WipRace on 2012-03-24
I haven't installed the drivers for the graphics card in Ubuntu. Is it possible that Ubuntu picked the wrong driver for my graphics card?

---

### Post by forrestcupp on 2012-03-24
You could try booting into recovery mode, which is a superuser command line, and type this code to reset xorg.
```
dpkg-reconfigure xserver-xorg
```

---


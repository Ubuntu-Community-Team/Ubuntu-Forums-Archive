---
title: "Big Bad Evil Linux"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by JBudOne on 2012-05-12
Hey guys, I've just recently run the update on Ubuntu to Natty Narwhal (11.04?). Everything was working fine until after this upgrade. I'm not sure if this has anything to do with it, but during the upgrade it asked if I'd like to keep my current grub configs, or replace it with the new; I choose to keep my current settings since they were working fine.


Low and behold, restarting the laptop made it impossible to boot into my system again! I should mention that I am NOT dual booted with anything else (although I was just yesterday, since then I've deleted the Windows partition, resized the /dev/sda4 partition (parent to my linux partition), and then resized my /dev/sda6 partition for linux). Again, everything was working great until I upgraded to Natty Narwhal this morning.

Grub went off into this really awkward screen that looks something like, [http://members.iinet.net.au/~herman546/p15/fig2grub.gif](http://members.iinet.net.au/~herman546/p15/fig2grub.gif) (image stolen from Google images). I followed some guides on the forum boards of people who ran into similar issues, and basically tried `update-grub` and then `grub-install /dev/sda`  which now brings my grub screen back.. Although it looks a little different than before, and suddenly trying to load up Linux does NOT work as I'd hope.


Grub Screen:
```

GNU GRUB version 1.99~rc1-13ubuntu3

Ubuntu, with Linux 2.6.38-15-generic pae
Ubuntu, with Linux 2.6.38-15-generic pae (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

```

EDIT mode on the first Ubuntu boot:
```

setparams 'Ubuntu, with Linux 2.6.38-15-generic pae'

recordfail
set gfxpayload=$linux_gfx_mode
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root cd1819b7-2c09-4fd7-8fda-d13e5646daf8
linux /boot/vmlinuz-2.6.38-15-generic-pae root=UUID=cd1819b7-2c09-4fd7-8fda-d13e5646daf8 r0   quiet splash vt.handoff=7
initrd /boot/initrd.img-2.6.38-15-generic-pae

```
Note: I know my filesystem should be ext4 NOT ext2; and why is msdos in here? I've completely deleted the windows partition already


Starting the main boot (non-recovery) makes the screen go black briefly, then displays the Ubuntu boot screen briefly, followed by a flashing black/darkdarkgray screen repeatedly until it hits this command-line screen:


```

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles                [ OK ]
 * Stopping System V initialisation compatibility [ OK ]
 * Starting System V runlevel compatibility  [ OK ]
 * Stopping automatic crash report generation [[COLOR="Red"]fail[/COLOR]]
 * Starting save kernel messages       [ OK ]
 * Starting anac(h)ronistic cron       [ OK ]
 * Starting ACPI daemon                [ OK ]
 * Starting regular background program processing daemon    [ OK ]
 * Starting deferred execution scheduler          [ OK ]
 * Stopping CPU interrupts balancing daemon       [ OK ]
 * Stopping anac(h)ronistic cron                  [ OK ]

 * Stopping save kernel messages                  [ OK ]

 * Starting MySQL Server                          [ OK ]

 * Configuring the Pidgin PPA                     [ OK ]
                                                      s
peech-dispatcher disabled: edit /etc/default/speech-dispatcher
                    * Starting the Winbind daemon winbind  [ OK ]
                                                      N
o make,you'll have to rebuild your databases by hand :(
                                   [COLOR="Red"]*[/COLOR] Not configured, not started.
                                 * Starting Mail Transport Agent (MTA) sendmail    [ OK ]
* Starting bluetooth
* PulseAudio configured for per-user sessions
                                    saned disabled; edit /etc/default/saned
                         * Enabling additional executable binary formats binfmt-support                          [ OK ]
Sat May 12 13:06:19 2012] [warn] NameVirtualHost 127.0.0.1:80 has no virtualHost                     [ OK ]
                         * Starting web server apache2           [ OK ]
                                                  f
sck from util-linux-ng 2.17.2
/dev/sda6: clean, 301855/13967360 files, 16088426/55845940 blocks
init: ureadahead-other mainprocess (897) terminated with status 4
 * Stopping save udev log and update rules           [ OK ]
 * Starting CUPS printing spooler/server             [ OK ]
 * Stopping Userspace bootsplash                     [ OK ]
 * Stopping Flush boot log to disk                   [ OK ]



```
Note: I tried to copy this out as accurately as possible, including the parts where the alignment was awkwardly offset
Note: At this point there is a cursor where I can start typing, however anything I type doesn't go through, its sort of like being in insert mode in vim
Note: As I was typing this all out, the screen went black (until I moved the mouse); possibly the screensaver?


So clearly nothing I can do here, next I try booting into the recovery..

This goes into the regular (I'm assuming) recovery menu for Linux. Everything works fine, so I choose the resume option. From here a console loads up from below, with some similar parts to the previous code (that I wrote above), except underneath it has,

```

* Checking battery state...                        [ OK ]

Ubuntu 11.04 jbud tty1

jbud login: jbud
Password:
Last login: Sat May 12 12:37:39 PDT 2012 on tty1
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-15-generic-pae i686)

* Documentation: https://help/ubuntu.com/

New release 'oneiric' available.
Run 'do-release-upgrade' to upgrade to it.

jbud@jbud:~$

```


At this point I have the standard terminal control of my system. Should I upgrade to the next release? I stopped myself from doing that, and decided to post here instead since my last upgrade clearly wasn't so successful.


Guys...I can't even boot into my system anymore, just after a simple upgrade. I looked all over google and was shocked to not be able to find many other users posting the same issues as me. I can't figure what I could have done wrong to produce such a monster out of my system. Anyways, any tips, suggestions, or insight into this whole situation would be very much appreciated. I'm (probably obviously) a major Linux noob, and only just recently swapped over from Windows. Thanks!

---

### Post by souravc83 on 2012-05-12
Always do a clean install instead of an upgrade.
Best advice from me, now is to back up the data that you have in this hard drive, and then get hold of a live CD of 11.04/11.10 and install from scratch.

---

### Post by JBudOne on 2012-05-12
> **souravc83 said:**
> Always do a clean install instead of an upgrade.
Best advice from me, now is to back up the data that you have in this hard drive, and then get hold of a live CD of 11.04/11.10 and install from scratch.

Damn, damn, damn! Is this really the best way to go about scenario? I was really hoping there would be some magical commandline script I could run that would fix all of this. Why is upgrading even an option if this is the case? And is this standard for everybody to completely re-install everything from scratch anytime they want to upgrade?

---

### Post by slixz85 on 2012-05-12
i will agree with souravc to just start fresh again unless you have alot to save somehow although if u look hard enough im sure there is a fix but it may be a headache. also you should install two different os's so that if one crashes u can boot into the other 1 possibly and visually fixi it without black screen bash crap if your like me and dont kmow all the needed codes. of course this doesnt help out all the way for grub crashes it does help out at other times not too mention you can see the other partitions to transfer any basic docs music vids etc to the non broken desktop.  i keep three os's on mine all of them lightweight and i always have one of my partitions strictly temporary for trying out new debian and ubuntu distros i do this alot. so  u might be famillar with unetbootin to burn iso to usb flash if not let me know and i respond later. iam typing on my damn ps3 with controller right now. but just install a os to usb drive with unetbootin i suggest zorin lite and w booting live with usb flash u can see your partitions and fiddle that way with it.  sorry little scattered but i get back with ya. try my fav used to be peppermint but i realized zorin is faster. i use zorin lite  now trying solus it seems great and peppermint but its about to be taken off it uses more ram than u ever would think. later

---

### Post by ubuntu27 on 2012-05-12
> **JBudOne said:**
>  And is this standard for everybody to completely re-install everything from scratch anytime they want to upgrade?

I say it is a popular custom to do that in Ubuntu. It is just much more reliable. 

If you use a Rolling Release Distro, then there will be no need to an fresh install to do an upgrade. So it is not a "Linux" thing per se.

Please note that  not everyone has bad experience in upgrading to a new Ubuntu Linux release. I guess your chances are 50/50.


I wish you good luck on your next install.

PS: Have you tried Ubuntu 12.04 or Linux Mint?

---

### Post by slixz85 on 2012-05-12
> **JBudOne said:**
> Damn, damn, damn! Is this really the best way to go about scenario? I was really hoping there would be some magical commandline script I could run that would fix all of this. Why is upgrading even an option if this is the case? And is this standard for everybody to completely re-install everything from scratch anytime they want to upgrade?

there probably is but the time it always takes me to find a solution sometimes it could actually already of been reinstalled and all your files transferred back to partition new install could be on as explained above. besides aint it nice to have that fresh feeling. it really aint a hassle if u just kepp 2 or 3 oss on system

---

### Post by pissedoffdude on 2012-05-12
It's always best to do a clean install.  But with that said, updating isn't always a nightmare.  If you don't have too many packages installed, or if most if your packages come from the official repos, you should be fine.  A good rule of thumb to follow is to uninstall ALL software that doesn't come from the official ubuntu repos, including any additional drivers you may have installed.  As for your problem with grub, give supergrubdisk a try.  It can detect any operating systems you have installed and boot them regardless of your current configuration. [http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

---

### Post by JBudOne on 2012-05-12
Hey guys, I just wanted to update that I've gone forward with the oneiric update. I booted into recovery mode, and ran the fail-safe graphical mode. From there I was able to do the next distro upgrade, and now everything works fine. 

I'm not sure if I should chance it with the final upgrade (12.04 LTS); but if I do, I will post the results here.

---

### Post by ubuntu27 on 2012-05-12
Since you needed to go to recovery mode after upgrading to Oneiric...
if you want to upgrade to Ubuntu 12.04 (Precise Pangolin), then definitely do a clean install. 

Good luck!


oh! By the way, what Video Card do you have? This is a important question since Ubuntu Precise includes a driver that has a major regression bug by nVidia. We are all waiting for it to be fixed.

Not all nVidia cards are affected.


If you have any other video card besides nVidia, then go ahead and install Ubuntu 12.04 with confidence. :guitar:

---

### Post by JBudOne on 2012-05-12
Final update: I've upgraded to 12.04 and everything went smoothly. Hope this thread helps somebody in the future :)

---

### Post by Hadaka on 2012-05-12
Hi, I noticed you said " I choose to keep my current settings since they were working fine."
thats why you still had dos6 in the root boot. Hopefully you got rid of that as you may end 
up with a situation where your system is looking for dos6. Glad you got it all sorted out.

---


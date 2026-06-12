---
title: "Authentication issues when booted into 14.10 - generally terminal works OK"
date: 2014-11-20
forum: New to Ubuntu
---

### Post by gelopa on 2014-11-20
[COLOR=#333333][FONT=UbuntuRegular]Intel core i7 running 14.10 (upgraded) 64bit with i386 adaptors. No dual boot - only Utopic[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have authentication issues across a range of programs and services when using Unity. As far as I can see, terminal authentication works fine.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Problem manifests as, inter alia:[/FONT][/COLOR]

[LIST=1]
[*]cannot shutdown or restart using notification bar. Terminal (sudo) shutdown -r now is fine
[*]Cannot control networking in notification bar: network names, connection info fine, all other options greyed out. I haven't tested networking in the terminal, but restarting nm-applet doesn't help
[*]I cannot install anything from the software centre: result "Software can't be installed or removed because the authentication service is not available. (org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name': ':1.114'}): org.debian.apt.install-or-remove-packages"... I can, however, install programs using the Terminal
[*]I cannot edit software sources in the software centre
[*]I cannot add users in Unity - unlock button greyed out. Probably can in terminal
[*]Ubuntu Tweak crashes. Unity tweak Tool runs fine.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]There are no doubt lots of other things buggy, all linked to permissions/authorisation/authentication in the GUI (but not the terminal)[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have done the following:[/FONT][/COLOR]

[LIST=1]
[*]Tested sudo completely in terminal: administrator sudo works perfectly
[*]Added gnome policykit to startup programs and checked
[*]sudo apt-get --fix-broken install
[*]sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
[*]sudo apt-get clean && sudo apt-get autoclean && sudo apt-get autoremove
[*]sudo dpkg --configure -a && sudo apt-get update
[*]purged and reinstalled Unity Desktop
[*]I've tried reverting to standard themes, icons, cursors with no luck.
[*]I tried booting to an old kernel: no difference.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]and a host of minor tweaks.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have found specific answers to specific questions, such as "what to do when wifi is greyed out", but my problem is definitely system wide. Importantly, I can confirm that:[/FONT][/COLOR]

[LIST=1]
[*]The problem exists by the time we get to the login screen - networking functions are already greyed out
[*]The problem seems to be confined to graphical authentication, but I'm a bit sketchy on display server issues
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]I'm thinking that some script may be confused and only allowing partial or lower level security authorisation to the GUI specifically as part of the boot. I do have keen young Minecraft players in the house, so anything is possible. I'm sketchy on where to go from here other than a complete reinstallation.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Please help!

[/FONT][/COLOR]

EDIT - possible confirmed issue: [https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336](https://bugs.launchpad.net/ubuntu/+source/policykit-desktop-privileges/+bug/1240336)

---

### Post by bashiergui on 2014-11-22
Did any of the resolutions in the bug report solve the issue?

---

### Post by gelopa on 2014-11-24
Thanks for response. No, nothing helped yet. I now have the further implication that I can't load live CD via or DVD (as permissions are not sufficient) - so I can't even overwrite system. I am investigating netInstall, but slowly, slowly catchee monkey.

---

### Post by gelopa on 2014-11-25
SOLVED: [COLOR=#000000]sudo apt-get dist-upgrade -f fixed it! i noticed a request for partial upgrade when running GUI software-updater. Actioning it did nothing, so I tried the terminal again....[/COLOR]

---


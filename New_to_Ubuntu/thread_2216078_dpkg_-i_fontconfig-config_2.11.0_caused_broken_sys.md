---
title: "dpkg -i fontconfig-config_2.11.0 caused broken system"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by roland3 on 2014-04-09
Hello everyone,
I am new and I am in trouble:
Wanting to install the latest version of gnucash to my Xubuntu 12.04 (precise, LTS) Linux x64, I started by entering the following dpkg command
(I translated part of the output back into English for easier reading):

root@Rechner/GnuCash# dpkg -i fontconfig-config_2.11.0-0ubuntu4_all.deb 
(Lese Datenbank ... 171716 Dateien und Verzeichnisse sind derzeit installiert.)
Preparing to replace fontconfig-config 2.8.0-3ubuntu9.1 (by fontconfig-config_2.11.0-0ubuntu4_all.deb) ...
Moving obsolete conffile /etc/fonts/conf.avail/11-lcd-filter-lcddefault.conf out of the way...
Moving obsolete conffile /etc/fonts/conf.avail/20-fix-globaladvance.conf out of the way...
Moving obsolete conffile /etc/fonts/fonts.dtd out of the way...
Replacement for fontconfig-config is being unpacked ...
dpkg: Dependency problems prevent configuration of fontconfig-config:
 fontconfig-config depends on fonts-dejavu-core | ttf-bitstream-vera | fonts-freefont-ttf | gsfonts-x11; but:
  Paket fonts-dejavu-core ist nicht installiert.
  Paket ttf-bitstream-vera ist nicht installiert.
  Paket fonts-freefont-ttf ist nicht installiert.
  Paket gsfonts-x11 ist nicht installiert.
dpkg: Fehler beim Bearbeiten von fontconfig-config (--install):
 Dependency problems - remains unconfigured
Trigger für man-db werden verarbeitet ...
Fehler traten auf beim Bearbeiten von:
 fontconfig-config

After this, synaptic informed me about a broken package conflict with libfontconfig1 and libfontconfig1:i386.
I tried to force downgrading to the old 2.8.0-3ubuntu9.1 package in Synaptic, but received message:
E: fontconfig-config: dependency problems - remains unconfigured
Also removing with dpkg failed:

root@Rechner/GnuCash# dpkg -r fontconfig-config
dpkg: Dependency problems prevent removal of fontconfig-config:
 libfontconfig1:i386 depends on fontconfig-config (= 2.8.0-3ubuntu9.1).
 libfontconfig1 depends on fontconfig-config (= 2.8.0-3ubuntu9.1).
 fontconfig depends on fontconfig-config.
dpkg: Fehler beim Bearbeiten von fontconfig-config (--remove):
 Abhängigkeitsprobleme - wird nicht entfernt
Fehler traten auf beim Bearbeiten von:
 fontconfig-config

It seems that I am trapped here.
Who can help?

---

### Post by UltimateCat on 2014-04-10
Hi:

Synaptic Package Manager should allow you to fix broken packages.
Try that--

If your not able to than the only other thing I can think of is to remove that package. 
```
 sudo remove fontconfig-config_2.11.0-0ubuntu4_all.deb 

```


This error:
```
Dependency problems prevent configuration of fontconfig-config:

```
Is basically saying that it can't be configured because it is dependent upon another package or library.
Dependencies have to be met in order for applications to work.

You might want to go directly to the Ubuntu repository and obtain the GNU package directly from there and than install it.

 ****'Broken packages' are packages that have unsatisfied  dependencies. If broken packages are detected, Synaptic will not allow  any further changes to the system until all broken packages have been  fixed.**** 
[LIST]
[*]**To fix broken packages** 

[LIST]
[*]Choose **Edit** > **Fix Broken Packages** from the menu. 

[*]Choose **Apply Marked Changes** from the **Edit** menu or press **Ctrl + P**. 

[*]Confirm the summary of changes and click **Apply**. 
[/LIST]
[/LIST]
If that does not help, then please follow this procedure: 
[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

[https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages](https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages)
[http://www.ehow.com/how_8447960_fix-broken-packages-ubuntu.html](http://www.ehow.com/how_8447960_fix-broken-packages-ubuntu.html)
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

Hope that helps--

---

### Post by roland3 on 2014-04-10
Thanks, UltimateCat, for your quick reply.
I had a sleepless night over this.
Unfortunately, for synaptic to fix the broken dependencies, it wants to uninstall half my system including ubuntu-desktop.
After some sleep and some thinking, I tried the following

[FONT=courier new]root@Rechner:/var/cache/apt/archives# dpkg -i fontconfig-config_2.8.0-3ubuntu9.1_all.deb[/FONT]

Which luckily worked and safely brought me back to my old version.
Thanks a lot again for being with me during this troubled night. :)
I learned a lot, and got involved in the ubuntuforums, which is enough of a reward anyways for my worries. :)

---


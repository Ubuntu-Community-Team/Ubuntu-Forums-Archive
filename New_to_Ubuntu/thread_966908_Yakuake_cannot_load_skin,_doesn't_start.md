---
title: "Yakuake cannot load skin, doesn't start"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-11-01
I'm running Ubuntu 8.10 (yes, no K) and Yakuake used to work fine on 8.04. Now Yakuake won't even start up. This shows:

[img]http://img515.imageshack.us/img515/5307/01novsat1601do8.png[/img]

The skin specified wasn't in the yakuake folder, so I added a skin, and edited yakuakerc appropriately. Same thing happens.

Here is what happens when I run Yakuake from terminal:

```
yakuake(6820) KToolInvocation::klauncher: klauncher not running... launching kdeinit
kdeinit4: preparing to launch /usr/bin/klauncher
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kdeinit4: Communication error with launcher. Exiting!
yakuake(6820)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::KCoreConfigSkeleton: Creating KCoreConfigSkeleton ( 0x96e90d8 )
yakuake(6820)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::readConfig: KCoreConfigSkeleton::readConfig()
yakuake(6820)/kdeui (KNotification) KNotification::slotReceivedId: 0
yakuake(6820)/kdeui (KNotification) KNotification::~KNotification: 0

```

And after I press 'OK' on the error window:

```
yakuake(6820)/kdecore (KLibLoader) findLibraryInternal: plugins should not have a 'lib' prefix: "libkonsolepart.so"
yakuake(6820)/kdecore (KLibLoader) findLibraryInternal: plugins should not have a 'lib' prefix: "libkonsolepart.so"
yakuake(6820)/kdecore (KLibLoader) kde4Factory: The library "/usr/lib/kde4/libkonsolepart.so" does not offer a qt_plugin_instance function.
yakuake(6820)/kdecore (KLibLoader) kde3Factory: The library "/usr/lib/kde4/libkonsolepart.so" does not offer an "init_libkonsolepart" function.
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2600019
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x2600019

```

---

### Post by dustman on 2008-11-04
You know you could uninstall Yakuake and then install it again? :)
The thing with the upgrade (and not just 8.04->8.10) is that not always all the programs and settings get happy together after the upgrade. I know I've had trouble every time I tried to upgrade, so I decided to fresh install every time, keeping my user folder mounted on a separate partition.

---

### Post by linkmaster03 on 2008-11-04
I tried uninstalling and reinstalling Yakuake a ton of times.

---

### Post by dustman on 2008-11-05
From what I've understood, you're not using KDE as a desktop manager. So you can uninstall all the KDE related packages (preferably the ones that were installed in order for Yakuake to run). 
Also another suggestion I can make is that you delete the .yakuake folder from your home folder. I presume it might have some settings remaining (after the uninstall) there that are reloaded every time you re-install Yakuake.

Regards,

Radu

---


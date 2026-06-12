---
title: "Problem at boot"
date: 2020-09-29
forum: New to Ubuntu
---

### Post by pedrorodr98 on 2020-09-29
[COLOR=#242729][FONT=Arial]I'm working on Ubuntu 18.04, and I'm trying to install lightdm as gdm is not working.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The problem with gdm is that when I boot the computer, it get stuck at the ubuntu splash screen.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I deleted the "quite splash" configuration from the grub configuration, and now the system goes into tty console.

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]If I go into the terminal while Ubuntu is stuck on the logo screen, I see the next message:

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]A start job is running for Hold until boot process finishes up (Xmin Xs/no limit)

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Also, I have noticed that some services fail to start at boot, such as Network Manager, WPA supplicant, LBM....

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My first approach was to install Lightdm

[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The problem is that whenever I try to install or update any package, I get this error:[/FONT][/COLOR]
Errors were encountered while processing: 
initramfs-tools

Error:GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.36" (uid = 0 pid = 7955 comm="/usr/bin/gdbus call --system --dest org.freedeskto" label="unconfined") interface="org.freedesktop.PackageKit" member)="StateHasChanged" error n.

E: Sub-process /usr/bin/dpkg returned an error code (1)[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks[/FONT][/COLOR]

---


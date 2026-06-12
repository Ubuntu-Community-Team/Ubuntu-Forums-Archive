---
title: "No Passwordprompt on apps with Admin rights"
date: 2020-04-14
forum: New to Ubuntu
---

### Post by adlerhorst on 2020-04-14
It seems that since some Time I have to start every application that need root with sudo. I do not get any password prompt on desktop.

---

### Post by deadflowr on 2020-04-14
If running sudo it has a default timeout of something like 15 minutes where no password is required.
Once you invoke sudo when running a terminal session the password authentication stands for that session for the allotted timeout time.
It dies either when the session ends/exits or the time has run out.

---

### Post by adlerhorst on 2020-04-14
How could I restore the password GUI prompt?

---

### Post by adlerhorst on 2020-04-14
meanwhile I got an error > polkit authority not available and caller is not 0

---

### Post by deadflowr on 2020-04-14
Can you give an example of what's not loading properly?
This seem to relate to policykit and not sudo.

And what is actually happening when you do try opening the application?
Does it load? Is it running it as root?

---

### Post by adlerhorst on 2020-04-15
1.) Gparted do not start
> gparted
localuser:root being added to access control list
Error checking for authorization org.gnome.gparted: GDBus.Error:org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
localuser:root being removed from access control list


2.) In the ubuntu settings, If I'm on the user tab and try to unlock this, nothig happens  

3.) In gnome-disks I could not start the performance test here I get this error > not authorized to perform operation (polkit authority not available and caller is not uid 0) (udisks-error-quark, 3)                      

---

### Post by deadflowr on 2020-04-15
Check what policykit/polkit packages are installed
```
dpkg -l | egrep "(polkit|policykit)"
```

---

### Post by adlerhorst on 2020-04-16
dpkg -l | egrep "(polkit|policykit)"
```

iii  gir1.2-polkit-1.0                          0.105-26ubuntu1                               amd64        GObject introspection data for PolicyKit
ii  libpolkit-agent-1-0:amd64                  0.105-26ubuntu1                               amd64        PolicyKit Authentication Agent API
ii  libpolkit-gobject-1-0:amd64                0.105-26ubuntu1                               amd64        PolicyKit Authorization API
ii  policykit-1                                0.105-26ubuntu1                               amd64        framework for managing administrative policies and privileges
ii  policykit-desktop-privileges               0.21                                          all          run common desktop actions without password

```

---

### Post by adlerhorst on 2020-04-20
Any Ideas?

---

### Post by deadflowr on 2020-04-20
Shot in the dark but what do polkit and dbus status tell you
```
systemctl status polkit dbus
```

---

### Post by adlerhorst on 2020-05-07
That seems interesting

```

&#9679; polkit.service - Authorization Manager
   Loaded: loaded (/lib/systemd/system/polkit.service; static; vendor preset: enabled)
   Active: [COLOR=#ff0000]failed[/COLOR] (Result: core-dump) since Thu 2020-05-07 11:40:50 CEST; 6min ago
     Docs: man:polkit(8)
 Main PID: 13016 (code=dumped, signal=SEGV)

Mai 07 11:12:57 michel-pc systemd[1]: Starting Authorization Manager...
Mai 07 11:12:57 michel-pc polkitd[13016]: started daemon version 0.105 using authority implementation `local' version `0.105'
Mai 07 11:12:57 michel-pc systemd[1]: Started Authorization Manager.
Mai 07 11:12:57 michel-pc polkitd(authority=local)[13016]: Registered Authentication Agent for unix-session:c3 (system bus name :1.2879 [/usr/bin/gnome-shell], object path /org/freed
Mai 07 11:12:58 michel-pc polkitd(authority=local)[13016]: Registered Authentication Agent for unix-session:1 (system bus name :1.73 [/usr/bin/gnome-shell], object path /org/freedesk
Mai 07 11:40:50 michel-pc systemd[1]: polkit.service: Main process exited, code=dumped, status=11/SEGV
Mai 07 11:40:50 michel-pc systemd[1]: polkit.service: Failed with result 'core-dump'.

&#9679; dbus.service - D-Bus System Message Bus
   Loaded: loaded (/lib/systemd/system/dbus.service; static; vendor preset: enabled)
   Active: active (running) since Mon 2020-05-04 20:13:13 CEST; 2 days ago
     Docs: man:dbus-daemon(1)
 Main PID: 1454 (dbus-daemon)
    Tasks: 1 (limit: 4915)
   Memory: 7.9M
   CGroup: /system.slice/dbus.service
           &#9492;&#9472;1454 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only

Mai 07 11:30:18 michel-pc dbus-daemon[1454]: [system] Activating via systemd: service name='net.reactivated.Fprint' unit='fprintd.service' requested by ':1.73' (uid=1000 pid=2670 com
Mai 07 11:30:19 michel-pc dbus-daemon[1454]: [system] Successfully activated service 'net.reactivated.Fprint'
Mai 07 11:31:01 michel-pc dbus-daemon[1454]: [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service' requested
Mai 07 11:31:01 michel-pc dbus-daemon[1454]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Mai 07 11:33:46 michel-pc dbus-daemon[1454]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.
Mai 07 11:33:47 michel-pc dbus-daemon[1454]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mai 07 11:40:34 michel-pc dbus-daemon[1454]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.
Mai 07 11:40:35 michel-pc dbus-daemon[1454]: [system] Successfully activated service 'org.freedesktop.timedate1'
Mai 07 11:42:40 michel-pc dbus-daemon[1454]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service' requested by ':1.
Mai 07 11:42:40 michel-pc dbus-daemon[1454]: [system] Successfully activated service 'org.freedesktop.hostname1'
```

---

### Post by ActionParsnip on 2020-05-07
Wait, what apps are you running using sudo please?

---

### Post by adlerhorst on 2020-05-08
at moment sudo -H ubuntu-software or gnome-disks as example.

---

### Post by adlerhorst on 2020-05-14
Is it may possible to reset all these to default?

---

### Post by adlerhorst on 2020-06-14
I do get this if I try to login an Ubuntu account on 20.04


> Jun 14 17:55:44 michel-pc polkitd(authority=local)[3504]: Registered Authentication Agent for unix-session:2 (system bus name :1.87 [/usr/bin/gnome-shell], object path /org/freedesktop/PolicyKit1/Authen>
Jun 14 17:55:44 michel-pc polkitd(authority=local)[3504]: Registered Authentication Agent for unix-session:c1 (system bus name :1.37 [/usr/bin/gnome-shell], object path /org/freedesktop/PolicyKit1/Authe>
Jun 14 17:55:44 michel-pc gnome-initial-s[2265]: Error logging in snapd: access denied (snapd-error-quark, 5)
Jun 14 17:55:44 michel-pc snapd[1092]: daemon.go:207: polkit error: Authorization requires interaction
Jun 14 17:55:44 michel-pc systemd[1]: Started Authorization Manager.
Jun 14 17:55:44 michel-pc dbus-daemon[1059]: [system] Successfully activated service 'org.freedesktop.PolicyKit1'
Jun 14 17:55:44 michel-pc polkitd[3504]: started daemon version 0.105 using authority implementation `local' version `0.105'
Jun 14 17:55:44 michel-pc systemd[1]: Starting Authorization Manager...
Jun 14 17:55:44 michel-pc dbus-daemon[1059]: [system] Activating via systemd: service name='org.freedesktop.PolicyKit1' unit='polkit.service' requested by ':1.107' (uid=0 pid=1092 comm="/usr/lib/snapd/s>


---


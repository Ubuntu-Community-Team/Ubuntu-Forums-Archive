---
title: "Keyring sometimes not workng"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by maart2 on 2014-07-08
Usually when I run a command like 'ssh somename@someserver' the keyring promt pops up as it should. But simetimes it does not. Then I have to use long random-string server passwords to get access to the ssh servers. After a reboot Keyring works again most of the times. Just logging out and back in does not solve it.

My login password and my Keyring password are different and I do not use autologin like in many other keyring questions. I am running Ubuntu 14.04, upgraded from 12.04.

This [old thread]("http://ubuntuforums.org/showthread.php?t=1459804") made me look at my auth.log file, but does not solve my problem. But I think it does contain some clues.

This one did NOT work:
```
Jul  8 09:10:55 maarten-laptop-ubuntu systemd-logind[863]: New seat seat0.
Jul  8 09:10:56 maarten-laptop-ubuntu systemd-logind[863]: Watching system buttons on /dev/input/event2 (Power Button)
Jul  8 09:10:56 maarten-laptop-ubuntu systemd-logind[863]: Watching system buttons on /dev/input/event9 (Video Bus)
Jul  8 09:10:56 maarten-laptop-ubuntu systemd-logind[863]: Watching system buttons on /dev/input/event8 (Video Bus)
Jul  8 09:10:56 maarten-laptop-ubuntu systemd-logind[863]: Watching system buttons on /dev/input/event0 (Lid Switch)
Jul  8 09:10:56 maarten-laptop-ubuntu systemd-logind[863]: Watching system buttons on /dev/input/event1 (Sleep Button)
Jul  8 09:11:01 maarten-laptop-ubuntu dbus[804]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.15" (uid=0 pid=1350 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=879 comm="NetworkManager ")
Jul  8 09:11:01 maarten-laptop-ubuntu lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  8 09:11:01 maarten-laptop-ubuntu lightdm: PAM adding faulty module: pam_kwallet.so
Jul  8 09:11:01 maarten-laptop-ubuntu lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jul  8 09:11:01 maarten-laptop-ubuntu systemd-logind[863]: New session c1 of user lightdm.
Jul  8 09:11:01 maarten-laptop-ubuntu systemd-logind[863]: Linked /tmp/.X11-unix/X0 to /run/user/104/X11-display.
Jul  8 09:11:01 maarten-laptop-ubuntu lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Jul  8 09:11:02 maarten-laptop-ubuntu dbus[804]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.15" (uid=0 pid=1350 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=879 comm="NetworkManager ")
Jul  8 09:11:05 maarten-laptop-ubuntu lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  8 09:11:05 maarten-laptop-ubuntu lightdm: PAM adding faulty module: pam_kwallet.so
Jul  8 09:11:05 maarten-laptop-ubuntu lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "maarten"
Jul  8 09:11:33 maarten-laptop-ubuntu lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Jul  8 09:11:33 maarten-laptop-ubuntu lightdm: pam_unix(lightdm:session): session opened for user maarten by (uid=0)
Jul  8 09:11:33 maarten-laptop-ubuntu systemd-logind[863]: New session c2 of user maarten.
Jul  8 09:11:33 maarten-laptop-ubuntu systemd-logind[863]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Jul  8 09:11:33 maarten-laptop-ubuntu lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jul  8 09:11:45 maarten-laptop-ubuntu gnome-keyring-daemon[2120]: Gkm: using old keyring directory: /home/maarten/.gnome2/keyrings
Jul  8 09:11:45 maarten-laptop-ubuntu gnome-keyring-daemon[2120]: Gkm: using old keyring directory: /home/maarten/.gnome2/keyrings
Jul  8 09:11:45 maarten-laptop-ubuntu gnome-keyring-daemon[2120]: couldn't set environment variable in session: Setenv interface is only available during the Initialization phase
Jul  8 09:11:47 maarten-laptop-ubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.76 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Jul  8 09:11:48 maarten-laptop-ubuntu gnome-keyring-daemon[2120]: keyring alias directory: /home/maarten/.gnome2/keyrings
Jul  8 09:11:58 maarten-laptop-ubuntu systemd-logind[863]: Removed session c1.
Jul  8 09:13:24 maarten-laptop-ubuntu gnome-keyring-daemon[2120]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk

```

This one did:
```
Jul  8 12:11:04 maarten-laptop-ubuntu systemd-logind[850]: New seat seat0.
Jul  8 12:11:04 maarten-laptop-ubuntu systemd-logind[850]: Watching system buttons on /dev/input/event2 (Power Button)
Jul  8 12:11:04 maarten-laptop-ubuntu systemd-logind[850]: Watching system buttons on /dev/input/event14 (Video Bus)
Jul  8 12:11:04 maarten-laptop-ubuntu systemd-logind[850]: Watching system buttons on /dev/input/event13 (Video Bus)
Jul  8 12:11:04 maarten-laptop-ubuntu systemd-logind[850]: Watching system buttons on /dev/input/event0 (Lid Switch)
Jul  8 12:11:04 maarten-laptop-ubuntu systemd-logind[850]: Watching system buttons on /dev/input/event1 (Sleep Button)
Jul  8 12:11:08 maarten-laptop-ubuntu dbus[785]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.15" (uid=0 pid=1314 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=864 comm="NetworkManager ")
Jul  8 12:11:08 maarten-laptop-ubuntu lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  8 12:11:08 maarten-laptop-ubuntu lightdm: PAM adding faulty module: pam_kwallet.so
Jul  8 12:11:09 maarten-laptop-ubuntu lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Jul  8 12:11:09 maarten-laptop-ubuntu systemd-logind[850]: New session c1 of user lightdm.
Jul  8 12:11:09 maarten-laptop-ubuntu systemd-logind[850]: Linked /tmp/.X11-unix/X0 to /run/user/104/X11-display.
Jul  8 12:11:09 maarten-laptop-ubuntu lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Jul  8 12:11:10 maarten-laptop-ubuntu lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Jul  8 12:11:10 maarten-laptop-ubuntu lightdm: PAM adding faulty module: pam_kwallet.so
Jul  8 12:11:10 maarten-laptop-ubuntu lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "maarten"
Jul  8 12:11:11 maarten-laptop-ubuntu dbus[785]: [system] Rejected send message, 7 matched rules; type="method_return", sender=":1.15" (uid=0 pid=1314 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.5" (uid=0 pid=864 comm="NetworkManager ")
Jul  8 12:11:22 maarten-laptop-ubuntu lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Jul  8 12:11:22 maarten-laptop-ubuntu lightdm: pam_unix(lightdm:session): session opened for user maarten by (uid=0)
Jul  8 12:11:22 maarten-laptop-ubuntu systemd-logind[850]: New session c2 of user maarten.
Jul  8 12:11:22 maarten-laptop-ubuntu systemd-logind[850]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
Jul  8 12:11:22 maarten-laptop-ubuntu lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jul  8 12:11:23 maarten-laptop-ubuntu gnome-keyring-daemon[2069]: Gkm: using old keyring directory: /home/maarten/.gnome2/keyrings
Jul  8 12:11:25 maarten-laptop-ubuntu polkitd(authority=local): Registered Authentication Agent for unix-session:c2 (system bus name :1.75 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Jul  8 12:11:23 maarten-laptop-ubuntu gnome-keyring-daemon[2069]: Gkm: using old keyring directory: /home/maarten/.gnome2/keyrings
Jul  8 12:11:26 maarten-laptop-ubuntu gnome-keyring-daemon[2069]: keyring alias directory: /home/maarten/.gnome2/keyrings
Jul  8 12:11:59 maarten-laptop-ubuntu gnome-keyring-daemon[2069]: exponent1 exponent1: no decoded value
Jul  8 12:13:00 maarten-laptop-ubuntu gnome-keyring-daemon[2069]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk

```

They both contain things that look like errors, but I cannot make out what is really wrong and what is not.

---


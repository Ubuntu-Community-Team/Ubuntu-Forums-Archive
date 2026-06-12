---
title: "Log in with only default background showing - console-kit error?"
date: 2011-11-19
forum: New to Ubuntu
---

### Post by incady on 2011-11-19
After leaving my Ubuntu 11.04 machine on for several days, I rebooted. After I entered my password, the screen showed only the background screen with a mouse pointer, and nothing else (no icons, etc). So I restarted my machine, and was able to log into my account in the Ubuntu safe mode.  Here is my auth.log file, but I can't figure out what's wrong:

Nov 18 22:37:34 linux-Inspiron-530 gdm-session-worker[1355]: pam_unix(gdm:session): session closed for user xxxxx
Nov 18 22:37:39 linux-Inspiron-530 gdm-session-worker[2500]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "xxxxx"
Nov 18 22:37:43 linux-Inspiron-530 gdm-session-worker[2500]: pam_unix(gdm:session): session opened for user xxxxx by (uid=0)
Nov 18 22:37:43 linux-Inspiron-530 gdm-session-worker[2500]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov 18 22:37:44 linux-Inspiron-530 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session4 (system bus name :1.67 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Nov 18 22:37:45 linux-Inspiron-530 dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.71" (uid=1000 pid=2613 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=902 comm="/usr/sbin/console-kit-daemon --no-daemon "))


Any help would be appreciated!

---

### Post by incady on 2011-11-19
So I had apache running, and I noticed it had the error "Could not reliably determine the server’s fully qualified domain name..", which I fixed by adding 'localhost' to the config file. Now I can fully log into my account. Not sure why something which isn't really a system error should prevent a user from logging in.

---


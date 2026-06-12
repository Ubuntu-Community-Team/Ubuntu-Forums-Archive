---
title: "Auth log help please"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by themanfromdelmonte on 2011-10-05
Why  do I keep seeing Consoles connecting to my box. GDM and thinks like that gain root. Is this normal? A Few examples:

pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "fumf"
Oct  3 10:52:39 EDC gdm-session-worker[1138]: pam_unix(gdm:auth): authentication failure; logname= uid=0 euid=0 tty=:0 ruser= rhost=  user=fumf
Oct  3 10:52:41 EDC gdm-session-worker[1288]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "fumf"
Oct  3 10:53:20 EDC gdm-session-worker[1288]: pam_unix(gdm:session): session opened for user fumf by (uid=0)
Oct  3 10:53:20 EDC gdm-session-worker[1288]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0

polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.36, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)#

dm-session-worker[1058]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "fumf"
Oct  4 11:36:22 EDC gdm-session-worker[1058]: pam_unix(gdm:session): session opened for user fumf by (uid=0)
Oct  4 11:36:22 EDC gdm-session-worker[1058]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  4 11:36:25 EDC polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.32 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)

Oct  4 11:36:29 EDC dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.35" (uid=1000 pid=1258 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=830 comm="/usr/sbin/console-kit-daemon --no-daemon "))[

---

### Post by Rubi1200 on 2011-10-05
Please post some example lines from the log so we can take a look.

Thanks.

---


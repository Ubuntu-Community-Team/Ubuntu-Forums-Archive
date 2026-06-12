---
title: "Keyring password error"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by freesitebuilder on 2011-10-13
Just switched on an logged on to my account OK. But I get a message that my login password and my keyring password don't match, and enter the password.

Are the admin password and keyring password usually the same? And what can I have done to change the keyring password? Updates yesterday included linux headers, and today I think was only Chrome.

I have 10.10 Ubuntu.

Thanks

---

### Post by collisionystm on 2011-10-13
just delete your key ring.

Applications, preferences, passwords and keys ( i think )

---

### Post by mcduck on 2011-10-13
> **collisionystm said:**
> just delete your key ring.

Applications, preferences, passwords and keys ( i think )

That's not really necessary, and anyway giving such destructive advice without at least a little warning of what it does isn't a good idea. Even while most users only have some trivial data like a wireless password there, other might have really important encryption and signing keys or server passwords in their keyrings....

freesitebuilder: Have you perhaps changed your login password lately? Or are you using automatic or password-free login? The keyring password is by default set to same as your login password, but changing hte login password won't change the keyring password accordingly. (in some cases one might want separate passwords for each, or even want to use several separate keyrings).

Anyway, make sure your keyring password is set to same as the login password you are currently using. You can do that using the PAsswords and Encryption keys-tool found in the settings, just right-clcik the default keyring and select "Change Password".

---

### Post by freesitebuilder on 2011-10-13
I haven't changed my login - but the passwords on the keyring are blank. When I try to reset the keyring password, it asks for my old password, and then the new password - but I don't know what it's set the "old" password to!

I did have a apport warning this morning, this is the log:

System: Linux 2.6.35-30-generic-pae #60-Ubuntu SMP Mon Sep 19 22:29:36 UTC 2011 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10900000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Clearlooks
Icon Theme: gnome
GTK+ Modules: gnomesegvhandler, canberra-gtk-module

Memory status: size: 391729152 vsize: 391729152 resident: 107524096 share: 32063488 rss: 107524096 rss_rlim: 18446744073709551615
CPU usage: start_time: 1318455097 rtime: 368 utime: 292 stime: 76 cutime:2 cstime: 2 timeout: 0 it_real_value: 0 frequency: 100

----------- .xsession-errors ---------------------
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/dianne/2543: No such file or directory.
No stack.
--------------------------------------------------

Is there anywhere I can (safely!) dig about to see what the password has been set to?

---

### Post by jockyburns on 2011-10-13
Dunno about passwords having to match? When I log in to Ubuntu (normally set to automatic login but I can log out and back in) I enter my login password. Whenever I use Evolution though I have to enter my Keyring Password (which is my password for my email service provider););)

---

### Post by mcduck on 2011-10-13
> **freesitebuilder said:**
> I haven't changed my login - but the passwords on the keyring are blank. When I try to reset the keyring password, it asks for my old password, and then the new password - but I don't know what it's set the "old" password to!

I did have a apport warning this morning, this is the log:

System: Linux 2.6.35-30-generic-pae #60-Ubuntu SMP Mon Sep 19 22:29:36 UTC 2011 i686
X Vendor: The X.Org Foundation
X Vendor Release: 10900000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Clearlooks
Icon Theme: gnome
GTK+ Modules: gnomesegvhandler, canberra-gtk-module

Memory status: size: 391729152 vsize: 391729152 resident: 107524096 share: 32063488 rss: 107524096 rss_rlim: 18446744073709551615
CPU usage: start_time: 1318455097 rtime: 368 utime: 292 stime: 76 cutime:2 cstime: 2 timeout: 0 it_real_value: 0 frequency: 100

----------- .xsession-errors ---------------------
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1473): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
Could not attach to process.  If your uid matches the uid of the target
process, check the setting of /proc/sys/kernel/yama/ptrace_scope, or try
again as the root user.  For more details, see /etc/sysctl.d/10-ptrace.conf
ptrace: Operation not permitted.
/home/dianne/2543: No such file or directory.
No stack.
--------------------------------------------------

Is there anywhere I can (safely!) dig about to see what the password has been set to?
The password should be the same as the login password you set when you installed Ubuntu. As far as I know there is no way how it could change on it's own, or really by any other means than the user manually changing it with the Passwords and Encryption Keys-tool..

If you are absolutely sure that you haven't stored any important data that you can't recover into the keyring, you could try deleting the existing one and creating a new one.

On the other hand the error you got would indicate that there's something else wrong on your system, and since the problems occurred at the same time they could very well be related. Canberra is used in Gnome for audio notifications and some accessibility features, so it failing should not have any effect on the keyring. Moe likely there's some other problem that resulted in both Canberra's and the keyring's problems. I have no idea what that might be, though. Have you checked ~/.xsession-errors file? Perhaps there's something relevant logged in there.

---

### Post by freesitebuilder on 2011-10-16
Don't know if this is relevant from authlog


Oct  9 17:35:14 dianne-desktop gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Oct  9 18:17:01 dianne-desktop CRON[3917]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct  9 18:17:01 dianne-desktop CRON[3917]: pam_unix(cron:session): session closed for user root
Oct  9 19:17:01 dianne-desktop CRON[4062]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct  9 19:17:01 dianne-desktop CRON[4062]: pam_unix(cron:session): session closed for user root
Oct  9 19:29:02 dianne-desktop gnome-screensaver-dialog: gkr-pam: unlocked login keyring
Oct  9 19:52:44 dianne-desktop gnome-keyring-daemon[1415]: dbus failure unregistering from session: Connection is closed
Oct  9 19:52:44 dianne-desktop polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.29, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf8) (disconnected from bus)
Oct  9 19:52:44 dianne-desktop gnome-keyring-daemon[1415]: dbus failure unregistering from session: Connection is closed
Oct  9 19:52:52 dianne-desktop gdm-session-worker[4569]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dianne"
Oct  9 19:52:56 dianne-desktop gdm-session-worker[4569]: pam_unix(gdm:session): session opened for user dianne by (uid=0)
Oct  9 19:52:56 dianne-desktop gdm-session-worker[4569]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Oct  9 19:52:57 dianne-desktop gnome-keyring-daemon[4591]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk
Oct  9 19:52:59 dianne-desktop polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session4 (system bus name :1.78 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf8)
Oct  9 19:53:16 dianne-desktop dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.91" (uid=1000 pid=4680 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=859 comm="/usr/sbin/console-kit-daemon))
Oct  9 19:53:21 dianne-desktop polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session4 (system bus name :1.78, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf8)
Oct 10 13:58:14 dianne-desktop gdm-session-worker[1288]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dianne"
Oct 10 13:58:18 dianne-desktop gdm-session-worker[1288]: pam_unix(gdm:session): session opened for user dianne by (uid=0)
Oct 10 13:58:18 dianne-desktop gdm-session-worker[1288]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Oct 10 13:58:19 dianne-desktop gnome-keyring-daemon[1455]: couldn't allocate secure memory to keep passwords and or keys from being written to the disk
Oct 10 13:58:20 dianne-desktop polkitd(authority=local): Registered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.29 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf8)
Oct 10 13:58:43 dianne-desktop dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.41" (uid=1000 pid=1544 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=850 comm="/usr/sbin/console-kit-daemon))
Oct 10 14:17:01 dianne-desktop CRON[2579]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 10 14:17:01 dianne-desktop CRON[2579]: pam_unix(cron:session): session closed for user root
Oct 10 15:17:01 dianne-desktop CRON[3028]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct 10 15:17:01 dianne-desktop CRON[3028]: pam_unix(cron:session): session closed for user root
Oct 10 16:09:54 dianne-desktop polkitd(authority=local): Unregistered Authentication Agent for session /org/freedesktop/ConsoleKit/Session2 (system bus name :1.29, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.utf8)

I have no problems logging in, and running things - but I get the keyring error message whenever I try to do anything that needs passwords - email for example.

---


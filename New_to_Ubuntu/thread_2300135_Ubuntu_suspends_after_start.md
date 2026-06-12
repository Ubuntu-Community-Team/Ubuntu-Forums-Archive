---
title: "Ubuntu suspends after start"
date: 2015-10-23
forum: New to Ubuntu
---

### Post by erick13 on 2015-10-23
Hello everybody, i'm new in this forum. First of all i want to thank everyone of you who could give me your help. I'm facing this issue since Ubuntu 15.04, when i turn on the pc and it shows me the login screen, it simply suspends, it is a very annoying problem i hope you could help me. This happens everytime i turn on or reboot into ubuntu. Here's a log taken immediately i log in the user account. 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Oct 23 15:36:09 Erick-UbuntuPC systemd-logind[553]: New seat seat0.
Oct 23 15:36:09 Erick-UbuntuPC systemd-logind[553]: Watching system buttons on /dev/input/event3 (Power Button)
Oct 23 15:36:09 Erick-UbuntuPC systemd-logind[553]: Watching system buttons on /dev/input/event5 (Video Bus)
Oct 23 15:36:09 Erick-UbuntuPC systemd-logind[553]: Watching system buttons on /dev/input/event0 (Power Button)
Oct 23 15:36:09 Erick-UbuntuPC systemd-logind[553]: Watching system buttons on /dev/input/event1 (Lid Switch)
Oct 23 15:36:09 Erick-UbuntuPC systemd-logind[553]: Watching system buttons on /dev/input/event2 (Sleep Button)
Oct 23 15:36:15 Erick-UbuntuPC lightdm: pam_unix(lightdm-autologin:session): session opened for user erick by (uid=0)
Oct 23 15:36:15 Erick-UbuntuPC systemd-logind[553]: New session c1 of user erick.
Oct 23 15:36:15 Erick-UbuntuPC systemd: pam_unix(systemd-user:session): session opened for user erick by (uid=0)
Oct 23 15:36:16 Erick-UbuntuPC gnome-keyring-daemon[825]: couldn't access control socket: /run/user/1000/keyring/control: No existe el archivo o el directorio
Oct 23 15:36:16 Erick-UbuntuPC gnome-keyring-daemon[820]: couldn't access control socket: /run/user/1000/keyring/control: No existe el archivo o el directorio
Oct 23 15:36:17 Erick-UbuntuPC systemd-logind[553]: Suspending...
Oct 23 15:39:41 Erick-UbuntuPC systemd-logind[553]: Lid opened.
Oct 23 15:39:41 Erick-UbuntuPC systemd-logind[553]: Operation finished.
Oct 23 15:39:43 Erick-UbuntuPC gnome-keyring-daemon[848]: The PKCS#11 component was already initialized
Oct 23 15:39:43 Erick-UbuntuPC gnome-keyring-daemon[848]: The Secret Service was already initialized
Oct 23 15:39:43 Erick-UbuntuPC gnome-keyring-daemon[848]: The SSH agent was already initialized
Oct 23 15:39:45 Erick-UbuntuPC polkitd(authority=local): Registered Authentication Agent for unix-session:c1 (system bus name :1.36 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale es_VE.UTF-8)
Oct 23 15:39:58 Erick-UbuntuPC dbus[575]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.42" (uid=0 pid=1185 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=554 comm="/usr/sbin/NetworkManager --no-daemon ")
Oct 23 15:39:58 Erick-UbuntuPC dbus[575]: [system] Rejected send message, 10 matched rules; type="method_return", sender=":1.42" (uid=0 pid=1185 comm="/usr/sbin/dnsmasq --no-resolv --keep-in-foreground") interface="(unset)" member="(unset)" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=554 comm="/usr/sbin/NetworkManager --no-daemon ")
Oct 23 15:40:09 Erick-UbuntuPC dbus[575]: [system] Failed to activate service 'org.bluez': timed out
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

---


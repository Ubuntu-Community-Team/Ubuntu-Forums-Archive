---
title: "A guest was logged on to my computer!"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Rokefuller on 2012-12-13
I am new to Ubuntu and Lenox.  Not to long after installing Ubuntu,  I booted up my computer and left the room for a few minutes and came back and discovered that the guest account was active.  Some one had logged into my computer.  I pulled the plug on my modem.  I began to wonder if this was due to a reported system error.  Do community support personnel access computers without permission or notification in response to reported system errors?    Thank You!

---

### Post by MG&amp;TL on 2012-12-13
> **Rokefuller said:**
> I am new to Ubuntu and Lenox.  Not to long after installing Ubuntu,  I booted up my computer and left the room for a few minutes and came back and discovered that the guest account was active.  Some one had logged into my computer.  I pulled the plug on my modem.  I began to wonder if this was due to a reported system error.  Do community support personnel access computers without permission or notification in response to reported system errors?    Thank You!

No, this isn't even possible unless you've installed desktop sharing software and configured your router appropriately. Even then, community support wouldn't do that, unless you asked *really* nicely. :) If you have done these things, then we can look at logs and such.

I suspect what's happened is someone in your house logged in. Or your cat. You get the picture. :)

---

### Post by Cheesehead on 2012-12-13
> **Rokefuller said:**
> Do community support personnel access computers without permission or notification in response to reported system errors?

No. Not possible. And quite rude.

If someone used your Guest account, then the most likely scenario is that they did so from your keyboard. The Guest account, last time I checked, could not be used remotely.

There *is* a way to get additional information on reported errors using the whoopsie/apport system. But it wouldn't request that info from your system...it would request additional data from the next machine to report the same problem, and it could only learn what apport has permissions to learn (stack traces and similar wild excitement). Apport has, as far as I know, no way to access personal data. Nor does whoopsie have any way to contact or login to another system. And neither apport nor whoopsie use the guest account.

---

### Post by jpeddicord on 2012-12-14
> **Rokefuller said:**
> I am new to Ubuntu and Lenox.  Not to long after installing Ubuntu,  I booted up my computer and left the room for a few minutes and came back and discovered that the guest account was active.  Some one had logged into my computer.  I pulled the plug on my modem.  I began to wonder if this was due to a reported system error.  Do community support personnel access computers without permission or notification in response to reported system errors?    Thank You!

Where did you see that the guest account was active? Was it in the menu on the top right? Or was it the only account signed in?

If you see "Guest Session" in the menu on the top right corner of the screen, that doesn't mean that it's in use; it's just giving you the option to use it if you please. The guest session is useful if you want to lend your computer to a friend for a moment, as your own session will be locked and everything they do will be erased once they're done.

---

### Post by resander on 2012-12-14
I think Ubuntu logs logins and logouts in file auth.log in directory log, which in turn is in directory var.
To view it you need to login as administrator.

---

### Post by Rokefuller on 2012-12-14
Thank you all for your replies.  For clarification.  I was the only one home.  This is the only computer in the house.  The computer was hard booted less than 15 minutes when I tried to save a file to my documents, my documents did not come up but another folder did.  I checked the drop down menu at the upper right hand corner of the screen.  Both My name and the guest account had a white dot to the left and a green check mark in a white circle to the right.  Only after I pulled the plug on the modem and terminated the guest session was I able to access my home folder to save the document.

---

### Post by Rokefuller on 2012-12-14
> **resander said:**
> I think Ubuntu logs logins and logouts in file auth.log in directory log, which in turn is in directory var.
To view it you need to login as administrator.


This was copied from Var/Log/auth.log.2.gz:

Nov 25 20:57:20 roger-Aspire-5920 dbus[671]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.29" (uid=110 pid=1483 comm="/usr/lib/indicator-session/indicator-session-servi") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1185 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov 25 20:57:20  dbus[671]: last message repeated 3 times
Nov 25 20:57:20 roger-Aspire-5920 dbus[671]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.38" (uid=110 pid=1485 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1185 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov 25 20:57:33 roger-Aspire-5920 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: group added to /etc/group: name=guest-Cls1iW, GID=125
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: group added to /etc/gshadow: name=guest-Cls1iW
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: new group: name=guest-Cls1iW, GID=125
Nov 25 20:57:35 roger-Aspire-5920 useradd[1723]: new user: name=guest-Cls1iW, UID=115, GID=125, home=/, shell=/bin/bash
Nov 25 20:57:35 roger-Aspire-5920 usermod[1728]: change user 'guest-Cls1iW' password
Nov 25 20:57:35 roger-Aspire-5920 chage[1733]: changed password expiry for guest-Cls1iW
Nov 25 20:57:35 roger-Aspire-5920 chfn[1736]: changed user 'guest-Cls1iW' information
Nov 25 20:57:35 roger-Aspire-5920 usermod[1744]: change user 'guest-Cls1iW' home from '/' to '/tmp/guest-Cls1iW'
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: Successful su for guest-Cls1iW by root
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: + ??? root:guest-Cls1iW
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: pam_unix(su:session): session opened for user guest-Cls1iW by (uid=0)
Nov 25 20:57:36 roger-Aspire-5920 su[1749]: pam_unix(su:session): session closed for user guest-Cls1iW
Nov 25 20:57:36 roger-Aspire-5920 su[1749]: pam_xdg_support(su:session): Called as non-root.
Nov 25 20:57:36 roger-Aspire-5920 lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-Cls1iW by (uid=0)
Nov 25 20:57:36 roger-Aspire-5920 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Nov 25 20:57:39 roger-Aspire-5920 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session3 (system bus name :1.55 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)

---

### Post by jpeddicord on 2012-12-14
> **Rokefuller said:**
> This was copied from Var/Log/auth.log.2.gz:

Nov 25 20:57:20 roger-Aspire-5920 dbus[671]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.29" (uid=110 pid=1483 comm="/usr/lib/indicator-session/indicator-session-servi") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1185 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov 25 20:57:20  dbus[671]: last message repeated 3 times
Nov 25 20:57:20 roger-Aspire-5920 dbus[671]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.38" (uid=110 pid=1485 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.17" (uid=0 pid=1185 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Nov 25 20:57:33 roger-Aspire-5920 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: group added to /etc/group: name=guest-Cls1iW, GID=125
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: group added to /etc/gshadow: name=guest-Cls1iW
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: new group: name=guest-Cls1iW, GID=125
Nov 25 20:57:35 roger-Aspire-5920 useradd[1723]: new user: name=guest-Cls1iW, UID=115, GID=125, home=/, shell=/bin/bash
Nov 25 20:57:35 roger-Aspire-5920 usermod[1728]: change user 'guest-Cls1iW' password
Nov 25 20:57:35 roger-Aspire-5920 chage[1733]: changed password expiry for guest-Cls1iW
Nov 25 20:57:35 roger-Aspire-5920 chfn[1736]: changed user 'guest-Cls1iW' information
Nov 25 20:57:35 roger-Aspire-5920 usermod[1744]: change user 'guest-Cls1iW' home from '/' to '/tmp/guest-Cls1iW'
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: Successful su for guest-Cls1iW by root
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: + ??? root:guest-Cls1iW
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: pam_unix(su:session): session opened for user guest-Cls1iW by (uid=0)
Nov 25 20:57:36 roger-Aspire-5920 su[1749]: pam_unix(su:session): session closed for user guest-Cls1iW
Nov 25 20:57:36 roger-Aspire-5920 su[1749]: pam_xdg_support(su:session): Called as non-root.
Nov 25 20:57:36 roger-Aspire-5920 lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-Cls1iW by (uid=0)
Nov 25 20:57:36 roger-Aspire-5920 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Nov 25 20:57:39 roger-Aspire-5920 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session3 (system bus name :1.55 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)

Is your clock set correctly? That looks like it's from November 25, and by its contents, looks like normal usage of the guest account from the login screen.

---

### Post by Rokefuller on 2012-12-14
> **jpeddicord said:**
> Is your clock set correctly? That looks like it's from November 25, and by its contents, looks like normal usage of the guest account from the login screen.

The clock is set right.  the original incident happened a few weeks back.  I just recently inquired about it.  I did not make note of the date but it was in the morning.  I was simply looking in the log for examples of guest usage.  If the numeric values separated by colons following the date is a time stamp, then this log in happened in the evening.  it is good to know that the log represents usage from the log in screen, but is peculiar.  My wife and I do not use the guest account and use only one profile.  What should I look for that would point to a remote guest login?

I will look further.  Thanks again for your help.

---

### Post by MoebusNet on 2012-12-15
Just as a possibility to consider, it is possible to accidentally log-in using the Guest account rather than your usual UserName account. I know it is possible because I have done it. I was attempting to perform several tasks at the same time, accidentally made some erroneous keyboard entries without noticing and voila I was logged in as Guest. It didn't really register until I wanted to perform some system updates; I just had to log out as Guest then log back into my regular UserName account - no biggie.

May I suggest the possibility that something similar occurred in your case?

---

### Post by Rokefuller on 2012-12-16
> **MoebusNet said:**
> Just as a possibility to consider, it is possible to accidentally log-in using the Guest account rather than your usual UserName account. I know it is possible because I have done it. I was attempting to perform several tasks at the same time, accidentally made some erroneous keyboard entries without noticing and voila I was logged in as Guest. It didn't really register until I wanted to perform some system updates; I just had to log out as Guest then log back into my regular UserName account - no biggie.

May I suggest the possibility that something similar occurred in your case?

Thank You!  I have been playing around with this and have discovered that you can log into the guest account after having logged in under your own user account and switching back with out logging out to the administrators account, it does show both accounts active.  I am thinking that maybe the computer went to sleep mode with the guest account active and I did not actually hard boot it as I thought.

---

### Post by guardsman85 on 2012-12-16
I'm going w/ the some of the other posters, and guessing this was a case of accidentally clicking the "Guest Session" option on the login screen.  I found a helpful blog post which details how to disable the guest account.  You can read it in full [here]("http://catlingmindswipe.blogspot.com/2012/10/how-to-disable-guest-account-on-ubuntu.html"), but I've summarized the important steps below:  

Open a terminal window and execute these command:
```
$ gksu gedit /etc/lightdm/lightdm.conf

```Add the following line to the end of the file:
```
allow-guest=false
```[FONT=&quot][FONT=&quot]

[/FONT][/FONT]
Save the document, and exit.

Reboot, or execute the following command in the terminal (will close all windows):
```
$ sudo restart lightdm
```[FONT=&quot]

[/FONT]
Let me know if you need more help.

EDIT:

I logged into my own computer with a guest session, and checked /var/log/auth.log to see what the entries looked like.  It was very similar to what was in your log file, so I think what you are seeing is normal for a guest login from the login screen.  I thought maybe it would be reassuring to break the entries down for you, so you can see what they mean.  Someone please correct me if I make a mistake.  (Log entry first followed by explaination.)


```
Nov 25 20:57:33 roger-Aspire-5920 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
```  This indicates that the login screen is closing.  This is your indication that the login happed locally, and not remotely through a service such as SSH.
```
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: group added to /etc/group: name=guest-Cls1iW, GID=125
```  A new group is going to be created for the guest user.  All Linux users belong to groups.  This line indicates that the group information is being written to /etc/groups, a file which defines groups to which users belong.
```
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: group added to /etc/gshadow: name=guest-Cls1iW
```  The group information is added to /etc/gshadow which contains an encrypted password for the group and group member information.  This file is only readable by root (the admin account on Linux systems).
```
Nov 25 20:57:34 roger-Aspire-5920 groupadd[1719]: new group: name=guest-Cls1iW, GID=125
```  The group is created.
```
Nov 25 20:57:35 roger-Aspire-5920 useradd[1723]: new user: name=guest-Cls1iW, UID=115, GID=125, home=/, shell=/bin/bash
```  The guest user account is created, the user id, group id, home and shell paths are all assigned.
```
Nov 25 20:57:35 roger-Aspire-5920 usermod[1728]: change user 'guest-Cls1iW' password
```  When a Linux user is created, it must have a password.  It looks like a random password is created for the guest at this point.
```
Nov 25 20:57:35 roger-Aspire-5920 chage[1733]: changed password expiry for guest-Cls1iW
```  The password expiration information is set.
```
Nov 25 20:57:35 roger-Aspire-5920 chfn[1736]: changed user 'guest-Cls1iW' information
```  I'm not sure exactly what changes here, but some arbitrary user information is set.
```
Nov 25 20:57:35 roger-Aspire-5920 usermod[1744]: change user 'guest-Cls1iW' home from '/' to '/tmp/guest-Cls1iW'
```  The guest's home directory is changed from the /home directory to a directory in /tmp.  This way anything in the directory will be gone after reboot.
```
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: Successful su for guest-Cls1iW by root
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: + ??? root:guest-Cls1iW

```  Switching users to guest-Cls1iW and starting a new session.
```
Nov 25 20:57:35 roger-Aspire-5920 su[1749]: pam_unix(su:session): session opened for user guest-Cls1iW by (uid=0)
Nov 25 20:57:36 roger-Aspire-5920 su[1749]: pam_unix(su:session): session closed for user guest-Cls1iW
``` I think that this is where the password authentication module authenticates the guest users.
```
Nov 25 20:57:36 roger-Aspire-5920 su[1749]: pam_xdg_support(su:session): Called as non-root.
Nov 25 20:57:36 roger-Aspire-5920 lightdm: pam_unix(lightdm-autologin:session): session opened for user guest-Cls1iW by (uid=0)
Nov 25 20:57:36 roger-Aspire-5920 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Nov 25 20:57:39 roger-Aspire-5920 polkitd(authority=local): Registered  Authentication Agent for  unix-session:/org/freedesktop/ConsoleKit/Session3 (system bus name :1.55  [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1],  object path /org/gnome/PolicyKit1/AuthenticationAgent, locale  en_US.UTF-8)
```  The rest of this appears to be related to the creating of the desktop session (someone else can elaborate if they think it's relevant).

Further down in your log file you should see messages indicating when the guest session was terminated.  You should also see indications the guest user and group groups were removed.  The logs really do seem to indicate that this was a local login from the login screen, so I don't think you have much to worry about.  Disabling the guest account as mentioned above would be a good idea though if you have concerns about accidentally starting a guest session (or having a kid in the house start one on purpose).

---

### Post by resander on 2012-12-17
I also wanted to remove Guest login by gksudo gedit /etc/lightdm/lightdm.conf, adding line allow-guest=false and restart by sudo restart lightdm.

This recipe worked for a 64-bit PC running 64-bit Ubuntu 12.04 LTS, but not for a 32-bit desktop with 12.04 LTS. It caused severe problems for 32-bit Ubuntu. Luckily I was rescued by help from the forum:

[http://ubuntuforums.org/showthread.php?t=2091211](http://ubuntuforums.org/showthread.php?t=2091211)

---


---
title: "How to mark that package requires user logout"
date: 2011-08-28
forum: Packaging and Compiling Programs
---

### Post by seeklinux on 2011-08-28
I am working on an debian package for Ubuntu which updates something that only takes effect after the user logs out and back in. I have seen updates of packages that put an indicator indicating that user logout/login is required. Similarly, some packages indicate reboot is required. Can someone point me to documentation on how that is done?

Thanks in advance.

---

### Post by SevenMachines on 2011-08-30
I've seen the reboot one in postinst scripts
```
if [ -x /usr/share/update-notifier/notify-reboot-required ]; then
            /usr/share/update-notifier/notify-reboot-required
        fi
```
Cant think of any packages offhand that do a logout notifier

---

### Post by seeklinux on 2011-09-29
Thanks for the information. I have done what was suggested, even though it is kind of overkill to indicate restart is needed when in actuality only a logout is needed. This works fine for the changes made at install time.

Now however, I have a similar issue the first time the user starts the application. I update the systray-whitelist which only takes effect after logout as well.  When running an application (not install processing) is there any system way to indicate a logout is needed? Or is it up to the application pop up its own notification?

Thanks.

---

### Post by SevenMachines on 2011-09-30
To bring up a logout dialog you can use a dbus request to the session manager as far as I recall. A simple dbus message to popup a notification sent from the application is probably what you want rather than a forced dialog though no? Along the lines of 
$ notify-send "Help me, I'm melting... logout is required..."
As you can tell, It's not something I really have had cause to do :)

---

### Post by seeklinux on 2011-10-01
Thanks, I decided to use zenity to pop up an informational message indicating that they should log out and back in. That worked pretty well.  It seems that zenity is installed by default, because I didn't do it myself. I have been testing on a pretty stock install of Ubuntu 10.04.

Still, with KDE there is a system indicator which shows the user should log-out, similar to the one that indicates a restart is needed. I wish I could find something like that with Unity, but I guess it doesn't exist.

---

### Post by seeklinux on 2011-10-13
OK, I just tried Ubuntu 11.10 with Unity.  /usr/share/update-notifier/notify-reboot-required is still there, but it doesn't turn the icon (the new one) red like it did the old one. So the user doesn't know they are supposed to restart.  It told me that "Some software updates won't apply until the computer next restarts " when I used the icon to tried to "log out" (and it provided a "restart instead" button) but the user is not likely to do that. Is anyone else seeing this?

Thanks.

---


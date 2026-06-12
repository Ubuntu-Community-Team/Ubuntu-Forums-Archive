---
title: "Creating Logon Banner in Ubuntu 16.04 LTS"
date: 2018-08-02
forum: New to Ubuntu
---

### Post by john3j on 2018-08-02
Greetings!

This is my first post and I am new to Ubuntu.  I am trying to make the switch over from Windows.  I downloaded the desktop version of Ubuntu 16.04 LTS and declined to install anything additional during setup, so it is a pretty clean system.  I am trying to figure out how to get a consent banner to display at login for all users.  I modified the /etc/issue file, but nothing changes at the login screen.  If anyone could provide advice on how to make it work, I would greatly appreciate it.  I am not sure if installing a gnome package of some sort is required.

-john

---

### Post by deadflowr on 2018-08-02
/etc/issues works better for console logins, rather than graphical logins, afaik.
You might be able to set a graphical login banner for Ubuntu 16.04 like these:
[https://ubuntuforums.org/showthread.php?t=2186061]("https://ubuntuforums.org/showthread.php?t=2186061")
[https://askubuntu.com/questions/193357/how-do-i-create-a-popup-banner-before-login-with-lightdm]("https://askubuntu.com/questions/193357/how-do-i-create-a-popup-banner-before-login-with-lightdm")
(Ubuntu 16.04 uses unity so you might try that method for your use, I would think it would still work)

I would recommend making a copy of the original ubuntu.desktop file first, before editing it
Something like
```
cp /usr/share/xsessions/ubuntu.desktop ~/Documents
```
which would save the copy in your own users Documents folder.
If the new one is broken, you can restore the old from a console settings (ctrl + alt + F1 (2-6) will move you to a console and allow you to login there, at which time you could restore the old desktop file like
```
sudo cp ~/Documents/ubuntu.desktop /usr/share/xsessions/ubuntu.desktop
```
and restart the display manager
```
sudo restart lightdm
```
(this reloads the login screen)
allowing you to start over.
Or that is what I would do; my 2 cents)


Sidenote:
On Ubuntu 18.04, it can set a banner, in a just as convoluted way. More or less
Here's how that can be done:
[https://help.gnome.org/admin/system-admin-guide/stable/login-banner.html.en]("https://help.gnome.org/admin/system-admin-guide/stable/login-banner.html.en")

---


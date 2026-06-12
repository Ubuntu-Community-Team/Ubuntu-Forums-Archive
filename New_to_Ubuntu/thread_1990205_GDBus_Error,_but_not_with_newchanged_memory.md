---
title: "GDBus Error, but not with new/changed memory"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by w0ipl on 2012-05-29
I am running 11.04 and have been having no problems. Yesterday afternoon I started receiving the same error messaage
> GConf error: Failed to contact configuration server; the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: GetIOR failed: GDBus.Error: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus))
that the person that changed his memory has/was getting. I have gone to the included URL and found nothing to indicate what has happened or what I need to do, or even where to start.

I do NOT have access to terminal, or any of the standard desktop features. It does display an icon of "Computer" and double clicking that gives me access to the files that reside on my desktop, without any of the other desktop function.

I have an HTML file on my desktop, and double clicking that provides a FireFox session. I overwrite the URL with the one for my web page and I then have access to all of my web page and all of my bookmarks (thus I am able to get here).

Since I do not have access to terminal, how do I uninstall/reinstall anything?

It was working fine yesterday morning, did my usual internet browsing, shut it down normally, and yesterday afternoon I started getting the error message shown above as I try to get going again.

As a PS, I can not access Thunderbird for E-mail.

Talk about feeling helpless . . . . 

Thanks
 Pat

Edit:
~~ Used CTRL+ALT+F2 to get console session. Logged in and tried to run gconf -editor and it tells me that is not
a valid command.
~~ It tells me that there is a new release of 'oneric' available and to use do-(something)-update. I try that and
it says there is no new release available, after just telling me it was. . . . . HUH?!

---

### Post by w0ipl on 2012-05-29
Resolved the issue with the following command:

sudo apt-get install xubuntu-desktop

No Unity = No problem.

---


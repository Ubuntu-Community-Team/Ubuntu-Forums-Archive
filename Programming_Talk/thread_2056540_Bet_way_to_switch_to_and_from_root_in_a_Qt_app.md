---
title: "Bet way to switch to and from root in a Qt app"
date: 2012-09-11
forum: Programming Talk
---

### Post by RichardUK on 2012-09-11
This is for an app written in Qt Creator to run on my, and maybe others, Ubuntu systems. Written in C++

I have an app that needs root access. Currently I set the app file owner to root and set the s bit. Then when the app starts it sets the effective user id to the real user id resetting the effective user id back to root when I need the access. Problem is that my Qt app does not like it, GTK+ moans about it.

```

This process is currently running setuid or setgid.
GTK+ does not allow this therefore Qt cannot use the GTK+ integration.
Try launching your app using 'gksudo', 'kdesudo' or a similar tool.

See http://www.gtk.org/setuid.html for more information.


```

Reading their doc they suggest having two apps, one for the root work, one for my non root GUI. Is this really the best way?

Really just need a simple answer:
A) "Yes, do it like that and stop over thinking the problem".
or
B) "No, there is a much better way for Ubuntu apps, read this ....."

Thanks. :)

---


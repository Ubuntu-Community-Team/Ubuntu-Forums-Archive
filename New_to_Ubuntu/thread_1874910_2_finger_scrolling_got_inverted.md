---
title: "2 finger scrolling got inverted"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by Droid Stark on 2011-11-04
Hello everyone,
I recently downloaded Ubuntu 11.10 and it was working perfectly.But now 2 finger scrolling suddenly got inverted, (when I swipe 2 fingers to scroll down the page scrolls up, and vice versa).

This problem started to happen alongside another problem which was title bars now showing for windows when they're not maximized, which I solve by removing the check from window decorations in compiz, and then rechecking it again.


Any ideas?

---

### Post by illgetit on 2011-11-04
Are you using a touch screen system?

---

### Post by Droid Stark on 2011-11-04
no it is not a touch screen system.
I am using a Sony VAIO (VPCCA series)

---

### Post by Droid Stark on 2011-11-04
I started using a Logitech mouse a few days ago, could that be causing the problem?

---

### Post by pierreyy on 2011-11-04
your pointer settings have changed, ive deliberately done this.... 


open your terminal and type in the following command

```
  gksu gedit 
```a gedit file will open inside it copy and pase this

>  pointer = 1 2 3  4 5 6 7 8 9 10 11 12 


 save the file as "   .Xmodmap  " in your home folder


let me know if it works

---

### Post by Droid Stark on 2011-11-04
Thanks for your reply, but this is what happened:
The file that opened was blank, and the terminal said 

""(gksu:1989): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap", ""

I pasted the string u gave me nonetheless and saved it in home folder, scrolling problem didn't change and this was the terminal's output:

"" (gedit:1991): Gtk-DEBUG: -- ""
"" (gedit:1991): Gtk-DEBUG: Finding out if Tracker is available via D-Bus... ""
"" (gedit:1991): Gtk-DEBUG: Tracker is not available, GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Tracker1 was not provided by any .service files""

""(gedit:1991): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.Z2ME4V': No such file or directory ""

---


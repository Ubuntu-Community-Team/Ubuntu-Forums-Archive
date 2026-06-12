---
title: "DVD playback broken in upgrade"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Famicommander on 2008-04-26
I was running Xubutnu 7.10, and everything was running flawlessly. I decided to see if I could just upgrade my distro to Xubuntu 8.04, and much to my surpise it went fine.

Everything is working great, and it is actually a lot faster.

But I did notice one thing: DVD playback no longer works. I'm not sure what went wrong or how to fix it, but here's what happens when I try to play a DVD in totem:

```
jason@ubuntu:~$ totem

** (totem:5974): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 58 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

(totem:5974): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(totem:5974): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(totem:5974): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GObject'

(totem:5974): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

And before someone tries to tell me that I need VLC instead, I've tried it and it doesn't work.

Any help would be very much appreciated.

---

### Post by warbread on 2008-04-26
Have you tried reinstalling the required codecs?  It seems like something mike have borked your permissions.

---

### Post by warbread on 2008-04-26
Also, do this:

```
 :-$ totem --debug >> totemdebug.txt
```

And post the contents of the file.

---

### Post by Famicommander on 2008-04-26
> **warbread said:**
> Also, do this:

```
 :-$ totem --debug >> totemdebug.txt
```

And post the contents of the file.

```
** (totem:6370): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

```

That's what I get.

---

### Post by warbread on 2008-04-26
Wow, that's it?  Ok, do this:

```
 :-$ ls /usr/share/dbus-1/ | grep org.* 
```

Let's see if org.SettingsDaemon is there at all.

---

### Post by Famicommander on 2008-04-26
> **warbread said:**
> Wow, that's it?  Ok, do this:

```
 :-$ ls /usr/share/dbus-1/ | grep org.* 
```

Let's see if org.SettingsDaemon is there at all.

Nothing happens.

---

### Post by warbread on 2008-04-26
```
 :-$ ls /usr/share/dbus-1/**services/** | grep org.* 
```


Whoops, my bad.  There's what we want.

---

### Post by Famicommander on 2008-04-26
```
jason@ubuntu:~$ ls /usr/share/dbus-1/services/ | grep org.*
gnome-org.freedesktop.PolicyKit.AuthenticationAgent.service
org.freedesktop.Notifications.service
org.gnome.keyring.service
org.gnome.PolicyKit.AuthorizationManager.service
org.gnome.PolicyKit.service
org.xfce.calendar.service
org.xfce.FileManager.service
org.xfce.orage.service
org.xfce.RunDialog.service
org.xfce.Thunar.service

```

That's what it gives me.

---

### Post by warbread on 2008-04-26
Ah ha!  Now we're getting somewhere.  You're missing org.gnome.SettingsDaemon.service for some reason. Totem was complaining about this.

Unfortunately, I don't know how to fix that.  I'll post here if I find anything.

Do you have ubuntu-desktop installed, or did you just install xfce?  If you have hard drive space to burn, I would try installing ubuntu-desktop, or even reinstalling it if you have it already, and see if that helps.  That's really all I've got for now.

---

### Post by Famicommander on 2008-04-26
> **warbread said:**
> Ah ha!  Now we're getting somewhere.  You're missing org.gnome.SettingsDaemon.service for some reason. Totem was complaining about this.

Unfortunately, I don't know how to fix that.  I'll post here if I find anything.

Do you have ubuntu-desktop installed, or did you just install xfce?  If you have hard drive space to burn, I would try installing ubuntu-desktop, or even reinstalling it if you have it already, and see if that helps.  That's really all I've got for now.
This is a regular Xubuntu 7.10 install from the Xubuntu alternate install CD. I just used the update manager to upgrade to 8.04.

---

### Post by warbread on 2008-04-26
Ok, here's an idea (though it's kind of out-there):  Boot to live cd and mount your hard drive.  Make a new folder in your /home directory and call it whatever you want.  Then do:

```
 :-$ sudo cp /usr/share/dbus-1/services/org.gnome.SettingsDaemon.service /home/yourname/yourdirectory 
```

Then boot as normal.  When in, type:

```
 :-$ sudo cp /home/yourname/yourdirectory/org.gnome.SettingsDaemon.service /usr/share/dbus-1/services/ 
```

I have no idea if that will work, or what it'll do if it does anything at all, but it's an easily undoable thing, so I don't see how it could hurt to try.

---


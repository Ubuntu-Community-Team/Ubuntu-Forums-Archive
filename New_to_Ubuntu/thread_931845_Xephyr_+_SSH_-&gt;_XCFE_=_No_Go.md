---
title: "Xephyr + SSH -&gt; XCFE = No Go"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Locke_99GS on 2008-09-27
I have an old PC running Xubuntu, and a newer one running Ubuntu. Both are Hardy. I intend to eventually run the Xubuntu machine headless, but would still like a DE available to more easily administer it.

On the XFCE machine, I have openssh-server intsalled, and can ssh into it without a hitch from my Ubuntu machine.

I installed Xephyr on my Ubuntu machine, so I can have the entire DE accessible from the Xubuntu machine.

When I run these commands, XFCE gets stuck on the splash screen.

```

locke@locke-desktop:~$ Xephyr -ac -screen 800x600 -br -reset -terminate 2> ~/xephyr.log :1 &
[1] 31188
locke@locke-desktop:~$ DISPLAY=:1.0
locke@locke-desktop:~$ ssh -Xf ducky@192.168.1.101 xfce4-session 2> ~/ssh.log
ducky@192.168.1.101's password: 

```

This is what my ssh.log looks like (edited to remove redundant entries)

```

Warning: No xauth data; using fake authentication data for X11 forwarding.

** Message: Querying XF86Misc extension
Xlib:  extension "XFree86-Misc" missing on display "localhost:10.0".

** (xfce-mcs-manager:6049): WARNING **: Your X server does not support XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
Xlib:  extension "XFree86-VidModeExtension" missing on display "localhost:10.0".
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found

** (update-notifier:6087): WARNING **: already running?


** (update-notifier:6095): WARNING **: already running?


** (nm-applet:6078): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.84" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'


** (nm-applet:6078): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.84" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'


** (nm-applet:6093): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.85" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'

```

It continues those two errors indefinitely.

In the meantime, the Xubuntu box is idling at the logon screen.

I've searched around and haven't found anything relevant. Would this be something that could be fixed by preventing XFCE from loading at boot - and if so, how would I go about doing that?

---

### Post by Locke_99GS on 2008-09-27
Any thoughts, guys?

---

### Post by Xiong Chiamiov on 2008-09-27
Hmm, I don't think it's a problem with XFCE running.  I don't know anything about xephyr, though, so I can't help you there.  Sorry.

Depending on what it is you need to be doing, [webmin]("http://www.webmin.com/") can be very useful.  I use it on a headless server when I don't want to edit my ssh config file by hand, or some such.

---

### Post by Locke_99GS on 2008-09-28
I appreciate the thought, but editing thing by hand doesn't really bother me. I'd just rather get this working, though.

---

### Post by Locke_99GS on 2008-09-28
Here is a screenshot showing about as far as I get - obviously X is forwarding correctly.

---

### Post by lykwydchykyn on 2008-09-28
I have to admit, I've never seen that method of remoting in to a machine before.  I've never managed to get Xephyr working right, but that' probably just my brain-deadness.

Looks like it's choking trying to load network manager applet.  I'm assuming your server box has a static IP, so maybe removing nm-applet would fix it?

I'll have to try this out myself.

EDIT: For what it's worth, I just tried this on my network, and it worked.  I got tons of dbus related errors, so apparently dbus is not happy about this arrangement and who knows what all that breaks.  But you should be getting past the splash.

Seems kind of slow, though (probably the encryption).  Can't you just query the server's X11 with Xephyr using XDMCP?

---

### Post by Locke_99GS on 2008-09-28
Well, aside from XDMCP being old and crappy, it doesn't work on this machine either. Of course, I have made plenty of changes, I could try again. I'd really like to it working this way, though.

I removed update-notifier and nm-applet from starting on the server box, and the status on the splash seems to get further, but now it hangs when the splash is saying "Performing Autostart".

The log tail shows nothing aside from the initial start-up stuff. No recurring errors, as before.

ssh.log:
```

locke@locke-desktop:~$ tail -f ssh.log
Xlib:  extension "XFree86-Misc" missing on display "localhost:10.0".

** (xfce-mcs-manager:4965): WARNING **: Your X server does not support XF86Misc extension
** Message: Querying Xkb extension
** Message: Xkb extension found
Xlib:  extension "XFree86-VidModeExtension" missing on display "localhost:10.0".
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found

```

xephyr.log
```

locke@locke-desktop:~$ tail -f xephyr.log
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!

```

And the screenshot showing where the splash is stuck, and the error-free log tails.


XFCE is warning about not having XF86Misc - could this be an issue? I wouldn't think so, and I thought it was enabled by default. I'll go check.

I just don't understand why this is not working. It *should* be working.

---

### Post by Locke_99GS on 2008-09-28
Ok, after a shitton of mostly xorg.conf and rc changes, XFCE successfully loads. (See attached) Surprisingly, the display is actually snappier through the tunnel to my desktop, than it is natively on the server. It does take quite a *long* time to load the session.

Now, I wrote a script load Xephyr and start the ssh tunnel, but when loading with the script, Xephyr crashes/closes after entering the password for ssh. It doesn't do this when I perform each command separately in a terminal.


Script ducky-xephyr:
```

#!/bin/bash

Xephyr -ac -screen 800x600 -br -reset -terminate 2> ~/xephyr.log :1 &
DISPLAY=:1
ssh -Xf ducky@192.168.1.151 xfce4-session 2> ~/ssh.log

```

Made executable and placed in /usr/bin:
```

chmod +x ducky-xephyr
sudo mv ducky-xephyr /usr/bin

```

Then a launcher is placed in the panel executing ducky-xephyr.



I suspect this is a simple scripting issue, but I don't hardly dabble with it. Any thoughts?

---

### Post by Locke_99GS on 2008-09-29
Ok, I discovered why Xephyr was closing when I used my script - After Xephyr's password prompt for the ssh connection, the -reset -terminate options caused it to close prematurely. I removed those, and now the script works from the launcher.

But, my current issue - it takes 34 minutes for XFCE to load after I start the tunnel. I'm sure it is likely some conflicting settings somewhere. When I login locally to that machine, it may take a minute or so to reach a usable desktop. (500mhz, 386m ram)

When the session finally loads, these lines po-up in my ssh.log tail:
```


(xfwm4:9309): libxfcegui4-WARNING **: ICE I/O Error

(xfwm4:9309): libxfcegui4-WARNING **: Disconnected from session manager.

(xfdesktop:9324): libxfcegui4-WARNING **: ICE I/O Error

(xfdesktop:9324): libxfcegui4-WARNING **: Disconnected from session manager.

(xfce4-panel:9311): libxfcegui4-WARNING **: ICE I/O Error

(xfce4-panel:9311): libxfcegui4-WARNING **: Disconnected from session manager.

```

Those mean nothing to me, but I haven't searched yet, either. :)

Once I get to a usable desktop over ssh, it is snappy and works *great*, so I doubt it is an issue with the network or speed/ram of either machine.

Again, any thoughts guys? 

Thanks in advance.

---


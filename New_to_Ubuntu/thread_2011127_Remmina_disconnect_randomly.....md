---
title: "Remmina disconnect randomly...."
date: 2012-06-26
forum: New to Ubuntu
---

### Post by d4m1r on 2012-06-26
I use Remmina in Ubuntu 12.04 LTS to connect to a Windows XP machine over RDP. Both local and remote monitors set to 1920x1080 so it displays fullscreen. It never disconnects while I am on the window, only when I minimize it, switch workspaces, etc. It is only when I go back to it do I realize it disconnected.....Copy of the error messages:

```
ERRINFO_DECRYPT_FAILED (0x00001192):
(a) Decryption using Standard RDP Security mechanisms (section 5.3.6) failed.
(b) Session key creation using Standard RDP Security mechanisms (section 5.3.5) failed.
recv: Connection reset by peer

PatBlt: unknown rop: 0x00A000C9

gdi_get_bitmap_pointer: requesting invalid pointer: (0,30) in 64x30
```

Using 0.9.99.1, anyone have any idea's on how to correct this or a workaround? :confused:

---

### Post by QIII on 2012-06-26
I've not encountered that with Xubuntu, although sometimes I do get an odd flicker image of my XP RDP session moving from workspace to workspace occasionally.

I have a machine running straight Ubuntu Quantal, so I don't know if it would be really helpful if I experimented.  I'll try to get to it sometime this week and see if I can reproduce it on 12.10.

---

### Post by d4m1r on 2012-08-22
> **QIII said:**
> I've not encountered that with Xubuntu, although sometimes I do get an odd flicker image of my XP RDP session moving from workspace to workspace occasionally.

I have a machine running straight Ubuntu Quantal, so I don't know if it would be really helpful if I experimented.  I'll try to get to it sometime this week and see if I can reproduce it on 12.10.

Bump, any update on this? ;)

Remmina is still crashing when connecting to a Windows XP machine over RDP:

```
ERRINFO_DECRYPT_FAILED (0x00001192):
(a) Decryption using Standard RDP Security mechanisms (section 5.3.6) failed.
(b) Session key creation using Standard RDP Security mechanisms (section 5.3.5) failed.

```and

```
(remmina:28780): Gtk-WARNING **: drawing failure for widget `GtkDrawingArea': invalid matrix (not invertible)

```

---

### Post by QIII on 2012-08-22
Wow.  Guess I forgot to get back with this one.

No update here, other than it works for me on Precise with Unity without problems, just like with Xubuntu.

But, you might be interested in this:

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1002363](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1002363)

Edit:  But I did just happen to realize something.  I have a little 15" screen on that machine off to the back corner of my desk, which normally just displays the logon screen because I'm RDPed into it rather than running it from its own IO devices.  The screen saver just came on and caught my eye.  Are you running your XP machine headless or with the monitor turned off?  Keyboard and mouse attached?

---

### Post by d4m1r on 2012-08-22
> **QIII said:**
> Wow.  Guess I forgot to get back with this one.

No update here, other than it works for me on Precise with Unity without problems, just like with Xubuntu.

But, you might be interested in this:

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1002363](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/1002363)

Edit:  But I did just happen to realize something.  I have a little 15" screen on that machine off to the back corner of my desk, which normally just displays the logon screen because I'm RDPed into it rather than running it from its own IO devices.  The screen saver just came on and caught my eye.  Are you running your XP machine headless or with the monitor turned off?  Keyboard and mouse attached?

I am appear of that bug report, and commented on it....Twice in fact ;) What version of Remmina are you using in 12.10? Did you try it full screen and switching workspaces? VPN?

Also, the machine at work is connected to a monitor/keyboard/mouse but they are all turned off. I don't see how that could be related though :-k

---


---
title: "Unable to Register Clicks"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by rsjc852 on 2014-02-23
Sorry for posting this a little out of place. However, since I decided to use the GNOME windows manager, and Linux Mint 16 being an offshoot of Ubuntu (as far as I know...), this should be answerable, or at least be able to be guessed at.

So I've been having a little bit of trouble here, and I get the feeling the answer is glaring me in the face:

When starting up a program, say firefox or anything with an editable area, this is what usually happens:

1. Program loads, everything is fine.
2. unable to exit, minimize, resize, or full screen the program (with the exception of pressing F11).
3. CTRL + ALT + DEL pulls up the Log off prompt, which is unclickable and 90% of the time unselectable with my keyboard.
4. any attempt to launch a program on the taskbar, pull up the application menu, or change any setting in the notification area (sound, wifi, etc) doesn't register.
5. In firefox, i have discovered that by pressing F12, this usually allows me to exit the program by giving me the ability to click the exit button, or minimize it if that's what I need to do.

If step 3 fails, then im logged off and returned to the login screen. Everything on that screen is clickable.
On return to the desktop, everything is registering once again.


But when this really becomes a problem is when I need to multitask and switch between several different windows.

Can anyone guess at what would cause this hell of a bug?

Related specs:

Acer V3-771G Laptop
USB R.A.T. 7
Internal PS/2 trackpad

Again, im using Linux Mint to hold me over until I can get Windows 7 back on my machine, but with the Mint forums being dead, and multiple projects and assignments coming up in a few days, I'm stressing over needing a fully functional laptop!

---

### Post by tgalati4 on 2014-02-24
It could be a hardware problem.  The keyboard works but the trackpad does not.  So let us look at some log files.  Open a terminal:

```
grep EE /var/log/Xorg.0.log
less ~/.xsession-errors
```

Spacebar to page forward, "q" to quit.

Have you spilled any liquid on your computer in the last few days?

In the meantime, get friendly with the keyboard [shortcuts]("http://community.linuxmint.com/tutorial/view/45").

---


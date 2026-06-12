---
title: "Login Screen Settings Problem"
date: 2010-06-18
forum: Philippine Team
---

### Post by stormsurge on 2010-06-18
Hi!

I have a problem when I try to unlock the Login Screen Settings.Nothing happens every time I click it that is why I can't configure my settings. Hoping for some feedbacks here. Thank you!

---

### Post by loell on 2010-06-18
in the command line, try executing, 

 ```
gdmsetup
```

if an error comes up, post it here.

---

### Post by aljoriz on 2010-06-18
Out of curiosity how does one access the command line during boot in Lucid?

---

### Post by stormsurge on 2010-06-18
```
** (gdmsetup:1503): DEBUG: init delay=30
** (gdmsetup:1503): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:1503): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:1503): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:1503): DEBUG: Init default session found:'gnome'
** (gdmsetup:1503): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:1503): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:1503): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:1503): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:1503): DEBUG: adding monitor for '/home/nelson/.face'
** (gdmsetup:1503): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:1503): DEBUG: Found 1 sessions for user nelson
** (gdmsetup:1503): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session1
** (gdmsetup:1503): DEBUG: GdmUserManager: sessions changed user=nelson num=1
** (gdmsetup:1503): DEBUG: GdmUserManager: added session for user: nelson
** (gdmsetup:1503): DEBUG: GdmUserManager: history output: nelson   77

** (gdmsetup:1503): DEBUG: init user='nelson' auto=True

```

The Login Screen Setting opened but still can't unlock and configure my Login Screen settings. 

Thank you!

---

### Post by loell on 2010-06-18
maybe it's  related to this  bug? [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/564094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/564094)

anyhow, try

```
ck-launch-session gdmsetup
```

---

### Post by stormsurge on 2010-06-18
Same problem encountered Sir.

---

### Post by loell on 2010-06-18
**sudo gmsetup**?

---

### Post by loell on 2010-06-18
**sudo gdmsetup**?

---

### Post by stormsurge on 2010-06-19
same problem.... :confused:

---

### Post by ursaminor on 2010-06-20
See [http://lani78.wordpress.com/2009/07/30/gnome-auto-login-in-ubuntu-9-10-karmic-koala-alpha-3/]("http://lani78.wordpress.com/2009/07/30/gnome-auto-login-in-ubuntu-9-10-karmic-koala-alpha-3/") for a workaround. By following its advice, one may alter Login Screen Settings.

Go to System/Administration/Login Screen and see if "Log in as [user] automatically" is checked. If not, follow the above advice. Reboot. Then see if "Log in as [user] automatically" is now checked. Then try to unlock Login Screen Settings.

---

### Post by JimZ in VT on 2010-10-24
Sorry to dredge up an old thread. But thank you Ursaminor for the fix! I'm new to Ubuntu and having to manually log in every time was driving me nuts.

---

### Post by swordsmith on 2010-12-19
I have a similar question,
I installed 10.10 from a minimal installation and built up from that. Originally I don´t have a login screen, which is just the way I wanted. However, after a few reboots, I suddenly got the login screen, how do I get rid of it?

---


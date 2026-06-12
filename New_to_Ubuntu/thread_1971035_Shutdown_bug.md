---
title: "Shutdown bug?"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by r3bol on 2012-05-02
I've created 2 user accounts and a guest account on my new 12.04 install, but most of the time I can't shutdown the system. If I try to shutdown in a logged in session (Menu > Shut down... Dialogue > Shut Down), it takes me to the log-in screen. If I try to shut down from the log-in screen, I'm taken back to the log-in screen. 

Is this a bug? 

Thanks.

---

### Post by Ms. Daisy on 2012-05-02
If you're logged in to more than one account when you're shutting down, then Ubuntu will take you back to the login screen.  You need to log out of each account first, then shut down.  (Or at least that's how previous versions worked, I'm assuming it's the same for 12.04).

---

### Post by r3bol on 2012-05-02
> **Ms. Daisy said:**
> If you're logged in to more than one account when you're shutting down, then Ubuntu will take you back to the login screen.  You need to log out of each account first, then shut down.  (Or at least that's how previous versions worked, I'm assuming it's the same for 12.04).
Sigh, that's annoying, but practical I guess. Shame there isn't a 'Completely log out' option.

---

### Post by mc4man on 2012-05-02
There is a bug on this, the intention is to allow the admin user to be able to restart or shutdown with other users logged in (and there is a policy in polkit concerning this.

The issue is that there is no confirmation prompt so until so it won't be allowed.
As a user of your own system you can override this thru a .pkla if you wish.

If desired I'll post one.

---

### Post by Radical Thought on 2012-05-03
I am affected by this as well. If this is not a bug then at least a flawed design. The interface is such that intuitively you do _not_ log out, but just point and click to switch to the desired user account. This then leaves you unintentionally with multiple users logged in, and when you (administrator) want to shut down you are in trouble. 

There should be a solution for this. 

By the way, I experienced this exact same problem in 11.10.

---

### Post by Radical Thought on 2012-05-03
I just noted that this has also been reported as a bug here:

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/872054](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/872054)

---

### Post by mc4man on 2012-05-03
If you wish to 'fix' for admin user

Edit: note that No confirmation prompt that other users are logged in will be given so use with that in mind

```
sudo gedit /var/lib/polkit-1/localauthority/50-local.d/console.pkla
```

***for 12.04 only***
```
[Stop the system when multiple users are logged in]
Identity=unix-group:sudo
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultActive=yes

[Restart the system when multiple users are logged in]
Identity=unix-group:sudo
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultActive=yes
```

***For 11.10***
```
[Stop the system when multiple users are logged in]
Identity=unix-group:admin
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultActive=yes

[Restart the system when multiple users are logged in]
Identity=unix-group:admin
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultActive=yes
```

---

### Post by Radical Thought on 2012-05-04
@[mc4man]("http://ubuntuforums.org/member.php?u=320715"):

Do I understand that I create a file called console.pkla with body the exact content of one of the boxes you have in your post?

---

### Post by Ms. Daisy on 2012-05-04
mc4man, your solution will halt the system without saving anything running in any of the active user's sessions, correct?

---

### Post by mc4man on 2012-05-04
> **Ms. Daisy said:**
> mc4man, your solution will halt the system without saving anything running in any of the active user's sessions, correct?

Correct - that's semi- noted in the bug report, the main reason it's not being allowed seems to be that there is no confirmation prompt that other users are logged in, do you want to proceed, ect.

Admin users that choose to implement this would have keep this in mind, honestly I use mainly for dev installs where multiple users are for testing & of no great importance anyway.

---


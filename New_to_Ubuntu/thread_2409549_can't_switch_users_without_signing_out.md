---
title: "can't switch users without signing out"
date: 2019-01-03
forum: New to Ubuntu
---

### Post by chopra on 2019-01-03
Dear Experts,
I just upgraded from 16.04 to 18.04 LTS, Bionic Beaver.
I happen to have set up more than one user account on my laptop, to separate work form leasure, among other reasons, and I used to be able to switch from one account to the other without actually logging out.

It's a bit complicated because one of my accounts was using the unity desktop, and the other was using metacity. It used to be possible to switch back and forth at the login screen, but now it seems that each identity is frozen with its respective desktop choice.
Anyway, the procedure for locking the screen is a bit different in the different desktops, but in both cases, with a locked screen, there's an option to "sign in as a different user".   This allows me to do something as one user even if there's a running process as the other.
The lock screen looks different for the different desktops, but the result is the same.
When I click "sign in as other user", it stalls, goes blank, and then switches back to the lock screen, asking for a password of the currently signed on user.

I'm not sure if this is connected to the fact that there are now different desktop settings for different accounts or not.

Thanks, Chopra

---

### Post by chopra on 2019-01-05
More information:
After attempting to switch users as described above, I checked the /var/log/syslog file and found the following message:
2019-01-05T14:46:26.632903-05:00 Satellite-E45-B gnome-session[2482]: gnome-session-binary[2482]: WARNING: Could not get session path for session. Check that logind is properly installed and pam_systemd is getting used at login.
2019-01-05T14:46:26.633044-05:00 Satellite-E45-B gnome-session-binary[2482]: WARNING: Could not get session path for session. Check that logind is properly installed and pam_systemd is getting used at login.

Thanks in advance,
Chopra

---

### Post by chopra on 2019-01-19
This problem seemed to self-correct, so I'll close this thread, even though it got no responses.
Chopra

---


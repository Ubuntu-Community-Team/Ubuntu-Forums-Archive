---
title: "Snapd User Session Agent -- Other Users Are Logged In"
date: 2022-09-03
forum: New to Ubuntu
---

### Post by bhubunt on 2022-09-03
Hi,
I am wondering if someone here is familiar with the Snapd User Session Agent that recently started showing up, whenever my screen switches to Login mode on my Ubuntu 20.04 desktop OS (I have no server set up).

When I next try to power off, I receive the following warning:  Other users are logged in.  

Any idea what this means? Does it mean what it seems to be saying: that there are other users on my computer? As mentioned, I do not have a server set up, nor am I sharing my desktop with anyone else.

Thanks for your thoughts.

---

### Post by TheFu on 2022-09-03
Unix systems, including Linux are all multi-user from the ground up.  Nearly every added service/daemon runs under a dedicated account, not just the human users who login on the console.

I don't really log out of my systems, unless a reboot is needed. When I patched today, no reboots were needed on any systems, so I didn't.  
I don't see any snap-user-session on my 20.04 system and no processes with "session" and "snap" in the name exist either, so I'm at a loss.

Which DE are you using?  Perhaps it is related to that or the display server (Wayland or X/Windows) being used?

---

### Post by grahammechanical on 2022-09-08
I am guessing that you are using Ubuntu 22.04. I am also guessing that the code that controls the login screen is now a snap package for greater security. Are you powering off using the drop down menu? On my install of 22.04 I see the message about the snaps user session agent when the screen blanks (logs out) and I try to resume the session. I have never tried to power off when at the log back in screen. I haver never see the message about other users logged in.

Regards

---

### Post by bhubunt on 2022-09-12
Hi,
I am using 20.04. I do use the drop-down menu in the upper right-hand corner and received the [COLOR=#000000]warning: Other users are logged in. Not sure, still, what it means.[/COLOR]

---

### Post by bhubunt on 2022-09-18
> **TheFu said:**
> Unix systems, including Linux are all multi-user from the ground up.  Nearly every added service/daemon runs under a dedicated account, not just the human users who login on the console.

I don't really log out of my systems, unless a reboot is needed. When I patched today, no reboots were needed on any systems, so I didn't.  
I don't see any snap-user-session on my 20.04 system and no processes with "session" and "snap" in the name exist either, so I'm at a loss.

Which DE are you using?  Perhaps it is related to that or the display server (Wayland or X/Windows) being used?

Hi The Fu,
I am using Gnome 3.36.8.

So are you saying that the users being logged in might be "system users," systems of the OS, not human users?

The strange thing is: I've only had it happen twice and not since I posted this post.

---


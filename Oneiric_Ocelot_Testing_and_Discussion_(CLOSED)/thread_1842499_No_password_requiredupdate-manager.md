---
title: "No password required/update-manager"
date: 2011-09-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by kevin2849 on 2011-09-11
I have two installations of 11.10 on two different laptops. Neither one requires me to enter my password to install updates through the update-manager. 

Synaptic wants my password to open and I do not use the Software Center.

I am not complaining but isn't this something that should request a password. I am the only user on my computers.

Nothing to solve but maybe I need to adjust something on my system?

---

### Post by RJ12 on 2011-09-11
> **kevin2849 said:**
> I have two installations of 11.10 on two different laptops. Neither one requires me to enter my password to install updates through the update-manager. 

Synaptic wants my password to open and I do not use the Software Center.

I am not complaining but isn't this something that should request a password. I am the only user on my computers.

Nothing to solve but maybe I need to adjust something on my system?

Synaptic runs as root using sudo which needs your password. That's not going to change and thats how it is on every linux system. If you changed it to no password (And we can't tell you how to do that if I'm correct), then you would have a huge security flaw.

I don't know why update-manager doesn't need a password. It was explained somewhere why though if I remember. Just can't think of it.

Edit: I made a thread asking why it doesn't ask for a password with checking for updates, but needs a password to install them which is right here [http://ubuntuforums.org/showthread.php?t=1774633](http://ubuntuforums.org/showthread.php?t=1774633)

---

### Post by kevin2849 on 2011-09-11
I searched and did not find that, so thank you for the link. I will follow up on Aptdaemon as that seems to be where I will find the answer. Thanks again.

---

### Post by kmsalex on 2011-09-11
I'm not complaning, and i hope your not either. Seams like every five minitues i'm punching in my 9 digit password. Especially considering in oneiric i'm updating twice a day. Are you realy worryed about someone trying to get root access on your home laptop? I imagine your worried about 2012 as well ;)

---

### Post by mc4man on 2011-09-11
There was change to allow the admin user to update existing packages in U-M without the need for auth.
ck. the changelog (either U-M or aptdaemon, forget

---

### Post by kevin2849 on 2011-09-11
kmsalax

As stated in my original post, I am not complaining, just looking to learn.

As for 2012, I have my concerns. ;)

---


---
title: "ME Menu is back!"
date: 2011-08-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2011-08-26
Man, I really missed the ME Menu!

Most of the stuff that "they" are getting rid of, in Unity; I could care less about, but...

I loved that little ME Menu - and now it's back.  Yeah, Team!

---

### Post by Sashin on 2011-08-26
Awesome. That is all, a little indicator that makes the desktop so much more personal.

---

### Post by jbicha on 2011-08-26
Technically, indicator-me is dead and the new me menu (user menu) is part of indicator-session. This is probably only important if you're worrying about bugs in it.

---

### Post by lucazade on 2011-08-26
> **jbicha said:**
> Technically, indicator-me is dead and the new me menu (user menu) is part of indicator-session. This is probably only important if you're worrying about bugs in it.

important also to find a way to hide it.

---

### Post by Sashin on 2011-08-26
Oh, a user switching menu isn't quite the same as one that you can change your IM status... and about me info.

---

### Post by Sashin on 2011-08-26
Also it gave an at a glance view of your IM status and social integration with the desktop. I wonder what the rationale for a user switching menu in its place is...

---

### Post by lucazade on 2011-08-26
wonderful..

disabling guest session capability in lightdm with:
allow-guest=false
in /etc/lightdm/lightdm.conf
it actually removes "guest" account from login manager

but the the guest account is still present in the "new" indicator-me (really session) and when clicking on it the only thing it does is lock the screen and nothing else.
really inconsistent.

---

### Post by Bowmore on 2011-08-26
> **Sashin said:**
> Also it gave an at a glance view of your IM status and social integration with the desktop. I wonder what the rationale for a user switching menu in its place is...Well, the Me &#7742;enu is obsolete and has been replaced by the User Menu AND addons to the Messaging Menu.

[Me Menu:](https://wiki.ubuntu.com/MeMenu/)
> This specification is for the “me menu” that appeared in Ubuntu 10.04, 10.10, and 11.04. It is due to be replaced by an IM status section in the messaging menu.

[Messaging Menu:](https://wiki.ubuntu.com/MessagingMenu/)
> Migration

In any version of Ubuntu that installs this version of the messaging menu:

    the Me menu (indicator-me) should not be installed by default
    the installer slide show should not mention the Me menu
    the only help page mentioning the Me menu should explain that it is no longer present; you can now use Gwibber or similar to post to Twitter etc, the messaging menu to change your IM status, and System Settings to change your password and account details.

---

### Post by Sashin on 2011-08-26
I understand that the changing status is in the me menu, but now we can't see our status at a glance. And social features aren't integrated right into the desktop, that was pretty neat being able to tweet just by clicking it.

Its not a horrible change, but I don't understand the rationale of replacing it with a user menu. Most people will post to twitter/facebook a hell of a lot more often than switching users.

---

### Post by ventrical on 2011-08-26
@vindsl,

Do you mean this one?

[http://www.youtube.com/watch?v=gaKKa5khKKw](http://www.youtube.com/watch?v=gaKKa5khKKw)

---

### Post by lucazade on 2011-08-27
> **lucazade said:**
> wonderful..

disabling guest session capability in lightdm with:
allow-guest=false
in /etc/lightdm/lightdm.conf
it actually removes "guest" account from login manager

but the the guest account is still present in the "new" indicator-me (really session) and when clicking on it the only thing it does is lock the screen and nothing else.
really inconsistent.

[https://bugs.launchpad.net/indicator-session/+bug/835084](https://bugs.launchpad.net/indicator-session/+bug/835084)

---


---
title: "Update manager doesn't ask for password"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by marin123 on 2011-10-07
Hello!

I upgraded successfully last night and now when I'm updating through Update Manager, it downloads and installs updates without prompting for password.

Is this in the blueprints or a bug?

---

### Post by dino99 on 2011-10-07
> **marin123 said:**
> Hello!

I upgraded successfully last night and now when I'm updating through Update Manager, it downloads and installs updates without prompting for password.

Is this in the blueprints or a bug?

i've never seen it asking for, by the way to open a session you need to enter your password, so i dont care to not re-enter it :)

---

### Post by ajgreeny on 2011-10-07
I am not sure what dino99 means in his reply, but the system should definitely ask for a password before allowing an update, whether using the update-manager or ```
sudo apt-get update
sudo apt-get upgrade
``` in terminal.

---

### Post by powder on 2011-10-07
I just updated without entering a password too.

---

### Post by dFlyer on 2011-10-07
This has been a bug IMHO since beta2 released. Just hope it's fixed before the final release. They also need to fix gnome-raw-thumbnailer. It also hasn't worked since the release of beta2. I have to admit that it's much more stabler since earlier in the week. I haven't had any major crash in the last 24 hours.

---

### Post by t1497f35 on 2011-10-07
I see it rather as a feature since the very essence of updates is to fix stuff, not break it, so not asking for a password by default is a good thing imho. Those who are "special" should change the default option.

---

### Post by marin123 on 2011-10-07
Updates are supposed to fix stuff, but it isn't always the case.

While I was using ATI proprietary drivers, xorg update would break my computer. If I didn't know what update was installed, I wouldn't know what was causing the problem.

So I prefer Update manager to ask me for the password.

---

### Post by ikt on 2011-10-07
> **marin123 said:**
> If I didn't know what update was installed, I wouldn't know what was causing the problem.

You still need to click install updates.

It doesn't automatically download and install without you even knowing what just happened.

---

### Post by oldgeekster on 2011-10-07
> **t1497f35 said:**
> i see it rather as a feature since the very essence of updates is to fix stuff, not break it, so not asking for a password by default is a good thing imho. Those who are "special" should change the default option.agreed!

---

### Post by tjeremiah on 2011-10-07
I love it like this.

---

### Post by grahammechanical on 2011-10-07
I thought that it was like that because it was a development release. Not much point in using a development release if you are not going to do daily/nightly updates. Why have the fuss of entering a password?

Regards.

---

### Post by mc4man on 2011-10-07
It was a specific change to allow the admin user to update/upgrade already installed packages without needing auth.
changelog for 
> policykit-desktop-privileges (0.7) oneiric; urgency=low

  * Allow local admins to do the less harmful usb-creator actions (mounting
    and writing image) without a password.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Wed, 06 Jul 2011 10:12:36 +0200

policykit-desktop-privileges (0.6) oneiric; urgency=low

  * Allow local admins to update already installed software without password.
  * Update passwordless time zone configuration to GNOME 3.

 -- Martin Pitt <martin.pitt@ubuntu.com>  Thu, 30 Jun 2011 16:43:39 +0100

---

### Post by marin123 on 2011-10-08
Just now I did an update and it asked me for password. I guess they have changed it during yesterday's updates...

---


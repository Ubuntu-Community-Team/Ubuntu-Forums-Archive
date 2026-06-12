---
title: "Update manager doesn't require a password?"
date: 2011-08-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Luffield on 2011-08-22
I just noticed that I can check for updates and install them without having to supply my password at any stage. Is anyone else experiencing this?

My system is a bit of a mess (I do partial updates and stuff like that, lightDM is not working etc) so I want to make sure this is a real bug and not something I somehow messed up myself before I submit a bug report.

---

### Post by VinDSL on 2011-08-22
> **Luffield said:**
> I just noticed that I can check for updates and install them without having to supply my password at any stage. Is anyone else experiencing this?
I just installed a new kernel, updated using apt-get, then Synaptic, and everything required a password.  ;)

---

### Post by Luffield on 2011-08-22
I don't quite understand, VinDSL. Did you use apt-get from the command line? Or did you use Synaptic? Or the update manager application?
If I use apt-get, aptitude or Synaptic I am also asked for a password. But update manager doesn't do it.

---

### Post by rbrick49 on 2011-08-22
I have noticed this on 86x64 system but when I want to install it asks for password

---

### Post by Luffield on 2011-08-22
You mean that you can check for updates without a password, but in order to install them you have to supply your password?
I think this is how it's intended to work, it's been like that for the past 2 releases IIRC.

---

### Post by mc4man on 2011-08-22
On an install from 08/20 the update manager does **not** require a password to install, obviously this is not intended.
Will ck. for a bug report

---

### Post by Dragonbite on 2011-08-22
Yeah, to check does no require passwords but to install it does I think is how it is supposed to work.

You can always try, without "sudo", ```
# apt-get update
```and ```
# apt-get upgrade
``` and see if it lets you do that or not.

I wonder, do you have your system auto-logging in, or perhaps a blank password?

---

### Post by Luffield on 2011-08-22
Thanks for the replies everyone. Funny that some of us have this problem and some don't.

Dragonbite, "apt-get update" without sudo doesn't work. I don't have auto-login enabled, and my password is not blank.

---

### Post by mc4man on 2011-08-22
This wasn't the case with an install from 08/15, but certainly is now from 08/20, and there is nothing amiss or modified here
(I generally will disable auth for U-M, synaptic and sudo, but haven't as yet
Saw 900 open bugs on U-M, so just went ahead w/ a new one
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/831039](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/831039)

---

### Post by Luffield on 2011-08-22
Thanks mc4man. Already confirmed :shock:

---

### Post by mc4man on 2011-08-22
What's strange here is that it does seem to require auth on some upgrades - though don't have a large enough sample atm to track down
So while not needed on about 10 or so that were avail. today it is required for the kernel upgrade.
(had noticed this ever since installing on sat.

There was a gnome-policykit update, thought possibly a factor but seems not to be.
(I downgraded it, U-M still wanted auth on the kernel, but not on the gnome-policykit one(s)

Will have to downgrade some others and ck.

Edit: seems to be just the kernel upgrades that are requiring auth

---

### Post by Rasa1111 on 2011-08-22
This same thing happened to me a few days ago..
Running 11.04 gNatty. 
I thought it was odd.....
and not seen it before, or since.

---

### Post by madjr on 2011-08-22
hehe i think i like not having to imput my password.

At least for the development release...

i think there should be an option to disable passwords for X amount of time (5 or 10 minutes), until you reboot or until you drop the privileges manually. Sometimes am doing work that require passwords and it can get tedious having to re-type it every minute....

---

### Post by Dragonbite on 2011-08-22
I know for logging into remote folders you have the option to forget or store the password for a session or forever.  Could the update manager somehow get caught with something like this?

Once you use sudo, you are able to use sudo without having to log in for a time period of something like 5 minutes.  Maybe something getting stuck or this has been changed to be unlimited or a very, very long time?

The paranoid side of me would think if a hacker could get my sudo to lock like that so I can install without a password, it would make it easier to plant something malicious.

---

### Post by godhika on 2011-08-22
hmm I think the behavior is like this: Whenever a new package (say a new kernel version) is installed or deinstalled during the update process a password is required, otherwise the updatemanager doe not require a password.

---

### Post by VinDSL on 2011-08-22
> **Luffield said:**
> I don't quite understand, VinDSL.[...]

If I use apt-get, aptitude or Synaptic I am also asked for a password. But update manager doesn't do it.
Oops!

I didn't realize you were talking about update manager, the app.

I thought you were talking about update management, in general.

Sorry, for the confusion.  ;)

---

### Post by mc4man on 2011-08-22
> **madjr said:**
> hehe i think i like not having to imput my password.

At least for the development release...
.
I typically do so (all the time
Update-manager uses aptdaemon so auth is set thru policykit. The new synaptic now also uses polictkit vs. prior of (gk)sudo

Those are taken care of here thru a .pkla though haven't done so on this install yet, may wait to see how this bug shakes out.

sudo is now a single instance auth, when inclined here to get rid of the need to auth I use an older sudo that applies to all instances, that and another workaround came up in natty dev

An Ex. pkla to open up U-M, S-C, S-S and synaptic

```
gksudo gedit /var/lib/polkit-1/localauthority/50-local.d/package-managers.pkla

```
```

[Install package file]
Identity=unix-group:admin
Action=org.debian.apt.install-file;org.debian.apt.update-cache;org.debian.apt.install-or-remove-packages;org.debian.apt.upgrade-packages
ResultActive=yes

[Change add repo]
Identity=unix-group:admin
Action=com.ubuntu.softwareproperties.applychanges;org.debian.apt.change-repository
ResultActive=yes

[Use synaptic]
Identity=unix-group:admin
Action=com.ubuntu.pkexec.synaptic
ResultActive=yes
```

---

### Post by mc4man on 2011-08-23
Didn't notice the changelog on this quite some time ago (& generally only use U-M to read changelogs, not install
Anyway this is the 'new' intended behavior for admin

> policykit-desktop-privileges (0.6) oneiric; urgency=low

  * Allow local admins to update already installed software without password.
  * Update passwordless time zone configuration to GNOME 3.
 -- Martin Pitt <martin.pitt@ubuntu.com>   Thu, 30 Jun 2011 16:43:39 +0100



---

### Post by t1497f35 on 2011-08-23
This is compensated by the startup disk creator which asks for the password 4 times!

---

### Post by xebian on 2011-08-23
> **mc4man said:**
> Didn't notice the changelog on this quite some time ago (& generally only use U-M to read changelogs, not install
Anyway this is the 'new' intended behavior for admin


Very BAD security policy IMHO.  Someone could just easily package a trojan/virus masquerading as an Ubuntu default package.

---

### Post by mc4man on 2011-08-23
> **t1497f35 said:**
> This is compensated by the startup disk creator which asks for the password 4 times!

That is also a pita, because I generally dump O installs weekly I don't bother to 'resolve' that.
 On my natty install I have 2 add. sections added to the .pkla posted above that take care of

```
[usbcreator format]
Identity=unix-group:admin
Action=com.ubuntu.usbcreator.format
ResultActive=yes

[Install bootloader]
Identity=unix-group:admin
Action=com.ubuntu.usbcreator.bootloader
ResultActive=yes
```

---

### Post by mc4man on 2011-08-23
> **xebian said:**
> Very BAD security policy IMHO.  Someone could just easily package a trojan/virus masquerading as an Ubuntu default package.
U-M only shows from enabled sources and at least in the past aptdaemon also only allowed installs from authenticated sources

---

### Post by Luffield on 2011-08-23
Thanks for doing all the hard work for me, mc4man, and for doing it much better than I would :D

---


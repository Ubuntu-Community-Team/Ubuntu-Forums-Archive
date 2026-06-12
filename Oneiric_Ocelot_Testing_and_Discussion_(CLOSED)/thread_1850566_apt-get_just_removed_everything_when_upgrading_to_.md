---
title: "apt-get just removed everything when upgrading to kernel 3.0.0.12"
date: 2011-09-26
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by scott.smedley on 2011-09-26
Just ran apt-get upgrade, apt-get dist-upgrade and then apt-get upgrade.

Each time new packages installed, but last command also removed pretty much everything (unity, lightDM and various other critical packages).

Carried out a reboot and just get stuck in an endless cycle as system tries to load lightDM and fails (X appears to be installed still as mouse appears briefly for a second before then showing message about battery state and then cycle starts again).

Any idea what could have caused this and how to rectify without a fresh install?

---

### Post by el_koraco on 2011-09-26
> **scott.smedley said:**
> 
Any idea what could have caused this and how to rectify without a fresh install?

There are ways, but a reinstall will be much quicker and much less painful.

---

### Post by sgage on 2011-09-26
I guess I don't understand why folks do dist-upgrades. Just do a plain upgrade, pay attention to the report of what's going to be done, and make your choice.

That said, your best bet at this point is probably a clean re-install.

---

### Post by effenberg0x0 on 2011-09-26
**EDIT**: I just finished transforming a broken xubuntu-oneiric alpha that had done a partial update and had no working X session, everything was broken from grub to samba, etc into a working Ubuntu-oneiric Beta 2. It took me 4 hours of finding and downloading the right packages, performing conditional updates (--no-install-recommends, --fix-broken etc), conditionally removing wrong ones, manually fixing stuff and conf files, dpkg-reconfiguring lots of things, etc to get the system sort of ok (and I still have doubts). It is possible but it is too hard and unnecessary. If you really removed many major packages, go for a clean install as others have recommended.

Regards,
Effenberg

---

### Post by alphacrucis2 on 2011-09-26
Isn't there a sticky warning about partial upgrades?

---

### Post by MAFoElffen on 2011-09-26
> **scott.smedley said:**
> Just ran apt-get upgrade, apt-get dist-upgrade and then apt-get upgrade.

Each time new packages installed, but last command also removed pretty much everything (unity, lightDM and various other critical packages).

Carried out a reboot and just get stuck in an endless cycle as system tries to load lightDM and fails (X appears to be installed still as mouse appears briefly for a second before then showing message about battery state and then cycle starts again).

Any idea what could have caused this and how to rectify without a fresh install?
A few ideas... At this point this is where the sys tries to load X and any proprietary video drivers.  What Video GPU are you running?
```

lspci -nn | grep VGA

```
Another 2 of the files that would good to see for info would be /var/log/Xorg.0.log and /etc/X11/xorg.conf. 

Another thing that might help is to get to your Grub menu, press "e" at the menu item... Go down to the line starting with linux and replace "quiet splash" with "--verbose text".  That should change the boot mode to a TTY Text Console mode, with verbose boot messaging turned on.

---

### Post by sammiev on 2011-09-26
> **alphacrucis2 said:**
> Isn't there a sticky warning about partial upgrades?

I read a warning in the stickies a while back.

---

### Post by rburkartjo on 2011-09-26
while in any of the alpha or beta builds i alway run this command from the terminal to check for and install any updates


 sudo aptitude update && sudo aptitude safe-upgrade
  

never install partial updates from experience you will usually bork your system

---

### Post by seeker5528 on 2011-09-28
> **scott.smedley said:**
> Just ran apt-get upgrade, apt-get dist-upgrade and then apt-get upgrade.

Each time new packages installed, but last command also removed pretty much everything (unity, lightDM and various other critical packages).

Carried out a reboot and just get stuck in an endless cycle as system tries to load lightDM and fails (X appears to be installed still as mouse appears briefly for a second before then showing message about battery state and then cycle starts again).

Any idea what could have caused this and how to rectify without a fresh install?

If you did 'apt-get dist-upgrade' without reviewing what would be removed before giving it the go ahead, that was probably it.

If 'apt-get dist-upgrade' did everything it wanted to do without errors, then in theory there should not have been anything left for 'apt-get upgrade' to do, since dist-upgrade will attempt to find a solution that leaves you with everything upgraded, even if it has to remove stuff to do it.

The normal upgrade will not install things that have new or changed dependencies, which is why you should do it first. After doing the normal upgrade, then if you are not actually doing a distribution upgrade and are not too far behind on updates, you should have a reasonably small list of changes to review when doing the dist-upgrade.

Assuming you still have a network connection, you can try the safe-boot and choose the 'netroot' option, if I remember the name correctly.

'apt-get install ubuntu-desktop' or 'apt-get install ubuntu-minimal lightdm unity unity-2d' might be enough to get you the basic Unity and Unity-2d desktops.

Later, Seeker

---

### Post by dino99 on 2011-09-28
:) :) for breakage, close eyes & stop to breath, then hit Enter key :) :)

---


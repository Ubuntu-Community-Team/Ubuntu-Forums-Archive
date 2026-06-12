---
title: "Switch user in gnome-shell"
date: 2011-08-31
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sennaista on 2011-08-31
"Switch user" in gnome-shell acts the same as "lock screen". The screen is blacked out with only the top bar visible. It's only by clicking "switch user" on the password box you are sent to lightdm greeting screen.

I'm using the gnome-shell version from Ricotz PPA.

Bug?

Also, while using the integrated chat interface it is not possible to paste anything into the chat box. Is it intended? The documentation also mentions file transfer options but there are no hints in the interface. It's also only possible to receive messages and I haven't found any way to initiate conversations.

---

### Post by gururise on 2011-09-29
+1

Same problem here using Gnome-Shell from ricotz repo.  Does "switch user" from the user menu work for you Gnome-Shell users on the regular ubuntu repository??

---

### Post by gururise on 2011-09-30
Even after updating to official GNOME 3.2, I still cannot switch user from the user menu.

Trying to do so results in a black screen.

---

### Post by gururise on 2011-09-30
Another thing I just noticed is, when I lock my screen, there is no way to switch users.  I only have the option of entering my password to unlock the screen or hitting the "cancel" button.  The "Switch User" button is missing!  :confused:

I have three separate user accounts on my machine.  Anyone else experiencing this?

---

### Post by gururise on 2011-09-30
Here is the [BUG #861790]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/861790").  If this problem affects you, please select "affects me" on this bug.

---

### Post by cariboo on 2011-09-30
> **gururise said:**
> Here is the [BUG #861790]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/861790").  If this problem affects you, please select "affects me" on this bug.

You reported the bug in the wrong place, it should be reported to [Bugzilla]("https://bugzilla.gnome.org/"), as it is a gnome problem, not an Ubuntu bug.

---

### Post by crdlb on 2011-10-01
Is everyone with this problem using LightDM? It looks like LightDM has a compatibility bridge for desktops that expect GDM, but it may be broken. I stuck with GDM and switch user is working fine.

---

### Post by gururise on 2011-10-01
Hmm... so it seems to be a lightDM issue.  How can one revert to GDM?

---

### Post by xgt001 on 2011-10-01
marked myself as being affected too..... but i am in a virtual bliss using gnome 3.2 + catalyst 11.9 + unity 3D :popcorn:

---

### Post by Mr. Picklesworth on 2011-10-01
> **cariboo907 said:**
> You reported the bug in the wrong place, it should be reported to [Bugzilla]("https://bugzilla.gnome.org/"), as it is a gnome problem, not an Ubuntu bug.

I disagree. It's likely an integration issue with lightdm, so the folks upstream aren't going to find that very interesting; it's only relevant if you're the one distro that uses gnome with lightdm instead of gdm. They might accept patches that come out of this, though, so a bug report in both places would be nice as long as the one upstream makes it really clear this is with an unusual configuration.

---

### Post by crdlb on 2011-10-01
> **gururise said:**
> How can one revert to GDM?

If GDM is already installed:
```
sudo dpkg-reconfigure gdm
```

Otherwise, just install it.

---


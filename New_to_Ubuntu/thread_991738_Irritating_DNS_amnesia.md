---
title: "Irritating DNS amnesia"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Zorgoth on 2008-11-24
I have the problem that I have 3 DNS servers (manually inputted) I use on my ethernet network (not anything I have any control over *sigh*) and 1 automatic DNS server on the wireless in the main building.  I have the problem that whenever I use the wireless network, the computer forgets the DNS for the other network and I have to type them in again.  It's not an essential thing, but it would be nice if someone knew how to fix it.

---

### Post by blazemore on 2008-11-24
Are you using Intrepid? If so, edit the settings for the relevant network, and make sure you tick the "System Setting" box. This could fix it, I don't know. Certainly won't do any harm.

---

### Post by Zorgoth on 2008-11-24
No sorry I should have mentioned I'm using Hardy 8.04.  I don't think I can do that in Hardy.

---

### Post by SamNSane on 2008-11-25
> **Zorgoth said:**
> No sorry I should have mentioned I'm using Hardy 8.04.  I don't think I can do that in Hardy.

I don't think you can do it in Hardy, either. Well, not with the standard network manager applet. But if you go to the wicd site, there are instructions for adding their repository to Synaptic in Hardy (and other Ubuntu versions). Once you've done that, you can use Synaptic to install wicd. (The old network manager will be removed automatically.) You'll find wicd to be really easy to work with.

One proviso - wicd does not use the gnome-keyring authentication system, so anyone with access to your unlocked desktop will be able to change your network settings.

The network manager in Intrepid us a H-U-G-E improvement over the version in Hardy. I'm afraid, though, that it is so different (and seems to keep its settings information in totally different places) that it might not ever get backported to Hardy. That's a shame, I think.

I'm using wicd under Hardy because my systems can't live with Intrepid (yet), and I cant live with the Hardy version of the network manager.

---


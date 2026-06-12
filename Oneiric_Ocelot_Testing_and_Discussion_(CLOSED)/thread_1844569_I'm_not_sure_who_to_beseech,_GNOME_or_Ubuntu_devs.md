---
title: "I'm not sure who to beseech, GNOME or Ubuntu devs"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by walt.smith1960 on 2011-09-15
I know there are a lot of functions & applets etc. in Gnome 2 that have not been migrated to Gnome 3. I think the "Users & Groups" is rather stark for a core function though.  How does one grant or deny different users different privileges or determine group membership?  There used to be a tab just for that purpose.  Now I see just Administrator or Standard with predefined privileges.  Sorry if I'm missing the obvious and thanks for any insight.

---

### Post by wgarcia on 2011-09-15
Now there are two interfaces, a simple one that is the one you refer and that sits in the System Settings menu in the rightmost indicator of the top panel, and the old one ("Users and groups") that you can access entering Users in the Dash.

---

### Post by coffeecat on 2011-09-15
> **wgarcia said:**
> Now there are two interfaces, a simple one that is the one you refer and that sits in the System Settings menu in the rightmost indicator of the top panel, and the old one ("Users and groups") that you can access entering Users in the Dash.

I don't think Users and Groups comes as default anymore. I've just installed a fresh Oneiric from yesterday's daily live and "users" in the dash just takes me to the simplified "User accounts" utility that you get from System Settings. I'll do a bit of digging and post back.

---

### Post by coffeecat on 2011-09-15
> **coffeecat said:**
> I'll do a bit of digging and post back.

If you install the package gnome-system-tools (which is a gnome2 package) with its dependencies, then you get the old Users and Groups from the dash. Which seems to still be functional in the gnome3 environment, from the limited tests I did.

I would hope that the newer gnome3 User Accounts utility will be further developed because it's a bit short on features at the moment. :|

---

### Post by wgarcia on 2011-09-15
It seems that my upgrade did not drop the "Users and groups" thing from my system or maybe gnome-system-tools was not deleted.

---

### Post by walt.smith1960 on 2011-09-16
> **coffeecat said:**
> If you install the package gnome-system-tools (which is a gnome2 package) with its dependencies, then you get the old Users and Groups from the dash. Which seems to still be functional in the gnome3 environment, from the limited tests I did.

I would hope that the newer gnome3 User Accounts utility will be further developed because it's a bit short on features at the moment. :|

I selected the gnome-system-tools package and it did install to my surprise and delight.  The "Users & Groups" did not change but when I opened a "Run" window and typed "users" a "users admin" option appeared.  That is the old "Users & Groups" option.  I'll have to go back and see what else was installed.

---


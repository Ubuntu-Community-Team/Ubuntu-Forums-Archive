---
title: "nmbus connection failed"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by SpongeBob SquarePants on 2008-06-10
Hi All,

On closing down my computer (Hardy)I get the following error message repeatedly.....

network manager: nmbus_signal_device_status_change :assertion cb_data -> data ->bus_connection_failed

Any ideas what's going on here?

---

### Post by skymera on 2008-06-10
I get those show (or ones similar), i never take any notice since it always shuts down.

Does it cause any problems for you?
Or is this just curiosity?

---

### Post by SpongeBob SquarePants on 2008-06-10
> **skymera said:**
> I get those show (or ones similar), i never take any notice since it always shuts down.

Does it cause any problems for you?
Or is this just curiosity?

No, it doesn't cause any problems....or at least I don't think it does. It is more of a curiosity, though I'd like to fix it if I can, or at the very least understand what the problem actually is..

---

### Post by skymera on 2008-06-10
+1 here, i don't use network-manager.

I use the /etc/network/interfaces to configure my networks.
I think it may be a communications error where dbus shuts down before network manager.

---

### Post by SpongeBob SquarePants on 2008-06-10
> **skymera said:**
> +1 here, i don't use network-manager.

Hmmm.....me neither. I wonder if uninstalling network-manager would be possible? I don't use wifi and am not on a network. Or is it needed for something else?

---


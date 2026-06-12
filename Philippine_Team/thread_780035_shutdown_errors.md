---
title: "shutdown errors"
date: 2008-05-03
forum: Philippine Team
---

### Post by lixx on 2008-05-03
kaka upgrade ko lng sa hardy ngaun. fresh install pla ginawa ko, bale, ang nakaretain lng sa laptop ko ay /home na partition. paano po ito tanggalin tuwing nag shushutdown?

```

NetworkManager: <WARN> nm_signal_handler(): caught signal 15, shutting down normally
NetworkManager: <info> Caught termination signal
NetworkManager: <debug> [1209293162.052758] nm_print_open_socks(): Open Sockets List:
NetworkManager: <debug> [1209293162.052269] nm_print_open_socks(): Open Sockets List Done.
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed -Connection is closed
NetowkrManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

```

Sucks eh, ang pangit sa mata :) Console user pa nman dn aq.
Thanks po. Hehe

---

### Post by jajabinx on 2008-05-12
I had that same problem before. But I noticed that I get those NM error messages when I don't disconnect from our network or I still have the bluetooth on thinking that with linux, my system will be checked and all open applix will be shut down anyway.

But somehow, my system hangs or gives NM error messages so before i log out, i have to make sure that i disconnected from our network, turned the bluetooth off... or from the console, as root, i do

```
shutdown -h now
```

it won't hurt to try. :)

---

### Post by Samhain13 on 2008-05-12
I had the same problem. This seems to have done the trick:

1) in /etc/modules, append:

apm power_off=1

2) in System > Login Window > General > Edit Commands...

Remove ' "Shut Down via gdm."' in the Path field, click Apply Command Changes. Then put the phrase back and hit Apply Command Changes again.

Do the same thing for Reboot Command. Remove then re-insert ' "Rebooted via gdm."'

Don't ask me why it works, it just does. :)

---

### Post by jajabinx on 2008-05-13
> **Samhain13 said:**
> I had the same problem. This seems to have done the trick:

1) in /etc/modules, append:

apm power_off=1

2) in System > Login Window > General > Edit Commands...

Remove ' "Shut Down via gdm."' in the Path field, click Apply Command Changes. Then put the phrase back and hit Apply Command Changes again.

Do the same thing for Reboot Command. Remove then re-insert ' "Rebooted via gdm."'

Don't ask me why it works, it just does. :)

i'll try this and see how good this works for me... ahmm, can't help but ask what gdm is... hehe. :)

---

### Post by Samhain13 on 2008-05-13
^Not sure. I think it's "GNOME Display Manager".

---


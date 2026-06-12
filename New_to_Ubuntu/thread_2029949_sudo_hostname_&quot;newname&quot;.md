---
title: "sudo hostname &quot;newname&quot;"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by aef54 on 2012-07-20
If I change the hostname in the terminal, using the command:
```
 sudo hostname *newhostname*
```

Then it indeed changes the hostname. However, after shutting down and restarting the machine, it changes back to the old name.

Is there a way to make it permanent?

---

### Post by MG&amp;TL on 2012-07-20
AFAIK you can change it in the details dialog.

Run this command:

```
gksu gnome-control-center
```

then click on 'details', then edit the hostname there.

Alternatively: [http://www.omgubuntu.co.uk/2012/01/how-to-change-hostname-in-ubuntu-11-10](http://www.omgubuntu.co.uk/2012/01/how-to-change-hostname-in-ubuntu-11-10)

---

### Post by aef54 on 2012-07-20
That worked. Thanks.

---

### Post by Wim Sturkenboom on 2012-07-20
No Linux system at hand to verify but the permanent way without a GUI is often to modify */etc/hostname*

---

### Post by CharlesA on 2012-07-20
> **Wim Sturkenboom said:**
> No Linux system at hand to verify but the permanent way without a GUI is often to modify */etc/hostname*
That is correct. If you change the hostname you also have to modify

/etc/hosts otherwise you will get errors when trying to sudo.

---


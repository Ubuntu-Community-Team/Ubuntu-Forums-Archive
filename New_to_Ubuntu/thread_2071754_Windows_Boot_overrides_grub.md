---
title: "Windows Boot overrides grub?"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by arcsin on 2012-10-16
I've managed to install ubuntu alongside windows 8 in a separate partition, however when I start up the pc it goes straight to windows 8 instead of opening grub?

---

### Post by arcsin on 2012-10-16
I tried running boot-repair and got this:

[http://paste.ubuntu.com/1282836/](http://paste.ubuntu.com/1282836/)

---

### Post by Wim Sturkenboom on 2012-10-16
Did you see this line at the end of your results?

```

Please do not forget to make your BIOS boot on sda2/efi/ubuntu/grubx64.efi file!

```

---

### Post by Clatterfordslim on 2012-10-16
> **arcsin said:**
> I tried running boot-repair and got this:

[http://paste.ubuntu.com/1282836/](http://paste.ubuntu.com/1282836/)

You need to go into bios, when you restart your computer press either delete or f11, one of the two to enter bios. There should be a list of which operating system you want to boot. Use your arrow keys to highlight which one, press enter and that should do the trick. I hope I am right, if not then can't say I did not try. :p

---

### Post by arcsin on 2012-10-16
Thanks,

I didn't need to change anything in the bios.

I shutdown after boot-repair had finished and restarted and it went straight to windows then I rebooted and grub came up straight after the bios splash screen.

---


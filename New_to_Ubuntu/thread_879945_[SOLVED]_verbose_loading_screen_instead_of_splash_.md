---
title: "[SOLVED] verbose loading screen instead of splash screen"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by abgemacht on 2008-08-04
Hello,

I was wondering if there was a way to get rid of the regular splash screen during startup/shutdown in favor of a more verbose screen.  This isn't necessary, but I'd like to see what type of things are loading.

Thanks

---

### Post by Het Irv on 2008-08-04
You might want to wait for confirmation on this, but I believe if you remove the "-quiet" flag from your boot command, it will show what you want.

EDIT: HymnToLife has a better explanation check out the 4th post here.

---

### Post by knightcoder on 2008-08-04
I wanted to install a new theme and so, installed splashy. Unfortunately, it didn't work and I uninstalled splashy. But splashy had removed the default theme. So, I ended up having the normal verbose text screen starup/shutdown.

And I like it now !!

---

### Post by Bachstelze on 2008-08-04
You can disable it by editing the kernel parameters in your GRUB config file, like:

```
kernel          /boot/vmlinuz-2.6.26-5-generic root=UUID=801683d9-5e74-4ad6-91e9-6f05622ac006 ro quiet splash
```

becomes

```
kernel          /boot/vmlinuz-2.6.26-5-generic root=UUID=801683d9-5e74-4ad6-91e9-6f05622ac006 ro
```

Alternatively, you can also uninstall usplash altogether.

---

### Post by abgemacht on 2008-08-04
Thanks!

I'm at work now but will give this a shot when I get home.

---

### Post by Stunt Double on 2008-08-04
Install startupmanager from Synaptic Package Manager and configure it to your preference. It installs under SYSTEM-->ADMINISTRATION.

---


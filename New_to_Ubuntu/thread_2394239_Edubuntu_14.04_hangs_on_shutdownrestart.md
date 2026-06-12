---
title: "Edubuntu 14.04 hangs on shutdown/restart"
date: 2018-06-14
forum: New to Ubuntu
---

### Post by rohitrobichan on 2018-06-14
Edubuntu 14.04 does not shut down or restart.When shutting down it hangs while showing Ubuntu title.While restarting the display turns off but power does not goes off. Tried the fix /etc/default/grub line:```
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

```  to```


  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
```
and not working.
My laptop is HP.

---

### Post by Autodave on 2018-06-14
Did you just install this for the first time?  I am not sure that 14.04 is even supported any longer.

What model laptop is it?  It may be to new for 14.04 to even work on.

---

### Post by rohitrobichan on 2018-06-15
I am working at a school. All other systems in my school are working in Edubuntu 14.04. It is the latest version of Edubuntu. My laptop model is hp-r250TU.

---

### Post by Impavidus on 2018-06-15
It seems Edubuntu 14.04 is supposed to have 10 months of support left. It is the latest release of Edubuntu and I woundn't be surprised if it's the last release. Their website hasn't been updated in over 2 years. But the only differences between all Ubuntu flavours are the live disk and the set of default applications, so using a recent version of a different Ubuntu flavour shouldn't be too much of a problem. Even the edubuntu metapackages, that conveniently pull in all edubuntu defaults, are available from the repositories of recent Ubuntu releases.

---

### Post by rohitrobichan on 2018-06-15
It is strict to use Edubuntu in schools here. Is there any solution without changing the Ubuntu version.

---

### Post by Impavidus on 2018-06-15
Is this system where you have that problem a fresh install or did it work previously? In the latter case it may be possible to fix it for the time being, else I suspect a more recent version of Ubuntu works better. In any case, you have just 10 months of support left, so it's time to think about a way to move on.

It's always annoying when people set up strict rules that may be useful one day, but neglect to update them when times change. Maybe it's time to find a new interpretation of "strict Edubuntu". What about installing Ubuntu 18.04 and adding the package **edubuntu-desktop** on top of that? You can call that Edubuntu, even though there may no longer be an install disk for the latest version.

---


---
title: "New gnome-themes-standard breaks Adwaita theme"
date: 2011-08-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-08-18
The newest version from yesterday (3.1.5-0ubuntu2) of gnome-themes-standard breaks at least Adwaita theming. This leads to a horribly ugly non theme window management.
I can see this on both of my 64-bit and 32-bit setups with open-source drivers and with only Oneiric official repos enabled.
Oh, yeas and the issue can be seen on Gnome-shell and Gnome-panel desktops.

This may be a theme issue or xserver issue, I haven't figured out yet.
Anyway, here is the bug (#828543) report.
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/828543](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/828543)

Does someone else see something like this too?

---

### Post by sgage on 2011-08-18
> **Harry33 said:**
> The newest version from yesterday (3.1.5-0ubuntu2) of gnome-themes-standard breaks at least Adwaita theming. This leads to a horribly ugly non theme window management.
I can see this on both of my 64-bit and 32-bit setups with open-source drivers and with only Oneiric official repos enabled.
Oh, yeas and the issue can be seen on Gnome-shell and Gnome-panel desktops.

This may be a theme issue or xserver issue, I haven't figured out yet.
Anyway, here is the bug (#828543) report.
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/828543](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/828543)

Does someone else see something like this too?

Hmmm... seems fine here (32-bit system).

---

### Post by hugmenot on 2011-08-18
Works here. BTW, copying gtk-dark.css over gtk.css looks quite cool.

---

### Post by pulpo69 on 2011-08-19
my Adwaita is broken, since last update.

---

### Post by budluva04 on 2011-08-19
is it normal for someone to NOT have gnome-themes-standard installed at all? i'm running an up to date 32bit install of 11.10....
```

billybigrigger@victor:/usr/share/themes$ sudo apt-cache policy gnome-themes-standard 
gnome-themes-standard:
  Installed: (none)
  Candidate: 3.1.5-0ubuntu2
  Version table:
     3.1.5-0ubuntu2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
```

---

### Post by jbicha on 2011-08-19
> **budluva04 said:**
> is it normal for someone to NOT have gnome-themes-standard installed at all? i'm running an up to date 32bit install of 11.10....


Yes, absolutely, gnome-themes-standard is not installed by default. However, the next gnome-shell update depends on gnome-themes-standards so all gnome-shell users will get it since Ambiance and Radiance don't fully support Gnome Shell yet.

Harry, I see your linked bug report and I duplicated it in a virtual machine. I just have to figure out why it works on my main computer and not the other one. And my Gnome Shell broke today so I'm having trouble testing it.

---

### Post by jbicha on 2011-08-19
As I posted on the bug report, the new gnome-themes-standard depends on a new mutter which depends on a new clutter. So to workaround this bug, either install the previous gnome-themes-standard or install the new mutter and clutter. I'm hoping clutter will get uploaded next week as it's absence is causing several issues with Gnome Shell.

---

### Post by Harry33 on 2011-08-19
> **jbicha said:**
> Yes, absolutely, gnome-themes-standard is not installed by default. However, the next gnome-shell update depends on gnome-themes-standards so all gnome-shell users will get it since Ambiance and Radiance don't fully support Gnome Shell yet.

Harry, I see your linked bug report and I duplicated it in a virtual machine. I just have to figure out why it works on my main computer and not the other one. And my Gnome Shell broke today so I'm having trouble testing it.

Right OK.

I may have something similar to that.
My 64-bit nvidia-current setup with Staging PPA works well with the gnome-themes-standard 3.1.5.
But then two setups without any additional PPA's do not.
I had to downgrade the theme to 3.1.2. Then everything is OK.

---

### Post by Harry33 on 2011-08-19
> **jbicha said:**
> As I posted on the bug report, the new gnome-themes-standard depends on a new mutter which depends on a new clutter. So to workaround this bug, either install the previous gnome-themes-standard or install the new mutter and clutter. I'm hoping clutter will get uploaded next week as it's absence is causing several issues with Gnome Shell.

Yes I can confirm this.
Newer mutter (3.1.4) works with gnome-themes-standard 3.1.5

---


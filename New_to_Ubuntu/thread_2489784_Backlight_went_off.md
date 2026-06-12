---
title: "Backlight went off"
date: 2023-08-10
forum: New to Ubuntu
---

### Post by alexbaqua on 2023-08-10
Dear all,
Yesterday I just updated LTS 24.02 in Asus Vivobook. Update was successful. But after this update i lost back light on this laptop. Now i can not figure out LCD laptop images easily. According to the recipe that i took from internet, just tested this recipe underline below.
```

> sudo gedit /etc/default/grub
> Find GRUB_CMDLINE_DEFAULT='quite splash' in settings file 
> then change the variable as  'quite splash acpi_backlight=vendor'
> save the file
> update-grub
> restart the system

```
But this command did not solve the problem. Could you please give me definitive explanation and solution for this issue
I would be much appreciated
Regards
alex

---

### Post by ActionParsnip on 2023-08-10
Does the laptop have a make and model?

---

### Post by alexbaqua on 2023-08-11
Sorry sir, Asus Vivobook x150ZZA with i5 intel processor...

---

### Post by MAFoElffen on 2023-08-11
Please post the output of this within [noparse]```

```[/noparse] Tags.
```

grep . /sys/class/backlight/acpi_video0/*

```

---


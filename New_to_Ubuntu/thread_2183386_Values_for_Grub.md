---
title: "Values for Grub"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Luc_Lacombe on 2013-10-24
Hello   I want to have Grub to boot to the last OS used...the last one. So I used the TERMINAL to open etc/default/grub in GEDIT. I changed the GRUB_DEFAULT to "saved". After which I used the terminal again  as : sudo update-grub.  For test, I restarted and used XP from grub but the default starting OS remainded to be Ubuntu. Wasn't it supposed to be XP again? What did I do wrong?  Luc

---

### Post by oldfred on 2013-10-24
You may also need another setting.

  info -f grub -n 'Simple configuration'

> `GRUB_SAVEDEFAULT'
     If this option is set to `true', then, when an entry is selected,
     save it as a new default entry for use by future runs of GRUB.
     This is only useful if `GRUB_DEFAULT=saved'; it is a separate
     option because `GRUB_DEFAULT=saved' is useful without this option,
--zz-Info: (grub.info.gz)Simple configuration, 242 lines --11%------------------



---


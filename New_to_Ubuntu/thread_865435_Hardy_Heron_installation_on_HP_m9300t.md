---
title: "Hardy Heron installation on HP m9300t"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by GoCool on 2008-07-20
Hi,
I am trying to install Hardy 64bit on HP m9300t and I have the following issues, 

1. At the boot up it gives me the below error

dmi_string : out of memory

(followed by another error, which I couldnt note down for it was a little too quick for me)

2. The it goes about installing, but when I reboot it just freezes

Any inputs will be highly appreciated.

gokul

---

### Post by steve-shinn on 2008-07-20
What amount of RAM do you have on the lappy ?

---

### Post by GoCool on 2008-07-20
> **steve-shinn said:**
> What amount of RAM do you have on the lappy ?

It's a desktop with 8GB RAM.

For more details about the specification click [here]("http://www.shopping.hp.com/webapp/shopping/load_configuration.do?destination=review&email_id=370789&jumpid=in_r329_emailconfig").

I did a reinstall, and it seemed like it fixed, but it started all over again. Beats me completely.

---

### Post by GoCool on 2008-07-20
dmi_string: out of memory
save_OEM_strings_devices: out of memory

these are the two error messages which appear at boot time before it freezes.

Any help would be deeply appreciated.

---

### Post by GoCool on 2008-07-20
I googled my problem and this is exactly what it is

[http://linux.derkeiler.com/Mailing-Lists/Kernel/2007-12/msg06598.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2007-12/msg06598.html)


but believe me its purely greek and latin to me...can anyone interpret in laymans term for me. Is there a patch or anything for me to apply?

---


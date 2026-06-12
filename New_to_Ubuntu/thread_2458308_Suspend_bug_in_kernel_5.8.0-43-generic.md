---
title: "Suspend bug in kernel 5.8.0-43-generic"
date: 2021-02-21
forum: New to Ubuntu
---

### Post by emilio-11 on 2021-02-21
For the past few days, I've been dealing with suspend issues happening in my Ubuntu OS 20.04. Due to some reasons, resuming after suspend does not work sometimes. I've checked kernel logs and noticed following log message


> **[COLOR=#ff0000]x86/pm: family 0x16 cpu detected, MSR saving is needed during suspending[/COLOR]**

I previously thought that recent kernel update could be a root cause but after downgrading to previous kernels nothing changed. Does anyone has an idea what could be a reason for this?

---

### Post by mrdc76 on 2021-02-22
So it used to work? Perhaps Nvidia drivers were upgraded as well and caused the issue?

---


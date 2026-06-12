---
title: "How I can Disable Anachronistic Cron Anacron via terminal?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Harmony_Of_Distortion on 2008-06-12
Hello! I'm New to ubuntu and I want to know how I can disable Anachronistic cron anacron via terminal. There is a problem when the ubuntu load's for first time (stucks at Anachronistic cron anacron) and I want to know how I can disable this sevice via terminal.

I have a notebook, Cor2Duo 1.83, 1GB Ram, 80GB HD, Intel 945GM on board graphics with 128MB shared memory.

Please if anyone know pleeeeeeeeeeeease help! 

Thanks!:confused:

---

### Post by HalPomeranz on 2008-06-12
```
sudo update-rc.d -f anacron remove
```

---

### Post by gr4nf on 2008-06-12
If that fails, would you post the contents of:
/etc/rc3.d

thanks.

---


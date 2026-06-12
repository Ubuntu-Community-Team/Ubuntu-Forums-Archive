---
title: "[SOLVED] [8.10] nvidia-settings won't load after reboot"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-11-04
I'm having issues with nvidia-settings on Intrepid. I loose brightness/contrast/gamma settings after reboot.

I have temporarily added nvidia-settings to the session, so when I reboot the nvidia gui show up and restore my custom settings. But this isn't a long-term solution and it is kind of annoying. Any ideas how to fix this?

---

### Post by Bölvaður on 2008-11-04
run nvidia-settings as root.

If you have luncher in the menu please change it to fit the terminal command that follows:
```

gksudo nvidia-settings
```

You can also use this under program luncher (Alt+F2)

---

### Post by lovinglinux on 2008-11-05
Thanks, but unfortunately it doesn't solve the problem.

---

### Post by lovinglinux on 2008-11-09
Nevermind. I have found the solution while googling for another issue.

Just had to add "-l" to nvidia-settings command in Sessions, like this:

```
nvidia-settings -l
```

---


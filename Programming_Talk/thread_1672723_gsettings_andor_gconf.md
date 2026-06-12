---
title: "gsettings and/or gconf"
date: 2011-01-21
forum: Programming Talk
---

### Post by tonemgub on 2011-01-21
Hello.
I have been writing an application for a few months and have used gconf for my first release. I know that maverick is using dconf and gsettings and that gnome recommends migrating to gsettings. The problem is that I want my application to run on both, maverick and lucid. Is there a seamless way (for the user) to use gsettings in lucid (something I, as a developer could do)? If possible, I would like to avoid having to code something like that:
```
#ifdef HAS_GSETTINGS
  g_settings_get...()
#else
  g_conf_get...()
#endif
```

Thank you for your help.

---

### Post by tonemgub on 2011-02-04
I have done some more research and found out that there exists a temporary solution namely creating a file .convert in /usr/share/GConf/gsettings/. However, this approach requires gconf 2.31.1 and as lucid uses an earlier version, I don't think this approach would work.

---

### Post by tonemgub on 2011-02-08
Anybody?!? :confused:

---

### Post by tonemgub on 2011-02-16
bump [-o<

---

### Post by tonemgub on 2011-03-02
Am I in the wrong thread?

---

### Post by altonbr on 2011-07-29
I've found Ubuntu Forums is lacking when it comes to technical talk. I would post this question on [Ask Ubuntu]("http://askubuntu.com/") or post this question to the Ubuntu or GNOME mailing lists.

---

### Post by Habitual on 2011-07-29
> **altonbr said:**
> I've found Ubuntu Forums is lacking when it comes to technical talk. I would post this question on [Ask Ubuntu]("http://askubuntu.com/") or post this question to the Ubuntu or GNOME mailing lists.

+5 for askubuntu.com

That's where the real "under the hood" folks hang out. :)

---


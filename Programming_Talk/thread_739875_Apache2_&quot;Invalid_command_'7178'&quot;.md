---
title: "Apache2 &quot;Invalid command '7178'&quot;"
date: 2008-03-30
forum: Programming Talk
---

### Post by Josh1 on 2008-03-30
Hey all,

My apache2 has just started giving me this error when i try to start it:

```

josh@josh-desktop:~$ sudo /etc/init.d/apache2 restart                            * Restarting web server apache2                                                Syntax error on line 1 of /etc/apache2/conf.d/charset.lock:
Invalid command '7178', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

```

Does anyone know why? I can't find anything by searching.

---

### Post by mssever on 2008-03-30
> **Josh1 said:**
> Hey all,

My apache2 has just started giving me this error when i try to start it:

```

josh@josh-desktop:~$ sudo /etc/init.d/apache2 restart                            * Restarting web server apache2                                                Syntax error on line 1 of /etc/apache2/conf.d/charset.lock:
Invalid command '7178', perhaps misspelled or defined by a module not included in the server configuration
                                                                         [fail]

```Does anyone know why? I can't find anything by searching.
You didn't specify how you searched. HAve you tried this? ```
grep -nr '7178' /etc/apache2/
```

---


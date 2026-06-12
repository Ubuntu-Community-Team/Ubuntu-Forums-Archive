---
title: "How Install Jdownloader Installer?"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by Ashfaqur Rahman on 2013-04-09
I have downloaded Jdownloader installer from their website which was saved in Desktop named jd_unix_0_9.sh .
Now how can i install it?

---

### Post by mamamia88 on 2013-04-09
cd /home/username/Desktop
chmod +x jd_unix_0_9.sh
./jd_unix_0_9.sh

---

### Post by mamamia88 on 2013-04-09
cd /home/username/Desktop
chmod +x jd_unix_0_9.sh
./jd_unix_0_9.sh

ps you may need root to do this.  never tried to use jdownloader.  or even better [https://launchpad.net/~jd-team/+archive/jdownloader](https://launchpad.net/~jd-team/+archive/jdownloader)

---

### Post by Ashfaqur Rahman on 2013-04-09
After giving code it shows " No suitable Java Virtual Machine could be found on your system.The version of the JVM must be at least 1.6 and at most 2.0.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file
 "

I think i have to download java first.

Can you plz explain this code?what we have acctually done with this code?
```

[COLOR=#000000]chmod +x jd_unix_0_9.sh[/COLOR]

```

---

### Post by mamamia88 on 2013-04-09
> **Ashfaqur Rahman said:**
> After giving code it shows " No suitable Java Virtual Machine could be found on your system.The version of the JVM must be at least 1.6 and at most 2.0.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file
 "

I think i have to download java first.

Can you plz explain this code?what we have acctually done with this code?
```

[COLOR=#000000]chmod +x jd_unix_0_9.sh[/COLOR]

```

chmod +x makes the script executable.

---


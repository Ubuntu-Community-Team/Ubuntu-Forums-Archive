---
title: "How to run script in Linux for windows command"
date: 2006-05-16
forum: Programming Talk
---

### Post by krypto_wizard on 2006-05-16
I have to remotely shut the windows px from linux box.

I run OpenSSH on windows PC. I remotely connect it from Linux box using ....

```

ssh Admin@IP_ADDR        # connects me fine now without problems (LOCAL)

```

Next, I wrote a script that would log me in and also shut the windows pc down, so I wrote a script
```

ssh Admin@IP_ADDR  # connects me fine now without problems (LOCAL)
shutdown -s            # This is a windows command (REMOTE)

```

Now, when I run this script, it successfully logs me into the windows box but doesn't run the second part of the script which is to shut down the windows PC.

Can you please tell me why ??

Every help is appreciated.

---

### Post by krypto_wizard on 2006-05-16
I found the right way which is to have them in one line to execute remotely.
```

ssh username@IP_ADDR shutdown -s

```

Hope this help others sometimes.

---


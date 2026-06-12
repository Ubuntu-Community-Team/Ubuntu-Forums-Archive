---
title: "bashrc shell in ubuntu"
date: 2013-06-28
forum: New to Ubuntu
---

### Post by emmagood on 2013-06-28
Hello,

  If I am correct, the default shell of Ubuntu is c shell. How to start/ install bash shell and make it default.

Thanks,
Emma Good.

---

### Post by steeldriver on 2013-06-28
AFAIK the default user login shell *is* bash - you can check your current shell with

```
echo $SHELL
```

You can check the currently available shells on your system using

```
cat /etc/shells
```

You can change your own login shell globally using the chsh command e.g.

```
chsh -s /bin/bash
```

---


---
title: "terminal prompt only shows $"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by ashakdwipeea on 2013-11-01
when i start my terminal from any account i dont get username

---

### Post by steeldriver on 2013-11-01
Hello and welcome to the forum

The 2 most likely explanations are either that you are not using the bash shell (perhaps your users default shells are set to /bin/sh, which is a symlink to dash?) or that the shell's PS1 environment variable is not being set

---

### Post by Lars Noodén on 2013-11-01
You can see which shell you are actually running like this:

```

echo $0

```

Or by looking at your entry in /etc/passwd

Usually PS1 (the prompt) gets set in ~/.bashrc, does that exist in your home directory?

```

ls -la ~/.bashrc

```

---


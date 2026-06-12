---
title: "Root Privileges"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Sorex on 2008-07-17
There are some things I need to do which are asking for root privileges... how do I get root privileges?

Thanks!

---

### Post by alienexplorers on 2008-07-17
sudo for non graphical items.
gksudo for graphical items.

---

### Post by Dedoimedo on 2008-07-17
Hi,

Ubuntu works with the sudo principle rather than typical root (su). This means that you can elevate your privilages very simply by typing sudo before any command that requires this.

Example:

```
sudo cp /etc/file /backup
```

Be careful though, as you can easily make "anything" with sudo, including self-inflicted damage. Use sudo with care.

Dedoimedo

---

### Post by Sorex on 2008-07-17
ahha yes right got it! didn't realise that's what sudo is!  thanks

---

### Post by lisati on 2008-07-17
> **Sorex said:**
> ahha yes right got it! didn't realise that's what sudo is!  thanks
"sudo" might be translated as "**S**uper **U**ser **Do**"......most things don't need super-user (root) privileges, sudo is there for the occasions that they would be useful. As has already be said, be careful: the prompt for a password might be thought of a way of asking, "are you sure?"

---


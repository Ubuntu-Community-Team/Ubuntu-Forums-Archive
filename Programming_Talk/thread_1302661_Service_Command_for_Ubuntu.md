---
title: "Service Command for Ubuntu"
date: 2009-10-27
forum: Programming Talk
---

### Post by EMCGFX on 2009-10-27
I've always wanted to have service command just like Fedora has for restarting, starting or stoping services. So I've finally figured out the way. What I do is add the following command in my .bash_aliases file, you can also just use .bashrc file instead.

```
# Service for Ubuntu
function service() {
  sudo /etc/init.d/$1 $2;
}
```

Now just use it like this;

service samba restart

Original command is;

sudo /etc/init.d/samba restart

I hope this helps some one too ;)

---


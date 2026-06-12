---
title: "Dumb problem: shut down while updating"
date: 2014-04-04
forum: New to Ubuntu
---

### Post by xuan3 on 2014-04-04
Hi, really idiotic problem here but I stopped my Ubuntu while it was updating. It had completed downloading updates and was running "post installation...." something or other - I can't remember. Obviously, I feel like a moron now, I should've left it to finish the installation completely but I got impatient when it seemed like nothing was happening. Lesson learned and I'd really just like to fix my computer now - I have some fairly important documents that I need access to.

Now when I try to run Ubuntu, the mouse doesn't move and everything is working very very slowly (not that I can access most things programs since the mouse isn't moving). Is there something I could try to do to fix this? I'm fairly computer illiterate and I don't really understand the solutions I google - I'm afraid to make it even worse. I've gone to recovery mode but I'd rather not try anything until someone with more knowledge can guide.

---

### Post by tgalati4 on 2014-04-05
Boot into a Rescue Shell from GRUB.  That will give you a root terminal.

```
apt-get install -f
```

Write down what it says to do.

---


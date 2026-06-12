---
title: "Two Xfce basic questions"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by regua on 2008-04-27
Hi there,

I've been using Ubuntu for a while now. I've decided to try a few graphical environments other than Gnome, and after trying out Xfce I decided to give it a chance as my default environment.

I have two problems, though.

First one: applications like Pidgin and Firefox are starting two instances of themselves after logging in. I haven't changed anything, I haven't added them to the "Autostarted apps" menu. What could be the cause of this?

Second one: I'm doing a lot of sudo-prefixed operations, and that Root Terminal seems interesting. I can't change the default prompt, though; PS1 isn't working. How can I do that?

Thanks.

---

### Post by SnakeHips on 2008-04-27
first one:
it *may* be a feature ;-)
anyway ,have a look here and change setting to one desktop.
applications/settings/settings manager/workspaces and margins.

second one:
not quite sure what you mean by PS1 dont work ??

---

### Post by shearn89 on 2008-04-27
2: you need to change the PS1 line in /root/.bashrc

---

### Post by regua on 2008-04-28
> **SnakeHips said:**
> first one:
it *may* be a feature ;-)
anyway ,have a look here and change setting to one desktop.
applications/settings/settings manager/workspaces and margins.
Nope, that didn't solve the problem. Firefox and Pidgin both open twice, whereas other apps I used when I was on Gnome, like Skype, open only once.

> **shearn89 said:**
> 2: you need to change the PS1 line in /root/.bashrc
Thanks, that's what I was looking for.

---

### Post by hyper_ch on 2008-04-28
close all pidgin (whatever), logout and check the box to save the session. The reboot and see if those are auto-started again. If not - which I hope, either start them again and again upon logout set to save the session or add it to auto-start.

---


---
title: "[SOLVED] Changing boot splash back to ubuntu default."
date: 2008-08-29
forum: New to Ubuntu
---

### Post by scweston on 2008-08-29
Hi,

I have Ubuntu Hardy Heron installed with the default Gnome desktop. I was curious to see what the fuss was about with KDE4.1 and so successfully followed a tutorial to install it. Although I like it, I've decided to keep gnome as my default (as thats what I'm more experienced with) and just use KDE4.1 for playing with.

However, my problem is that since installing KDE4.1 it has changed my computer's boot splash to the blue Kubuntu one. I would much rather have the original default Ubuntu splash.

My question is.. how do I change the boot splash back to the ubuntu installed default?

Thanks in advance to anybody who reads this and helps me out.

Stephen

---

### Post by kpkeerthi on 2008-08-29
Run these commands in a terminal:

```

sudo update-alternatives --config usplash-artwork.so

```

```

sudo update-initramfs -u

```

---

### Post by scweston on 2008-08-29
Perfect!

Thank you very much for your incredibly quick response.

---

### Post by yrohinkumar on 2012-04-28
Does it work for latest ubuntu versions too?

---

### Post by yrohinkumar on 2012-05-16
I figured in the latest versions (or the ones with gnome installed) one needs to remove the corresponding plymouth package of boot splash to get back the ubuntu default...that works...:)

---

### Post by robgraves on 2012-05-17
wow 2008

---

### Post by yrohinkumar on 2012-05-17
I appreciate the sarcasm :) but this method that [SOLVED] the problem doesn't work anymore in many cases...thought I'll post the latest solution just in case someone needs ;)

---


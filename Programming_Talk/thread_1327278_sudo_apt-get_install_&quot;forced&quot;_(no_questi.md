---
title: "sudo apt-get install &quot;forced&quot; (no questions)"
date: 2009-11-15
forum: Programming Talk
---

### Post by giuspen on 2009-11-15
Hi,
I need to insert in a script the installation of some packages but my script stucks as some packages (like audacious for instance) ask in the terminal if i really want to install it and wait for me to insert [Y/n],
does anybody know if there's an option to avoid questions and just go on?
Thanks in advance.

---

### Post by Zugzwang on 2009-11-15
Use the man-page:

```

man apt-get

```

You will see that there exists some option "-y", which should do what you want. Carefully read the description.

---

### Post by giuspen on 2009-11-15
> **Zugzwang said:**
> Use the man-page:

```

man apt-get

```

You will see that there exists some option "-y", which should do what you want. Carefully read the description.

thanks a lot

---


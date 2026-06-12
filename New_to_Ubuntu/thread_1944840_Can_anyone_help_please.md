---
title: "Can anyone help please?"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by Technologist on 2012-03-22
I'm a newbie and I was just wondering if anyone knows how to make your pc play dvds? I installed the restricted extras package and it still doesn't work.

---

### Post by VinnyJ1701 on 2012-03-22
What player are you using, and what happens when you try to play one?

---

### Post by zombifier25 on 2012-03-22
If you want to play encrypted DVDs, you need to install the package libdvdread4 that can help decode DVDs. However, due to legal reasons, Ubuntu cannot include it in the restricted extras.
```

sudo apt-get install libdvdread4[FONT=monospace]
[/FONT]sudo /usr/share/doc/libdvdread4/install-css.sh

```

Be warned; depends on where you live, using it may be illegal. But so far, no one has been sued because of this.

---

### Post by oldos2er on 2012-03-22
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

In the future you might find it helpful to give your threads a more descriptive title.

---


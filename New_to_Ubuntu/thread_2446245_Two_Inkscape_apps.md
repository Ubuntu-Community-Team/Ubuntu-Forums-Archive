---
title: "Two Inkscape apps"
date: 2020-06-27
forum: New to Ubuntu
---

### Post by catafilaz on 2020-06-27
I hav installed inkscape using terminal. But now i hav two inkscape applications.

1. Version 1.0(1.0+r73+1)
2. Version 1.0(6e3e5246a0, 2020-05-07)

I need to delete one of them &#128549; plz help.

---

### Post by Dennis N on 2020-06-27
The second one is the Inkscape snap package and the first one is not the current version in the Ubuntu 20.04 repository - that one is 0.92.5. Where did you get it? Knowing that informs the method of removal. If you wish, you can easily remove the snap package from the terminal:

```
snap remove inkscape
```

---


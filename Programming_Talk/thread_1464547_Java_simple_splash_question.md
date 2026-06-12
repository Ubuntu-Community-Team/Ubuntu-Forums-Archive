---
title: "Java simple splash question"
date: 2010-04-28
forum: Programming Talk
---

### Post by .:PiXi²:. on 2010-04-28
I've added a splash screen to my program using the VM option "-splash:...". From the moment that the first objects are drawn, the splash closes, which is normal. But how can I set a delay for the splash to close?

Thanks in advance.

---

### Post by Zugzwang on 2010-04-28
I don't think that this is a supported feature. You can, however, just open a window at the same position and size as the first action that you application does and thus replace the splash window with something self-written and more sophisticated (where you can do what you want).

---

### Post by .:PiXi²:. on 2010-04-28
Thanks Zugzwang, problem solved, thread solved.

---


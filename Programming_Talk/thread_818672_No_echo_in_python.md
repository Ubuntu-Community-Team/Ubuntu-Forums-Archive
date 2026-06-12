---
title: "No echo in python"
date: 2008-06-04
forum: Programming Talk
---

### Post by blithen on 2008-06-04
I'm making a fake login screen, and I was wondering how would I go about getting no echo in the terminal, or even better getting the password to come out like ********. Any ideas?

---

### Post by Bichromat on 2008-06-04
Use the 'getpass' module:
```

import getpass

password = getpass.getpass("Password: ")

```

---

### Post by LaRoza on 2008-06-04
> **blithen said:**
> I'm making a fake login screen, and I was wondering how would I go about getting no echo in the terminal, or even better getting the password to come out like ********. Any ideas?

In addition to the solution given, you can use the curses module to control the terminal output more. However, that might be overkill for this (as you seem to want the ** mostly)

---


---
title: "[SOLVED] Question on apturl"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-05-20
I was just wondering if there was anyway of putting a script onto apturl? I would like to be able to have an apturl link on my website that will install multiple programs, instead of just one. Is that even possible? If not, any suggestions on the best way to do that?

---

### Post by Paqman on 2008-05-26
Good question. Normal apt syntax allows you to string as many install commands together as you like. For example:
```

sudo apt-get install amarok pidgin deluge

```

...installs all three of those packages.

I don't see why that wouldn't work for apturl, too. Give it a try.

---


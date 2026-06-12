---
title: "How can I change to using gcc-3.4 and friends?"
date: 2006-11-25
forum: Programming Talk
---

### Post by enigma_0Z on 2006-11-25
How can I reconfigure the compiler symlinks to change from gcc-4.1 (and friends) without manually changing them?

---

### Post by hod139 on 2006-11-27
you shouldn't have to touch any sim links.  You can install gcc-3.4, and then use update-alternatives to select the desired version.  I think it will be 
```

sudo update-alternatives --config cc

```

and you can select your desired version of gcc.  For C++, you would do 
```

sudo update-alternatives --config c++

```

---


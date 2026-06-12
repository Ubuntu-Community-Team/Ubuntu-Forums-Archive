---
title: "include all files"
date: 2010-05-07
forum: Programming Talk
---

### Post by TehCodr on 2010-05-07
Hi, I'm trying to include the whole X11 header files, but I don't want to include every single one individually, so is there a way to include en mass a whole folder, like this:

```

#include <X11/*>
#include <X11/*/*>

```

please reply soon

---

### Post by soltanis on 2010-05-07
I'm pretty sure ANSI C does not allow you to glob header files. You need to include them all individually.

If you don't want to do that, you can try putting all your includes in one header file and then include that header file. Since #include'ing a file just means the preprocessor pastes it into its appointed location in the source file, includes are inherited.

---


---
title: "C++ and POSIX functions"
date: 2010-07-30
forum: Programming Talk
---

### Post by dawwin on 2010-07-30
Is this ok to use linux/unix API functions in c++ programs? Are there any problems with that?

---

### Post by WRDN on 2010-07-30
Theres no problem with it. However, if you want to create a cross platform application, then you should safe guard platform independant functions and headers using "#ifdef".

For Linux systems:

```

#ifdef __linux__
// Linux specific code
#endif

```

For Windows:

```

#ifdef _WIN32
// Windows code
#endif

```

---


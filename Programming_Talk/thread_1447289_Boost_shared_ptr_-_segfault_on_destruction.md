---
title: "Boost shared ptr - segfault on destruction"
date: 2010-04-05
forum: Programming Talk
---

### Post by MattThLinuxNewb on 2010-04-05
I've written a simple 2D game in C++ using the boost shared pointer library. I recently compiled it on a different computer running Debian Lenny. It compiles and runs fine up until I exit, at which point it gives a segmentation fault. (It doesn't segfault on my normal PC running Ubuntu 8.04)

The gdb backtrace revealed the source to be the shared_ptr destructor for one of my objects:
```
#0  0x0805e428 in missile::Logger::debug ()
#1  0x08065a10 in missile::OGLRenderer::~OGLRenderer ()
#2  0x0804be8d in boost::checked_delete<missile::OGLRenderer> ()
#3  0x0804c055 in boost::detail::sp_counted_impl_p<missile::OGLRenderer>::dispose ()
#4  0x0804bac1 in boost::detail::sp_counted_base::release ()
#5  0x0804bb03 in boost::detail::shared_count::~shared_count ()
#6  0x0804bd23 in boost::shared_ptr<missile::Renderer>::~shared_ptr ()
#7  0xb7adcab9 in exit () from /lib/i686/cmov/libc.so.6
#8  0xb7ac445d in __libc_start_main () from /lib/i686/cmov/libc.so.6
#9  0x0804a9e1 in _start ()
```

Some further explanation of the objects involved: The OGLRenderer class derives from Renderer. In order to be able to treat my OGLRenderer instance as a Renderer (i.e. use it polymorphically) with a boost smart pointer I use the following code:
```
    // Initialize Renderer
    boost::shared_ptr<OGLRenderer> oglrenderer(new OGLRenderer());
    boost::shared_ptr<Renderer> renderer =
        boost::dynamic_pointer_cast<Renderer>(oglrenderer);
```

Can anyone tell me what might be causing the shared_ptr to segfault when destructed?

Thanks heaps

---

### Post by MadCow108 on 2010-04-05
according to your backtrace the bug seems somewhere in destructor of OGLRenderer or the logger and has little to do with the shared_ptr (except that it is the shared_ptr that calls the destructor)
Check if there are double deletes of your object, if yes there is probably some other reference to it which is not a shared_ptr deleteing the object
and if all the values the logger access in the destructor are still valid.

without code, I can't help. I can just say the boost shared_ptr should be bug free, the problem will be in your code.

---

### Post by MattThLinuxNewb on 2010-04-05
Thanks. The problem was with the logger. I pinpointed the line by compiling with debugging enabled (-g flag) and running gdb backtrace again.

---


---
title: "update glibc"
date: 2011-11-04
forum: Programming Talk
---

### Post by cohenguy1 on 2011-11-04
Hello!

I'm having troubles compiling a project with opencv included.
I'm using Karmic and when I try to compile my code I get this linker errors:

```

libopencv_calib3d.so: undefined reference to `std::__detail::_List_node_base::_M_transfer(std::__detail::_List_node_base*, std::__detail::_List_node_base*)@GLIBCXX_3.4.15'
libopencv_calib3d.so: undefined reference to `std::__detail::_List_node_base::_M_hook(std::__detail::_List_node_base*)@GLIBCXX_3.4.15'
libopencv_ts.so: undefined reference to `__longjmp_chk@GLIBC_2.11'

```
When I compile the same code under oneiric ocelot I get no errors.

I think the problem is my glibc isn't updated enough.
I tried to figure what my glibc version is and got this: 
```

strings /usr/lib/libstdc++.so.6 | grep GLIBC
GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBC_2.0
GLIBC_2.3
GLIBC_2.4
GLIBC_2.1
GLIBC_2.3.4
GLIBC_2.1.3
GLIBC_2.3.2
GLIBC_2.2
GLIBCXX_FORCE_NEW
GLIBCXX_DEBUG_MESSAGE_LENGTH

```
Like the above log, I don't see GLIBCXX_3.4.15 or GLIBC_2.11 so I suspect this is the problem.

Please note that I don't want update my ubuntu version, so is there a solution without it?
I might be wrong figuring out the  problem so feel free to share your ideas.

I appreciate your help.
Guy

---

### Post by lisati on 2011-11-04
*Thread moved to **Programming Talk**.*

---

### Post by gsmanners on 2011-11-04
You could always downgrade to Hardy and use [libcv1]("http://packages.ubuntu.com/hardy/libcv1"), I suppose, but then you'd only have support for server stuff. Since karmic isn't supported, you obviously can't expect them to backport glibc. I think your only choice is really either upgrade or downgrade.

---

### Post by cohenguy1 on 2011-11-06
I'm still receiving the same error (and the same log) under ubuntu 10.04. 
Probably I'm doing something wrong. Can anyone tell me how to update glibc properly?
Or maybe this isn't the problem, please share your ideas.

---

### Post by nvteighen on 2011-11-06
> **lisati said:**
> *Thread moved to **Programming Talk**.*

Why was this moved here? This is not about programming, but about updating a package which just happens to be related to programming.

---

### Post by cohenguy1 on 2011-11-06
Dunno why it was moved. In the meantime a googled some more and find out the problem is I can install only up to gcc 4.4 in Lucid and Karmic, while on Oneiric I can install up to gcc 4.6.
I'm convinced this is the problem, and I appreciate if anyone could tell me how to update to gcc 4.6 on Karmic (or at least on Lucid)

Thanks

---


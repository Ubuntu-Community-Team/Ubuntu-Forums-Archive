---
title: "template template build error that once compiled fine"
date: 2008-08-24
forum: Programming Talk
---

### Post by spamalot on 2008-08-24
Hi all,

I have some build errors related to template templates that once compiled fine. I'm wondering if the upgrade from 7.10 to 8.04 has anything to do with it, perhaps the upgrade of gcc itself (currently it is 4.2.3, i believe but i'm not sure it was 4.1.3 under 7.10)?

suppose i have a template class like this:

template<typename ValueType,template<typename> class F>
A{
 typedef F<ValueType> f_type;
};

and in a source file I have:

typedef A<ValueType,std::vector> a_type;

This used to work fine, not anymore:

expected a template of type ‘template<class> class F’, got ‘template<class _Tp, class _Alloc> class std::vector’

I perfectly understand this error message, no need to explain it to me. it's just that _Alloc usually has a default, which previously allowed the definition of A as above, not anymore! I have to refactor my code, any suggestion?

Thanks!

---

### Post by spamalot on 2008-08-25
This has been answered here:

[http://groups.google.com/group/comp.lang.c++/browse_thread/thread/669dc8a9ba04c39d](http://groups.google.com/group/comp.lang.c++/browse_thread/thread/669dc8a9ba04c39d)

---


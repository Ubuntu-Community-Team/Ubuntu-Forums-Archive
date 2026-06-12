---
title: "eclipse and sigc"
date: 2010-03-07
forum: Programming Talk
---

### Post by mazzzterZ on 2010-03-07
Hi!
For a long time I was using code::blocks as IDE on ubuntu but now I decided to test Eclipse CDT. First of all I compiled a simple console application... no problem. Later I tried gtkmm and I compiled an application containing only an empty window... no problem so I decided everythig works. But it didn't I tried connecting a signal but it gives an error. Here is the signal:
```
button.signal_clicked().connect(sigc::mem_fun(*this, &SDWindow::test));
```
Error:
```
make all 
Building file: ../src/main_form.cpp
Invoking: GCC C++ Compiler
g++ -I/usr/include/gtkmm-2.4 -I/usr/lib/sigc++-2.0/include -I"/home/mazzzterz/workspace/ps_project/src" -I/usr/include/atkmm-1.6 -I/usr/include/cairomm-1.0 -I/usr/include/gdkmm-2.4 -I/usr/include/giomm-2.4 -I/usr/include/pangomm-1.4 -I/usr/include/sigc++-2.0 -I/usr/include/glibmm-2.4 -O0 -g3 -Wall -c -fmessage-length=0 `pkg-config gtkmm-2.4 --cflags` -MMD -MP -MF"src/main_form.d" -MT"src/main_form.d" -o"src/main_form.o" "../src/main_form.cpp"
In file included from /usr/include/sigc++-2.0/sigc++/signal_base.h:26,
                 from /usr/include/sigc++-2.0/sigc++/signal.h:8,
                 from /usr/include/sigc++-2.0/sigc++/sigc++.h:23,
                 from /usr/include/glibmm-2.4/glibmm/signalproxy.h:13,
                 from /usr/include/glibmm-2.4/glibmm/objectbase.h:23,
                 from /usr/include/glibmm-2.4/glibmm/wrap.h:26,
                 from /usr/include/glibmm-2.4/glibmm/containerhandle_shared.h:25,
                 from /usr/include/glibmm-2.4/glibmm/arrayhandle.h:23,
                 from /usr/include/glibmm-2.4/glibmm.h:27,
                 from /usr/include/gtkmm-2.4/gtkmm/window.h:7,
                 from /home/mazzzterz/workspace/ps_project/src/main_form.hpp:11,
                 from ../src/main_form.cpp:10:
/usr/include/sigc++-2.0/sigc++/type_traits.h: In instantiation of &#8216;const bool sigc::is_base_and_derived<sigc::trackable, SDWindow>::value&#8217;:
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1792:   instantiated from &#8216;sigc::bound_mem_functor0<void, SDWindow>&#8217;
../src/main_form.cpp:59:   instantiated from here
/usr/include/sigc++-2.0/sigc++/type_traits.h:132: error: &#8216;sigc::trackable&#8217; is an inaccessible base of &#8216;SDWindow&#8217;
In file included from /usr/include/sigc++-2.0/sigc++/adaptors/adaptor_trait.h:9,
                 from /usr/include/sigc++-2.0/sigc++/functors/slot.h:7,
                 from /usr/include/sigc++-2.0/sigc++/signal_base.h:28,
                 from /usr/include/sigc++-2.0/sigc++/signal.h:8,
                 from /usr/include/sigc++-2.0/sigc++/sigc++.h:23,
                 from /usr/include/glibmm-2.4/glibmm/signalproxy.h:13,
                 from /usr/include/glibmm-2.4/glibmm/objectbase.h:23,
                 from /usr/include/glibmm-2.4/glibmm/wrap.h:26,
                 from /usr/include/glibmm-2.4/glibmm/containerhandle_shared.h:25,
                 from /usr/include/glibmm-2.4/glibmm/arrayhandle.h:23,
                 from /usr/include/glibmm-2.4/glibmm.h:27,
                 from /usr/include/gtkmm-2.4/gtkmm/window.h:7,
                 from /home/mazzzterz/workspace/ps_project/src/main_form.hpp:11,
                 from ../src/main_form.cpp:10:
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h: In instantiation of &#8216;sigc::bound_mem_functor0<void, SDWindow>&#8217;:
../src/main_form.cpp:59:   instantiated from here
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1792: error: &#8216;sigc::is_base_and_derived<sigc::trackable, SDWindow>::value&#8217; is not a valid template argument for type &#8216;bool&#8217; because it is a non-constant expression
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h: In constructor &#8216;sigc::bound_mem_functor0<T_return, T_obj>::bound_mem_functor0(T_obj&, typename sigc::mem_functor0<T_return, T_obj>::function_type) [with T_return = void, T_obj = SDWindow]&#8217;:
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:5453:   instantiated from &#8216;sigc::bound_mem_functor0<T_return, T_obj> sigc::mem_fun(T_obj&, T_return (T_obj2::*)()) [with T_return = void, T_obj = SDWindow, T_obj2 = SDWindow]&#8217;
../src/main_form.cpp:59:   instantiated from here
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1780: error: using invalid field &#8216;sigc::bound_mem_functor0<T_return, T_obj>::obj_&#8217;
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h: In function &#8216;void sigc::visit_each(const T_action&, const sigc::bound_mem_functor0<T_return, T_obj>&) [with T_action = sigc::internal::limit_derived_target<sigc::trackable*, sigc::internal::slot_do_bind>, T_return = void, T_obj = SDWindow]&#8217;:
/usr/include/sigc++-2.0/sigc++/adaptors/adaptor_trait.h:267:   instantiated from &#8216;void sigc::visit_each(const T_action&, const sigc::adaptor_functor<T_functor>&) [with T_action = sigc::visit_each_type(const T_action&, const T_functor&) [with T_type = sigc::trackable*, T_action = sigc::internal::slot_do_bind, T_functor = sigc::adaptor_functor<sigc::bound_mem_functor0<void, SDWindow> >]::type_limited_action, T_functor = sigc::bound_mem_functor0<void, SDWindow>]&#8217;
/usr/include/sigc++-2.0/sigc++/visit_each.h:170:   instantiated from &#8216;void sigc::visit_each_type(const T_action&, const T_functor&) [with T_type = sigc::trackable*, T_action = sigc::internal::slot_do_bind, T_functor = sigc::adaptor_functor<sigc::bound_mem_functor0<void, SDWindow> >]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:39:   instantiated from &#8216;sigc::internal::typed_slot_rep<T_functor>::typed_slot_rep(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:451:   instantiated from &#8216;sigc::slot0<T_return>::slot0(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:1130:   instantiated from &#8216;sigc::slot<T_return, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::slot(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
../src/main_form.cpp:59:   instantiated from here
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1806: error: &#8216;const class sigc::bound_mem_functor0<void, SDWindow>&#8217; has no member named &#8216;obj_&#8217;
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h: In member function &#8216;T_return sigc::bound_mem_functor0<T_return, T_obj>::operator()() const [with T_return = void, T_obj = SDWindow]&#8217;:
/usr/include/sigc++-2.0/sigc++/adaptors/adaptor_trait.h:251:   instantiated from &#8216;typename sigc::adaptor_functor<T_functor>::result_type sigc::adaptor_functor<T_functor>::operator()() const [with T_functor = sigc::bound_mem_functor0<void, SDWindow>]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:103:   instantiated from &#8216;static T_return sigc::internal::slot_call0<T_functor, T_return>::call_it(sigc::internal::slot_rep*) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:110:   instantiated from &#8216;static void* (* sigc::internal::slot_call0<T_functor, T_return>::address())(void*) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:454:   instantiated from &#8216;sigc::slot0<T_return>::slot0(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:1130:   instantiated from &#8216;sigc::slot<T_return, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::slot(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
../src/main_form.cpp:59:   instantiated from here
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1787: error: using invalid field &#8216;sigc::bound_mem_functor0<T_return, T_obj>::obj_&#8217;
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1787: error: return-statement with a value, in function returning 'void'
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h: In function &#8216;void sigc::visit_each(const T_action&, const sigc::bound_mem_functor0<T_return, T_obj>&) [with T_action = sigc::internal::limit_derived_target<sigc::trackable*, sigc::internal::slot_do_unbind>, T_return = void, T_obj = SDWindow]&#8217;:
/usr/include/sigc++-2.0/sigc++/adaptors/adaptor_trait.h:267:   instantiated from &#8216;void sigc::visit_each(const T_action&, const sigc::adaptor_functor<T_functor>&) [with T_action = sigc::visit_each_type(const T_action&, const T_functor&) [with T_type = sigc::trackable*, T_action = sigc::internal::slot_do_unbind, T_functor = sigc::adaptor_functor<sigc::bound_mem_functor0<void, SDWindow> >]::type_limited_action, T_functor = sigc::bound_mem_functor0<void, SDWindow>]&#8217;
/usr/include/sigc++-2.0/sigc++/visit_each.h:170:   instantiated from &#8216;void sigc::visit_each_type(const T_action&, const T_functor&) [with T_type = sigc::trackable*, T_action = sigc::internal::slot_do_unbind, T_functor = sigc::adaptor_functor<sigc::bound_mem_functor0<void, SDWindow> >]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:60:   instantiated from &#8216;static void* sigc::internal::typed_slot_rep<T_functor>::destroy(void*) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:38:   instantiated from &#8216;sigc::internal::typed_slot_rep<T_functor>::typed_slot_rep(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:451:   instantiated from &#8216;sigc::slot0<T_return>::slot0(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
/usr/include/sigc++-2.0/sigc++/functors/slot.h:1130:   instantiated from &#8216;sigc::slot<T_return, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::slot(const T_functor&) [with T_functor = sigc::bound_mem_functor0<void, SDWindow>, T_return = void]&#8217;
../src/main_form.cpp:59:   instantiated from here
/usr/include/sigc++-2.0/sigc++/functors/mem_fun.h:1806: error: &#8216;const class sigc::bound_mem_functor0<void, SDWindow>&#8217; has no member named &#8216;obj_&#8217;
make: *** [src/main_form.o] Error 1
```

I noticed that if I typed the namespace sigc:: Eclipse doesn't recognize it. I mean it doesn't auto complete the code while if I try Gtk or Glib everything is ok. I noticed that I have the same problems with the namespaces Gdk and Cairo and a few more but these ones I'll need.

I jsut tried something else:
```
sigc::signal<void, int> signal;
signal.emit(5);
Gdk::Color color;
Cairo::RefPtr<Cairo::Context> cairo;
```
and it compiled without a problem. Looks like the problem is only when I try to connect a signal.
So does anyone have any idea why I can't connect signals ?

---

### Post by MadCow108 on 2010-03-07
button.signal_clicked().connect(sigc::prt_fun(&test));

shouldn't this be ptr_fun not prt_fun?

---

### Post by mazzzterZ on 2010-03-07
> **MadCow108 said:**
> button.signal_clicked().connect(sigc::prt_fun(&test));

shouldn't this be ptr_fun not prt_fun?

Oh yes... my bad I miss typed it while writing... but that's not the problem.

Edit: I fixed it. I have make a stupid error... I forgot to write public when inheriting Gtk::Window and so I inherited it private. when I changed it to public everything was ok.

---


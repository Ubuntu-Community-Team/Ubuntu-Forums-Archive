---
title: "Compiling Compiz From Git"
date: 2011-05-12
forum: Packaging and Compiling Programs
---

### Post by Andruk Tatum on 2011-05-12
Hi, I was following the instructions from 
[here]("http://wiki.compiz.org/C%2B%2BCompiling")

but I ran into compiling errors at step 6 of compiling the Core:
```
[ 33%] Building CXX object src/CMakeFiles/compiz.dir/region.cpp.o
In file included from 
.../compiz/src/region.cpp:32:
.../compiz/include/core/core.h:55: fatal error: glib.h: No such file or directory
compilation terminated.
make[2]: *** [src/CMakeFiles/compiz.dir/region.cpp.o] Error 1
make[1]: *** [src/CMakeFiles/compiz.dir/all] Error 2
make: *** [all] Error 2
```

The file /usr/include/glib-2.0/glib.h does exist, so I think the command to gcc to compile region.cpp is not being passed the proper -I flag to include /usr/include/glib-2.0 in the include search path (and possibly an -L and -l flag to link in glib).

How do I fix this problem?  I don't know CMake well enough to know what to look for in the CMakeLists.txt file, but I do know Makefiles.  I am on Maverick, and I have all of the packages from sudo apt-get build-dep compiz installed.  Thanks for your help.

---

### Post by MadCow108 on 2011-05-12
the dependency list on that page is not complete, it lack at least boost serialization and libgtkmm.
But also installing these does not fix the glib.h failure.

A quick fix is to tell cmake yourself where to find the header:
cmake ../ -DCMAKE_CXX_FLAGS="-g -O2 -I/usr/include/glib-2.0"

---

### Post by gusnan on 2011-05-16
This bug might be related:

[https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/751940](https://bugs.launchpad.net/ubuntu/+source/cmake/+bug/751940)

---

### Post by Andruk Tatum on 2011-05-18
> **MadCow108 said:**
> the dependency list on that page is not complete, it lack at least boost serialization and libgtkmm.
But also installing these does not fix the glib.h failure.

A quick fix is to tell cmake yourself where to find the header:
cmake ../ -DCMAKE_CXX_FLAGS="-g -O2 -I/usr/include/glib-2.0"

Thanks for that - I used that and I got glibmm errors, so the cmake command I ended up using was 
```
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr/local/compiz -DCMAKE_CXX_FLAGS="`pkg-config --cflags glib-2.0` `pkg-config --cflags glibmm-2.4`"
```

but now I'm getting errors like

```
[  0%] Built target decoration
[  6%] Built target gtk-window-decorator
[  8%] Built target gnome-compiz
[  8%] Built target kde4-window-decorator_automoc
[ 12%] Built target kde4-window-decorator
[ 31%] Built target nls
[ 32%] Built target core-gconf-schema
[ 33%] Built target core-xml-file
Linking CXX executable compiz
CMakeFiles/compiz.dir/timer.cpp.o: In function `CompTimeoutSource':
.../Desktop/Compiz/compiz/src/timer.cpp:32: undefined reference to `Glib::Source::Source()'
.../Desktop/Compiz/compiz/src/timer.cpp:40: undefined reference to `Glib::Source::set_priority(int)'
.../Desktop/Compiz/compiz/src/timer.cpp:41: undefined reference to `Glib::Source::attach(Glib::RefPtr<Glib::MainContext> const&)'
.../Desktop/Compiz/compiz/src/timer.cpp:42: undefined reference to `sigc::connection::~connection()'
.../Desktop/Compiz/compiz/src/timer.cpp:43: undefined reference to `Glib::Source::~Source()'
.../Desktop/Compiz/compiz/src/timer.cpp:32: undefined reference to `Glib::Source::Source()'
.../Desktop/Compiz/compiz/src/timer.cpp:40: undefined reference to `Glib::Source::set_priority(int)'
.../Desktop/Compiz/compiz/src/timer.cpp:41: undefined reference to `Glib::Source::attach(Glib::RefPtr<Glib::MainContext> const&)'
.../Desktop/Compiz/compiz/src/timer.cpp:42: undefined reference to `sigc::connection::~connection()'
.../Desktop/Compiz/compiz/src/timer.cpp:43: undefined reference to `Glib::Source::~Source()'
CMakeFiles/compiz.dir/timer.cpp.o: In function `~CompTimeoutSource':
.../Desktop/Compiz/compiz/src/timer.cpp:47: undefined reference to `Glib::Source::~Source()'
.../Desktop/Compiz/compiz/src/timer.cpp:47: undefined reference to `Glib::Source::~Source()'
.../Desktop/Compiz/compiz/src/timer.cpp:47: undefined reference to `Glib::Source::~Source()'
CMakeFiles/compiz.dir/timer.cpp.o: In function `CompTimeoutSource::connect(sigc::slot<bool, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> const&)':
.../Desktop/Compiz/compiz/src/timer.cpp:52: undefined reference to `Glib::Source::connect_generic(sigc::slot_base const&)'
CMakeFiles/compiz.dir/timer.cpp.o: In function `slot_rep':
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:84: undefined reference to `sigc::trackable::trackable()'
CMakeFiles/compiz.dir/timer.cpp.o: In function `~slot_rep':
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:87: undefined reference to `sigc::trackable::~trackable()'
/usr/include/sigc++-2.0/sigc++/functors/slot_base.h:87: undefined reference to `sigc::trackable::~trackable()'
CMakeFiles/compiz.dir/timer.cpp.o: In function `~slot0':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:422: undefined reference to `sigc::slot_base::~slot_base()'
CMakeFiles/compiz.dir/timer.cpp.o: In function `slot0<sigc::bound_mem_functor0<bool, CompTimeoutSource> >':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:451: undefined reference to `sigc::slot_base::slot_base(sigc::internal::slot_rep*)'
CMakeFiles/compiz.dir/timer.cpp.o:(.rodata._ZTI17CompTimeoutSource[typeinfo for CompTimeoutSource]+0x8): undefined reference to `typeinfo for Glib::Source'
CMakeFiles/compiz.dir/screen.cpp.o: In function `CompScreen::eventLoop()':
.../Desktop/Compiz/compiz/src/screen.cpp:118: undefined reference to `Glib::MainContext::get_default()'
.../Desktop/Compiz/compiz/src/screen.cpp:119: undefined reference to `Glib::MainLoop::create(Glib::RefPtr<Glib::MainContext> const&, bool)'
.../Desktop/Compiz/compiz/src/screen.cpp:123: undefined reference to `Glib::Source::attach(Glib::RefPtr<Glib::MainContext> const&)'
.../Desktop/Compiz/compiz/src/screen.cpp:126: undefined reference to `Glib::MainContext::iteration(bool)'
.../Desktop/Compiz/compiz/src/screen.cpp:128: undefined reference to `Glib::MainLoop::run()'
CMakeFiles/compiz.dir/screen.cpp.o: In function `CompWatchFd':
.../Desktop/Compiz/compiz/src/screen.cpp:224: undefined reference to `Glib::IOSource::IOSource(int, Glib::IOCondition)'
.../Desktop/Compiz/compiz/src/screen.cpp:227: undefined reference to `Glib::IOSource::connect(sigc::slot<bool, Glib::IOCondition, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> const&)'
.../Desktop/Compiz/compiz/src/screen.cpp:227: undefined reference to `sigc::connection::~connection()'
.../Desktop/Compiz/compiz/src/screen.cpp:228: undefined reference to `Glib::IOSource::~IOSource()'
.../Desktop/Compiz/compiz/src/screen.cpp:224: undefined reference to `Glib::IOSource::IOSource(int, Glib::IOCondition)'
.../Desktop/Compiz/compiz/src/screen.cpp:227: undefined reference to `Glib::IOSource::connect(sigc::slot<bool, Glib::IOCondition, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> const&)'
.../Desktop/Compiz/compiz/src/screen.cpp:227: undefined reference to `sigc::connection::~connection()'
.../Desktop/Compiz/compiz/src/screen.cpp:228: undefined reference to `Glib::IOSource::~IOSource()'
CMakeFiles/compiz.dir/screen.cpp.o: In function `CompScreen::addWatchFd(int, short, boost::function<void ()(short)>)':
.../Desktop/Compiz/compiz/src/screen.cpp:260: undefined reference to `Glib::Source::attach(Glib::RefPtr<Glib::MainContext> const&)'
CMakeFiles/compiz.dir/screen.cpp.o: In function `~slot1':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:495: undefined reference to `sigc::slot_base::~slot_base()'
CMakeFiles/compiz.dir/screen.cpp.o: In function `~RefPtr':
/usr/include/glibmm-2.4/glibmm/refptr.h:184: undefined reference to `Glib::MainContext::unreference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:184: undefined reference to `Glib::MainLoop::unreference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:184: undefined reference to `Glib::Source::unreference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:184: undefined reference to `Glib::Source::unreference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:184: undefined reference to `Glib::Source::unreference() const'
CMakeFiles/compiz.dir/screen.cpp.o: In function `RefPtr':
/usr/include/glibmm-2.4/glibmm/refptr.h:199: undefined reference to `Glib::Source::reference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:199: undefined reference to `Glib::MainContext::reference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:199: undefined reference to `Glib::MainLoop::reference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:199: undefined reference to `Glib::Source::reference() const'
/usr/include/glibmm-2.4/glibmm/refptr.h:199: undefined reference to `Glib::Source::reference() const'
CMakeFiles/compiz.dir/screen.cpp.o: In function `slot1<sigc::bound_mem_functor1<bool, CompWatchFd, Glib::IOCondition> >':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:526: undefined reference to `sigc::slot_base::slot_base(sigc::internal::slot_rep*)'
CMakeFiles/compiz.dir/screen.cpp.o:(.rodata._ZTV11CompWatchFd[vtable for CompWatchFd]+0x10): undefined reference to `Glib::IOSource::prepare(int&)'
CMakeFiles/compiz.dir/screen.cpp.o:(.rodata._ZTV11CompWatchFd[vtable for CompWatchFd]+0x14): undefined reference to `Glib::IOSource::check()'
CMakeFiles/compiz.dir/screen.cpp.o:(.rodata._ZTV11CompWatchFd[vtable for CompWatchFd]+0x18): undefined reference to `Glib::IOSource::dispatch(sigc::slot_base*)'
CMakeFiles/compiz.dir/screen.cpp.o:(.rodata._ZTI11CompWatchFd[typeinfo for CompWatchFd]+0x8): undefined reference to `typeinfo for Glib::IOSource'
CMakeFiles/compiz.dir/screen.cpp.o: In function `~CompWatchFd':
.../Desktop/Compiz/compiz/src/privatescreen.h:52: undefined reference to `Glib::IOSource::~IOSource()'
.../Desktop/Compiz/compiz/src/privatescreen.h:52: undefined reference to `Glib::IOSource::~IOSource()'
.../Desktop/Compiz/compiz/src/privatescreen.h:52: undefined reference to `Glib::IOSource::~IOSource()'
.../Desktop/Compiz/compiz/src/privatescreen.h:52: undefined reference to `Glib::IOSource::~IOSource()'
CMakeFiles/compiz.dir/eventsource.cpp.o: In function `CompEventSource::connect(sigc::slot<bool, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil> const&)':
.../Desktop/Compiz/compiz/src/eventsource.cpp:38: undefined reference to `Glib::Source::connect_generic(sigc::slot_base const&)'
CMakeFiles/compiz.dir/eventsource.cpp.o: In function `CompEventSource':
.../Desktop/Compiz/compiz/src/eventsource.cpp:44: undefined reference to `Glib::Source::Source()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:44: undefined reference to `Glib::PollFD::PollFD()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:49: undefined reference to `Glib::Source::set_priority(int)'
.../Desktop/Compiz/compiz/src/eventsource.cpp:50: undefined reference to `Glib::Source::add_poll(Glib::PollFD&)'
.../Desktop/Compiz/compiz/src/eventsource.cpp:51: undefined reference to `Glib::Source::set_can_recurse(bool)'
.../Desktop/Compiz/compiz/src/eventsource.cpp:53: undefined reference to `sigc::connection::~connection()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:54: undefined reference to `Glib::Source::~Source()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:44: undefined reference to `Glib::Source::Source()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:44: undefined reference to `Glib::PollFD::PollFD()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:49: undefined reference to `Glib::Source::set_priority(int)'
.../Desktop/Compiz/compiz/src/eventsource.cpp:50: undefined reference to `Glib::Source::add_poll(Glib::PollFD&)'
.../Desktop/Compiz/compiz/src/eventsource.cpp:51: undefined reference to `Glib::Source::set_can_recurse(bool)'
.../Desktop/Compiz/compiz/src/eventsource.cpp:53: undefined reference to `sigc::connection::~connection()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:54: undefined reference to `Glib::Source::~Source()'
CMakeFiles/compiz.dir/eventsource.cpp.o: In function `~CompEventSource':
.../Desktop/Compiz/compiz/src/eventsource.cpp:58: undefined reference to `Glib::Source::~Source()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:58: undefined reference to `Glib::Source::~Source()'
.../Desktop/Compiz/compiz/src/eventsource.cpp:58: undefined reference to `Glib::Source::~Source()'
CMakeFiles/compiz.dir/eventsource.cpp.o: In function `CompEventSource::callback()':
.../Desktop/Compiz/compiz/src/eventsource.cpp:65: undefined reference to `Glib::MainLoop::quit()'
CMakeFiles/compiz.dir/eventsource.cpp.o: In function `slot0<sigc::bound_mem_functor0<bool, CompEventSource> >':
/usr/include/sigc++-2.0/sigc++/functors/slot.h:451: undefined reference to `sigc::slot_base::slot_base(sigc::internal::slot_rep*)'
CMakeFiles/compiz.dir/eventsource.cpp.o:(.rodata._ZTI15CompEventSource[typeinfo for CompEventSource]+0x8): undefined reference to `typeinfo for Glib::Source'
collect2: ld returned 1 exit status
make[2]: *** [src/compiz] Error 1
make[1]: *** [src/CMakeFiles/compiz.dir/all] Error 2
make: *** [all] Error 2

```

How do I fix those errors?

---

### Post by artichoke on 2011-05-19
> **Andruk Tatum said:**
> 
How do I fix those errors?

-DCMAKE_CXX_FLAGS="`pkg-config --libs --cflags glib-2.0 glibmm-2.4`

---

### Post by PhosPhoton on 2011-06-07
I found a fix I think.
You do not have to add the flags you mentioned, all you need to do is install libgtkmm-2.4-dev

---


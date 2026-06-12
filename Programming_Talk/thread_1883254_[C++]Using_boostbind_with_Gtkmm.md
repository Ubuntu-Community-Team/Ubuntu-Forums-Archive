---
title: "[C++]Using boost::bind with Gtkmm"
date: 2011-11-18
forum: Programming Talk
---

### Post by ehmicky on 2011-11-18
Hi,

It looks like Gtkmm signals have some issues to be connected with boost::bind functors, when the callback returns a non-void value :
```
#include    <boost/bind.hpp>
#include    <gtkmm.h>

bool Fonc( Gtk::ScrollType, double )
{ return true; }        

int main(void)
{
    Gtk::HScrollbar scrollbar;
    scrollbar.signal_change_value().connect( boost::bind( Fonc, _1, _2 ) );
    return 0;    
}
```
```
$ g++ $(pkg-config gtkmm-3.0 --cflags --libs) d.cpp
/usr/include/sigc++-2.0/sigc++/functors/slot.h: In static member function ‘static T_return sigc::internal::slot_call2<T_functor, T_return, T_arg1, T_arg2>::call_it(sigc::internal::slot_rep*, typename sigc::type_trait<T_arg3>::take, typename sigc::type_trait<T_arg2>::take) [with T_functor = boost::_bi::bind_t<bool, bool (*)(Gtk::ScrollType, double), boost::_bi::list2<boost::arg<1>, boost::arg<2> > >, T_return = bool, T_arg1 = Gtk::ScrollType, T_arg2 = double, typename sigc::type_trait<T_arg3>::take = const Gtk::ScrollType&, typename sigc::type_trait<T_arg2>::take = const double&]’:
d.cpp:10:71:   instantiated from here
/usr/include/sigc++-2.0/sigc++/functors/slot.h:173:25: error: void value not ignored as it ought to be
/usr/include/sigc++-2.0/sigc++/adaptors/adaptor_trait.h: In member function ‘typename sigc::adaptor_functor<T_functor>::deduce_result_type<T_arg1, T_arg2>::type sigc::adaptor_functor<T_functor>::operator()(T_arg1, T_arg2) const [with T_arg1 = const Gtk::ScrollType&, T_arg2 = const double&, T_functor = boost::_bi::bind_t<bool, bool (*)(Gtk::ScrollType, double), boost::_bi::list2<boost::arg<1>, boost::arg<2> > >, typename sigc::adaptor_functor<T_functor>::deduce_result_type<T_arg1, T_arg2>::type = void]’:
d.cpp:10:71:   instantiated from here
/usr/include/sigc++-2.0/sigc++/adaptors/adaptor_trait.h:103:39: error: return-statement with a value, in function returning 'void' [-fpermissive]
```

I've found the source of the problem being Gtkmm using libsigc++ : sigc::slot cannot be constructed with functors returning a value, except with the functors defined in libsigc++.
The problem is solved by defining :
```
namespace sigc { SIGC_FUNCTORS_HAVE_RESULT_TYPE }
```

However, I'd like to know if there was a better way to solve this issue (and keep on using boost::bind instead of say sigc::mem_fun). Thank you !

---


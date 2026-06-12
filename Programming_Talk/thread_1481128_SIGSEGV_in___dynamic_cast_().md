---
title: "SIGSEGV in __dynamic_cast ()"
date: 2010-05-12
forum: Programming Talk
---

### Post by tbastian on 2010-05-12
I'm usually not one to post my compiler errors and let other people sort them out for me, but this one is really bothering me!

I keep getting a segfault in '__dynamic_cast () from /usr/lib/libstdc++.so.6'. I ran a debugger and looked at the back trace, and it doesn't seem to be coming from any of my subroutines!

I'll post the backtrace if anybody is interested.

```
#0  0x00ebe7bc in __dynamic_cast () from /usr/lib/libstdc++.so.6
#1  0x002dda62 in Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) ()
   from /usr/local/lib/libgtkmm-2.4.so.1
#2  0x006541f4 in IA__gtk_container_forall (container=0x822e320, callback=0x7c10b0 <child_location_foreach>, callback_data=0xbfffecc8)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkcontainer.c:1499
#3  0x007c11bb in child_location_foreach (child=0x822e320, data=0xbfffee08) at /build/buildd/gtk+2.0-2.18.3/gtk/gtktooltip.c:568
#4  0x006209b5 in gtk_box_forall (container=0x80f0178, include_internals=1, callback=0x7c10b0 <child_location_foreach>, callback_data=0xbfffee08)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkbox.c:1249
#5  0x002ddad7 in Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) ()
   from /usr/local/lib/libgtkmm-2.4.so.1
#6  0x006541f4 in IA__gtk_container_forall (container=0x80f0178, callback=0x7c10b0 <child_location_foreach>, callback_data=0xbfffee08)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkcontainer.c:1499
#7  0x007c11bb in child_location_foreach (child=0x80f0178, data=0xbfffef48) at /build/buildd/gtk+2.0-2.18.3/gtk/gtktooltip.c:568
#8  0x006209b5 in gtk_box_forall (container=0x822e2c8, include_internals=1, callback=0x7c10b0 <child_location_foreach>, callback_data=0xbfffef48)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkbox.c:1249
#9  0x002ddad7 in Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) ()
   from /usr/local/lib/libgtkmm-2.4.so.1
#10 0x006541f4 in IA__gtk_container_forall (container=0x822e2c8, callback=0x7c10b0 <child_location_foreach>, callback_data=0xbfffef48)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkcontainer.c:1499
#11 0x007c11bb in child_location_foreach (child=0x822e2c8, data=0xbffff064) at /build/buildd/gtk+2.0-2.18.3/gtk/gtktooltip.c:568
#12 0x0061c82d in gtk_bin_forall (container=0x80ec460, include_internals=1, callback=0x7c10b0 <child_location_foreach>, callback_data=0xbffff064)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkbin.c:128
#13 0x002dc50a in Gtk::Container::forall_vfunc(int, void (*)(_GtkWidget*, void*), void*) () from /usr/local/lib/libgtkmm-2.4.so.1
#14 0x002dda83 in Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) ()
   from /usr/local/lib/libgtkmm-2.4.so.1
#15 0x006541f4 in IA__gtk_container_forall (container=0x80ec460, callback=0x7c10b0 <child_location_foreach>, callback_data=0xbffff064)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtkcontainer.c:1499
#16 0x007c104b in find_widget_under_pointer (window=<value optimized out>, x=<value optimized out>, y=0xbffff0fc)
    at /build/buildd/gtk+2.0-2.18.3/gtk/gtktooltip.c:679
#17 0x007c2457 in find_topmost_widget_coords_from_event (event=0x80a2460) at /build/buildd/gtk+2.0-2.18.3/gtk/gtktooltip.c:724
#18 _gtk_tooltip_handle_event (event=0x80a2460) at /build/buildd/gtk+2.0-2.18.3/gtk/gtktooltip.c:1256
#19 0x006e1ee8 in IA__gtk_main_do_event (event=0x80a2460) at /build/buildd/gtk+2.0-2.18.3/gtk/gtkmain.c:1664
#20 0x00a4265a in gdk_event_dispatch (source=0x80a5100, callback=0, user_data=0x0) at /build/buildd/gtk+2.0-2.18.3/gdk/x11/gdkevents-x11.c:2369
#21 0x00d6ee88 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#22 0x00d72730 in ?? () from /lib/libglib-2.0.so.0
#23 0x00d72b9f in g_main_loop_run () from /lib/libglib-2.0.so.0
#24 0x006e2419 in IA__gtk_main () at /build/buildd/gtk+2.0-2.18.3/gtk/gtkmain.c:1218
#25 0x0030cc27 in Gtk::Main::run_impl() () from /usr/local/lib/libgtkmm-2.4.so.1
#26 0x0030cd48 in Gtk::Main::run(Gtk::Window&) () from /usr/local/lib/libgtkmm-2.4.so.1
#27 0x0805057c in main (argc=1, argv=0xbffff4b4) at src/Main.cc:22

```

EDIT: I don't expect anybody to solve this for me, but hopefully point me in the right direction/where I should start with it!

---

### Post by tbastian on 2010-05-14
I just figured out that it is triggered when I move my mouse over my canvas, but only after I've plotted 4 parameters on it... This confuses me more. It isn't triggered from any of my event callbacks...

---

### Post by dwhitney67 on 2010-05-14
Can you post the lines of code leading up to line 22 of Main.cc.

---

### Post by tbastian on 2010-05-14
```
int main ( int argc, char ** argv )
{
	Gtk::Main kit(argc, argv);
	
	MainWindow * mw = new MainWindow ( new FileReader());
	Gtk::Main::run ((Gtk::Window&) *mw );

	return 0;
}
```

I don't think its very helpful, but here it is anyway. I'm actually going through the process of running the program with a profiler (valgrind) and its looking like it has something to do with a call to 'realloc' somewhere.

```
==30454==    by 0x42A1DB1: ??? (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==30454==  Address 0x15880020 is 8 bytes before a block of size 2,689,016 alloc'd
==30454==    at 0x4024D12: realloc (vg_replace_malloc.c:476)
==30454==    by 0x8053AEE: ElasticArray<double>::to_array(int*) (ElasticArray.impl:132)
==30454==    by 0x80537DE: Parameter::to_array(int*) (Parameter.cc:59)
==30454==    by 0x805F564: Series::update() (Series.hpp:42)
==30454==    by 0x805ED1B: PlotPanel::add_series(Series) (PlotPanel.cc:77)
==30454==    by 0x805DCA9: PlotWindow::add_data(int, Packet*, int) (PlotWindow.cc:97)
==30454==    by 0x805A5A0: MainWindow::on_parameter_clicked(_GdkEventButton*, ParameterButton&) (MainWindow.cc:433)
==30454==    by 0x805CBB7: sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>::operator()(_GdkEventButton* const&, ParameterButton&) const (mem_fun.h:1917)
```

---

### Post by MadCow108 on 2010-05-14
can you provide a small runnable example reproducing the problem.

It is probably some bug in your code which just surfaces late or at a weird location.
That it crashes in malloc is often a sign for some memory corruption.
Try running it with the environment variable MALLOC_CHECK_=2 set.

---

### Post by tbastian on 2010-05-14
> **MadCow108 said:**
> can you provide a small runnable example reproducing the problem.

It is probably some bug in your code which just surfaces late or at a weird location.
That it crashes in malloc is often a sign for some memory corruption.
Try running it with the environment variable MALLOC_CHECK_=2 set.

MadCow, thanks for your input.

The piece of software I'm working on is not small, nor would it be easy to make one. (otherwise I would)

I'm not sure what you mean by 'Try running it with the environment variable MALLOC_CHECK_=2 set.' could you clarify this?

---

### Post by tbastian on 2010-05-14
As I stated earlier, I've been using valgrind to profile this bug, and it seems to complain on this, which strikes me as the most likely cause for the bug, but I can't see anything wrong with it...

```
// returns a standard array. The parameter 'first_element' is the first
// element the user wants, and size is the number of elements the user wants.
// If there isn't enough data, the first element is moved back. If size is
// greater than size to_array is called and a segmetation fault will likely
// occur
template <class T>
T * ElasticArray<T>::to_array ( int first_element, int size )
{
	if ( first_element + size > this -> size ())
		first_element = this -> size () - size;
	if ( size > this -> size () || first_element < 0 )
		return to_array ( &size );

	array = (T*) realloc ( array, sizeof ( T ) * size );
	assert ( array != NULL );

	for ( int i = first_element; i < first_element + size; i++ )
		array [ i - first_element ] = get ( i );

	return array;
}
```

and here is the output of valgrind regarding it:

```
==30678==  Address 0x18c80020 is 8 bytes before a block of size 3,817,552 alloc'd
==30678==    at 0x4024D12: realloc (vg_replace_malloc.c:476)
==30678==    by 0x8053AEE: ElasticArray<double>::to_array(int*) (ElasticArray.impl:132)
==30678==    by 0x80537DE: Parameter::to_array(int*) (Parameter.cc:59)
==30678==    by 0x805F57F: Series::update() (Series.hpp:43)
==30678==    by 0x805ED1B: PlotPanel::add_series(Series) (PlotPanel.cc:77)
==30678==    by 0x805DCA9: PlotWindow::add_data(int, Packet*, int) (PlotWindow.cc:97)
==30678==    by 0x805A5A0: MainWindow::on_parameter_clicked(_GdkEventButton*, ParameterButton&) (MainWindow.cc:433)
==30678==    by 0x805CBB7: sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>::operator()(_GdkEventButton* const&, ParameterButton&) const (mem_fun.h:1917)

```

---

### Post by soltanis on 2010-05-14
EDIT: Hold on, looks like I was wrong on the code segment I cited here earlier. Anyways, read down.

I'm sure that you obviously know:
```

int *ptr;
ptr = malloc(sizeof(int) * 40); /* 40 ints */

```

If I decide to write to my heap memory at ptr, then I should never write outside of the range of (ptr + 0) to (ptr + 39).

Valgrind is telling you that you're writing before the first element of your allocated memory if I read it correctly. Maybe you should check to make sure that first_element is always a positive integer (or perhaps it should be unsigned).

---

### Post by MadCow108 on 2010-05-14
> **tbastian said:**
> MadCow, thanks for your input.

The piece of software I'm working on is not small, nor would it be easy to make one. (otherwise I would)

I'm not sure what you mean by 'Try running it with the environment variable MALLOC_CHECK_=2 set.' could you clarify this?


execute your program like this:
MALLOC_CHECK_=2 ./your_executable

this changes to a debugging allocator (assuming you are using standard gnu allocator) which checks memory bounds, double free's etc.
the 2 means abort on error. So with an attached debugger you can inspect directly where it happens.
1 would only warn, 0 is off.

btw also useful is MALLOC_PERTURB_=somenumber, which initializes allocated memory to the specified number, very useful to find certain bugs like uninitialized use.

---

### Post by tbastian on 2010-05-14
soltanis:

I do indeed know that.
I was reading over my code, and realized I had actually posted the wrong function! Sorry for the confusion. Here is the one it quotes as being an issue.

```

// returns the entire ElasticArray as a standard array. The parameter 'size' will
// be set to the size of the returned array.
template <class T>
T * ElasticArray<T>::to_array ( int *arr_size )
{
	
	*arr_size = size();
	array = (T*) realloc ( array, sizeof ( T ) * ( *arr_size ) );
	assert ( array != NULL );

	for ( int i = plainArraySize; i < *arr_size; i++ ) {
		array [ i ] = get ( i );
	}

	plainArraySize = *arr_size;

	return array;
}
```

MadCow:

I'm assuming I'm using the gnu allocator. I haven't (intentionally) played with that.

I ran my program like you suggested I should, and got the same error at the same point, so I'm not sure what that means...

---

### Post by MadCow108 on 2010-05-14
the snippet of valgrind you posted only says the invalid whatever (please post the whole report...) occurs on memory allocated by that function.
It would be interesting to know what exactly access that memory wrongly (which is in the other part of the valgrind report).

to really help we need more information.

two generic notes:
array = (T*) realloc ( array, sizeof ( T ) * ( *arr_size ) );
assert ( array != NULL );

assert is no error handling function! it does nothing when compiled in release mode, so at least call exit or abort instead of assert.

why are you using C alloc functions instead of the c++ ones?
C alloc functions to not construct objects in the memory location!
For reserving memory without construction use the placement new operator
[http://www.parashift.com/c++-faq-lite/dtors.html#faq-11.10](http://www.parashift.com/c++-faq-lite/dtors.html#faq-11.10)

---

### Post by tbastian on 2010-05-14
Here is all the applicable valigrind output:

```
==32086== Invalid read of size 8
==32086==    at 0x8061F96: canvas_oPlot(double*, double*, int, PlottingContext_t*, LineContext_t*, canvas_t*) (canvas.c:970)
==32086==    by 0x80631E1: canvas_StripChart(double**, double**, int*, int*, int, PlottingContext_t*, LineContext_t*, canvas_t*) (canvas.c:1345)
==32086==    by 0x8064654: plot_Plot(plot_t*) (plot.c:330)
==32086==    by 0x8064A98: plot_Redraw(plot_t*) (plot.c:422)
==32086==    by 0x805F183: PlotPanel::add_series(Series) (PlotPanel.cc:129)
==32086==    by 0x805DCFD: PlotWindow::add_data(int, Packet*, int) (PlotWindow.cc:97)
==32086==    by 0x805A5F4: MainWindow::on_parameter_clicked(_GdkEventButton*, ParameterButton&) (MainWindow.cc:433)
==32086==    by 0x805CC0B: sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>::operator()(_GdkEventButton* const&, ParameterButton&) const (mem_fun.h:1917)
==32086==    by 0x805C8E9: sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::deduce_result_type<_GdkEventButton* const&, ParameterButton&, void, void, void, void, void>::type sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::operator()<_GdkEventButton* const&, ParameterButton&>(_GdkEventButton* const&, ParameterButton&) const (adaptor_trait.h:103)
==32086==    by 0x805C692: sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::deduce_result_type<_GdkEventButton* const&, void, void, void, void, void, void>::type sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::operator()<_GdkEventButton* const&>(_GdkEventButton* const&) (bind.h:1122)
==32086==    by 0x805C204: sigc::internal::slot_call1<sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>, bool, _GdkEventButton*>::call_it(sigc::internal::slot_rep*, _GdkEventButton* const&) (slot.h:137)
==32086==    by 0x42A1DB1: ??? (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==  Address 0xaa0caa8 is 8 bytes before a block of size 253,896 alloc'd
==32086==    at 0x4024D12: realloc (vg_replace_malloc.c:476)
==32086==    by 0x8053B42: ElasticArray<double>::to_array(int*) (ElasticArray.impl:133)
==32086==    by 0x8053816: Parameter::to_array(int*) (Parameter.cc:59)
==32086==    by 0x805F5B8: Series::update() (Series.hpp:42)
==32086==    by 0x805ED6F: PlotPanel::add_series(Series) (PlotPanel.cc:77)
==32086==    by 0x805DCFD: PlotWindow::add_data(int, Packet*, int) (PlotWindow.cc:97)
==32086==    by 0x805A5F4: MainWindow::on_parameter_clicked(_GdkEventButton*, ParameterButton&) (MainWindow.cc:433)
==32086==    by 0x805CC0B: sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>::operator()(_GdkEventButton* const&, ParameterButton&) const (mem_fun.h:1917)
==32086==    by 0x805C8E9: sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::deduce_result_type<_GdkEventButton* const&, ParameterButton&, void, void, void, void, void>::type sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::operator()<_GdkEventButton* const&, ParameterButton&>(_GdkEventButton* const&, ParameterButton&) const (adaptor_trait.h:103)
==32086==    by 0x805C692: sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::deduce_result_type<_GdkEventButton* const&, void, void, void, void, void, void>::type sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::operator()<_GdkEventButton* const&>(_GdkEventButton* const&) (bind.h:1122)
==32086==    by 0x805C204: sigc::internal::slot_call1<sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>, bool, _GdkEventButton*>::call_it(sigc::internal::slot_rep*, _GdkEventButton* const&) (slot.h:137)
==32086==    by 0x42A1DB1: ??? (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086== 
==32086== Invalid read of size 8
==32086==    at 0x8061FFA: canvas_oPlot(double*, double*, int, PlottingContext_t*, LineContext_t*, canvas_t*) (canvas.c:976)
==32086==    by 0x80631E1: canvas_StripChart(double**, double**, int*, int*, int, PlottingContext_t*, LineContext_t*, canvas_t*) (canvas.c:1345)
==32086==    by 0x8064654: plot_Plot(plot_t*) (plot.c:330)
==32086==    by 0x8064A98: plot_Redraw(plot_t*) (plot.c:422)
==32086==    by 0x805F183: PlotPanel::add_series(Series) (PlotPanel.cc:129)
==32086==    by 0x805DCFD: PlotWindow::add_data(int, Packet*, int) (PlotWindow.cc:97)
==32086==    by 0x805A5F4: MainWindow::on_parameter_clicked(_GdkEventButton*, ParameterButton&) (MainWindow.cc:433)
==32086==    by 0x805CC0B: sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>::operator()(_GdkEventButton* const&, ParameterButton&) const (mem_fun.h:1917)
==32086==    by 0x805C8E9: sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::deduce_result_type<_GdkEventButton* const&, ParameterButton&, void, void, void, void, void>::type sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::operator()<_GdkEventButton* const&, ParameterButton&>(_GdkEventButton* const&, ParameterButton&) const (adaptor_trait.h:103)
==32086==    by 0x805C692: sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::deduce_result_type<_GdkEventButton* const&, void, void, void, void, void, void>::type sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::operator()<_GdkEventButton* const&>(_GdkEventButton* const&) (bind.h:1122)
==32086==    by 0x805C204: sigc::internal::slot_call1<sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>, bool, _GdkEventButton*>::call_it(sigc::internal::slot_rep*, _GdkEventButton* const&) (slot.h:137)
==32086==    by 0x42A1DB1: ??? (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==  Address 0x9bb6ef0 is 8 bytes before a block of size 253,896 alloc'd
==32086==    at 0x4024D12: realloc (vg_replace_malloc.c:476)
==32086==    by 0x8053B42: ElasticArray<double>::to_array(int*) (ElasticArray.impl:133)
==32086==    by 0x8053816: Parameter::to_array(int*) (Parameter.cc:59)
==32086==    by 0x805F5D3: Series::update() (Series.hpp:43)
==32086==    by 0x805ED6F: PlotPanel::add_series(Series) (PlotPanel.cc:77)
==32086==    by 0x805DCFD: PlotWindow::add_data(int, Packet*, int) (PlotWindow.cc:97)
==32086==    by 0x805A5F4: MainWindow::on_parameter_clicked(_GdkEventButton*, ParameterButton&) (MainWindow.cc:433)
==32086==    by 0x805CC0B: sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>::operator()(_GdkEventButton* const&, ParameterButton&) const (mem_fun.h:1917)
==32086==    by 0x805C8E9: sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::deduce_result_type<_GdkEventButton* const&, ParameterButton&, void, void, void, void, void>::type sigc::adaptor_functor<sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&> >::operator()<_GdkEventButton* const&, ParameterButton&>(_GdkEventButton* const&, ParameterButton&) const (adaptor_trait.h:103)
==32086==    by 0x805C692: sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::deduce_result_type<_GdkEventButton* const&, void, void, void, void, void, void>::type sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>::operator()<_GdkEventButton* const&>(_GdkEventButton* const&) (bind.h:1122)
==32086==    by 0x805C204: sigc::internal::slot_call1<sigc::bind_functor<-1, sigc::bound_mem_functor2<bool, MainWindow, _GdkEventButton*, ParameterButton&>, ParameterButton&, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil, sigc::nil>, bool, _GdkEventButton*>::call_it(sigc::internal::slot_rep*, _GdkEventButton* const&) (slot.h:137)
==32086==    by 0x42A1DB1: ??? (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086== 
==32086== Invalid read of size 4
==32086==    at 0x4DD37BC: __dynamic_cast (in /usr/lib/libstdc++.so.6.0.13)
==32086==    by 0x41EDA61: Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==    by 0x45651F3: gtk_container_forall (gtkcontainer.c:1499)
==32086==    by 0x46D21BA: child_location_foreach (gtktooltip.c:568)
==32086==    by 0x45319B4: gtk_box_forall (gtkbox.c:1249)
==32086==    by 0x41EDAD6: Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==    by 0x45651F3: gtk_container_forall (gtkcontainer.c:1499)
==32086==    by 0x46D21BA: child_location_foreach (gtktooltip.c:568)
==32086==    by 0x45319B4: gtk_box_forall (gtkbox.c:1249)
==32086==    by 0x41EDAD6: Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==    by 0x45651F3: gtk_container_forall (gtkcontainer.c:1499)
==32086==    by 0x46D21BA: child_location_foreach (gtktooltip.c:568)
==32086==  Address 0x20674818 is not stack'd, malloc'd or (recently) free'd
==32086== 
==32086== 
==32086== Process terminating with default action of signal 11 (SIGSEGV)
==32086==  Access not within mapped region at address 0x20674818
==32086==    at 0x4DD37BC: __dynamic_cast (in /usr/lib/libstdc++.so.6.0.13)
==32086==    by 0x41EDA61: Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==    by 0x45651F3: gtk_container_forall (gtkcontainer.c:1499)
==32086==    by 0x46D21BA: child_location_foreach (gtktooltip.c:568)
==32086==    by 0x45319B4: gtk_box_forall (gtkbox.c:1249)
==32086==    by 0x41EDAD6: Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==    by 0x45651F3: gtk_container_forall (gtkcontainer.c:1499)
==32086==    by 0x46D21BA: child_location_foreach (gtktooltip.c:568)
==32086==    by 0x45319B4: gtk_box_forall (gtkbox.c:1249)
==32086==    by 0x41EDAD6: Gtk::Container_Class::forall_vfunc_callback(_GtkContainer*, int, void (*)(_GtkWidget*, void*), void*) (in /usr/local/lib/libgtkmm-2.4.so.1.1.0)
==32086==    by 0x45651F3: gtk_container_forall (gtkcontainer.c:1499)
==32086==    by 0x46D21BA: child_location_foreach (gtktooltip.c:568)
==32086==  If you believe this happened as a result of a stack
==32086==  overflow in your program's main thread (unlikely but
==32086==  possible), you can try to increase the size of the
==32086==  main thread stack using the --main-stacksize= flag.
==32086==  The main thread stack size used in this run was 8388608.
==32086== 
==32086== HEAP SUMMARY:
==32086==     in use at exit: 57,850,624 bytes in 37,795 blocks
==32086==   total heap usage: 530,742 allocs, 492,947 frees, 633,510,342 bytes allocated
==32086== 
==32086== LEAK SUMMARY:
==32086==    definitely lost: 3,884 bytes in 12 blocks
==32086==    indirectly lost: 8,892 bytes in 423 blocks
==32086==      possibly lost: 8,656,444 bytes in 25,177 blocks
==32086==    still reachable: 49,181,404 bytes in 12,183 blocks
==32086==         suppressed: 0 bytes in 0 blocks
==32086== Rerun with --leak-check=full to see details of leaked memory
==32086== 
==32086== For counts of detected and suppressed errors, rerun with: -v
==32086== Use --track-origins=yes to see where uninitialised values come from
==32086== ERROR SUMMARY: 412 errors from 85 contexts (suppressed: 199 from 14)
Killed

```

I'm using realloc instead of new because sofar as I know, you can't do a 'realloc' equivalent with new. (the placement new example isn't really what I want). Also, in this case I'm just creating an array of doubles, not high level objects.

---

### Post by MadCow108 on 2010-05-14
in that case you should be using vectors (or fixed size arrays provided by e.g. boost and c++0x).
they are also guaranteed to use the same structures as classic C arrays under the hood, so you have full compatibility with C code by using T * carray = &vec[0];

and the problem can very well be in the plot functions, you should have a look at these.

---

### Post by tbastian on 2010-05-17
I found the reason for my program crashing. It turned out to be an array of characters that was overrun by the time I had plotted 4 parameters because the title had gotten too long!

As for the realloc issues, they're still there and I'm looking into them (I'll post when/if I find a solution). Thanks everybody for your help, it was much appreciated!

---

### Post by dwhitney67 on 2010-05-17
I recall you mentioning earlier about your issues with realloc() and C++.

I believe this is all you need:
```

template <typename T>
T* realloc(T*& mem, const size_t oldsize, const size_t newsize)
{
   if (newsize <= oldsize) return mem;

   T* tmp = new T[newsize];

   std::copy(mem, mem + oldsize, tmp);

   delete [] mem;

   mem = tmp;

   return mem;
}

```

Typical usage:
```

int* array = new int[10];

//...

array = realloc(array, 10, 20);

//...

```
Now, in as far as arrays are concerned, in C++ it would be much easier to utilize an STL vector.

---

### Post by tbastian on 2010-05-17
> **dwhitney67 said:**
> 
Now, in as far as arrays are concerned, in C++ it would be much easier to utilize an STL vector.

Thanks, I think I'll implement that code. As for why I'm not using vectors, its because I've specifically designed my class for frequent expansion, and making vectors bigger is more overhead than I'm willing to deal with. (I have no idea how much data I want to store. Could be anywhere between 100 and 500000 data points!)

---

### Post by MadCow108 on 2010-05-17
vectors are pretty efficient for a large range of sizes.
normally they double their size when needed. This is very often a good approach. Depending on implementation the vector may even use other heuristics for more efficient growing depending on situation.

also library implementations may include all kind of optimizations which are hard to implement. e.g. this:
[http://gcc.gnu.org/ml/libstdc++/2002-04/msg00105.html](http://gcc.gnu.org/ml/libstdc++/2002-04/msg00105.html)

If that is not good enough you can always manually resize your vector with resize or reserve

the overhead is vectors is negligible and hardly higher than C arrays. a vector is only a 3 word structure, pointer + size + capacity. The same amount is needed for expandable C arrays-

maybe you should also consider a list instead of a vector, they don't have resizing issues at all (but of course with other drawbacks).

---


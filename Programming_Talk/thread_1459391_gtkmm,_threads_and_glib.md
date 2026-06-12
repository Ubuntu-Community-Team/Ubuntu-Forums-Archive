---
title: "gtkmm, threads and glib"
date: 2010-04-21
forum: Programming Talk
---

### Post by iochinome on 2010-04-21
hey guys, so i am writing a program that needs to use gtkmm as a thread, but for some reason, i keep getting glib errors during runtime. i have heard that you need to initialize glib somehow when using gtkmm and threads... does anyone know how to do this? what should i do?

thanks!

---

### Post by iochinome on 2010-04-21
you know what, scratch that, i think i have solved my own problem. i just had to call 

	Glib::thread_init();

right before the 

	Gtk::Main kit(my_gui_data->argc, my_gui_data->argv);

call. another, different issue popped up though- now, my threads do not run simultaneously. in fact, the gtkmm thread (which i initiate first, btw) continues until it closes, then the other thread begins until it closes. any ideas what is going on? thanks!

---

### Post by MadCow108 on 2010-04-21
some code example would be helpful

---

### Post by iochinome on 2010-04-22
here is the code of the window:

```
void *gui_routine(void * threadarg) {

	struct gui_thread_data 		*my_gui_data;

	my_gui_data = (struct gui_thread_data *) threadarg;

	Glib::thread_init();

	Gtk::Main kit(my_gui_data->argc, my_gui_data->argv);

	GUIwindow window;
	//Shows the window and returns when it is closed.
	Gtk::Main::run(window);

	return 0;
}
```

and i just summon that window right after another thread.
i am doing the other thread with opencv, to be perfectly clear-
and, as i now understand, the first thread only stops in execution once it hits the 
'cvWaitKey(20)'
function. (it executes until then, then stops, until i close the window of the gtkmm thread)

any ideas??
thanks!

---

### Post by MadCow108 on 2010-04-22
how are you starting the threads?

Are you also using glib threads for that?
is that the thread routine?
if yes then you must call Glib::thread_init(); _before_ you start any threads
one of the first things in main is usually a good place

---

### Post by iochinome on 2010-04-23
hmmm... no, I am using pthreads for it. here is what my starting the threads looks like:

(this is all in main)
```
	iret_2 = pthread_create(&thread_capture, 	NULL, capture_routine, 	 NULL);
	iret_1 = pthread_create(&thread_gui, 		NULL, gui_routine,		 (void*) &gui_thread_data_array[1]);


	pthread_join(thread_capture,	NULL);
	pthread_join(thread_gui,		NULL);

```

i tried it with glib in the main function before doing any of this, and it was the same. thanks!

---

### Post by MadCow108 on 2010-04-23
probably gtk uses some kind of global lock to protect itself (especially the main event loop) and thus singlethreads your application.
You'll have to read up about gtk and multithreaded applications.
Also maybe your gtk implementation is not compiled with thread support?

I guess its also not a good idea to mix pthreads and glib threads

---


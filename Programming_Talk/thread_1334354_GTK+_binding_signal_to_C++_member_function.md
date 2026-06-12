---
title: "GTK+ binding signal to C++ member function"
date: 2009-11-22
forum: Programming Talk
---

### Post by bluedalmatian on 2009-11-22
Ive encapsulated a GTK+ window and all its widgets into a class called SubsystemEditWindow and I want an instance method / member function called doSave() to be called when the Save button in the window is clicked.

If I do g_signal_connect(G_OBJECT(this->savebutton),"clicked",G_CALLBACK(&SubsystemEditWindow::doSave),NULL);

it calls the function code but not in the object instance concerned - all instance varaibles are set to null!

is there a way to make it point to a particular instance? i tried

g_signal_connect(G_OBJECT(this->savebutton),"clicked",G_CALLBACK(&this->doSave),NULL);

but that wont compile.

Thanks

---

### Post by dwhitney67 on 2009-11-22
To call a non-static class function/method, you need to convey to GTK a pointer to the instance of the class.

I am not familiar with GTK, so I am not sure how to do this.  From this [webpage]("http://library.gnome.org/devel/gobject/unstable/gobject-Signals.html"), it appears that the GTK-function you are attempting to use has a signature as follows:
```

#define g_signal_connect (instance, detailed_signal, c_handler, data)

```

P.S.  Upon doing a little more research, it would seem that you need to pass your object's instance as the 'data' parameter, instead of NULL, as you are passing now.  The callback function needs to be declared as static.  Once inside it, use the 'data' parameter as the instance to your object.

```

class MyClass
{
public:
   MyClass()
   {
      g_signal_connect(G_OBJECT(this->savebutton), "clicked", G_CALLBACK(&this->doSaveCallback), this);
   }

   static void doSaveCallback(GstElement* element, GstPad* pad, MyClass* data)
   {
      data->doSave();
   }
private:
   void doSave()
   {
      ...
   }
};

```

---

### Post by nvteighen on 2009-11-22
Er... wouldn't be better to use GTKmm (GTK+ C++ binding) instead?

---

### Post by bluedalmatian on 2009-11-23
thats great thanks. i guess gtkmm might be a better long term solution but ill stick with gtk+ for now

---

### Post by bluedalmatian on 2009-11-26
Is it possible to mix gtkmm and gtk+ in the same program? I donbt really want to have to re-write everything else to use gtkmm.

im thinking about the calls to Gtk::Main::run(); versus gtk_main()

---


---
title: "GTKmm: Porting to GTK3"
date: 2011-11-02
forum: Programming Talk
---

### Post by fallenshadow on 2011-11-02
Im currently porting my GTK2 codebase to GTK3 with GTKmm. I tried compiling and reduced my errors from 35 to 22 and now to 11.

I really don't know how to fix this section of code, so I would appreciate some help on it.

[PHP]app->size_allocate().connect(sigc::mem_fun(*this, &mainWindow::on_size_allocate));

void mainWindow::on_size_allocate(Gtk::Requisition* req)
{
	std::cout << "in on_size_request" << std::endl;
	int width, height;
	app->get_size(width, height);
	
	Gtk::HPaned* pane;
	refBuilder->get_widget("hpaned1", pane);
	pane->set_position(width - 200);
}[/PHP]


This may be of help: [http://developer.gnome.org/gtkmm/stable/deprecated.html]("http://developer.gnome.org/gtkmm/stable/deprecated.html")

> Errors:
mainwindow.cc: In member function ‘Gtk::Window* mainWindow::init()’:
mainwindow.cc:74:21: error: no matching function for call to ‘Gtk::Window::size_allocate()’
mainwindow.cc:74:21: note: candidate is:
/usr/include/gtkmm-3.0/gtkmm/widget.h:460:8: note: void Gtk::Widget::size_allocate(const Allocation&)
/usr/include/gtkmm-3.0/gtkmm/widget.h:460:8: note:   candidate expects 1 argument, 0 provided


Im sure its something to do with the function call expecting another parameter and hpaned should be paned. I could use a helping hand on this one.

---

### Post by cgroza on 2011-11-02
That function expects an Allocation object. I tried to google it and all i had was trash.
It seems to me that you have to create or get an Allocation object somehow.
I would look more careful in the API for methods that return Allocation.

---

### Post by fallenshadow on 2011-11-10
Here is an updated attempt... however I might not need this code anymore as I have partially solved the problem within the Glade file.

[PHP]
app->size_allocate(r).connect(sigc::mem_fun(*this, &mainWindow::on_size_allocate));

void mainWindow::on_size_allocate(Gtk::Allocation& r)
{
	set_allocation(r);
	int width, height;	
	app->get_size(width, height);		
	Gtk::HPaned* pane;	
	refBuilder->get_widget("hpaned1", pane);	
	pane->set_position(width - 200);	
}
[/PHP]

I still would prefer to have this working as it provides alot more control over the width of my hpane.

Error message:
> 
"mainwindow.cc:74:21: error: &#8216;r&#8217; was not declared in this scope"


If anyone knows what the problem is then please let me know!

---

### Post by crdlb on 2011-11-10
> **fallenshadow said:**
> 
[PHP]
app->size_allocate(r).connect(sigc::mem_fun(*this, &mainWindow::on_size_allocate));
[/PHP]


I'm not very familiar with gtkmm, but it seems the signal is 'signal_size_allocate', not just 'size_allocate'

The actual error is probably due to that 'r', which shouldn't be there.

---

### Post by pbrane on 2011-11-11
> **fallenshadow said:**
> Here is an updated attempt... however I might not need this code anymore as I have partially solved the problem within the Glade file.

[PHP]
app->size_allocate(r).connect(sigc::mem_fun(*this, &mainWindow::on_size_allocate));

void mainWindow::on_size_allocate(Gtk::Allocation& r)
{
	set_allocation(r);
	int width, height;	
	app->get_size(width, height);		
	Gtk::HPaned* pane;	
	refBuilder->get_widget("hpaned1", pane);	
	pane->set_position(width - 200);	
}
[/PHP]

I still would prefer to have this working as it provides alot more control over the width of my hpane.

Error message:


If anyone knows what the problem is then please let me know!
crdlb is right about the signal name. So... for posterity:

[PHP]
app->signal_size_allocate().connect(sigc::mem_fun(*this, &mainWindow::on_size_allocate));

void mainWindow::on_size_allocate(Gtk::Allocation& allocation)
{
  //
  // make any changes to the Gtk::Allocation structure here
  //
  set_allocation(allocation);
	
  Gtk::HPaned* pane;
  refBuilder->get_widget("hpaned1", pane);
  // use the allocated width
  pane->set_position(allocation.get_width() - 200);
}

[/PHP]

---


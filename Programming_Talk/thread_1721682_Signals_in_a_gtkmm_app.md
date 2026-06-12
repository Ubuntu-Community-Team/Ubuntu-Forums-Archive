---
title: "Signals in a gtkmm app"
date: 2011-04-04
forum: Programming Talk
---

### Post by vivichrist on 2011-04-04
```
class Permutations : public Window
{
		Button *button;
		Gtk::TextView *listview, *inputline;
		
		string startstring;
		int length;
		typedef std::map <string, int> MapType;
		MapType data;
	protected:
		void findPermutations(string initString, int increment);
		virtual void on_activate(ImageMenuItem *menu);
		virtual void on_button_clicked();
		virtual void destroy_notify_();
		virtual void set_manage();
	public:
		Permutations();
		~Permutations();
};
Permutations::Permutations() 
{
...
button.signal_clicked().connect(sigc::mem_fun(*this, &Permutations::on_button_clicked));
...
};
```

the above doesn't seem to work for me...?

```
Permutations.cpp:69: error: request for member ‘signal_clicked’ in ‘((Permutations*)this)->Permutations::button’, which is of non-class type ‘Gtk::Button*’
```

---

### Post by SledgeHammer_999 on 2011-04-04
'button' is a pointer. Use **button->signal_clicked().connect()** instead of **button.signal_clicked().connect()**

---

### Post by vivichrist on 2011-04-04
yes I just noticed after posting ... sorry

---

### Post by vivichrist on 2011-04-04
> *** glibc detected *** ./Permutations: double free or corruption (out): 0x00007ffffbe70e50 ***

BTW any idea what this means?

---

### Post by SledgeHammer_999 on 2011-04-05
You delete the same pointer twice or in other words "you free the same memory block twice".

You need to provide more code if you want help for this too.

---

### Post by vivichrist on 2011-04-11
yes, basically I was trying to delete a member variable that was not created by new. sorted that mess out. I'm coming from a java programming perspective and memory management is new and confusing. thank you for the reply. I am currently reading up on the subject so I don't create leaky code and can avoid these embarrassingly obvious questions in future.

---

### Post by vivichrist on 2011-04-19
as you can see I am now trying to make a basic drawing program but I get a 'Could not attach to process' error and:

> Memory status: size: 149213184 vsize: 149213184 resident: 12980224 share: 10674176 rss: 12980224 rss_rlim: 18446744073709551615
CPU usage: start_time: 1303268762 rtime: 3 utime: 3 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100



----------- .xsession-errors ---------------------
** (gnome-session:1643): DEBUG: GsmXSMPClient:   RestartCommand = '/usr/bin/xterm' '-xtsessionID' '10f61e27731111f15f130326876314465100000016430118' '-e' '/bin/sh ./geany_run_script.sh' 
** (gnome-session:1643): DEBUG: GsmXSMPClient:   UserID = 'vivy'
** (gnome-session:1643): DEBUG: GsmXSMPClient:   ProcessID = '17632'
** (gnome-session:1643): DEBUG: GsmXSMPClient: Client '0x1ccbe70 [/usr/bin/xterm 10f61e27731111f15f130326876314465100000016430118]' received SaveYourselfDone(success = True)
** (gnome-session:1643): DEBUG: GsmManager: Response from end session request: is-ok=1 do-last=0 cancel=0 reason=
** (gnome-session:1643): DEBUG: GsmXsmpServer: sms_error_handler (0x1ccc400, FALSE, 3, 9, 32771, 0)
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
--------------------------------------------------

```
#include <stdio.h>
#include <iostream>
#include <string>
// #include "config.h"
#include <giomm/file.h>
#include <gtkmm/main.h>
#include <gtkmm/stock.h>
#include <gtkmm/window.h>
#include <gtkmm/drawingarea.h>
#include <gtkmm/scrolledwindow.h>
#include <gtkmm/menu.h>
#include <gtkmm/menubar.h>
#include <gtkmm/menuitem.h>
#include <gtkmm/toolbar.h>
#include <gtkmm/box.h>
#include <gtkmm/buttonbox.h>
#include <gtkmm/filechooserdialog.h>
#include <gtkmm/messagedialog.h>
#include <giomm/file.h>
#include <giomm/cancellable.h>
#include <giomm/dataoutputstream.h>
#include <giomm/fileoutputstream.h>
#include <glibmm/iochannel.h>
#include <cairommconfig.h>
#include <cairomm/context.h>
#include <cairomm/surface.h>


using namespace Glib;
using namespace Gtk;
using namespace std;

class DrawingApp : public Window
{
	Gtk::DrawingArea * dr;
	Cairo::RefPtr<Cairo::Context> cr;
	
	public:
	
		DrawingApp(){
			// string filename = "image.svg";
	    double width = 600;
	    double height = 400;
			dr = manage(new DrawingArea());
	    [COLOR="Red"]cr = dr->get_window()->create_cairo_context();[/COLOR]
	
			VBox * top = manage(new VBox(false, 2));
			Menu * aMenu = manage(new Menu());
			MenuBar * menuBar = manage(new MenuBar());
			MenuItem * aMenuItem = manage(new MenuItem("File"));
			ImageMenuItem * mitem = manage(new ImageMenuItem(Stock::SAVE));
			ImageMenuItem * mitem2 = manage(new ImageMenuItem(Stock::QUIT));
			
			hide();
			set_title("DrawingApp");
			set_default_size(width, height);
			mitem->set_label("Save");
			mitem2->set_label("Quit");
			// mitem->signal_activate().connect(sigc::mem_fun(*this, &DrawingApp::on_activate_save));
			// mitem2->signal_activate().connect(sigc::mem_fun(*this, &DrawingApp::on_activate_quit));
			Toolbar * toolbar = manage(new Toolbar());
			ToolButton * tb1 = manage(new ToolButton("buttn 1"));
			ToolButton * tb2 = manage(new ToolButton("buttn 2"));
			ToolButton * tb3 = manage(new ToolButton("buttn 3"));
			ToolButton * tb4 = manage(new ToolButton("buttn 4"));
			
			toolbar->append(*tb1);
			toolbar->append(*tb2);
			toolbar->append(*tb3);
			toolbar->append(*tb4);
			aMenu->append(*mitem);
			aMenu->append(*mitem2);
			aMenuItem->set_submenu(*aMenu);
			menuBar->append(*aMenuItem);
	
			top->pack_start(*menuBar, false, false, 0);
			top->pack_start(*toolbar, false, false, 0);
			top->pack_start(*dr, true, true, 2);
			add(*top);
			show_all(); // display
	
		};
		~DrawingApp(){
		// delete cr;
		delete dr;
		};
		void on_button1_clicked(){
	
		};
		void on_activate_save(){
	
		};
		void on_activate_quit(){
	
		};
	
};

int main(int argc, char *argv[]) {
	Main kit(argc, argv);
	DrawingApp d;
	Main::run(d);
  return EXIT_SUCCESS;
};

```

---

### Post by vivichrist on 2011-04-20
oops ok not so obvious as to the order of operations the line in red must be done after show_all();

---

### Post by vivichrist on 2011-04-20
ok I really don't know why this crashes:

```
System: Linux 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64
X Vendor: The X.Org Foundation
X Vendor Release: 10900000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Turrican
Icon Theme: Elegant-AwOken
GTK+ Modules: gnomesegvhandler

Memory status: size: 154619904 vsize: 154619904 resident: 18128896 share: 15265792 rss: 18128896 rss_rlim: 18446744073709551615
CPU usage: start_time: 1303341128 rtime: 8 utime: 5 stime: 3 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100



----------- .xsession-errors ---------------------
** (gnome-session:1643): DEBUG: GsmXSMPClient:   RestartCommand = '/usr/bin/xterm' '-xtsessionID' '10f61e27731111f15f130334112868093400000016430167' '-e' '/bin/sh ./geany_run_script.sh' 
** (gnome-session:1643): DEBUG: GsmXSMPClient:   UserID = 'vivy'
** (gnome-session:1643): DEBUG: GsmXSMPClient:   ProcessID = '2817'
** (gnome-session:1643): DEBUG: GsmXSMPClient: Client '0x1ccbf10 [/usr/bin/xterm 10f61e27731111f15f130334112868093400000016430167]' received SaveYourselfDone(success = True)
** (gnome-session:1643): DEBUG: GsmManager: Response from end session request: is-ok=1 do-last=0 cancel=0 reason=
** (gnome-session:1643): DEBUG: GsmXsmpServer: sms_error_handler (0x1cbdb30, FALSE, 3, 9, 32771, 0)
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
** (gnome-session:1643): DEBUG: GsmDBusClient: obj_path=/org/freedesktop/DBus interface=org.freedesktop.DBus method=NameOwnerChanged
--------------------------------------------------
```


```
// #include "TreeShape.h"
#include <stdio.h>
#include <iostream>
#include <cmath>
#include <string>
#include <list>
#include <gdkmm.h>
#include <giomm/file.h>
#include <gtkmm/main.h>
#include <gtkmm/stock.h>
#include <gtkmm/window.h>
#include <gtkmm/drawingarea.h>
#include <gtkmm/scrolledwindow.h>
#include <gtkmm/menu.h>
#include <gtkmm/menubar.h>
#include <gtkmm/menuitem.h>
#include <gtkmm/toolbar.h>
#include <gtkmm/box.h>
#include <gtkmm/buttonbox.h>
#include <gtkmm/filechooserdialog.h>
#include <gtkmm/messagedialog.h>
#include <giomm/file.h>
#include <giomm/cancellable.h>
#include <giomm/dataoutputstream.h>
#include <giomm/fileoutputstream.h>
#include <glibmm/iochannel.h>
#include <glibmm/refptr.h>


using namespace Glib;
using namespace Gtk;
using namespace std;


class TreeShape // : public Plant
{
    double x, y, length;
    double branchAngle;
    double shrinkage;
    int numBranches;
    Glib::RefPtr<Gdk::Window> canvas;
    Glib::RefPtr<Gdk::GC> gc;
    Gdk::Color fgcol, bgcol;
    bool show_draw;
    
		void draw(double x, double y, double dist, double ang, int branches, double propor){
			if (show_draw){
				
			};/* Draw a line from (x,y) of length dist at angle ang */
			// double rnddist = dist*((1-branches*0.1d)*Math.random()+(branches*0.1d));
			double newx = x + dist*cos(ang);
			double newy = y + dist*sin(ang);
			gc->set_foreground(fgcol);
			canvas->draw_line(gc, (int)x, (int)y, (int)newx, (int)newy);
			int cap = fmin(branches, numBranches);
			if (dist>3+(5.0/length))
				for (int i=1;i<=cap;i++)
					draw(newx, newy, dist*shrinkage, ang-(branchAngle*propor*i*(i%2>0?-1:1)), branches+1, propor);
		};
		
	public:
		TreeShape(Glib::RefPtr<Gdk::Window> w){
			branchAngle = M_PI/3 * (0.1+rand()*0.000012207);
			shrinkage = 0.5 + rand()*0.0000030518;
			numBranches = 5+rand()*0.000091553;
			canvas = w;
			gc = Gdk::GC::create();
			bgcol.set_rgb(65535, 65535, 65535);
			gc->set_background(bgcol);
			fgcol.set_rgb(rand(), rand(), rand());
			gc->set_foreground(fgcol);
			x = (double)(rand()%900);
			y = (double)(400.0 + rand()%100);
			length = (double)(50 +(rand()%150));
			show_draw=true;
			draw(x, y, length, -M_PI/2, 2, 1.0);
		};
		
		~TreeShape(){};
		
		void grow(double pptn){
			draw(x, y, length*pptn, -M_PI/2, 2, pptn);
			show_draw=false;
		};
};

class DrawingApp : public Window
{
	DrawingArea dr;
	list<TreeShape> ls;
	public:
	
		DrawingApp(){
			// string filename = "image.svg";
	    double width = 600;
	    double height = 400;
			hide();
			// initialize
			VBox * top = manage(new VBox(false, 2));
			Menu * aMenu = manage(new Menu());
			MenuBar * menuBar = manage(new MenuBar());
			MenuItem * aMenuItem = manage(new MenuItem("File"));
			ImageMenuItem * mitem = manage(new ImageMenuItem(Stock::SAVE));
			ImageMenuItem * mitem2 = manage(new ImageMenuItem(Stock::QUIT));
			// configure
			set_title("DrawingApp");
			set_default_size(width, height);
			mitem->set_label("Save");
			mitem2->set_label("Quit");
			mitem->signal_activate().connect(sigc::mem_fun(*this,
					&DrawingApp::on_activate_save));
			mitem2->signal_activate().connect(sigc::mem_fun(*this,
					&DrawingApp::on_activate_quit));
			Toolbar * toolbar = manage(new Toolbar());
			ToolButton * tb1 = manage(new ToolButton("Plant a Tree"));
			tb1->signal_clicked().connect(sigc::mem_fun(*this,
					&DrawingApp::on_button1_clicked));
			ToolButton * tb2 = manage(new ToolButton("buttn 2"));
			tb2->signal_clicked().connect(sigc::mem_fun(*this,
					&DrawingApp::on_button2_clicked));
			ToolButton * tb3 = manage(new ToolButton("buttn 3"));
			tb3->signal_clicked().connect(sigc::mem_fun(*this,
					&DrawingApp::on_button3_clicked));
			ToolButton * tb4 = manage(new ToolButton("buttn 4"));
			tb4->signal_clicked().connect(sigc::mem_fun(*this,
					&DrawingApp::on_button4_clicked));
			// load into window
			toolbar->append(*tb1);
			toolbar->append(*tb2);
			toolbar->append(*tb3);
			toolbar->append(*tb4);
			aMenu->append(*mitem);
			aMenu->append(*mitem2);
			aMenuItem->set_submenu(*aMenu);
			menuBar->append(*aMenuItem);
			top->pack_start(*menuBar, false, false, 0);
			top->pack_start(*toolbar, false, false, 0);
			top->pack_start(dr, true, true, 2);
			add(*top); show_all();dr.show(); // display
			Gdk::Color *c = new Gdk::Color();
		  c->set_grey(65535);
	    dr.get_window()->set_background(*c);
		};

		void on_button1_clicked(){
			Glib::RefPtr<Gdk::Window> wgtk = dr.get_window();
			TreeShape t(wgtk);
			ls.push_back(t);
		};
		void on_button2_clicked(){
	
		};
		void on_button3_clicked(){
	
		};
		void on_button4_clicked(){
	
		};
		void on_activate_save(){
	
		};
		void on_activate_quit(){
			Main::quit();
		};
	
};

int main(int argc, char *argv[]) {
	Main kit(argc, argv);
	DrawingApp d;
	Main::run(d);
  return EXIT_SUCCESS;
};

```

---

### Post by vivichrist on 2011-04-21
what find puzzling is when you start having to deal with these:

```
Glib::RefPtr<Gdk::Window>
Cairo::RefPtr<Cairo::Context>
```

I can't figure out how to pass them safely to functions. I get a segmentation fault...

edit: actually this is not true, there were other reasons for this seg fault stuff

---


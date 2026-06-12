---
title: "Launch Standalone GTKMM Dialog"
date: 2015-12-29
forum: Programming Talk
---

### Post by Phasmus on 2015-12-29
In a particular situation I need my command line based C++ application to launch a quick dialog using gtkmm 2.4. I could really use some direction here.

I tried launching the dialog as a standalone without initializing the top level window:

```
  Gtk::Main kit( NULL,NULL );
  Gtk::Window toplevel;
  MyApp::myDialog d(toplevel);
  int result = d.run();
```
  
This created my dialog but it doesn't close when the ok or cancel button is hit and none of quit/delete/hide api calls I could find could get rid of it. It only goes away when the program exits (even if it is created in a method which exits earlier). I'm guessing this is in part because it needs an active main window to handle some of its lifetime/visibility management. If I could make it respond normally to the ok/cancel buttons I would be all set!

Next I tried creating and launching the main window properly and launching the dialog from within the constructor of the main window. (It takes the Gtk::Main as an argument so I could try killing that directly.)

```
class cprompt : public Gtk::Window
{
  public:    
	cprompt(Gtk::Main* prompt){
MyApp::myDialog* d = new MyApp::myDialog (*this);
std::cout << "ABOUT TO RUN DIALOG" << std::endl;
int result = d->run();
std::cout << "RAN DIALOG" << std::endl;
d->hide();
delete d;

std::cout << "CALLING QUIT" << std::endl;
this->hide();
Gtk::Main::quit();
prompt->quit();
//None of the above calls do anything. The empty 'top level' window hangs around and blocks until manually closed.
std::cout << "CALLED QUIT" << std::endl;
};
	virtual                 ~cprompt(){};
};
```

Now the dialog works as expected, but the main window pops up after the dialog is closed (an empty gray square with an exit button) and I can't find a way to hide or exit it outside of clicking the exit button. All the calls I make to close it or quit the gtk loop automatically are inside the constructor so I'm guessing they aren't valid at that point. If I could make the whole operation shut down after the dialog returns in the window constructor, again I would be all set.

My next approach is going to be to use the top level window itself as the dialog, but I was hoping to avoid this because the dialog I need is already provided by another library and I'll have to re-implement the ui from scratch if I can't launch the dialog straight up.

---


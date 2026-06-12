---
title: "looking for a _sane_ way to use GTK with C++"
date: 2008-08-18
forum: Programming Talk
---

### Post by CC_machine on 2008-08-18
I've been learning SDL with C++ lately, but wanted to give some other graphic libraries a try. So i used GTK (specifically gtkmm).

take a look at this example code:

```

#include <gtkmm/main.h>
#include <iostream>

#include <gtkmm/button.h>
#include <gtkmm/window.h>

using namespace std;

class HelloWorld : public Gtk::Window
{
public:
  HelloWorld();
  virtual ~HelloWorld();

protected:
  //Signal handlers:
  virtual void on_button_clicked();

  //Member widgets:
  Gtk::Button m_button;
};

HelloWorld::HelloWorld()
: m_button("Hello World")   // creates a new button with label "Hello World".
{
  // Sets the border width of the window.
  set_border_width(10);

  // When the button receives the "clicked" signal, it will call the
  // on_button_clicked() method defined below.
  m_button.signal_clicked().connect(sigc::mem_fun(*this,
              &HelloWorld::on_button_clicked));

  // This packs the button into the Window (a container).
  add(m_button);

  // The final step is to display this newly created widget...
  m_button.show();
}

HelloWorld::~HelloWorld()
{
}

void HelloWorld::on_button_clicked()
{
  cout << "Hello World" << endl;
}


int main (int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);

  HelloWorld helloworld;
  //Shows the window and returns when it is closed.
  Gtk::Main::run(helloworld);

  return 0;
}

```

and guess what it does? it draws one button on one window and executes one line of code when the button is clicked. that's all. For 55-60 lines of code!

Why so complex? seriously, reading the gtkmm manual, half of it is completely confusing. I'm halfway through the Lazyfoo SDL tutorials. I've used SDL_image, mixer, ttf. I have classes to spawn enemies drawn on the screen.

Seriously, just to draw a button, you have to use advanced classes? Why so much? I hate dealing with huge amounts of code. It should work like this:

```

#include <gtksomething.h>
#include <iostream>

int main()
{
  NewWindow (windowname)
  windowname.TitleText = "Hello World in GTK";

  NewButton (buttonname, x, y, w, h)	//x,y, width and height of button
  buttonname.ButtonText = "Hello World";

  bool quit=false;

  while(quit == false)
  {
    windowname.show();
    buttonname.show();
    if (buttonname.clicked==true)
    {
      cout << "hello world" << endl;
      quit = true;
    }
  }
  return 0;
}

```

20 lines of code. Much better. As I'm still learning C++, I'd like to know what each line of code does, which with SDL, I do. I'm still grasping pointers, etc. Is there a library like the above I can use, or should i fumble about trying to learn GTKmm?

---

### Post by LaRoza on 2008-08-18
C++ is like that across the board from what I have seen...

Here is an example in C: [http://bo.majewski.name/bluear/gnu/GTK/plain/index.htm](http://bo.majewski.name/bluear/gnu/GTK/plain/index.htm)

That C++ example is using classes. It doesn't have to. I am sure you can do it shorter (use the C code for starting)

---

### Post by StOoZ on 2008-08-18
its the same for wxwidgets , and I use event talbes instead of connect ,and make my code a bit longer(!), but I dont care as long as it does what I want to , its the C++ way.
if it bothers you , try to make a more sensible(?) C++ wrapper for gtk+.

---

### Post by nrs on 2008-08-18
Don't take this as an insult, but the problem is just that you don't know what you're doing. The reason examples aren't demonstrated as such in the tutorials is because it's Bad Design(TM). Not because it's incapable.

[PHP]#include <gtkmm/main.h> 
#include <gtkmm/window.h>
#include <gtkmm/button.h>

int main (int argc, char** argv) 
{
    Gtk::Main kit (argc, argv); 

    Gtk::Window window; 
    Gtk::Button button; 

    window.set_title ("huh?"); 
    window.set_default_size (200, 50);
    button.set_label ("oh snap.."); 
    button.show (); 

    window.add (button); 
    kit.run (window);

    return 0;  
}[/PHP]

---

### Post by StOoZ on 2008-08-18
I wouldnt call it a bad design... its OOP.
deriving your own frame (window) class from the base gtk's one , is good , that way you can customize it as you wish.

---

### Post by nrs on 2008-08-18
> **StOoZ said:**
> I wouldnt call it a bad design... its OOP.
deriving your own frame (window) class from the base gtk's one , is good , that way you can customize it as you wish.

No, I agree, the model in my code and his example is what I was refferring to as Bad Design.

---

### Post by bruce89 on 2008-08-18
It's interesting to note that the equivalent in Vala is a good bit shorter:

```

using Gtk;

public class Example : Window
{
	construct
	{
  		set_border_width (10);

		var button = new Button.with_label ("Hello World");
		button.clicked += (btn) =>
		{
			print ("Hello World\n");
		};

		add (button);
	}

	static void main (string[] args)
	{
		Gtk.init (ref args);

		var example = new Example ();
		example.show_all ();

		Gtk.main ();
	}
}

```

---

### Post by NovaAesa on 2008-08-19
You might want to check out libglademm and then use glade to create you interface. You design the interface, export it as an XML document which is then loaded into you C++ programme. You can then just worry about event calls rather than having to put all the widgets in manually.

---

### Post by samjh on 2008-08-19
> **NovaAesa said:**
> You might want to check out libglademm and then use glade to create you interface. You design the interface, export it as an XML document which is then loaded into you C++ programme. You can then just worry about event calls rather than having to put all the widgets in manually.

Seconded.

Seriously, hand-coding a GUI is a pain-in-the-posterior in almost any library and language.  GTK+ and its various incarnations are no exceptions to this general observation.

Glade works fantastically, and it's much simpler to use than hand-coding.

---

### Post by Darkhack on 2008-08-19
I also really like Glade, although I am somewhat annoyed that they removed the ability to generate C code from version 3.  I might sound like a nut for worrying about something so negligible, but I really liked having the C code for the UI to be compiled in for performance reasons.

---

### Post by LaRoza on 2008-08-19
> **Darkhack said:**
> I also really like Glade, although I am somewhat annoyed that they removed the ability to generate C code from version 3.  I might sound like a nut for worrying about something so negligible, but I really liked having the C code for the UI to be compiled in for performance reasons.

Glade works with many languages.

Also, for performance reasons is possible not possible. It is a GUI, the thing it does the most is just sit there waiting for the user to do something. Performance shouldn't be an issue.

---

### Post by NovaAesa on 2008-08-19
Maybe darkhack is talking about the performance when the programme loads. Surely executing code straight up to create the gui is more efficinent than parsing XML and then loading the interface. I wouldn't think that it would make all that much difference though.

---

### Post by bruce89 on 2008-08-19
I encourage people to use [GtkBuilder]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1Builder.html"). It's not difficult to hand code the UI files (Glade in Subversion can output GtkBuilder files.

---

### Post by kknd on 2008-08-19
> **NovaAesa said:**
> Maybe darkhack is talking about the performance when the programme loads. Surely executing code straight up to create the gui is more efficinent than parsing XML and then loading the interface. I wouldn't think that it would make all that much difference though.

Agreed. The time spent parsing the Glade / GtkBuilder XML is negligible.
The best thing about Glade IMHO is the separation of the UI and the code.
Need to change a label? Ok, just edit the XML.

---

### Post by CC_machine on 2008-08-19
> **nrs said:**
> Don't take this as an insult, but the problem is just that you don't know what you're doing. The reason examples aren't demonstrated as such in the tutorials is because it's Bad Design(TM). Not because it's incapable.

[PHP]#include <gtkmm/main.h> 
#include <gtkmm/window.h>
#include <gtkmm/button.h>

int main (int argc, char** argv) 
{
    Gtk::Main kit (argc, argv); 

    Gtk::Window window; 
    Gtk::Button button; 

    window.set_title ("huh?"); 
    window.set_default_size (200, 50);
    button.set_label ("oh snap.."); 
    button.show (); 

    window.add (button); 
    kit.run (window);

    return 0;  
}[/PHP]

looks good, but how do set some code to be executed when the button is pressed? also, nowhere sets coordinates or size of the button. I pretty much knew how to do something similiar to that, but it's useless in terms of productivity.

btw, enable deadkeys as the secondary keymap, and you can type ", ' etc but loads of symbols also with the AltGr key (e.g. ™ is AltGr+Shift+8)
this may work even without the deadkeys keymap ;p

---

### Post by nrs on 2008-08-19
> **CC_machine said:**
> looks good, but how do set some code to be executed when the button is pressed? also, nowhere sets coordinates or size of the button. I pretty much knew how to do something similiar to that, but it's useless in terms of productivity.

btw, enable deadkeys as the secondary keymap, and you can type ", ' etc but loads of symbols also with the AltGr key (e.g. &#8482; is AltGr+Shift+8)
this may work even without the deadkeys keymap ;p
> 
GTK+ is a container based toolkit, meaning you don't specify where the widget is, but you specify in what container it is. Some widgets, such as a window or a frame or a button, are containers that hold only one other widget. For example a button with a label is actually a button into which we added a label widget. If you need to put more widgets into that container, you will need to add another container into them, one that holds more then one widget such as a horizontal box.
[IMG]http://developer.gnome.org/doc/tutorials/gnome-libs/gtkhierarchy.gif[/IMG]
[http://developer.gnome.org/doc/tutorials/gnome-libs/gtk.html](http://developer.gnome.org/doc/tutorials/gnome-libs/gtk.html)

There is no reason I can think of why you'd want to control the size of the button, it only adds problems. For example, the size you specify may be smaller than the label. Best is to allow it to fill, expand, and shrink with the container it's fitted in, which it does by default. Still, I showed how. 
[PHP]#include <gtkmm/main.h> 
#include <gtkmm/window.h>
#include <gtkmm/button.h>

void button_pressed () 
{ 
    Gtk::Main::quit ();
}

int main (int argc, char** argv) 
{
    Gtk::Main kit (argc, argv); 

    Gtk::Window window; 
    window.set_title ("Example"); 

    Gtk::Button button; 
    button.set_label ("oh snap..."); 
    button.signal_clicked().connect(sigc::ptr_fun(&button_pressed)); 
    button.set_size_request (200, 50);
    button.show (); 

    window.add (button); 

    kit.run (window);

    return 0;  
}

[/PHP]

---

### Post by CC_machine on 2008-08-19
thanks! are there some simple tutorials for this? something equivalent to LazyFoo's SDL tutorials? I'm sure I'm wasting your time, but I tried to mod the program, like so:

```

#include <gtkmm/main.h> 
#include <gtkmm/window.h>
#include <gtkmm/button.h>

void button_pressed () 
{ 
    Gtk::Main::quit ();
}

int main (int argc, char** argv) 
{
    Gtk::Main kit (argc, argv); 

    Gtk::Window window; 
    window.set_title ("Example"); 

    Gtk::Button button;
    Gtk::Button button2;

    button.set_label ("oh snap..."); 
    button2.set_label ("oh wooo..."); 

    button.signal_clicked().connect(&button_pressed);
    button2.signal_clicked().connect(&button_pressed);

    //button.set_size_request (200, 50);
    button.show (); 
    button2.show ();

    window.add (button); 
    window.add (button2); 

    kit.run (window);

    return 0;  
}

``` 

and on runtime I get:
> 
(a.out:11871): Gtk-WARNING **: Attempting to add a widget with type gtkmm__GtkButton to a gtkmm__GtkWindow, but as a GtkBin subclass a gtkmm__GtkWindow can only contain one widget at a time; it already contains a widget of type gtkmm__GtkButton


I guess this is the Bad Design™ you were talking about. my first thoughts were "wow, this obviously doesn't follow common sense, why add a button to a window if you can only add one" but I realise i should probably make it object oriented. However, wouldn't a class do the exact same thing?

---

### Post by nrs on 2008-08-19
I think you should try using Glade, you don't have to use it on your program if you don't want to, but it'll definately give you an idea of how widget layout, etc. works with GTK+. 

You would indeed have the same problem if you just shifted the current code over to a class. This isn't particularly why I referred to it as bad design, I'm not really going to go into why because I'm lazy, and others could explain it better than I could, but the gist of it is: #1 it was designed with OO in mind #2 while fine for excedingly simple applications it just isn't extensible, and a lot of things simply can't be accomplished like this.

Carefully look at the diagram I posted earlier, the error, and fool around with Glade and I think you'll find your solution pretty quickly.

---

### Post by bruce89 on 2008-08-19
> **CC_machine said:**
> I guess this is the Bad Design&#8482; you were talking about. my first thoughts were "wow, this obviously doesn't follow common sense, why add a button to a window if you can only add one" but I realise i should probably make it object oriented. However, wouldn't a class do the exact same thing?

GtkBin (of which GtkWindow is a subclass) can only contain one widget. Put a GtkHBox or a GtkVBox in the window, then use pack_{start|end} to pack widgets into the box.

---

### Post by days_of_ruin on 2008-08-19
> **bruce89 said:**
> I encourage people to use [GtkBuilder]("http://www.gtkmm.org/docs/gtkmm-2.4/docs/reference/html/classGtk_1_1Builder.html"). It's not difficult to hand code the UI files (Glade in Subversion can output GtkBuilder files.

You don't have to handcode anything with gtk builder.
As of the current glade implementation you have to convert the .glade file
to xml using gtk-builder-convert.
Read this:

[http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html]("http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html")

---


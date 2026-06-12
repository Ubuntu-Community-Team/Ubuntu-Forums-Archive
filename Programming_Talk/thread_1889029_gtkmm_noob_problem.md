---
title: "gtkmm noob problem"
date: 2011-11-30
forum: Programming Talk
---

### Post by wisuzu on 2011-11-30
Hello and thx in advance!

I'm new programming in GUI's and kind of modderate in c++ . I've been working in a application in opencv/c++ and now i want to link it with a very simple GUI.

I got some little noob (i think) problems trying to get some arguments for my opencv class:

Miwindow.h
```

#ifndef MIWINDOW_H
#define MIWINDOW_H

#include <libglademm.h>
#include <gtkmm.h>

class Miwindow : public Gtk::Window {

public: 


	Miwindow(BaseObjectType* cobject, Glib::RefPtr<Gtk::Builder> refBuilder);
	virtual ~Miwindow();
	
protected:

  // Xml pointer
		Glib::RefPtr<Gtk::Builder> m_refBuilder;
	
	// Widgets
	Gtk::ImageMenuItem *imagemenuitem2;
	Gtk::ImageMenuItem *imagemenuitem5;
	Gtk::ImageMenuItem *imagemenuitem6;
	Gtk::SpinButton *spinbutton1;
	Gtk::Button *button1;	

	// Signal handlers
	void on_button1_clicked();
	void on_imagemenuitem2_activate();
	void on_imagemenuitem5_activate();
	void on_imagemenuitem6_activate();


};

#endif

```

Miwindow.cc
```

//#include "cv.h"
//#include "highgui.h"
//#include "ml.h"
#include "Miwindow.h"
#include "Evaluador.h"

#include <iostream>


Miwindow::Miwindow(BaseObjectType* cobject, 	Glib::RefPtr<Gtk::Builder> refBuilder): 
  Gtk::Window(cobject),
  m_refBuilder(refBuilder) {

  m_refBuilder->get_widget("imagemenuitem5", imagemenuitem5);
  
  if (imagemenuitem5) {
    imagemenuitem5->signal_activate().connect(sigc::mem_fun(*this, &Miwindow::on_imagemenuitem5_activate) );
  }
  
  m_refBuilder->get_widget("imagemenuitem6", imagemenuitem6);
  if (imagemenuitem6) {
    imagemenuitem6->signal_activate().connect(sigc::mem_fun(*this, &Miwindow::on_imagemenuitem6_activate) );
  }
  
  m_refBuilder->get_widget("imagemenuitem2", imagemenuitem2);
  

  
  if (imagemenuitem2) {
	imagemenuitem2->signal_activate().connect(sigc::mem_fun(*this, &Miwindow::on_imagemenuitem2_activate) );  	
  }
  
  m_refBuilder->get_widget("button1", button1);
  m_refBuilder->get_widget("spinbutton1", spinbutton1);
  
  if (button1 && spinbutton1){
    button1->signal_clicked().connect(sigc::mem_fun(*this, &Miwindow::on_button1_clicked) );
  }
  
}


Miwindow::~Miwindow() {
  delete imagemenuitem2;
  delete imagemenuitem5;
  delete imagemenuitem6;
  delete button1;
  delete spinbutton1;
}

void Miwindow::on_button1_clicked() { //run the opencv  method

   ***** int spinvalue = spinbutton1->get_value();
   ***** std::cout << "Parameter 1 = " << spinvalue << std::endl;

//    Evaluador evaluador;
//    eval resultado;
++++//    resultado = evaluador.evaluar(spinvalue,"/PathToOneImage");
//    std::cout << "ratio = " << resultado.ratio << std::endl;

}


void Miwindow::on_imagemenuitem2_activate() { //open and show the image to the opencv method
	Gtk::Window* visor_win = new Gtk::Window(Gtk::WINDOW_TOPLEVEL);
	visor_win->set_title ("visor de imágenes");

	Gtk::HBox* box = new Gtk::HBox();
	box->set_spacing(5);
 

	Gtk::Image* image = new Gtk::Image();

	box->pack_start (*image, true, true);

	visor_win->add(*box);

	Gtk::FileChooserDialog dialog("Selecciona imagen a procesar",
	                              Gtk::FILE_CHOOSER_ACTION_OPEN);
	dialog.add_button (Gtk::Stock::OPEN,
	                   Gtk::RESPONSE_ACCEPT);
	dialog.add_button (Gtk::Stock::CANCEL,
	                   Gtk::RESPONSE_CANCEL);

	switch (dialog.run())
	{
		case Gtk::RESPONSE_ACCEPT:
    {
      Glib::RefPtr<Gdk::Pixbuf> pb = Gdk::Pixbuf::create_from_file(dialog.get_filename());
      pb = pb->scale_simple(800, 600,Gdk::INTERP_BILINEAR);
      image->set(pb);
    	visor_win->show_all();


%%%%% std::cout << "pathImagen = " << dialog.get_filename() << std::endl;
//      std::cout << "w x h: " <<     pb->get_width() << " x " << pb->get_height() << std::endl;

    	break;
    }
		default:
			break;
	}
	dialog.hide();
}

void Miwindow::on_imagemenuitem5_activate() { // Close item
  exit(1);
}

void Miwindow::on_imagemenuitem6_activate() { //about item
  Gtk::AboutDialog *aboutDialog = new Gtk::AboutDialog();
  
  aboutDialog->set_license(Glib::ustring("LGPL"));
 //more aboutDialog stuff
}

```

I dont know why (*****) the spinbutton keep returning 0 no matter what you put in it. And i need (++++) opencv method a const char* or char* (%%%%)of the path about the opened image. Any clue/hint/fix will be appreciated.

---

### Post by ehmicky on 2011-11-30
Hola,
For the SpinButton, the min/max/value/etc. attributes are set up by  giving a RefPtr<Adjustment> during the instantiation. But here  since you're using Glade, we can't figure out what's wrong without the  .glade file. Or with the content of the variables set by get_range() and get_increments().
In order for dialog.get_filename() to return a C-string, use dialog.get_filename().c_str()
Espero que te ayuda :)

---

### Post by wisuzu on 2011-12-01
Thank you very much ehmicky!! I solve the first problem (the spinbutton one) as you said:

```

  m_refBuilder->get_widget("spinbutton1", spinbutton1);
  
  double f = 50;
  double t = 1000;
  spinbutton1->set_range(f,t);
  spinbutton1->set_increments(f,f);

  if (button1 && spinbutton1){
    button1->signal_clicked().connect(sigc::mem_fun(*this, &Miwindow::on_button1_clicked));
  }
  
}

```

For the second problem ... the dialog.get_filename().c_str() return a const char *, I need a char * in my on_button1_clicked(). I tried some possibilities, all envolving creating a new class variable.

I tried for this variable a char * path, char path[] ... and tried to convert the const char * in that, but for most i got a memory crash and for others i was not obtaining the value in on_button1_clicked().

This last one i don't know what is wrong with it:

Miwindow.h
```

#ifndef MIWINDOW_H
#define MIWINDOW_H

#include <gtkmm.h>

class Miwindow : public Gtk::Window {

public: 


	Miwindow(BaseObjectType* cobject, Glib::RefPtr<Gtk::Builder> refBuilder);
	virtual ~Miwindow();
	
protected:

        //same stuff

	char * path;

        //same stuff

};

#endif

```

Miwindow.cc
```

//same includes

Miwindow::Miwindow(BaseObjectType * cobject, Glib::RefPtr<Gtk::Builder> refBuilder)
    : Gtk::Window(cobject), m_refBuilder(refBuilder)
{
//same stuff


Miwindow::~Miwindow() {
}

void Miwindow::on_button1_clicked() {

		int spinvalue = spinbutton1->get_value_as_int();
    std::cout << "Parameter 1 = " << spinvalue << std::endl;
		std::cout << path << std::endl;
}


void Miwindow::on_imagemenuitem2_activate() 
{
  //same stuff

  path = const_cast<char*> ( dialog.get_filename().c_str() );
      std::cout << "pathImagen = " << path << std::endl;

  //same stuff
}
void Miwindow::on_imagemenuitem5_activate() {
 //same stuff
}

void Miwindow::on_imagemenuitem6_activate() {
  //same stuff
}


```
When i run those parts, i got the following:

1  pathImagen = /home/myhome/pathToImage/image.jpg
2  Parameter 1 = 50
3  &#65533;6&#65533;	&#65533;

The 1, is the cout just after the const_cast<char*>, the 2 is the spinbutton working and the 3 is some random garbage :S

Anyone know what i'm doing wrong or know the way to do what i want? any lead/hint/help will be appreciated.

Thx in advance for all!

---

### Post by wisuzu on 2011-12-01
I answer it myself

the problem was that the memory that the pointer was pointing is free when the function ends, so i use a std::string as the variable in the header and then use path = std::string(dialog.get_filename().c_str()) and path.c_str() to access where i want
Solved 

Thx to all the leads and hints!

---


---
title: "GTKmm Linking/Signals?"
date: 2010-03-01
forum: Programming Talk
---

### Post by fallenshadow on 2010-03-01
Ok I want to link my newfiledialog to a button in my mainwindow. I have 5 files: main.cc mainwindow.cc, mainwindow.h, new.cc and new.h.

This line is for the button to link it in mainwindow.cc:
[PHP]
sigc::mem_fun(*this, &MWindow::show_newfiledialog) );
[/PHP]

This is the signal handler in mainwindow.h:
[PHP]
virtual void show_newfiledialog();
[/PHP]

This is at the begining of my newfiledialog:
[PHP]void Newfile::show_newfiledialog()
{
  Gtk::NewfileDialog newfileDialog;
[/PHP]

This is the current error message when I compile:

```

new.cc: In constructor ‘Newfile::Newfile()’:
new.cc:39: error: expected `{' before ‘void’
new.cc: At global scope:
new.cc:39: error: no ‘void Newfile::show_newfiledialog()’ member function declared in class ‘Newfile’

```

Note that MWindow is the mainwindow function and Newfile is the new file dialog function. Any ideas on where im going wrong?

---

### Post by kahumba on 2010-03-01
The compiler says you have a syntactical error. Post the whole source code and preferably the header.

---

### Post by fallenshadow on 2010-03-01
new.cc:
[PHP]
#include "new.h"
#include <iostream>

Newfile::Newfile()
:
	m_Frame("Size in pixels/memory"),
	m_Frame1("New size"),
	m_VBox_Main(false, 5),
	m_HBox_Content(),
	m_VBox_Content(), m_VBox_Width(), m_VBox_Height(), m_VBox_Memory(), m_VBox_Frame1(), 
	m_Label_Width("Width: "),
	m_Label_Height("Height: "),
	m_Label_Memory("Memory: "),
	m_SpinButton_Width(),
	m_SpinButton_Height(),
	m_SpinButton_Memory(),
	m_Entry_Height(), m_Entry_Width()

void Newfile::show_newfiledialog()
{
  Gtk::NewfileDialog newfileDialog;
  
  //Set some window properties 
  set_title("New");
  set_size_request(300, 450);

  //Sets the border width of the window.
  set_border_width(10);

  //m_Frame.add(m_VBox_Main);
  //m_Frame1.add(m_VBox_Main);

  //Put in frames
  add(m_Frame);
  add(m_Frame1);
  
  //Set the frames label 
  //m_Frame.set_label("Size in pixels/memory");
 // m_Frame1.set_label("New size");
  
  
  //Align the label at the right of the frame
  //m_Frame.set_label_align(Gtk::ALIGN_RIGHT, Gtk::ALIGN_TOP);

  //Set the style of the frame 
  m_Frame.set_shadow_type(Gtk::SHADOW_ETCHED_OUT);
  m_Frame1.set_shadow_type(Gtk::SHADOW_ETCHED_OUT);
   
  //First Frame
				//m_Frame.add(m_HBox_Frame);

  //Start of VBox container
  add(m_VBox_Main);
  m_VBox_Main.set_border_width(10);
  m_VBox_Main.pack_start(m_Frame, Gtk::PACK_SHRINK);
  m_VBox_Main.pack_start(m_Frame1);
  
  m_VBox_Content.set_border_width(5);
  m_Frame.add(m_VBox_Content);
//----------------------------------------------  
  m_VBox_Content.pack_start(m_HBox_Content, Gtk::PACK_EXPAND_WIDGET, 5);

  m_Label_Width.set_alignment(Gtk::ALIGN_LEFT);
  m_VBox_Width.pack_start(m_Label_Width);

  m_SpinButton_Width.set_wrap();

  m_VBox_Width.pack_start(m_SpinButton_Width);
//----------------------------------------------
  m_HBox_Content.pack_start(m_VBox_Width, Gtk::PACK_EXPAND_WIDGET, 5);

  m_Label_Height.set_alignment(Gtk::ALIGN_LEFT);
  m_VBox_Height.pack_start(m_Label_Height);

  m_SpinButton_Height.set_wrap();
  m_VBox_Height.pack_start(m_SpinButton_Height);
//----------------------------------------------
  m_HBox_Content.pack_start(m_VBox_Height, Gtk::PACK_EXPAND_WIDGET, 5);

  m_Label_Memory.set_alignment(Gtk::ALIGN_LEFT);
  m_VBox_Memory.pack_start(m_Label_Memory);

  m_SpinButton_Memory.set_wrap();
  m_SpinButton_Memory.set_size_request(55, -1);
  m_VBox_Memory.pack_start(m_SpinButton_Memory);

  m_HBox_Content.pack_start(m_VBox_Memory, Gtk::PACK_EXPAND_WIDGET, 5);
//----------------------------------------------

//Second Frame
  m_Frame1.add(m_VBox_Frame1);
  
  m_VBox_Frame1.set_border_width(80);
  add(m_VBox_Frame1);
  
  //Textboxes
  m_Entry_Width.set_max_length(5);
  m_Entry_Width.set_text("800");
  //m_Entry.set_text(m_Entry.get_text() + " secondarytext");
  m_Entry_Width.select_region(0, m_Entry_Width.get_text_length());
  m_VBox_Frame1.pack_start(m_Entry_Width);
  
  m_Entry_Height.set_max_length(5);
  m_Entry_Height.set_text("600");
  //m_Entry.set_text(m_Entry.get_text() + " secondarytext");
  m_Entry_Height.select_region(0, m_Entry_Height.get_text_length());
  m_VBox_Frame1.pack_start(m_Entry_Height);

  show_all_children();
  
  newfileDialog.run();
} //End of Newfile dialog

Newfile::~Newfile()
{
}[/PHP]

new.h:
[PHP]#ifndef GTKMM_NEWFILE_H
#define GTKMM_NEWFILE_H

#include <gtkmm.h>

class Newfile : public Gtk::Window
{
public:
  Newfile();
  virtual ~Newfile();

protected:

  //Signal Handlers
  //virtual void show_newfiledialog();

  //Child widgets:
  Gtk::Frame m_Frame, m_Frame1;
  Gtk::VBox m_VBox_Main;
  Gtk::HBox m_HBox_Content;
  Gtk::VBox m_VBox_Content, m_VBox_Width, m_VBox_Height, m_VBox_Memory, m_VBox_Frame1;
  Gtk::Label m_Label_Width, m_Label_Height, m_Label_Memory;
  Gtk::SpinButton m_SpinButton_Width, m_SpinButton_Height, m_SpinButton_Memory;
  Gtk::Entry m_Entry_Width, m_Entry_Height;
};

#endif //GTKMM_NEWFILE_H[/PHP]

I presume you mean't the source of new.cc and new.h.

---

### Post by PaulM1985 on 2010-03-01
From your original code, you have used:

sigc::mem_fun(*this, &MWindow::show_newfiledialog) );  

to link the button and specified that on the button click, it should call the function show_newfiledialog in the MWindow class.

You have then created a show_newfiledialog function in the NewFile class.

In your NewFile class header file, you have commented out the declaration of the show_newfiledialog function:

  //virtual void show_newfiledialog(); 

Try uncommenting this line in the NewFile class header file.  Also, does your MWindow have a show_newfiledialog function, or do you mean to have
sigc::mem_fun(*this, &NewFile::show_newfiledialog) ); 

Basically, you have asked for a function in one class and then looks like you have tried to declare it in another.  Which class should show_newfiledialog be in, and make sure you use the correct class type when linking it.

Hope this has helped.

Paul

---

### Post by fallenshadow on 2010-03-01
When I uncomment that line I end up with a slightly different list of errors:

```

new.cc: In constructor ‘Newfile::Newfile()’:
new.cc:39: error: expected `{' before ‘void’
new.cc: In member function ‘virtual void Newfile::show_newfiledialog()’:
new.cc:41: error: ‘NewfileDialog’ is not a member of ‘Gtk’
new.cc:41: error: expected `;' before ‘newfileDialog’
new.cc:131: error: ‘newfileDialog’ was not declared in this scope

```

I have already tried both:
[PHP]
sigc::mem_fun(*this, &NewFile::show_newfiledialog) ); 
[/PHP]

and

[PHP]
sigc::mem_fun(*this, &MWindow::show_newfiledialog) ); 
[/PHP]

Either one results in the same error messages as above.

---

### Post by PaulM1985 on 2010-03-01
```
new.cc: In constructor ‘Newfile::Newfile()’:
new.cc:39: error: expected `{' before ‘void’


```
You need to put 

{
}

after your constructor.  You haven't actually shown an explicit function body for it.

```

new.cc: In member function ‘virtual void Newfile::show_newfiledialog()’:
new.cc:41: error: ‘NewfileDialog’ is not a member of ‘Gtk’
new.cc:41: error: expected `;' before ‘newfileDialog’
new.cc:131: error: ‘newfileDialog’ was not declared in this scope

```

Is NewFileDialog a Gtk class?  I am not sure it it.  What type of object are you trying to create using the line:

  Gtk::NewfileDialog newfileDialog;

Is there such thing as a Gtk::NewfileDialog class?  Is this a class you are trying to create?

Paul

---

### Post by fallenshadow on 2010-03-01
Ok I have put in the two brackets: {}.

I have commented out:

[PHP]
Gtk::NewfileDialog newfileDialog;
[/PHP]

Now my list of errors is down to just one:

```

new.cc: In member function ‘virtual void Newfile::show_newfileDialog()’:
new.cc:134: error: ‘newfileDialog’ was not declared in this scope

```

---

### Post by PaulM1985 on 2010-03-01
At line 134 you are trying to use the object newfileDialog.  You commented out the declaration of this object in your last post.  Remove this line and it should compile.

Paul

---

### Post by fallenshadow on 2010-03-01
After removing line 134 I have this error message:

```

/tmp/ccNKrAHd.o:(.rodata._ZTV7MWindow[vtable for MWindow]+0x15c): undefined reference to `MWindow::show_newfileDialog()'
collect2: ld returned 1 exit status

```

:confused:

---

### Post by PaulM1985 on 2010-03-01
The error you have got is an undefined reference error.

This basically means you are asking it to look for something that isn't really there.  This will probably be from when you are linking the button click.

1 - Do you have a show_newfileDialog() function in your MWindow class?
2 - Do you have it in the header file for the MWindow class?

Think about what this button is supposed to do and what happens when you click on the button.  What code is going to be executed.

If you are new to using gtkmm, try to do something really simple like getting a function to be called which will print some code at command line so you get used to program flow, rather than creating more complex windows.

Also, Google tends to give pretty good advice of what error messages mean.

Paul

---

### Post by fallenshadow on 2010-03-02
> 
1 - Do you have a show_newfileDialog() function in your MWindow class?
2 - Do you have it in the header file for the MWindow class?

The answer to both these questions is yes. I have linked a dialog already but it was in the mainwindow.cc not in separate files. I could put it into mainwindow.cc but then my program would start becoming bloated and harder to program.

Anyway I will keep trying to solve these errors.

---

### Post by PaulM1985 on 2010-03-02
Ok.  Just to clarify what you are exactly trying to do..

1 - Program starts up with your MWindow class.
2 - On a button click on your MWindow, a second window opens.

If this is the case you will need to look at doing the following:

For your MWindow class:

1 - Your MWindow class with need to inherit from Gtk::Window.
2 - You will need to have a Gtk::Button which is a member of your MWindow class.
3 - You will need a function in the MWindow class (lets call this ShowDialog()). Define this function in your MWindow header file.
4 - In your constructor for the MWindow class, call the constructor for the button passing in the correct label for it.
5 - Link your button to the function using something like:
```
m_MyButton.signal_clicked().connect(sigc::mem_fun(*this, &MWindow::ShowDialog));
```
6 - In your ShowDialog() function in the MWindow cpp file, call the constructor for the NewFile class.

For your NewFile class:

1 - Your NewFile class will also need to inherit from Gtk::Window.
2 - In the constructor add all the things you want.

This should work (provided I have guess correctly the problem).

Paul

---


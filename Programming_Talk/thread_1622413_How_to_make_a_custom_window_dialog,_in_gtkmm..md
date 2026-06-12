---
title: "How to make a custom window dialog, in gtkmm."
date: 2010-11-15
forum: Programming Talk
---

### Post by LuxVan on 2010-11-15
Hi, I do not understand how to make a dialog with gtkmm.
I am only a beginner programmer.
My exercise is this:
I have a main window with some buttons. After clicking one of this, I would like to show a simple window dialog with 2 button (the classic "ok" button and "cancel" button).
I have wrote this code:
dialog.h
```
#ifndef DIALOG_H
#define DIALOG_H

#include<gtkmm.h>

class dialogo : public Gtk::Dialog
{
   public:
      dialogo();
      virtual ~dialogo();
   protected:
      void show_dialog();
      Gtk::VButtonBox box;
      Gtk::Button ok,annulla;
      Gtk::HBox hbox;
};         

#endif
```

dialog.cpp
```
#include"dialog.h"
#include<gtkmm.h>

dialogo::dialogo()
: ok("OK"),
  annulla("ANNULLA")
{
   set_title("primo dialgo");
      
   add(box);
      
   box.pack_start(ok);
   box.pack_start(annulla);
   
   show_all_children();
}

dialogo::~dialogo()
{

}

void dialogo::show_dialog()
{
   dialogo dialogo(*this, "questo è un esempio");
   //dialogo.set_secondary_test("prova testo secondario");
   dialogo.run();
}
```

main.cpp
```
#include "MainWindow.h"

int main(int argc, char *argv[])
{
   Gtk::Main kit(argc, argv);
   window win;
   Gtk::Main::run(win);  
   return 0;
}
```

Mainwindow.cpp
```
#include "MainWindow.h"
#include "dialog.h"
#include <iostream>
#include <string>
#include <sstream>

using namespace std;

window::window()

{
   //maximize(); //massimizza la finestra
   set_title("Finestra principale");
   set_resizable(false);
   set_border_width(13);
   set_size_request(250,250);
   set_position(Gtk::WIN_POS_CENTER); //avvia l'applicazione al centro dello schermo
   
   
   button.set_label("Ciao Mondo!");
   close.set_label("Close");
   summ.set_label("Somma");
   clear.set_label("Clear");
   dia.set_label("Dialog");
   entry.set_text("Clicca il pulsante!");
   label.set_text("Somma:");
   hbox.set_spacing(2);
   hbox1.set_spacing(2);
      
   button.signal_clicked().connect(sigc::mem_fun(*this,&window::click_button));
   close.signal_clicked().connect(sigc::mem_fun(*this, &window::close_button));
   summ.signal_clicked().connect(sigc::mem_fun(*this, &window::somma_button));
   clear.signal_clicked().connect(sigc::mem_fun(*this, &window::clear_button));
   dia.signal_clicked().connect(sigc::mem_fun(*this, &dialogo::show_dialog));
   
   hbox.pack_start(label);
   hbox.pack_start(entry3);
   hbox1.pack_start(close);
   hbox1.pack_start(dia);
   
   add(vbox);
   
   vbox.pack_start(button);
   vbox.pack_start(hbox1);
   vbox.pack_start(summ);
   vbox.pack_start(clear);
   vbox.pack_start(entry);
   vbox.pack_start(entry1);
   vbox.pack_start(entry2);
   vbox.pack_start(hbox);
   
   show_all();
}

window::~window()
{
}   

void window::click_button()
{
   stringa = button.get_label();
   if (stringa == "Ciao Mondo!")
   { 
      entry.set_text(stringa);
      button.set_label("Clicca ancora:)");
   }
   else
   {
      stringa = "Ciao Mondo!";   
      button.set_label(stringa);
      stringa = "Clicca ancora:)";
      entry.set_text(stringa);
   }     
}

void window::close_button()
{
   hide(); //Chiude l'applicazione
}

void window::somma_button()
{
   istringstream in, in2;//Uso sstream per convertire la stringa in numero 
   ostringstream out;//Uso sstream per convertire il numero in stringa

   stringa = entry1.get_text();//prendo la stringa iniziale
   in.str(stringa);//la inserisco nella variabile in e la converto in numero
   in>>a;//la posiziono in a
   
   s=entry2.get_text();
   in2.str(s);
   in2>>b;
   
   c=a+b;//eseguo la somma
   
   out<<c;//la posiziono in out per riconvertire in stringa il numero ottenuto
   o=out.str();//converto il numero in stringa e la metto in s
   entry3.set_text(o);//stampo il valore ottenuto
}

void window::clear_button()
{
   entry.set_text("Clicca il pulsante!");
   entry1.set_text("");
   entry2.set_text("");
   entry3.set_text("");
}   

```

MainWindow.h
```
#ifndef MAINWINDOW_H
#define MAINWINDOW_H

#include <gtkmm.h>
#include <glibmm.h>
#include <string>

using namespace std;
using Glib::ustring;

class window : public Gtk::Window
{
   public:
       window(); //costruttore
       virtual ~window(); //distruttore
   protected:
       void click_button(); //funzione click button  
       void close_button(); //pulsante di chiusura
       void somma_button(); //pulsnte per la somma
       void clear_button(); //pulsante che cancella i 3 entry
       void dialog_button(); //pulsante che lancia una finestra di dialogo
       
       Gtk::Button button,close,summ,clear,dia;  // oggetti che compongono la finestra window
       Gtk::Entry entry,entry1,entry2,entry3;    // altri oggetti della finestra window
       Gtk::Label label;
       Gtk::VBox vbox;  //contenitore principale della finestra window
       Gtk::HBox hbox,hbox1; //contenitore secondario per un label ed un pulsante
       
       double a,b,c;
       string stringa,s,o;
};  
       
#endif       
```
but it do not run...
Can you help me?

---

### Post by SledgeHammer_999 on 2010-11-15
I didn't compile your code but I suggest this:

1. Remove "show_dialog()" from dialog.h
2. Remove the implementation of "show_dialog()" in dialog.cpp
3. In MainWindow.h add another Gtk::Button named "open_dialog". 
4. In MainWindow.cpp add "open_dialog" in the appropriate container and connect to it's "clicked" signal. 
5. In open_dialog's signal handler do exactly what you do in "show_dialog()".

I hope you understood me. You mentioned in another thread that you don't understand English very well. If something I said is confusing to you, please let me know and I will clarify.

Some more tips:
Since you want to use "OK/CANCEL" dialogs then you should use the StockID constructor of Gtk::Button. This will ensure that the correct text will be used as label according to the user's system-language. Eg in your system it will be "OK/ANNULLA", but in an english system it will be(automatically) "OK/CANCEL".

So in the dialog.cpp in the constructor write this:
[php]dialogo::dialogo()
: ok(Gtk::Stock::OK),
  annulla(Gtk::Stock::CANCEL)
[/php]

Link1: [http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Button.html#af44d6e2efbb8342da17f7259626e67cc](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Button.html#af44d6e2efbb8342da17f7259626e67cc)
Link2: [http://library.gnome.org/devel/gtkmm/unstable/namespaceGtk_1_1Stock.html#a783d80fdc67520898ed369836f1f3390](http://library.gnome.org/devel/gtkmm/unstable/namespaceGtk_1_1Stock.html#a783d80fdc67520898ed369836f1f3390)

---

### Post by SledgeHammer_999 on 2010-11-15
Oops sorry. I just noticed your problem.

I think you wanted to impement "show_dialog()" in the MainWindow class and not in the dialogo class.

In MainWindow class you tell gtk to connect **dia**'s clicked-signal to "window::show_dialog" function, but you don't provide such function in MainWindow.h/MainWindow.cpp. I propose you cut/paste the relevant parts from dialog.h/dialog.cpp.

This is the offending line:
[php]dia.signal_clicked().connect(sigc::mem_fun(*this, &dialogo::show_dialog));[/php]

EDIT: I made a mess of things. Do what I propose above AND also change the above line to this:
[php]dia.signal_clicked().connect(sigc::mem_fun(*this, &window::show_dialog));[/php]

---

### Post by SledgeHammer_999 on 2010-11-15
Hmmm on further investigation your code seems to have multiple errors. Most of them involve wrong usage of the Gtkmm API. Since this is an exercise I don't know how to proceed and not spoil "the fun" for you.

I will not give you working code for your whole project.
I will try to push you in the right direction.
But you HAVE TO try things yourself too. If something fails and you can't discover why, you can ask here reporting the error and being as SPECIFIC as you can. Don't come and say "this does not compile". Give more feedback.

And to push you in the right direction. Gtk::Dialog is a special window. You don't need to create special containers to add buttons. It has it's own internal layout. Instead create a button using this method->**Gtk::Dialog::add_button()**.

I suggest you read how Gtk::Dialog works(aka the docs) [here](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Dialog.html) and [here](http://library.gnome.org/devel/gtk/stable/GtkDialog.html)(the original C docs usually have more documentation).

---

### Post by LuxVan on 2010-11-15
Many thanks...Now, it run. But I do not know how to add the two buttons inside the dialog...
Maybe I should to use Gtk::VBox widget?
I have wrote this:
```
#include"dialog.h"
#include<gtkmm.h>

dialogo::dialogo()
: ok(Gtk::Stock::OK),
  annulla(Gtk::Stock::CANCEL)
{
   set_title("Primo dialgo");
   add(vbox);
   vbox.pack_start(ok);
   vbox.pack_start(annulla);
   
   show_all_children();
}
```
When the window dialog is starting, there are not the two buttons, and, so on,  it show me this message:
```
(MainWindow:2210): Gtk-WARNING **: Attempting to add a widget with type gtkmm__GtkVBox to a gtkmm__GtkDialog, but as a GtkBin subclass a gtkmm__GtkDialog can only contain one widget at a time; it already contains a widget of type GtkVBox

```
So, my dialog have three buttons:  "close", "maximize", "minimize". 
It is strange for me...a window dialog should to have only two button ("close" and "minimize") or not?
Thank you for your help! So, I am learning how to programm in c++ and gtkmm and to speak in english too.\\:D/

---

### Post by SledgeHammer_999 on 2010-11-15
Re-read my last post. 

Clue: you don't create the buttons beforehand. You create them when you call "add_button".

---

### Post by LuxVan on 2010-11-15
Sorry but I do not understand...maybe becouse it is 11 pm o' clock?#-o

---

### Post by SledgeHammer_999 on 2010-11-15
Well, here it is midnight :p 
I'll try to explain tomorrow if I have time.

---

### Post by LuxVan on 2010-11-15
Ok, I'm going to sleep! I will read you tomorrow! good night!

---

### Post by LuxVan on 2010-11-21
](*,)

---

### Post by worksofcraft on 2010-11-22
> **LuxVan said:**
> ](*,)

Looks like you are not having much fun there LuxVan :shock:
So if I gather correctly... you want to make a pop up modal dialog box with an OK button?

Have you checked the [gtkmm dialog tutorial]("http://library.gnome.org/devel/gtkmm-tutorial/2.21/chapter-dialogs.html.en") ?

If I get time tomorrow I'll may try to have a look at your code.

---

### Post by worksofcraft on 2010-11-22
I bunged all your code in one big file and the compile command you need is on the first line.
I think it does what you wanted now and I put some English comments in to explain what I changed.
Me 'spiace molto ma non so scrivere in Italiano ;)
[php]

// g++ dialogbox.cpp `pkg-config --libs --cflags gtkmm-2.4`

#include<gtkmm.h>

class dialogo : public Gtk::Dialog
{
   public:
      dialogo(const char *pTitle);
      virtual ~dialogo();
   protected:
//      Gtk::VButtonBox box; // dialogs already have a VBox
//      Gtk::Button ok,annulla; // use add_button to set the response
//     Gtk::HBox hbox; // not used
};         

dialogo::dialogo(const char *pTitle)
//: ok("OK"),
//  annulla("ANNULLA")
{
   set_title(pTitle);
      
//   add(box); // already has a box
/*
// you could have tried this way, but IDK how to get the response then   
	Gtk::VBox *box = get_vbox();
	box->pack_start(ok);
	box->pack_start(annulla);
*/
// dialogo.run() method returns an int.
// This may be a value from the Gtk::ResponseType if the user closed the
// button by clicking a standard button, or it could be the custom response
// value that you specified when using add_button().
// so here you see I make "OK" return a 0, and ANNULLA return a 1 from the Dialog.run() method
	add_button("OK", 0)	;
	add_button("ANNULLA", 1);
   
   show_all_children();
}

dialogo::~dialogo()
{

}


#include <gtkmm.h>
#include <glibmm.h>
#include <string>

using namespace std;
using Glib::ustring;

class window : public Gtk::Window
{
   public:
       window(); //costruttore
       virtual ~window(); //distruttore
   protected:
       void click_button(); //funzione click button  
       void close_button(); //pulsante di chiusura
       void somma_button(); //pulsnte per la somma
       void clear_button(); //pulsante che cancella i 3 entry
       void dialog_button(); //pulsante che lancia una finestra di dialogo
       
       Gtk::Button button,close,summ,clear,dia;  // oggetti che compongono la finestra window
       Gtk::Entry entry,entry1,entry2,entry3;    // altri oggetti della finestra window
       Gtk::Label label;
       Gtk::VBox vbox;  //contenitore principale della finestra window
       Gtk::HBox hbox,hbox1; //contenitore secondario per un label ed un pulsante
       
       double a,b,c;
       string stringa,s,o;
};  

#include <iostream>
#include <string>
#include <sstream>

using namespace std;

window::window()

{
   //maximize(); //massimizza la finestra
   set_title("Finestra principale");
   set_resizable(false);
   set_border_width(13);
   set_size_request(250,250);
   set_position(Gtk::WIN_POS_CENTER); //avvia l'applicazione al centro dello schermo
   
   
   button.set_label("Ciao Mondo!");
   close.set_label("Close");
   summ.set_label("Somma");
   clear.set_label("Clear");
   dia.set_label("Dialog");
   entry.set_text("Clicca il pulsante!");
   label.set_text("Somma:");
   hbox.set_spacing(2);
   hbox1.set_spacing(2);
      
   button.signal_clicked().connect(sigc::mem_fun(*this,&window::click_button));
   close.signal_clicked().connect(sigc::mem_fun(*this, &window::close_button));
   summ.signal_clicked().connect(sigc::mem_fun(*this, &window::somma_button));
   clear.signal_clicked().connect(sigc::mem_fun(*this, &window::clear_button));
   dia.signal_clicked().connect(sigc::mem_fun(*this, &window::dialog_button));
   
   hbox.pack_start(label);
   hbox.pack_start(entry3);
   hbox1.pack_start(close);
   hbox1.pack_start(dia);
   
   add(vbox);
   
   vbox.pack_start(button);
   vbox.pack_start(hbox1);
   vbox.pack_start(summ);
   vbox.pack_start(clear);
   vbox.pack_start(entry);
   vbox.pack_start(entry1);
   vbox.pack_start(entry2);
   vbox.pack_start(hbox);
   
   show_all();
}

window::~window()
{
}   

void window::click_button()
{
   stringa = button.get_label();
   if (stringa == "Ciao Mondo!")
   { 
      entry.set_text(stringa);
      button.set_label("Clicca ancora:)");
   }
   else
   {
      stringa = "Ciao Mondo!";   
      button.set_label(stringa);
      stringa = "Clicca ancora:)";
      entry.set_text(stringa);
   }     
}

void window::close_button()
{
   hide(); //Chiude l'applicazione
}

void window::somma_button()
{
   istringstream in, in2;//Uso sstream per convertire la stringa in numero 
   ostringstream out;//Uso sstream per convertire il numero in stringa

   stringa = entry1.get_text();//prendo la stringa iniziale
   in.str(stringa);//la inserisco nella variabile in e la converto in numero
   in>>a;//la posiziono in a
   
   s=entry2.get_text();
   in2.str(s);
   in2>>b;
   
   c=a+b;//eseguo la somma
   
   out<<c;//la posiziono in out per riconvertire in stringa il numero ottenuto
   o=out.str();//converto il numero in stringa e la metto in s
   entry3.set_text(o);//stampo il valore ottenuto
}

void window::clear_button()
{
   entry.set_text("Clicca il pulsante!");
   entry1.set_text("");
   entry2.set_text("");
   entry3.set_text("");
}

void window::dialog_button()
{
   dialogo dialogo("questo è un esempio");
   //dialogo.set_secondary_test("prova testo secondario");
   int iResult = dialogo.run();
	std::cout << "dialog result =" << iResult << endl;
}


int main(int argc, char *argv[])
{
   Gtk::Main kit(argc, argv);
   window win;
   Gtk::Main::run(win);  
   return 0;
}
[/php]

---

### Post by LuxVan on 2010-11-23
Thank you very much!!!!!! It work!!!! \\:D/
Now I have another question: Why my dialog have all (maximize, minimize and close), buttons?
How I can delete the maximize button?
Can you explain me this: ```
dialogo(const char *pTitle);
```
*pTitle is the title of dialog?

> Me 'spiace molto ma non so scrivere in Italiano
Your italian is good!;) If you want, you can correct it so:
> Mi dispiace, ma non so scrivere in italiano
Where are you from?:popcorn:

---

### Post by worksofcraft on 2010-11-23
> **LuxVan said:**
> Thank you very much!!!!!! It work!!!! \\:D/
Now I have another question: Why my dialog have all (maximize, minimize and close), buttons?
How I can delete the maximize button?

yes, these are what they call "window decorations" and the default is that they get added by the window manager to all windows.
Gtk:: Dialog is a sub-class of Gtk::Window so you can use all the standard methods of Gtk::Window on a Gtk:: Dialog. E.g. include in your dialogo constructor the following to get rid of them:
```

	set_decorated(false); // don't add window manager decorations (like close and minimize)

```

> 
Can you explain me this: ```
dialogo(const char *pTitle);
```
*pTitle is the title of dialog?

Yes, in your dialogo constructor is a call to set_title(pTitle).
This is also a method of Gtk::Window and you can find a description of all your Gtk::Window methods at [http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Window.html](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Window.html)

From reading earlier replies you received I see I must apologize for confusing things by declaring it as a pointer to const char * when others have been telling you to use C++ std::string and Glib::ustring. I was using a C style string which is simply a pointer to characters.

If it were my code I would rewrite this class more succinctly as follows.
[php]
struct dialogo: Gtk::Dialog {
      dialogo(const Glib::ustring & rTitle);
};         

dialogo::dialogo(const Glib::ustring & rTitle): Gtk::Dialog(rTitle, true) {
	// don't add window manager decorations (like close and minimize)
	set_decorated(false);
	add_button("OK", 0)	;
	add_button("ANNULLA", 1);
	show_all_children();
}
[/php]

OTOH, I've been told that other people don't like the way I write code :(

> 
 Your italian is good!...

Where are you from?:popcorn:
Grazie tante :)
Sono della Nuova Zelanda

---

### Post by LuxVan on 2010-11-24
Thank you very much it work and I have understand another bit of gtkmm!!
I have wrote this code:
```
#include"dialog.h"
#include<gtkmm.h>

dialogo::dialogo()
{
   set_title("Primo dialgo");
   set_default_size(200,200);
   add_button("ok",0);
   add_button("annulla",1);   
   
   label.set_text("Prova di una label nella dialog.");
   
   add_action_widget(label,0);
   
   
   set_resizable(false);
   
   show_all_children();
}
```
but label is near to "ok" and "annulla" buttons...and I do not want it.
I would like the label is over the button...
How I can to add widget in my dialog?

```
Grazie tante
Sono della Nuova Zelanda 
```
Bella! La Nuova Zelanda è un bellissimo posto...
Il mio sogno è quello di vivere a Auckland, oppure a Sydney, in Australia.
Ma il mio inglese non è molto buono....
Io invece sono di Napoli...la città è bella, ma la gente non lo è.
Ciao.

---

### Post by SledgeHammer_999 on 2010-11-24
1. If you want to just have an "x" button and not a minimize/maximize button you could also use these:
[Gtk::Window::set_skip_taskbar_hint()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Window.html#a0b88348a3d7c69b8930a0e2e11a63a88) <--- this removes the minimize button
[Gtk::Window::set_resizable](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Window.html#a1ec816449fe941e5fe330bfa509eeb7f) <---- this removes the maximize button.

An example from your code would be:
[php]
dialogo::dialogo()
{
   set_title("Primo dialgo");
   set_default_size(200,200);
   add_button("ok",0);
   add_button("annulla",1);
   set_resizable(false);
   set_skip_taskbar_hint(true);   
   
   label.set_text("Prova di una label nella dialog.");
   
   add_action_widget(label,0);
   
   
   set_resizable(false);
   
   show_all_children();
}
[/php]

2. About your label's location. From the Gtk::Dialog's [docs](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Dialog.html):
> gtkmm treats a dialog as a window split vertically. The top section is a Gtk::VBox, and is where widgets such as a Gtk::Label or a Gtk::Entry should be packed. The bottom area is known as the action_area. This is generally used for packing buttons into the dialog which may perform functions such as cancel, ok, or apply. The two areas are separated by a Gtk::HSeparator. 
I think what this means is that the bottom section acts as a Gtk::HButtonBox(this is hinted by the return type of [Gtk::Dialog::get_action_area()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Dialog.html#ae56668b63a4f134c7135e98b74f2acab) ) that's why the label is beside the buttons and not above/below them. And when you use add_action_widget() it puts the widgets in this "horizontal box". Obviously you need a way to add your label in the Gtk::VBox above. Hopefully there is this function-> [Gtk::Dialog::get_vbox()](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1Dialog.html#a137564e57b5a35e69b4eeb88bfe81715)

So to sum it up, in your code you should do something like this:
[php]
dialogo::dialogo()
{
   set_title("Primo dialgo");
   set_default_size(200,200);
   add_button("ok",0);
   add_button("annulla",1);   
   
   label.set_text("Prova di una label nella dialog.");
   
   Gtk::Box *box = get_vbox();
   box->pack_start(label, false, false);
   
   
   set_resizable(false);
   
   show_all_children();
}
[/php]

NOTE: I haven't tested the above code examples. I currently don't have access to my build machine.

One serious question: Why don't you use a [Gtk::MessageDialog](http://library.gnome.org/devel/gtkmm/unstable/classGtk_1_1MessageDialog.html) instead?

---

### Post by LuxVan on 2010-11-26
Thank you very much!;)
> One serious question: Why don't you use a Gtk::MessageDialog instead?

Only for learning! I am only a c++/gtkmm beginner programmer, and I am learning only in my free time....
If you know a best method for learning, you can suggest it , to me!;)

---

### Post by SledgeHammer_999 on 2010-11-26
Well, if it's for learning, then is no better way than experimenting. So keep working.

---


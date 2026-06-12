---
title: "C++ Passwrd Generator"
date: 2009-09-25
forum: Programming Talk
---

### Post by matmatmat on 2009-09-25
```

/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */

#include <libglademm/xml.h>
#include <gtkmm.h>
#include <iostream>
#include <string.h>
#include <cstdlib> 
#include <ctime> 


#ifdef ENABLE_NLS
#  include <libintl.h>
#endif


/* For testing propose use the local (not installed) glade file */
/* #define GLADE_FILE PACKAGE_DATA_DIR"/passwrdgenerator/glade/passwrdgenerator.glade" */
#define GLADE_FILE "passwrdgenerator.glade"

using namespace std;

Gtk::Window* main_win = 0;
Gtk::CheckButton* letters = 0;
Gtk::CheckButton* numbers = 0;
Gtk::CheckButton* symbols = 0;
Gtk::SpinButton* lengthb = 0;
Gtk::Entry* password = 0;

int length;
int randn;

string passwrd;
string choice;	

void on_generate()
{
	choice = "";
	passwrd = "";
	length = 0;
	randn = 0;
	srand((unsigned)time(0)); 
	if (letters->get_active())
	{
		choice += "qwertyuiopasdfghjklzxcvbnm";
	}
	if (numbers->get_active())
	{
		choice += "1234567890";
	}
	if (symbols->get_active())
	{
		choice += "!$%^&*~#@<>";
	}
	length = lengthb->get_value_as_int();
	if (length == 0){
		cout << length;
		return;
	}	
	int i;
	const char* cchoice = choice.c_str();
	for(i=0;i<length;i++){
		randn = (rand()%strlen(cchoice))+1;
		passwrd += cchoice[randn];
	}
	password->set_text(passwrd);
}

void on_quit()
{
    main_win->hide();
}
   
int
main (int argc, char *argv[])
{
	Gtk::Main kit(argc, argv);

	Gtk::Button* generate = NULL;
	Gtk::Button* quit = NULL;
	
	//Load the Glade file and instiate its widgets:
	Glib::RefPtr<Gnome::Glade::Xml> refXml;
	try
	{
		refXml = Gnome::Glade::Xml::create(GLADE_FILE);
	}
	catch(const Gnome::Glade::XmlError& ex)
    {
		std::cerr << ex.what() << std::endl;
		return 1;
	}
	
	refXml->get_widget("main_window", main_win);
	refXml->get_widget("generate", generate);
	refXml->get_widget("quit", quit);
	refXml->get_widget("letters", letters);	
	refXml->get_widget("numbers", numbers);
	refXml->get_widget("symbols", symbols);
	refXml->get_widget("length", lengthb);
	refXml->get_widget("password", password);
	
	if (quit){
		quit->signal_clicked().connect(sigc::ptr_fun(&on_quit));
	}
	if (generate){
		generate->signal_clicked().connect(sigc::ptr_fun(&on_generate));
	}
	if (main_win)
	{
		kit.run(*main_win);
	}
	return 0;
}


```
it generates passwords that aren't the correct length

---

### Post by Arndt on 2009-09-25
> **matmatmat said:**
> ```

/* -*- Mode: C; indent-tabs-mode: t; c-basic-offset: 4; tab-width: 4 -*- */

#include <libglademm/xml.h>
#include <gtkmm.h>
#include <iostream>
#include <string.h>
#include <cstdlib> 
#include <ctime> 


#ifdef ENABLE_NLS
#  include <libintl.h>
#endif


/* For testing propose use the local (not installed) glade file */
/* #define GLADE_FILE PACKAGE_DATA_DIR"/passwrdgenerator/glade/passwrdgenerator.glade" */
#define GLADE_FILE "passwrdgenerator.glade"

using namespace std;

Gtk::Window* main_win = 0;
Gtk::CheckButton* letters = 0;
Gtk::CheckButton* numbers = 0;
Gtk::CheckButton* symbols = 0;
Gtk::SpinButton* lengthb = 0;
Gtk::Entry* password = 0;

int length;
int randn;

string passwrd;
string choice;	

void on_generate()
{
	choice = "";
	passwrd = "";
	length = 0;
	randn = 0;
	srand((unsigned)time(0)); 
	if (letters->get_active())
	{
		choice += "qwertyuiopasdfghjklzxcvbnm";
	}
	if (numbers->get_active())
	{
		choice += "1234567890";
	}
	if (symbols->get_active())
	{
		choice += "!$%^&*~#@<>";
	}
	length = lengthb->get_value_as_int();
	if (length == 0){
		cout << length;
		return;
	}	
	int i;
	const char* cchoice = choice.c_str();
	for(i=0;i<length;i++){
		randn = (rand()%strlen(cchoice))+1;
		passwrd += cchoice[randn];
	}
	password->set_text(passwrd);
}

void on_quit()
{
    main_win->hide();
}
   
int
main (int argc, char *argv[])
{
	Gtk::Main kit(argc, argv);

	Gtk::Button* generate = NULL;
	Gtk::Button* quit = NULL;
	
	//Load the Glade file and instiate its widgets:
	Glib::RefPtr<Gnome::Glade::Xml> refXml;
	try
	{
		refXml = Gnome::Glade::Xml::create(GLADE_FILE);
	}
	catch(const Gnome::Glade::XmlError& ex)
    {
		std::cerr << ex.what() << std::endl;
		return 1;
	}
	
	refXml->get_widget("main_window", main_win);
	refXml->get_widget("generate", generate);
	refXml->get_widget("quit", quit);
	refXml->get_widget("letters", letters);	
	refXml->get_widget("numbers", numbers);
	refXml->get_widget("symbols", symbols);
	refXml->get_widget("length", lengthb);
	refXml->get_widget("password", password);
	
	if (quit){
		quit->signal_clicked().connect(sigc::ptr_fun(&on_quit));
	}
	if (generate){
		generate->signal_clicked().connect(sigc::ptr_fun(&on_generate));
	}
	if (main_win)
	{
		kit.run(*main_win);
	}
	return 0;
}


```
it generates passwords that aren't the correct length

Why not?

---

### Post by MadCow108 on 2009-09-25
your random number is off by one
drop the + 1

also this is very bad code:
randn = (rand()%strlen(cchoice))+1;

strlen is a O(N) operation it interates over every character until it finds the end
either do it once and save the length
or use strings and theith .length() method instead

btw there is no need to convert to cstrings the c++ strings also have the [] operator overloaded

---

### Post by dwhitney67 on 2009-09-25
And do not forget to allow for uppercase letters.  That could probably be added here:
```

	if (letters->get_active())
	{
		choice += "qwertyuiopasdfghjklzxcvbnm";
	}

```

Also, ensure that the passwords are valid to one's specification; ie it must contain at least one uppercase letter, at lease one number, etc.  It seems your code only takes 'length' random characters from the available pool of characters, but does not take into consideration the criteria that one may require to use for their password.

---


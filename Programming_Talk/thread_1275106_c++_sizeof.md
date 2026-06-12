---
title: "c++ sizeof"
date: 2009-09-25
forum: Programming Talk
---

### Post by matmatmat on 2009-09-25
I have this code:
```

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
[B]	const char* cchoice = choice.c_str();
	cout << sizeof(cchoice) << "\n";
	for(i=0;i<=length;i++){
		randn = (rand()%sizeof(cchoice)/sizeof(char))+1;
		passwrd += cchoice[randn];
	}
	cout << passwrd << "\n";
	cout << choice << "\n";[/B]
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
the sizeof doesn't work, it is always 4.

---

### Post by napsy on 2009-09-25
The sizeof operator gives you the size of char * type. What size do you expect?

---

### Post by MadCow108 on 2009-09-25
sizeof is a compile time operator and can be very dangerous when used wrong like you did
it can not be used to determine the size of something which is not know at compile time

it returns the length of the variable/type you give it
in your case this is a string, strings have the size 4 in most implementations
this is not the length of the string because that is allocated dynamically and the string just keeps a pointer to this memory
use the length() method to get the length

edit: just saw you use a char pointer, which are also length 4 byte in 32 bit systems

---

### Post by imbjr on 2009-09-25
> **matmatmat said:**
> I have this code:
```

[B]	const char* cchoice = choice.c_str();
	cout << sizeof(cchoice) << "\n";
	for(i=0;i<=length;i++){
		randn = (rand()%sizeof(cchoice)/sizeof(char))+1;
		passwrd += cchoice[randn];
	}
	cout << passwrd << "\n";
	cout << choice << "\n";[/B]

```
the sizeof doesn't work, it is always 4.

That's because cchoice is a pointer to a char and pointers usually are made of 4 bytes no matter what they are pointing at.

---

### Post by matmatmat on 2009-09-25
How should I find the size?

---

### Post by imbjr on 2009-09-25
> **matmatmat said:**
> How should I find the size?

If I understand your code correctly, you need strlen to find the length of the string.

---

### Post by MadCow108 on 2009-09-25
strlen would be inefficient as he already has the length
it is saved inside the string
but strlen is the way to go if you don't have other knowledge and the string is null terminated

just do: unsigned int len = choice.length();

---

### Post by imbjr on 2009-09-25
> **MadCow108 said:**
> strlen would be inefficient as he already has the length
it is saved inside the string
but strlen is the way to go if you don't have other knowledge and the string is null terminated

just do: unsigned int len = choice.length();

Yes, I just realised the full context of the code.

---

### Post by matmatmat on 2009-09-25
> **imbjr said:**
> If I understand your code correctly, you need strlen to find the length of the string.
Thanks, that's it

---


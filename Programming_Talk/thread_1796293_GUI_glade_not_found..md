---
title: "GUI glade not found."
date: 2011-07-03
forum: Programming Talk
---

### Post by akshay.sulakhe on 2011-07-03
Hello guys,i am running a program of messaging,everytime i run it,i get the error gui/gui.glade not found. As far as i have researched GMP is missing,i have already installed it. I dont know why GMP is not found. Can anyone tell me what shall i do so that it can be find my other programs also. Link for GMP is :- [http://gmplib.org/](http://gmplib.org/)

Also is it because of that i am getting the error.Kindly let me know guys. I am also pasting the catch statement of the code.

#include <gtkmm/main.h>
#include <gtkmm/builder.h>
#include <gtkmm/messagedialog.h>
#include <iostream>
#include <boost/lexical_cast.hpp>
#include <boost/date_time/posix_time/posix_time.hpp>

#include "SetupWindow.h"
#include "ChatWindow.h"

#include "ChatApplication.h"

ChatApplication::ChatApplication() : network(this)
{
	setupWindow = NULL;
	chatWindow = NULL;
}

ChatApplication::~ChatApplication()
{
	if(NULL != setupWindow) delete setupWindow;
	if(NULL != chatWindow) delete chatWindow;
}

int ChatApplication::run()
{
	Glib::RefPtr<Gtk::Builder> builder;
	std::string guiFile = "gui/gui.glade";

	try
	{
		builder = Gtk::Builder::create_from_file(guiFile);
	} catch (Glib::FileError fe)
	{
		std::cerr << "Could not load GUI file: " << fe.what() << std::endl;
		return 1;
	} catch (Gtk::BuilderError be)
	{
		std::cerr << "Error while parsing GUI file: " << be.what() << std::endl;
		return 1;
	} catch (Glib::MarkupError me)
	{
		std::cerr << "Error while loading GUI file: " << me.what() << std::endl;
		return 1;

---

### Post by akshay.sulakhe on 2011-07-03
There is a file named glade.gui already present,i thought the program cant find it,so i even placed it in many places in different folders.still,no luck

---

### Post by smilinggoomba on 2011-07-03
Errors like this happen if the compiler can't find a file that the program refers to.  Are you sure that gui glade exists?

---

### Post by akshay.sulakhe on 2011-07-03
100 percent sure. i can see that file,i even pasted it around,to avoid it searching everywhere.still no luck. i am also uploading the whole code file,and the gui file too.

---


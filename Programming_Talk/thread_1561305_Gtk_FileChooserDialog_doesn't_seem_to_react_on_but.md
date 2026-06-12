---
title: "Gtk FileChooserDialog doesn't seem to react on button input."
date: 2010-08-26
forum: Programming Talk
---

### Post by Pistolpete2 on 2010-08-26
Hi,

I wanna make an application using Glade and Gtk so that the users can use a graphical user interface.  But I don't get the FileChooserDialog to work.  Currently I use the stock FileChooserDialog from within glade and I do the following:

```

builder->get_widget("filechooserdialogSave",pSaveDialog); //filechooserdialogSave is defined in .glade file
pSaveDialog->add_button(Gtk::Stock::CANCEL, Gtk::RESPONSE_CANCEL);
pSaveDialog->add_button("Save", Gtk::RESPONSE_OK);

/* The Dialog opens when btnOutput is clicked */
void on_btnOutput_clicked(){
	int result = pSaveDialog->run();
	switch(result){
	case(Gtk::RESPONSE_OK):
	{
		std::cout << "Folder Selected: "<< pSaveDialog->get_uri() <<std::endl;
		break;
	}
	case(Gtk::RESPONSE_CANCEL):
		std::cout << "Cancel clicked." << std::endl;
		break;
	default:
		std::cout<< "Unexpected program flow"<<std::endl;
		break;
	}


}

```

All the code seems to work fine but the program doesn't react on the buttons Save and Cancel.  It's only when I press the close button of the Dialog that the app print's out the appropriate string.  E.g.  I open the Dialog and I click cancel.  Nothing happens but If I close the Dialog "Cancel clicked" will be printed to console.

In the dialog the stock buttons (e.g. creating a new folder) do work the way I want, so I only got the problem with the buttons I defined.

First I added Save button in glade but then I had the same problem.  It looks like a problem with a thread who only starts after the dialog is finished but I can't seem to find the problem.

I hope anybody can help me.

Thanks!

---

### Post by Pistolpete2 on 2010-08-26
Apparently it's working now but I don't know the reason why.  Because I didn't change the code for the fileChooserDialog (I only added code for other parts), is it possible that a Clean & Build has solved my problem?

I'm glad that it's working now but I like to know why :-).

---


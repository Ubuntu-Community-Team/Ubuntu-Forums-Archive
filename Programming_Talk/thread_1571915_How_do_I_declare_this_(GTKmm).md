---
title: "How do I declare this? (GTKmm)"
date: 2010-09-10
forum: Programming Talk
---

### Post by fallenshadow on 2010-09-10
I want to declare this response signal to solve this error.

```
mainwindow.cc:768: error: no ‘void MWindow::on_action_file_new_response(gint)’ member function declared in class ‘MWindow’

```

I know I can declare things in "mainwindow.h" because I have all my declarations for "mainwindow.cc" in there.

However I don't know exactly what I have to declare for a response signal. Any ideas?

---

As Im posting... another problem I have is this small section of code. I think it needs to be changed because "main" is included in similar code in "main.cc".

CODE FROM MAIN.CC
```

int main(int argc, char *argv[])
{
  Gtk::Main kit(argc, argv);

  MWindow window;
  //Shows the window and returns when it is closed.
  Gtk::Main::run(window);

  return 0;
}

```

CODE FROM NEWFILE.CC
```

int main (int argc, char **argv)
{
	Gtk::Main kit(argc, argv);
	
	newDialog win;
	Gtk::Dialog *app = win.get_app();
		
	kit.run(*app);

	return 0;
}

```

As you can see both sections are similar and seem to cause bugs with the app. I think the "newfile.cc" code needs to be changed in someway for this to work.

---

### Post by kahumba on 2010-09-10
This is how you can do it:
> 
I declare that this response signal must solve this error!

Please let me know if this worked for you.

---

### Post by fallenshadow on 2010-09-10
> This is how you can do it:
Quote:
I declare that this response signal must solve this error!
Please let me know if this worked for you.

Haha very helpful! :D :p

---

### Post by kahumba on 2010-09-10
The header file of the MWindow class should contain something like this:
[PHP]
virtual void on_action_file_new_response(gint);
[/PHP].. and in the clas file:
> void MWindow:: on_action_file_new_response(gint num) {
std::cout << "something happened" << std::endl;
}As to the second question: afaik you may **not** have 2 main() functions inside same application.

---

### Post by fallenshadow on 2010-09-10
Here is what happens when I declare like you showed me.

```

mainwindow.cc: In member function ‘virtual void MWindow::on_action_file_new_response(gint)’:
mainwindow.cc:770: error: ‘response_id’ was not declared in this scope
mainwindow.cc:770: error: expected ‘)’ before ‘{’ token
mainwindow.cc:773: warning: suggest braces around empty body in an ‘if’ statement
mainwindow.cc: At global scope:
mainwindow.cc:768: warning: unused parameter ‘respsonse_id’

```

Hmm... as for the second thing. I don't want 2 main functions inside my application. However when I attempt to change the one in "newfile.cc" I end up with lots and lots of errors. 

I don't know how to change it to make it work.

---

### Post by kahumba on 2010-09-10
You need to post (all) your source code (i.e. as a zip file), otherwise people are left guessing what could be wrong, from the looks you have several typos/mistakes in your code.

---

### Post by fallenshadow on 2010-09-10
Ok here is the full source im working with at the moment.

I changed the second main function and now my code compiles but various things are messed up.

To test what im talking about. Compile the code. Click on "New" in the "File" menu.

Notice that the really tiny blob that appears is actually a window. (its not meant to be there but somehow it is)

The declaration thing isnt actually all that important. Whats more important is figuring out what the hell is happening! I have no idea how this is going wrong myself.

---

### Post by pbrane on 2010-09-10
newfile.cc was written as an example of creating and running a dialog from a glade file. You can't reuse the newDialog code as is. First thing to do is remove the main() function from newfile.cc. I don't think this particular class is going to work as it is written. Part of your program uses glade and part of it doesn't. You need to rework the mainWindow class so that it loads the glade file. And then it can load and run the newDialog.

---

### Post by kahumba on 2010-09-11
In file mainwindow.cc at approximately line 740 you got
[PHP]
newDialog dlg;
dlg.run();
[/PHP]Remove the last line and the blob from action File->New won't appear anymore.

A little cleanup should help too I guess, the "newfile" files should be renamed to the class they contain (newDialog, which should also be renamed to start with upper case, thus "NewDialog").
And the function int newfile (int argc, char **argv) from newfile.cc isn't needed at all because the constructor of newDialog is used instead to create and show this dialog.

---

### Post by kahumba on 2010-09-11
And btw thanks for posting the full source code for your app I'm now trying to sell your app on the black market.

---

### Post by fallenshadow on 2010-09-11
Good luck trying to sell something that does nothing! :D

Its from my own personal project: PhotoFiltre LX. However its in the early stages and doesn't do anything yet.

Thanks for helping me out with those fixes. That stupid blank window is now gone. I also got rid of that int function in "newfile.cc".

However when the newDialog is opened from the "New" button its missing the comboboxes. I have 2 pics here... one shows the newDialog running on its own. The other shows it running after "New" is clicked.

I have a feeling the class information or some part of newDialog is not being read and used in the compilation.

---

### Post by fallenshadow on 2010-09-12
Ok I got this sorted thanks to pbrane! :)

Kahumba would you like to be listed as a contributor to the project? (since you did contribute to the codebase.)

PM me your name if you want your name listed... or alternatively I can just use your forum name. :)

---


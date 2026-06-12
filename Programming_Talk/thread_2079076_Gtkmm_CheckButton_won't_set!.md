---
title: "Gtkmm: CheckButton won't set?!"
date: 2012-11-01
forum: Programming Talk
---

### Post by fallenshadow on 2012-11-01
Can't someone explain why on earth this won't set the checkButton?

```

Gtk::CheckButton *checkbutton;
refBuilder->get_widget("maximize", checkbutton);
checkbutton->set_active(true);
```

Its driving me insane at this point! :mad:

---

### Post by spjackson on 2012-11-01
Well, that looks fine to me, in principle. Some wild guesses... Maybe get_widget isn't getting the widget you think it is. Or maybe you have some other code that calls set_active(false), or in some other way overrides what is happening here before the screen gets painted.

---

### Post by fallenshadow on 2012-11-01
Here is some more complete code:

```

getline (myfile,line);
cout << line << endl;

if(line.compare("maximize=1")==0)
{
  cout << "Maximize checked" << endl;
  Gtk::CheckButton *checkbutton;
  refBuilder->get_widget("maximize", checkbutton);
  checkbutton->set_active(true);
  bool maxStatus = checkbutton->get_active();
  cout << maxStatus << endl;
}

```

Output:
> 
maximize=1
Maximize checked
1


So the comparison is successful with the value read in from the file. Somehow it just won't set the checkButton. It is not being set to false from anywhere else. :/

---

### Post by SledgeHammer_999 on 2012-11-01
Can you post the glade file? Are you sure that "maximize" identifies a checkbutton?

---

### Post by fallenshadow on 2012-11-01
Yes it does! No need to post the full file, I did all the basic checks already.

[IMG]http://i47.tinypic.com/5f5d15.png[/IMG]

---

### Post by fallenshadow on 2012-11-05
My code snippet is from around line 60 on this file:

[http://bazaar.launchpad.net/~dylan-coakley/photofiltre-lx/main/view/head:/src/prefs.cc](http://bazaar.launchpad.net/~dylan-coakley/photofiltre-lx/main/view/head:/src/prefs.cc)

(but the problem might be elsewhere in this file or in my mainwindow file.

Any help on the matter is appreciated! :)

---

### Post by SuperCamel on 2012-11-05
I'm just perusing your code. I recommend checking for NULL pointers after calling get_widget(), just to protect against potential seg faults.

I can't see anything that would cause your problem though. Perhaps you could post the entire project?

---

### Post by fallenshadow on 2012-11-06
The whole of my current codebase can be downloaded here:

[http://bazaar.launchpad.net/~dylan-coakley/photofiltre-lx/main/tarball/125](http://bazaar.launchpad.net/~dylan-coakley/photofiltre-lx/main/tarball/125)

Compile using the make system or using the simple compile script in the src folder. 

To test: 

Go to Tools>>Preferences. Click Startup tab. Click the "Maximize on startup" checkButton. The click the Ok button to confirm.

The restart the app. The checkButton is supposed to be active but it is not for some unknown reason.

---

### Post by SuperCamel on 2012-11-06
Got it! 

```
while ( myfile.good() ) 
            {
                getline (myfile,line);
                cout << line << endl;
                if(line.compare("maximize=1")==0)
                {
                    cout << "Maximize checked" << endl;
                    Gtk::CheckButton *checkbutton;
                    refBuilder->get_widget("maximize", checkbutton);
                    checkbutton->set_active(true);
                    bool maxStatus = checkbutton->get_active();
                    cout << maxStatus << endl;
                }
                if(line.compare("maximize=0")==0) //this was else if(line.compare("maximize=0")!=0)

                //that meant any line read in that was NOT "maximise=1" would uncheck the button. 
                {
                    //maximize unchecked
                    cout << "Maximize unchecked" << endl;
                    Gtk::CheckButton *checkbutton;
                    refBuilder->get_widget("maximize", checkbutton);
                    checkbutton->set_active(false);
                }
            }
```

---

### Post by SuperCamel on 2012-11-06
Also, does your prefsDialog class inherit Gtk::Dialog for any reason?

I think you may want to check out Gtk::Builder::get_widget_derived(). It allows you to create a class that inherits a widget, and then load the widget from a glade file. It's very useful.

---

### Post by fallenshadow on 2012-11-06
Awesome! :cool: You just saved me from insanity! :o

Funnily enough this was the first feature I had working. I developed further features and then replaced the version on my Launchpad. However, I never noticed this bug until now! 

This shall only remind me to test more often in case I go breaking things in my code without realising it! :)

My preferences inherits Gtk:: Dialog because its a dialog I guess. Thats about the only reason for doing it! :D

I will check out Gtk::Builder::get_widget_derived(). Thanks for the tip!

---


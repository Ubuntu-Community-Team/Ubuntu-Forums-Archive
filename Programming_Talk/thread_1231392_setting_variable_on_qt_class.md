---
title: "setting variable on qt class"
date: 2009-08-04
forum: Programming Talk
---

### Post by slaiyer on 2009-08-04
Hello, i am trying to pass a variable from one class to another, well, from one qt window to another. The user will log in, then the username they used to log in gets carried to the main window. I have everything working except that the username is not getting carried forward.

```
main_window::main_window() {
    widget.setupUi(this);
    //This should load the username
    QString value = this->get_username();
   
    qDebug("%s", qPrintable(value));
    widget.user_namelbl->setText(value);


   this->load();
    
}
```
The code above is the one for the main window. The qDebug is also blank, which i guess means that the username wasnt set.


```
       
{
 main_window *mainWin = new main_window;
        mainWin->show();
        carrier =usr_name;
        mainWin->set_username(carrier);
        close();
}
```

This is the code from the log in window which passes the username to the set_username function which sets the variable username in the class.

---

### Post by dwhitney67 on 2009-08-04
Whoa!... In your main_window() constructor, there is no initialization until you get to the body of the constructor.  How do you expect get_username() to provide any significant data?

In case you are a newbie to C++...
```

class MyClass
{
public:
   MyClass();   // constructor declaration
private:
   int _data;   // member data
};

MyClass::MyClass()    // constructor implementation
  :  _data(20)        // example of class initialization
{
   // constructor body... occurs after initialization

   assert(_data == 20);
}

```
Now, looking at the code you supplied in the OP, I see widget object being used, but never initialized.  Perhaps it has a no-arg constructor?

Then magically, you access this->get_username() where somehow I suppose the user name has been initialized.  If so, it is not apparent from the code you posted.

---

### Post by slaiyer on 2009-08-05
hahahaha...that was the most stupid error i have made, had totally fogotten.. thanks.

---


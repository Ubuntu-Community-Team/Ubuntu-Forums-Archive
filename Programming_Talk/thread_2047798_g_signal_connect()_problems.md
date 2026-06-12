---
title: "g_signal_connect() problems"
date: 2012-08-25
forum: Programming Talk
---

### Post by hakermania on 2012-08-25
Hello there!

I've seen this thread: [http://ubuntuforums.org/showthread.php?t=1476814](http://ubuntuforums.org/showthread.php?t=1476814) and, to tell the truth, I've though of exactly the same thing. The thing is that it doesn't let me use 'this' in static void functions, which is logical, I never could.

I just need a way to connect, using g_signal_connect() a menu item to a non-static void function and to tell the truth I don't really care if this can be done directly or indirectly.

By the way, why doesn't g_signal_connect() support non-static function? Isn't it quite weird?

Thanks in advance for any help and sorry, but I develop in QtCreator and I am not familiar with such code.

---

### Post by SledgeHammer_999 on 2012-08-25
Since I have done the same thing on gstreamer and g_signal_connect() I will try to clarify the way you do it. I am a bit sleepy right now though...

First of all the example code on your link is incomplete and maybe wrong. Here is a better example(I am writing it by memory so it may not be entirely correct):

Class prototype:
[php]class myClass
{
private:
    void connect_function();
    static void fake_callback(...,gpointer data); //this MUST have the exact parameter signature that the signal you're connecting to expects.
    void actual_callback(); //this can have any parameters you like or none at all. Normally you make the same parameter signature as the fake_callback() minus the 'data' variable  
};[/php]

Class implementation:
[php]
void myClass::connect_function() {
g_signal_connect(...,G_CALLBACK(fack_callback),(gpointer)this);
}

void myClass::fake_callback(...,gpointer data)  {

     myClass* instance = (myClass*)data;
     instance->actual_callback();
}
    
void myClass::actual_callback()  {
//do something here
}[/php]

Also I think that your static methods should be public in order to work. The "actual_callback()" can be private of course.

You cannot use non-static methods in C callbacks they cannot be called directly by the C code. Static functions are seen by C code as standalone functions and thus can be called by it. I am sure someone else can explain it more technically than me :p

---

### Post by SledgeHammer_999 on 2012-08-25
Similar question by me 4 years ago.

[http://ubuntuforums.org/showthread.php?t=870076](http://ubuntuforums.org/showthread.php?t=870076)

Contains solutions too.

---

### Post by hakermania on 2012-08-26
Thanks for your answers. Let's see what I am doing....

Creation of the Unity Quicklist and connection (mainwindow.cpp):

```
void MainWindow::enable_unity_quicklist(){
    Unity_Menu = dbusmenu_menuitem_new();

    dbusmenu_menuitem_property_set_bool (Unity_Menu, DBUSMENU_MENUITEM_PROP_VISIBLE, FALSE);

    Unity_Stop = dbusmenu_menuitem_new();
    dbusmenu_menuitem_property_set(Unity_Stop, DBUSMENU_MENUITEM_PROP_LABEL, "Stop");

    dbusmenu_menuitem_child_append (Unity_Menu, Unity_Stop);

    **g_signal_connect (Unity_Stop, DBUSMENU_MENUITEM_SIGNAL_ITEM_ACTIVATED, G_CALLBACK(&fake_callback), (gpointer)this);**

    if(!unity_entry)
        unity_entry = unity_launcher_entry_get_for_desktop_id("myapp.desktop");

    unity_launcher_entry_set_quicklist(unity_entry, Unity_Menu);

    dbusmenu_menuitem_property_set_bool(Unity_Menu, DBUSMENU_MENUITEM_PROP_VISIBLE, true);
    dbusmenu_menuitem_property_set_bool(Unity_Stop, DBUSMENU_MENUITEM_PROP_VISIBLE, true);
}

void MainWindow::fake_callback(gpointer data){
    MainWindow* m = (MainWindow*)data;
    m->on_stopButton_clicked();
}

void MainWindow::on_stopButton_clicked(){
   //stopping the process...
}

```

mainwindow.h:

```
private slots:
   void enable_unity_quicklist();
   void on_stopButton_clicked();
public slots:
   static void fake_callback(gpointer data);
```

The program crashes immediately after I choose the 'Stop' action from the Unity Quicklist. Debugging the program shows that I am not able to access anything MainWindow related inside the on_stopButton_clicked() without crashing. For example, it crashes when doing this check (which is the first 2 lines of code inside this function):
```
if (!ui->stopButton->isEnabled())
        return;
```

Thanks for trying to help...

---

### Post by SledgeHammer_999 on 2012-08-26
The crash is almost certainly related to NOT providing a function with the correct parameter signature as callback function. Although the docs are very clear on this the fake_callback parameter signature should be like this:

[php]
void fake_callback(DbusmenuMenuitem* mi, gpointer data)
{
//something
}
[/php]

C style callbacks/signals won't give a compile time error, only at runtime they will error(crash) if you pass the wrong parameters at *_connect(). On the other hand C++ style signals will error at compile time when you're connecting with the wrong parameters(although gcc will give some cryptic error deescription)

---

### Post by hakermania on 2012-08-27
> **SledgeHammer_999 said:**
> The crash is almost certainly related to NOT providing a function with the correct parameter signature as callback function. Although the docs are very clear on this the fake_callback parameter signature should be like this:

[php]
void fake_callback(DbusmenuMenuitem* mi, gpointer data)
{
//something
}
[/php]

C style callbacks/signals won't give a compile time error, only at runtime they will error(crash) if you pass the wrong parameters at *_connect(). On the other hand C++ style signals will error at compile time when you're connecting with the wrong parameters(although gcc will give some cryptic error deescription)

Thanks for answering. Where is this being said by the docs? What am I supposed to do with the passed 'mi' item?

---

### Post by hakermania on 2012-08-28
The problem was solved. Please see [http://askubuntu.com/questions/180395/what-is-the-correct-way-to-use-g-signal-connect-in-c-for-dynamic-unity-quick](http://askubuntu.com/questions/180395/what-is-the-correct-way-to-use-g-signal-connect-in-c-for-dynamic-unity-quick)

---


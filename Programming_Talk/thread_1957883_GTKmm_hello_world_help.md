---
title: "GTKmm hello world help"
date: 2012-04-13
forum: Programming Talk
---

### Post by vanangamudi on 2012-04-13
I tried comiling a basic gtkmm program... it throws me lot of errors..

[http://pastebin.com/QnuaXEgE](http://pastebin.com/QnuaXEgE)

---

### Post by r-senior on 2012-04-13
Could you show us the code and explain how you tried to compile it?

---

### Post by vanangamudi on 2012-04-13
> **r-senior said:**
> Could you show us the code and explain how you tried to compile it?


buttons.h
```
#ifndef GTKMM_TUTS_BUTTONS_H
#define GTKMM_TUTS_BUTTONS_H

#include<gtkmm/window.h>
#include<gtkmm/button.h>
//#include<iostream.h>


class Buttons:Gtk::Window
{
    public:
        Buttons();
        ~Buttons();

    protected:
        virtual void onBtnHelloWorld_clicked();

        Gtk::Button btnHelloWorld;

};



#endif  //GTKMM_TUTS_BUTTONS_H

```



buttons.cpp

```
#include"buttons.h"



Buttons::Buttons()
{
    btnHelloWorld.add_pixlabel("info.xpm","Hello World");

    set_title("Hello world with imaged button");
    set_border_width(10);

    btnHelloWorld.signal_clicked().connect(sigc::mem_fun(*this,&Buttons::onBtnHelloWorld_clicked));

    add(btnHelloWorld);

    show_all_children();
}


Buttons::~Buttons()
{

}

void Buttons::onBtnHelloWorld_clicked()
{
    std::cout<<"Hello world !!"<<std::endl;
}

```

---

### Post by r-senior on 2012-04-13
You'll need the iostream header otherwise the cout won't work. Do you still get errors if you put that back in?

And, how are you trying to compile it? Are you using pkg-config?

---

### Post by vanangamudi on 2012-04-13
> **r-senior said:**
> You'll need the iostream header otherwise the cout won't work. Do you still get errors if you put that back in?

And, how are you trying to compile it? Are you using pkg-config?

I changed cout into printf()...

still the problem remains... sigc problem...

and yes I'm using pkg-config for compiling..

---

### Post by r-senior on 2012-04-13
I installed libgtkmm-3 and I get the same error, which goes away if you remove this line (apart from the fact you don't have main(), etc).

```
btnHelloWorld.signal_clicked().connect(sigc::mem_fun(*this,&Buttons::onBtnHelloWorld_clicked));
```

But this example: [http://developer.gnome.org/gtkmm-tutorial/stable/sec-helloworld.html.en](http://developer.gnome.org/gtkmm-tutorial/stable/sec-helloworld.html.en), which has virtually the same line of code, works:

```
m_button.signal_clicked().connect(sigc::mem_fun(*this,
              &HelloWorld::on_button_clicked));
```

So there's something weird with your code. Maybe try compiling the example from the Gtkmm site and see how you get on with that?

---

### Post by vanangamudi on 2012-04-13
> **r-senior said:**
> I installed libgtkmm-3 and I get the same error, which goes away if you remove this line (apart from the fact you don't have main(), etc).

```
btnHelloWorld.signal_clicked().connect(sigc::mem_fun(*this,&Buttons::onBtnHelloWorld_clicked));
```

But this example: [http://developer.gnome.org/gtkmm-tutorial/stable/sec-helloworld.html.en](http://developer.gnome.org/gtkmm-tutorial/stable/sec-helloworld.html.en), which has virtually the same line of code, works:

```
m_button.signal_clicked().connect(sigc::mem_fun(*this,
              &HelloWorld::on_button_clicked));
```

So there's something weird with your code. Maybe try compiling the example from the Gtkmm site and see how you get on with that?


I tried and the tut code compiles with no problem... but I did the same thing but it troubles...

---

### Post by vanangamudi on 2012-04-13
I got it.... I forgot to specify the public modifier for Gtk::Window from which the Buttons class is inherited from... 
problem solved...

---


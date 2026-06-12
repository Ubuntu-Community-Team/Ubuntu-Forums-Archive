---
title: "gtkmm signal problems"
date: 2006-09-21
forum: Programming Talk
---

### Post by yankees26 on 2006-09-21
I just started trying Gtkmm and I was trying out the following code: ```
#include <gtkmm/button.h>
#include <gtkmm/window.h>
#include <gtkmm/main.h>
#include <iostream>
class Hello: public Gtk::Window
{
public:
	Hello(): m_button("Hello World")
	{
		set_border_width(10);
		m_button.signal_clicked().connect(SigC::slot(*this, &Hello::on_button_clicked));
		add(m_button);
		m_button.show();
	}
	virtual ~Hello(){}
private:
	virtual void on_button_clicked()
	{
		std::cout << "Hello World" << std::endl;
	}
	Gtk::Button m_button;
};


int main(int argc, char **argv)
{
	Gtk::Main kit(argc, argv);
	Hello hello;
	Gtk::Main::run(hello);
	return 0;
}
```
I get the following error: ```
hello.cpp: In constructor ‘Hello::Hello()’:
hello.cpp:11: error: ‘slot’ is not a member of ‘SigC’
```

I don't understand why I get this error.  I'm doing exactly what the tutorial says.

---

### Post by g8m on 2006-09-22
hmm, try

m_button.signal_clicked().connect(sigc::mem_fun(*this, &Hello::on_button_clicked));

I dont know SigC, maybe version problem?

---

### Post by yankees26 on 2006-09-22
Thanks, that is what I did.  I found out that the tutorial I was using was outdated and so I downloaded gtkmm source and looked at the samples and saw that mem_fun was used.  Thanks anyway.  So now it works. :)

---


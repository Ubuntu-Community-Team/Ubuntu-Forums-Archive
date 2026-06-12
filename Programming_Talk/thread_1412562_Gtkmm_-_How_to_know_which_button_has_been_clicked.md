---
title: "Gtkmm - How to know which button has been clicked?"
date: 2010-02-21
forum: Programming Talk
---

### Post by PaulM1985 on 2010-02-21
Hi

I am creating a program which will display a variable number of buttons depending on the system state. Since there will be a varied amount, I want to use one function to respond to any of the clicks and then deal with the click in the function.

```

for (int i = 0; i < m_Button.length(); i++) {
	m_Button[i].signal_clicked().connect(sigc::mem_fun(*this,
					&NavPanel::OnButtonClick));
}

```

Then in OnButtonClick:

```

void NavPanel::OnButtonClick() {
// Know which button from the list was clicked
}

```

Maybe somehow passing in some sort of argument into the OnButtonClick function, the index of the button in the list perhaps.

Is this possible and does the question make sense?

Paul

---

### Post by PaulM1985 on 2010-02-21
Solved my own problem.  Solution below if anyone else has this problem.

```

m_button2.signal_clicked().connect(sigc::bind<-1, Glib::ustring>(
              sigc::mem_fun(*this, &HelloWorld::on_button_clicked), "button 2"));

```

Links to:

```

// Our new improved signal handler.  The data passed to this method is
// printed to stdout.
void HelloWorld::on_button_clicked(Glib::ustring data)
{
  std::cout << "Hello World - " << data << " was pressed" << std::endl;
}

```

---

### Post by SledgeHammer_999 on 2010-02-21
Yes, look at sigc::bind() here->[http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-binding-extra-arguments.html.en](http://library.gnome.org/devel/gtkmm-tutorial/unstable/sec-binding-extra-arguments.html.en)

So an approach could be:
```
for (int i = 0; i < m_Button.length(); i++) {
	m_Button[i].signal_clicked().connect(sigc::bind<int>(sigc::mem_fun(*this, &NavPanel::OnButtonClick), i));
}
```

```
void NavPanel::OnButtonClick(int index) {
// Know which button from the list was clicked
//check 'index' and find the the correct button
}
```

EDIT: you got there first :P

---


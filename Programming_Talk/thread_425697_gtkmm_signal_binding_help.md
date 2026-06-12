---
title: "gtkmm signal binding help"
date: 2007-04-27
forum: Programming Talk
---

### Post by rekahsoft on 2007-04-27
Hi all...i have been learning gtkmm and have ran into a little issue...i need to bind an argument to a click signal of a button but for some reason i cannot figure it out...my code goes wrong on this:```
button.signal_clicked().connect(sigc::bind<Gtk::Button>(sigc::ptr_fun(&on_button_click), button));
```What is the problem with that line?...note if more info is needed i will happily supply it :P

---

### Post by rekahsoft on 2007-04-28
ok...i have found the answer and am going to answer my thread so people who have the same problem can have a faster solution :D
```
button.signal_clicked().connect(sigc::bind<int>(sigc::ptr_fun(&on_button_click), 10);
```Note that you can substitude the type for sigc::bind...you can also have more then one too (ex. sigc::bind<int, int. std::string>)

---


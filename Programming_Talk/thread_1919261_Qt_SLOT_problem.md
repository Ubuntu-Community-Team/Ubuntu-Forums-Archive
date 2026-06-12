---
title: "Qt SLOT problem"
date: 2012-02-02
forum: Programming Talk
---

### Post by SPK201 on 2012-02-02
So, I just don't know how to solve my problem.

I have a class derived from QMainWindow and QOBJECT defined.
There I have a private slot - called attack(Target *target) { // do something}

Now, it all works fine - if I use slots without parameters.
If I try to call SLOT(attack(&target)) I get QOBJECT::connect: No such slot ...

Why is that not working?!?!

---

### Post by karlson on 2012-02-02
Could you post the class declaration?  And if you want to call it as a function you just call it as a function the SLOT() modifier is used with ```
 connect(); 
``` function.

---

### Post by SPK201 on 2012-02-03
I use connect();

Window.hpp
```
class Window : public QMainWindow {
QOBJECT
public: 
    Window();

private slots:
    attack(Target*);
};
```Window.cpp

```
Window::Window() {
    QPushButton*attackButton = new QPushButton("&Attack!", this);
    setCentralWidget( attackButton );
    Target* target = new Target("Name");
    connect(attackButton, SIGNAL(clicked()), this, SLOT(attack(target)));
}
Window::attack(Target* target) {
    cout << target->name << " was attacked." << endl;
}
```As I said, if I use a Slot without parameters (e.g attack() instead of attack(Target*)) it works. :confused:

---


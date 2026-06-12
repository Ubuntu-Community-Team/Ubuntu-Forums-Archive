---
title: "how to use .ui objects in Qt??"
date: 2009-07-10
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-10
when we declare some widgets by drag and drop in Qt , say slide.ui is the file, and class name is slide
i used label and combobox in .ui design layout, so now how do i access these widgets in slide.cpp function??
```

// this is slide.cpp file
char slide:: abhi()
{
    QPushButton *button=new QPushButton();
    button->setText("abhilash");
    button->show();
}

void slide::labels()
{



```

```

//this is slide.h file
#include "slide.h"
#include "ui_slide.h"
#include<QWidget>
#include "QPushButton"
#include "slide.ui"

class slide : public QWidget
{
    Q_OBJECT

public:
    slide(QWidget *parent = 0);
    char abhi();
    void labels();
    ~slide();

private:
    Ui::slideClass *ui;
};

```

also my big doubt is we can create widgets using c++ code, so how exactly designer .ui should be used??

---

### Post by JordyD on 2009-07-10
Yes, widgets can be created using C++ code, the designer makes it easier.

To access those widgets, using the code that they set you up with, it's simple:
```
ui->yourWidget
```

What is slide::abhi()? If you're using the designer, you can just drag'n'drop in the designer view and then use ui->button. You can set the text from the designer, too. Just change the property in the properties window. If you want to change the text after you've created the widget, though, you'll want to use ui->button->setText("abhilash"), just as you did in your slide.cpp.

EDIT: Oh! I didn't notice your name. That must be where slide::abhi() comes from, then.

Looking at your headers, you do not need to include slide.ui. Qt Creator turns slide.ui into ui_slide.h when it builds your project. You also should not include QPushButton unless you *really* want to create a QPushButton after the GUI has been made. You can create all the GUI stuff using Qt Designer/Creator, and it will automatically add the needed headers.

Basically, you use the Designer to create the GUI, and only use your C++ code to create more GUI elements when you really need to, and to code the non-GUI stuff, of course.

If you want Qt Creator to autocomplete ui->button, you should rebuild the project everytime you add elements to the GUI, that way it recreates the ui_slide.h file, and it can find the stuff for autocompletion.

Hope that helps.

---

### Post by abhilashm86 on 2009-07-10
> **JordyD said:**
> Yes, widgets can be created using C++ code, the designer makes it easier.

To access those widgets, using the code that they set you up with, it's simple:
```
ui->yourWidget
```

What is slide::abhi()? If you're using the designer, you can just drag'n'drop in the designer view and then use ui->button. You can set the text from the designer, too. Just change the property in the properties window. If you want to change the text after you've created the widget, though, you'll want to use ui->button->setText("abhilash"), just as you did in your slide.cpp.

EDIT: Oh! I didn't notice your name. That must be where slide::abhi() comes from, then.

Looking at your headers, you do not need to include slide.ui. Qt Creator turns slide.ui into ui_slide.h when it builds your project. You also should not include QPushButton unless you *really* want to create a QPushButton after the GUI has been made. You can create all the GUI stuff using Qt Designer/Creator, and it will automatically add the needed headers.

Basically, you use the Designer to create the GUI, and only use your C++ code to create more GUI elements when you really need to, and to code the non-GUI stuff, of course.

If you want Qt Creator to autocomplete ui->button, you should rebuild the project everytime you add elements to the GUI, that way it recreates the ui_slide.h file, and it can find the stuff for autocompletion.

Hope that helps.

thanks a lot jordyD, yes abhi is my name!!, 
i noticed that,
when i create an widget in designer, when i right click on it, we get option of "go to slot" option, this is so fantastic, it creates signal to other functions,
my question is it create private slots, so for communication between widgets is this best method or do we have another method( except signal and slots), as i am beginner and first time doing GUI, i am getting things slowly,
thanks once again

---

### Post by JordyD on 2009-07-10
> **abhilashm86 said:**
> thanks a lot jordyD, yes abhi is my name!!, 
i noticed that,
when i create an widget in designer, when i right click on it, we get option of "go to slot" option, this is so fantastic, it creates signal to other functions,
my question is it create private slots, so for communication between widgets is this best method or do we have another method( except signal and slots), as i am beginner and first time doing GUI, i am getting things slowly,
thanks once again

I myself am actually also a beginner. As far as I can tell, all GUIs that I've used have used the method that Qt uses (slots). It all has to do with callbacks. Even Visual Basic (my first programming language) uses this method.

Perhaps other programming languages of other paradigms use different methods, but the slots one seems most convenient. The best way to learn how everything works is to look at the ui_slide.h file that Qt Creator creates for you. Just build the project, then click on the little button at the top-right of your sidebar and uncheck the option that says hide generated files, or something like that.

EDIT: It's not on the top-right, sorry. It's in the middle somewhat. If you hover your mouse over it is says "Filter Tree". If you closed your sidebar accidentally, you can click on the button in the lower left (left of the search bar) to get it back.

Hope you're having fun with Qt. I just wish it looked native in GNOME.

EDIT: Unfortunately, there doesn't seem to be many other people here that use Qt. But that's not really too surprising, since Ubuntu is a GNOME-by-default distro.

EDIT2: Oh! Nevermind! I didn't know Qt had the ability to theme itself after my GNOME desktop settings. This makes me so happy! I can play with Qt again.

---

### Post by Mirge on 2009-07-10
I started playing around with Qt4, but then work really kicked up and I've been busy as ever with that. I plan on coming back to Qt4 in my spare time and as soon as I actually find time.

I use Kubuntu 9.04, so I'm a little biased towards Qt4 I guess :).

---

### Post by JordyD on 2009-07-10
> **Mirge said:**
> I started playing around with Qt4, but then work really kicked up and I've been busy as ever with that. I plan on coming back to Qt4 in my spare time and as soon as I actually find time.

I use Kubuntu 9.04, so I'm a little biased towards Qt4 I guess :).

I love Qt4, and I love KDE, and I love GNOME. I wish I could have a KDE-GNOME mash-up.

On the other hand, I don't particularly like GTK or wxWidgets. wxWidgets always looks un-GNOMEish, and GTK looks ugly under anything not GNOME.

---

### Post by Mirge on 2009-07-10
> **JordyD said:**
> I love Qt4, and I love KDE, and I love GNOME. I wish I could have a KDE-GNOME mash-up.

On the other hand, I don't particularly like GTK or wxWidgets. wxWidgets always looks un-GNOMEish, and GTK looks ugly under anything not GNOME.

That's what I had heard, but I never did any personal testing myself. I just picked Qt4 because I liked KDE... and because it was written in/for C++... despite the fact bindings exist for GTK for C++ yadda yadda.

---

### Post by JordyD on 2009-07-10
> **Mirge said:**
> That's what I had heard, but I never did any personal testing myself. I just picked Qt4 because I liked KDE... and because it was written in/for C++... despite the fact bindings exist for GTK for C++ yadda yadda.

Well, I've never tested either, so the only thing I have to base it on is screenshots and hearsay. But, Qt nowadays uses the platform's own GUI toolkit to render their buttons and such, so it should look more native than GTK, which does not.

I like the Qt documentation and Qt Creator, too.

---


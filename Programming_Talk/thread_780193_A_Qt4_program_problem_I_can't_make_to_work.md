---
title: "A Qt4 program problem I can't make to work"
date: 2008-05-03
forum: Programming Talk
---

### Post by cherva on 2008-05-03
Hi,
I'm trying to make a QListWidget and
1)--------------------------------
or
2) connect all the items on one slot and somehow identify witch item 
was double clicked ....
Please help me :( I'm trying to do this for 2 days now ...
here is my code:
```
#include <QApplication>
#include <QLabel>
#include <QVBoxLayout>
#include <QListWidget>
#include <QListWidgetItem>
int main(int argc, char *argv[]) 
{
QApplication app(argc, argv); 
QWidget *window = new QWidget; 
QLabel *label = new QLabel("test");
label->show();
QListWidget *listWidget = new QListWidget;
QListWidgetItem *Test = new QListWidgetItem("Test", listWidget);
new QListWidgetItem("Test2", listWidget);
new QListWidgetItem("Test3", listWidget);
window-> setWindowTitle("Test list view");

QObject::connect(listWidget, SIGNAL(itemDoubleClicked(QListWidgetItem*)),label , SLOT(hide()));

QVBoxLayout *layout = new QVBoxLayout; 
    layout->addWidget(label);
    layout->addWidget(listWidget);
    window->setLayout(layout); 
    window->show(); 
return app.exec();
}

```
This thing works, but hides the label no matter witch item is double clicked ... I'm asking you for the ultimate help ... add the code it needs to fulfill either 1) or 2) because if I think over this for another day I'll break something.

---

### Post by GeneralZod on 2008-05-03
I'm an absolute beginner at Qt programming, so I'm probably using a sledgehammer to crack a walnut, here :)

[Here](etotheipiplusone.com/signalsandslots.tar.gz)'s my very ugly stab at a solution, which unfortunately involves the subclassing of both QListWidget and QListWidgetItem (*shudder*).  Comments in the code should explain what's going on and how to use it.

Here, only "Test" will call hide().  You'll need to connect other MyQListWidgetItems in the same way if you want them to hide(), too.

```
qmake -project && qmake && make
```

to build!

NOTE: 

The [docs](http://doc.trolltech.com/4.1/qlistwidgetitem.html) advise using QListView if you want more flexibility, so you might want to investigate this - Qt4's model/ view stuff is supposed to be pretty neat :)

---

### Post by luisromangz on 2008-05-03
Instead of connecting it to the label's hide slot, define a window class which will encapsulate all your window code (widget creation, etc) and there define a slot in which you check which element was clicked and hide the label accordingly.

---

### Post by cherva on 2008-05-04
You saved two lives today. Mine because I was going crazy and my computer's life because I was going to kill him with a hammer :) THANKS A LOT 
Cherva bows infront of GeneralZod

luisromangz thank you too :)

Edit:
Arrrrr I'm so stupid now when I see your code I realize that calling a different function won't help me because the menu items are dynamic and should not have a limit ... because I'm making a small Messenger and it will be stupid to have a limit of the users ... It's funny how I managed to make the chat function, but I can't make the users menu ... GeneralZod sorry for the wasted time :( I'll edit the first post so I'm waiting for solutions about 2). If no one help me I'll use the GeneralZod's code and somehow manage to make a nice program ;).
P.S
I'll include your name when the program has RC1, so what are you waiting for :)

---

### Post by luisromangz on 2008-05-04
Ok but just be sure of not subclassing widget classes just for functionality like this, because that's not the easy nor the correct way.

---

### Post by GeneralZod on 2008-05-04
> **cherva said:**
> You saved two lives today. Mine because I was going crazy and my computer's life because I was going to kill him with a hammer :) THANKS A LOT 
Cherva bows infront of GeneralZod

luisromangz thank you too :)

Edit:
Arrrrr I'm so stupid now when I see your code I realize that calling a different function won't help me because the menu items are dynamic and should not have a limit ... because I'm making a small Messenger and it will be stupid to have a limit of the users ... It's funny how I managed to make the chat function, but I can't make the users menu ... GeneralZod sorry for the wasted time :( I'll edit the first post so I'm waiting for solutions about 2). If no one help me I'll use the GeneralZod's code and somehow manage to make a nice program ;).
P.S
I'll include your name when the program has RC1, so what are you waiting for :)

Heh - I think you're going to have to explain a little more about what you're doing, here - I'm not sure why this approach would not be dynamic nor why it would impose limits on the number of users, and Luis's suggestion fulfils #2 quite admirably.  

What do the items in the list represent, and what distinct behaviours do you want when different list elements are double-clicked?

---

### Post by luisromangz on 2008-05-04
Hey mate, the signal launched when the item is double-clicked (itemDoubleClicked(QListWidgetItem*)) passes the clicked item as a parameter, provided your slot uses it.

So in your generic slot for all items you just have to check if the passed item should be hidden.

---

### Post by cherva on 2008-05-04
The items in the list reprisent the users in your user list they will be read from a file ... after you double click one the program will search the file for the IP of the user and start the chat program with him.
> Hey mate, the signal launched when the item is double-clicked (itemDoubleClicked(QListWidgetItem*)) passes the clicked item as a parameter, provided your slot uses it.

So in your generic slot for all items you just have to check if the passed item should be hidden. Yes I know that, but I don't know hot to do it can you show me an example code ?

---

### Post by luisromangz on 2008-05-04
Ok, let's see.

In your ContactListWindow (as you should be subclassing Window as I wrote in a previous post) class header file you should define a non public slot in this way:

```


protected slots:
  /*$PROTECTED_SLOTS$*/
  void onItemDoubleClicked(QListWidgetItem * item );


```

Then in the class' implementation file, you should write a body for that slot:

```

void ContactListWindow::onItemDoubleClicked(QListWidgetItem * item)
{
  if(item->text() == "Paco")
    item->setHidden(true);
}


```

And you should link the listwidget's doubleclick signal with the slot using

```

QObject::connect(listWidget, SIGNAL(itemDoubleClicked(QListWidgetItem *)),
                   this, SLOT(onItemDoubleClicked(QListWidgetItem * )));

```

for exaple in the ContactListWindow's constructor method.

Maybe you should consider purchasing a book as "C++ GUI Programming with Qt 4", which covers from begginer's problems like this and goes into far more complex problems and have a lot of code examples.

---

### Post by cherva on 2008-05-04
Thanks I'll test this right away  :)

---

### Post by luisromangz on 2008-05-04
ContactListWindow would be a QWindow subclass in which you handle all the contact list window logic.

---

### Post by cherva on 2008-05-18
So no one will help me ? Sure why not ... I spent 3 days in making the chat part of the program and now when I ask for something so easy just to finish it (because I'm 12th class now and I have to study to go to university) you say "go learn it"... Thanks only to GeneralZod... I guess my program will stay unfinished till the summer ......:(

---


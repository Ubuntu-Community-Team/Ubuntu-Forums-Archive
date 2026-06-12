---
title: "Compiling code with QT3 headers"
date: 2006-01-02
forum: Programming Talk
---

### Post by Neeko on 2006-01-02
Hi there,
I've recently switched from Gnome to KDE, and and trying a little c++ with QT3. I'm not using the GUI designer, as I'd prefer to learn what I was doing before dragging widgets around a form.

Anyway, I'm trying to complie a basic 'hello world' program. I have found the headers in /usr/include/qt3 and the info I have suggests this is the way to compile my program:
```
g++ -I/usr/include/qt3 -L/usr/lib/qt3 -lqt -o helloworld helloworld.cpp
```
The compiler spits the dummy and says:
```
/usr/bin/ld: cannot find -lqt
collect2: ld returned 1 exit status

```

My helloworld program* is about as simple as it can get:
```
#include <qapplication.h>
#include <qlabel.h>

int main(int argc, char *argv[])
{
	QApplication myapp(argc, argv);
	QLabel *mylabel = new QLabel("Helloworld", 0);
	mylabel->resize(120, 30);
	myapp.setMainWidget(mylabel);
	mylabel->show();
	return myapp.exec();
}

```

Can someone give me a clue please?

Thx

--
* Actually it's from O'Reilly's 'Programming with QT'

---

### Post by toojays on 2006-01-02
Try using -lqt-mt instead. The 'mt' means 'multithreaded', which is what is usually installed.

---

### Post by Neeko on 2006-01-02
aye carumba - as simple as that. 
Thanks

---

### Post by Jessehk on 2006-01-02
The easier way to do it would be to place the file in its own directory and simply

```


qmake -project
qmake
make


```

:)

---

### Post by Neeko on 2006-01-02
ohhh I like that!
cheers

---


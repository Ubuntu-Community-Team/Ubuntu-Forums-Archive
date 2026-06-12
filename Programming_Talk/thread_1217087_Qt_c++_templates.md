---
title: "Qt c++ templates??"
date: 2009-07-19
forum: Programming Talk
---

### Post by abhilashm86 on 2009-07-19
i'm using Qt 4.5, created QList templates for lines, arcs which i'll be using to store values and use it to draw at time of exceution, 
so after initialization like this, component.h
```


        QList<Line> Lines;
        QList<Arc> Arcs;
        QList<Area> Rectangles, Ellipses;
        QList<Port> Ports;
        QList<Text> Texts;
        QList<Property> Properties;

```
then i tried using this in capacitor.cpp file, 
```

void Capacitor::createSymbol()
{
    Lines.append(new Line(-11, -5, -11, -11, QPen(Qt::blue,1)));
    Lines.append(new Line(14, -8, -8, -8, QPen(Qt::red,1)));
    Lines.append(new Line(-4, -11, -4, -11, QPen(Qt::blue,3)));

    Arcs.append(new Arc(4,-12, 20, 24, 16*122, 16*116,QPen(Qt::blue, 3)));
     ...........
    ...........

```

the main declaration of these functions is in element.h,
```

class Property
{
    private:
        QString Name, Value;
        bool display;
        QString Description;

    public:
        Property(const QString &_Name= "", const QString &_Value= "", bool _display=false,
             const QString &_Description= "")
        : Name(_Name), Value(_Value), display(_display), Description(_Description) {}
};

```

so when i compile, i get this error, 
```

capacitor.cpp:7: error: no matching function for call to ‘QList<Property>::append(Property*)’
../../qtsdk-2009.01/qt/include/QtCore/qlist.h:422: note: candidates are: void QList<T>::append(const T&) [with T = Property]
../../qtsdk-2009.01/qt/include/QtCore/qlist.h:623: note: void QList<T>::append(const QList<T>&) [with T = Property]
capacitor.cpp:8: error: no matching function for call to ‘QList<Property>::append(Property*)’
../../qtsdk-2009.01/qt/include/QtCore/qlist.h:422: note: candidates are: void QList<T>::append(const T&) [with T = Property]
../../qtsdk-2009.01/qt/include/QtCore/qlist.h:623: note: void QList<T>::append(const QList<T>&) [with T = Property]

```
how i exactly need to use Lines,Arcs after initialization of templates, or is the templates declaration is wrong??

---

### Post by Kazade on 2009-07-19
You have declared containers of objects, and then tried to store pointers in them :)

I have never used QT so I don't know if they have their own smart pointers.. but in std C++ with TR1 support I would do:

QList<std::tr1::shared_ptr<Line> > Lines;

otherwise try:

QList<Line*> Lines; ///< Whatever you put in here will need "delete"-ing.

---

### Post by abhilashm86 on 2009-07-19
> **Kazade said:**
> 

QList<Line*> Lines; ///< Whatever you put in here will need "delete"-ing.

yes this declaration works fine, now i'm creating pointers to store value and access them, thanks

---

### Post by mdurham on 2009-07-19
> **abhilashm86 said:**
> yes this declaration works fine, now i'm creating pointers to store value and access them, thanks

Why make work by storing pointers, why not just store the object itself?

---


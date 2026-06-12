---
title: "must use '.*' or '-&gt;*' to call pointer-to-member function"
date: 2009-07-16
forum: Programming Talk
---

### Post by KIAaze on 2009-07-16
Hi,

I'm trying to adapt an example from the [qwt library]("http://qwt.sourceforge.net/") to my needs.
I need to pass a member function of a class ("Plot") to the constructor of another class ("ComplexData"), but I just can't get it to work.
(I have a function with more than one argument and plan to store the constant arguments as member variables of a class ("Plot").)

Here's the modified qwt-5.2.0/examples/simple_plot/simple.cpp from the qwt source tarball:

```
#include <qapplication.h>
#include <qwt_plot.h>
#include <qwt_plot_marker.h>
#include <qwt_plot_curve.h>
#include <qwt_legend.h>
#include <qwt_data.h>
#include <qwt_text.h>
// #include <qwt_math.h>
// #include <math.h>

//-----------------------------------------------------------------
//              simple.cpp
//
//      A simple example which shows how to use QwtPlot and QwtData
//-----------------------------------------------------------------

class SimpleData: public QwtData
{
    // The x values depend on its index and the y values
    // can be calculated from the corresponding x value. 
    // So we don´t need to store the values.
    // Such an implementation is slower because every point 
    // has to be recalculated for every replot, but it demonstrates how
    // QwtData can be used.

public:
    SimpleData(double(*y)(double), size_t size):
        d_size(size),
        d_y(y)
    {
    }

    virtual QwtData *copy() const
    {
        return new SimpleData(d_y, d_size);
    }

    virtual size_t size() const
    {
        return d_size;
    }

    virtual double x(size_t i) const
    {
        return 0.1 * i;
    }

    virtual double y(size_t i) const
    {
        return d_y(x(i));
    }
private:
    size_t d_size;
    double(*d_y)(double);
};

class Plot : public QwtPlot
{
public:
    Plot();
public:
    double myfunc(double x) {
      return x;
    }
};

class ComplexData: public QwtData
{
    // The x values depend on its index and the y values
    // can be calculated from the corresponding x value. 
    // So we don´t need to store the values.
    // Such an implementation is slower because every point 
    // has to be recalculated for every replot, but it demonstrates how
    // QwtData can be used.

public:
    ComplexData(double (Plot::*y)(double), size_t size):
        d_size(size),
        d_y(y)
    {
    }

    virtual QwtData *copy() const
    {
        return new ComplexData(d_y, d_size);
    }

    virtual size_t size() const
    {
        return d_size;
    }

    virtual double x(size_t i) const
    {
        return 0.1 * i;
    }

    virtual double y(size_t i) const
    {
        return d_y(x(i));
    }
private:
    size_t d_size;
    double (Plot::*d_y)(double);
};

Plot::Plot()
{
    setTitle("A Simple QwtPlot Demonstration");
    insertLegend(new QwtLegend(), QwtPlot::RightLegend);

    // Set axis titles
    setAxisTitle(xBottom, "x -->");
    setAxisTitle(yLeft, "y -->");
    
    // Insert new curves
    QwtPlotCurve *cSin = new QwtPlotCurve("y = sin(x)");
#if QT_VERSION >= 0x040000
    cSin->setRenderHint(QwtPlotItem::RenderAntialiased);
#endif
    cSin->setPen(QPen(Qt::red));
    cSin->attach(this);

    QwtPlotCurve *cCos = new QwtPlotCurve("y = cos(x)");
#if QT_VERSION >= 0x040000
    cCos->setRenderHint(QwtPlotItem::RenderAntialiased);
#endif
    cCos->setPen(QPen(Qt::blue));
    cCos->attach(this);

    // Create sin and cos data
    const int nPoints = 100;
    cSin->setData(SimpleData(::sin, nPoints));
//     double (*)double foo = &Plot::myfunc;
    cCos->setData(ComplexData(&Plot::myfunc, nPoints));

    // Insert markers
    
    //  ...a horizontal line at y = 0...
    QwtPlotMarker *mY = new QwtPlotMarker();
    mY->setLabel(QString::fromLatin1("y = 0"));
    mY->setLabelAlignment(Qt::AlignRight|Qt::AlignTop);
    mY->setLineStyle(QwtPlotMarker::HLine);
    mY->setYValue(0.0);
    mY->attach(this);

    //  ...a vertical line at x = 2 * pi
    QwtPlotMarker *mX = new QwtPlotMarker();
    mX->setLabel(QString::fromLatin1("x = 2 pi"));
    mX->setLabelAlignment(Qt::AlignLeft | Qt::AlignBottom);
    mX->setLabelOrientation(Qt::Vertical);
    mX->setLineStyle(QwtPlotMarker::VLine);
    mX->setLinePen(QPen(Qt::black, 0, Qt::DashDotLine));
    mX->setXValue(2.0 * M_PI);
    mX->attach(this);
}

int main(int argc, char **argv)
{
    QApplication a(argc, argv);

    Plot plot;
#if QT_VERSION < 0x040000
    a.setMainWidget(&plot);
#endif
    plot.resize(600,400);
    plot.show();
    return a.exec(); 
}

```

After qmake && make:
```
g++ -c -m64 -pipe -O2 -D_REENTRANT -Wall -W -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/opt/shared/Qt/4.5.0/debug/mkspecs/linux-g++-64 -I. -I/opt/shared/Qt/4.5.0/debug/include/QtCore -I/opt/shared/Qt/4.5.0/debug/include/QtGui -I/opt/shared/Qt/4.5.0/debug/include -I../../src -Imoc -I. -o obj/simple.o simple.cpp
simple.cpp: In member function 'virtual double ComplexData::y(size_t) const':
simple.cpp:100: error: must use '.*' or '->*' to call pointer-to-member function in '((const ComplexData*)this)->ComplexData::d_y (...)'
make: *** [obj/simple.o] Error 1

```

---

### Post by dwhitney67 on 2009-07-16
Your member data item, d_y, is a pointer to a function.  Thus you need to dereference it before calling the function.  Try something like:
```

    virtual double y(size_t i) const
    {
        return (*d_y)(x(i));    // <----  d_y dereferenced before use
    }

```

---

### Post by Habbit on 2009-07-16
No, the problem is actually that you are trying to invoke a member function. Thus, you need an object on which to perform the call, a Plot instance actually. Then, you'd do something along the lines of "myPlotInstance.*d_y(args)". I don't remember whether more parentheses are needed because of operator precedence rules, but the C++ FAQ (lite) can provide you with more enlightenment.

---

### Post by dwhitney67 on 2009-07-16
> **Habbit said:**
> No, the problem is actually that you are trying to invoke a member function. Thus, you need an object on which to perform the call, a Plot instance actually. Then, you'd do something along the lines of "myPlotInstance.*d_y(args)". I don't remember whether more parentheses are needed because of operator precedence rules, but the C++ FAQ (lite) can provide you with more enlightenment.

Oops, my mistake.  Unless the method is declared static, an instance is needed to call the method.

I believe the parenthesis are required before calling the function.  Something like:  (myPlotInstance.*d_y)(args).

---

### Post by KIAaze on 2009-07-17
Thanks, making the method static worked:
```
#include <qapplication.h>
#include <qwt_plot.h>
#include <qwt_plot_marker.h>
#include <qwt_plot_curve.h>
#include <qwt_legend.h>
#include <qwt_data.h>
#include <qwt_text.h>
// #include <qwt_math.h>
// #include <math.h>

#include <iostream>
using namespace std;

//-----------------------------------------------------------------
//              simple.cpp
//
//      A simple example which shows how to use QwtPlot and QwtData
//-----------------------------------------------------------------

class SimpleData: public QwtData
{
    // The x values depend on its index and the y values
    // can be calculated from the corresponding x value. 
    // So we don´t need to store the values.
    // Such an implementation is slower because every point 
    // has to be recalculated for every replot, but it demonstrates how
    // QwtData can be used.

public:
    SimpleData(double(*y)(double), size_t size):
        d_size(size),
        d_y(y)
    {
    }

    virtual QwtData *copy() const
    {
        return new SimpleData(d_y, d_size);
    }

    virtual size_t size() const
    {
        return d_size;
    }

    virtual double x(size_t i) const
    {
        return 0.1 * i;
    }

    virtual double y(size_t i) const
    {
        return d_y(x(i));
    }
private:
    size_t d_size;
    double(*d_y)(double);
};

class Plot : public QwtPlot
{
public:
    Plot();
    static double m_slope;
public:
    static double myfunc(double x) {
      return m_slope * x;
    }
};

double Plot::m_slope = 0;

Plot::Plot()
{
    setTitle("A Simple QwtPlot Demonstration");
    insertLegend(new QwtLegend(), QwtPlot::RightLegend);

    // Set axis titles
    setAxisTitle(xBottom, "x -->");
    setAxisTitle(yLeft, "y -->");
    
    // Insert new curves
    QwtPlotCurve *cSin = new QwtPlotCurve("y = sin(x)");
#if QT_VERSION >= 0x040000
    cSin->setRenderHint(QwtPlotItem::RenderAntialiased);
#endif
    cSin->setPen(QPen(Qt::red));
    cSin->attach(this);

    QwtPlotCurve *cCos = new QwtPlotCurve("y = cos(x)");
#if QT_VERSION >= 0x040000
    cCos->setRenderHint(QwtPlotItem::RenderAntialiased);
#endif
    cCos->setPen(QPen(Qt::blue));
    cCos->attach(this);

    // Create sin and cos data
    const int nPoints = 100;
    

    m_slope = 2;
    cSin->setData(SimpleData(Plot::myfunc, nPoints));
    m_slope = 3;
    cCos->setData(SimpleData(Plot::myfunc, nPoints));

    // Insert markers
    
    //  ...a horizontal line at y = 0...
    QwtPlotMarker *mY = new QwtPlotMarker();
    mY->setLabel(QString::fromLatin1("y = 0"));
    mY->setLabelAlignment(Qt::AlignRight|Qt::AlignTop);
    mY->setLineStyle(QwtPlotMarker::HLine);
    mY->setYValue(0.0);
    mY->attach(this);

    //  ...a vertical line at x = 2 * pi
    QwtPlotMarker *mX = new QwtPlotMarker();
    mX->setLabel(QString::fromLatin1("x = 2 pi"));
    mX->setLabelAlignment(Qt::AlignLeft | Qt::AlignBottom);
    mX->setLabelOrientation(Qt::Vertical);
    mX->setLineStyle(QwtPlotMarker::VLine);
    mX->setLinePen(QPen(Qt::black, 0, Qt::DashDotLine));
    mX->setXValue(2.0 * M_PI);
    mX->attach(this);
}

int main(int argc, char **argv)
{
    QApplication a(argc, argv);

    Plot plot;
#if QT_VERSION < 0x040000
    a.setMainWidget(&plot);
#endif
    plot.resize(600,400);
    plot.show();

    return a.exec(); 
}

```

Unfortunately, it forces me to make the variables static too, and so the functions end up using the same variables (same slope for both curves in this case).

I worked around the problem by simply creating a new subclass of QwtData for each function now. Maybe that's also a better way of doing things.:rolleyes:

---

### Post by dwhitney67 on 2009-07-17
Forgive me for asking, but why did you go that route?  It wasn't necessary to declare the method static.  If you had taken Habbit's suggestion, and passed a reference of the Plot object to SimpleData, then all would have worked fine with the non-static method.

```

...

class Plot;   // forward declaration

class SimpleData : public QwtData
{
public:
   SimpleData(Plot& p, double(*y)(double), size_t size):
      d_p(p),
      d_y(y),
      d_size(size)
   {
   }

   ...

   virtual double y(size_t i) const
   {
      return (d_p.*d_y)(x(i));
   }

private:
   Plot& d_p;
   double(*d_y)(double);
   size_t d_size;
};

...

Plot::Plot()
{
   ...

   m_slope = 2;
   cSin->setData(SimpleData(*this, Plot::myfunc, nPoints));
   m_slope = 3;
   cCos->setData(SimpleData(*this, Plot::myfunc, nPoints));

   ...
}

```

P.S.  I do not know if the forward declaration will be sufficient; you may need to define class Plot before class SimpleData.

---

### Post by KIAaze on 2009-07-17
Yes, but the problem is that I have more than one function.
Even if the class Plot contains all the functions, SimpleData can only use one of them (d_y).

I could of course pass SimpleData some additional int argument and put if/else if structures into SimpleData::y.

But it seems easier to me to create separate classes for each function, especially since I shouldn't have too many of them and they can have different variables.

---

### Post by dwhitney67 on 2009-07-17
How about:
```

template <class T>
class SimpleData : public QwtData
{
public:
   SimpleData(T& instance, double(*func)(double), size_t size):
      d_instance(instance),
      d_func(func),
      d_size(size)
   {
   }

   ...

   virtual double y(size_t i) const
   {
      return (d_instance.*d_func)(x(i));
   }

private:
   T& d_instance;
   double(*d_func)(double);
   size_t d_size;
};

```

---

### Post by Habbit on 2009-07-17
Shouldn't the function pointer type be declared as double (***T::**func)(double) or something like that, in order to be interpreted as a ponter-to-member function?

---

### Post by dwhitney67 on 2009-07-17
> **Habbit said:**
> Shouldn't the function pointer type be declared as double (***T::**func)(double) or something like that, in order to be interpreted as a ponter-to-member function?
Yes.  My number of mistakes is tallying up.  Is there a way to deduct beans from my account?

---

### Post by Habbit on 2009-07-17
> **dwhitney67 said:**
> Yes.  My number of mistakes is tallying up.  Is there a way to deduct beans from my account?
Most likely not, but even then you'd still be our resident C++ guru. Everyone has a bad day, and pulling good code off the top of your mind, without a compiler telling you that something is wrong, is not particularly easy.

---


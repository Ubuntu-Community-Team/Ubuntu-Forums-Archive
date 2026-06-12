---
title: "Simple C++ template question."
date: 2007-07-28
forum: Programming Talk
---

### Post by moma on 2007-07-28
Hello all,

I have created a template class for Point. The template can create a Point for several basic types such as Integer, Float and Double.

In this first example everything is OK, but the second example fails. Read on....

The first example:

```
template <typename T>
class Point
{
public:
    T x;
    T y;

    Point() : x(0), y(0) {}

    Point(T _x, T _y) : x(_x), y(_y) {}
};


int main()
{
    Point<int> point(15,17);

    Point<int> point2 = Point<int>(2,2);

    return 0;
}
```

Compile  and run
$ [COLOR="SeaGreen"]g++  -Wall main.cpp -o main[/COLOR]
$ [COLOR="SeaGreen"]./main [/COLOR]

It's Ok.
----------------------------------------------------------------------------------

Example 2;
Now I want to extend the Point class with a 'copy constructor' and a function for operator '=' .

```
template <typename T>
class Point
{
public:
    T x;
    T y;

    Point() : x(0), y(0) {}

    Point(T _x, T _y) : x(_x), y(_y) {}

    Point (Point &_other)
    {
        *this = _other;
    }

    Point &operator = (Point &_other)
    {
        x = _other.x;
        y = _other.y;
        return *this;
    }

}; 
```

No changes in the  main() functions.

Compilation fails. Do you know why and how to fix this?  What happens?

/home/moma/code/test5/main.cpp:: In function &#8216;int main()&#8217;:
[COLOR="Red"]/home/moma/code/test5/main.cpp:98: error: no matching function for call to &#8216;Point<int>::Point(Point<int>)&#8217;
/home/moma/code/test5/main.cpp:65: note: candidates are: Point<T>::Point(Point<T>&) [with T = int]
[/COLOR]:: === Build finished: 2 errors, 0 warnings ===
----------------------------------------------------------------------------------

I have also tried this but no success.

```
template <class T>
class Point
{
   ....

    Point<T> (Point<T> &_other)
    {
        *this = _other;
    }

    Point<T> &operator = (Point<T> &_other)
    {
        x = _other.x;
        y = _other.y;
        return *this;
    }

}; 
```

I thought I could do templates but now am quite confused.
TIA a lot.

---

### Post by PandaGoat on 2007-07-28
I am not exactly sure why this cause that error, but the arguments for the copy constructor and operator need to have the const keyword.

```

template <typename T>
class Point
{
public:
    T x;
    T y;

    Point() : x(0), y(0) {}

    Point(T _x, T _y) : x(_x), y(_y) {}

    Point(const Point &_other)
    {
        *this = _other;
    }

    Point &operator = (const Point &_other)
    {
        x = _other.x;
        y = _other.y;
        return *this;
    }

};

```

---

### Post by moma on 2007-07-28
Ok, thank you.

The [COLOR="Purple"]const[/COLOR] keyword fixed it. Now it compiles without errors.

Here is the code: [http://www.futuredesktop.org/stdkit/basictypes.h](http://www.futuredesktop.org/stdkit/basictypes.h)

---


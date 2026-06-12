---
title: "C++ Segmentation fault"
date: 2009-06-01
forum: Programming Talk
---

### Post by PaulM1985 on 2009-06-01
Hi

I have a pointer to a Shape object, which contains an array of pointers to Face objects.

Shape has a function described below:

```

Face* Shape::get_face(int the_face)
{
  std::cout << "returning a face" << std::endl;
  return faces[the_face];
}

```

I get the "returning the face" output and then get:
```

returning a face
./run.sh: line 1:  8927 Segmentation fault      LD_LIBRARY_PATH=./Core ./run

``` 

I have narrowed down the error to the line:

Face *a_face = shape->get_face(0);

which should get me the first Face in my array.  I am not sure why this has happened, I looked up segmentation errors and the website (good ole Wikipedia) said it was usually due to assigning a value to a pointer that was already assigned, which I didn't think made much sense, as my pointer is only assigned this first time.

Any ideas.

Paul

---

### Post by crdlb on 2009-06-01
Seeing (more of) the actual code would be helpful. You could also try using valgrind and/or gdb. From the bit of code you did post, you should probably bounds-check that array index before using it, or use something fancier than an array (e.g. a vector).

---

### Post by PaulM1985 on 2009-06-01
MyArea.h
```

#ifndef MYAREA_H
#define MYAREA_H

#include <gtkmm/drawingarea.h>
#include "Shape.h"

class MyArea : public Gtk::DrawingArea
{
public:
  MyArea();
  virtual ~MyArea();

  virtual void redraw(Shape *s);

  Shape *shape;

  int go;

  //Override default signal handler:
  virtual bool on_expose_event(GdkEventExpose* event);
};

#endif // MYAREA_H

```

MyArea.cpp
```

#include "MyArea.h"
#include "Shape.h"
#include "Face.h"
#include <cairomm/context.h>
#include <iostream>

MyArea::MyArea()
{
  go = 0;
}

MyArea::~MyArea()
{
}

void MyArea::redraw(Shape *s)
{
  go = 1;
  shape = s;

   Glib::RefPtr<Gdk::Window> win = get_window();
    if (win)
    {
        Gdk::Rectangle r(0, 0, get_allocation().get_width(),
                get_allocation().get_height());
        win->invalidate_rect(r, false);
    }
}

bool MyArea::on_expose_event(GdkEventExpose* event)
{
// This is where we draw on the window
  Glib::RefPtr<Gdk::Window> window = get_window();
  Face *a_face;

  if(window)
  {
    std::cout << "Drawing" << std::endl;
    Gtk::Allocation allocation = get_allocation();
    const int width = allocation.get_width();
    const int height = allocation.get_height();

    // coordinates for the center of the window
    int xc, yc;
    xc = width / 2;
    yc = height / 2;

    Cairo::RefPtr<Cairo::Context> cr = window->create_cairo_context();
    cr->set_line_width(1.0);

    // clip to the area indicated by the expose event so that we only redraw
    // the portion of the window that needs to be redrawn
    cr->rectangle(event->area.x, event->area.y,
            event->area.width, event->area.height);
    cr->clip();

    // draw red lines out from the center of the window
    cr->set_source_rgb(0.0, 0.0, 0.0);
    
    if (go)
      a_face = shape->get_face(0);
    else 
      std::cout << "shape is null" << std::endl;

    std::cout << "got a face" << std::endl;
    cr->move_to(xc, yc);
    //    int **corners = face->get_corners();

    //    std::cout << "a corner " << corners[0][0] << std::endl;

    /*    for (int i = 0; i < shape->get_number_of_faces(); i++)
      {
	Face *face = shape->get_face(i);

	cr->move_to(xc, yc);

	int **corners = face->get_corners();

	for (int j = 0; j < face->get_number_of_corners(); j++)
	  {
	    cr->line_to(corners[0][j], corners[1][j]);
	  }
      } */

    cr->move_to(0, 0);
    cr->line_to(xc, yc);
    cr->line_to(0, height);
    cr->move_to(xc, yc);
    cr->line_to(width, yc);
    cr->stroke();
  }
    return true;
}

```

Shape.h
```

#include "Face.h"

#ifndef SHAPE_H
#define SHAPE_H

class Shape
{
  Face **faces;
  int number_of_faces;


 public:
  Shape(int a_number_of_faces);
  ~Shape();
  Face* get_face(int the_face);
  int get_number_of_faces();
};

#endif

```

Shape.cpp
```

#include "Shape.h"
#include "Face.h"
#include <iostream>

Shape::Shape(int a_number_of_faces)
{
  std::cout << "Creating a shape" << std::endl;

  number_of_faces = a_number_of_faces;

  faces = new Face*[number_of_faces];

  int **a = new int*[3];

  for (int i = 0; i < 3; i++)
    {
      a[i] = new int[4];
    }

  a[0][0] = 0;
  a[1][0] = 0;
  a[2][0] = 0;

  a[0][1] = 0;
  a[1][1] = 100;
  a[2][1] = 0;

  a[0][2] = 100;
  a[1][2] = 100;
  a[2][2] = 0;

  a[0][3] = 100;
  a[1][3] = 0;
  a[2][3] = 0;

  faces[0] = new Face(a, 4);
}

Shape::~Shape()
{
  delete faces;
  delete &number_of_faces;
}

Face* Shape::get_face(int the_face)
{
  std::cout << "returning a face" << std::endl;
  return faces[the_face];
}

int Shape::get_number_of_faces()
{
  return number_of_faces;
}

```

Paul

---

### Post by MadCow108 on 2009-06-01
didn't find the reason for segfault yet but found a memory leak:
Shape::~Shape()
{
  delete faces;
  delete &number_of_faces;
}

this destructor is only deleting your pointer but not what it points to
loop over the array delete everything and the call delete [] faces
(or use vectors...they really make live easier also with this segfault issues.
If you decide to use vectors keep in mind not to add raw pointers to the vector as you'll end up with a similar problem. Also readup on auto_ptr (or the better boost::shared_ptr) then)

possible reason for the segfault (as thers code missing i can't say):
you only initialise faces[0] but maybe you call more in the loop (depending on the construction which has not been posted)
e.g. is number_of_faces > 1 then this is your segfault

---

### Post by mdawg414 on 2009-06-01
It also looks like faces is a 2-d dynamic array and you set the face to faces[0] which should be an array in itself. I agree with MadCow, whatever is supposed to be happening on the assignment of faces[0] is probably not what is actually happening as that doesn't look too right.

---

### Post by dwhitney67 on 2009-06-01
The destructor in Shape definitely is wrong.  Should probably be:
```

Shape::~Shape()
{
  delete [] faces;
}

```

As for the rest of the code, I am still examining it to figure out this fascination with using pointers and arrays, when they do not seem absolutely necessary.

If pointers are required, consider declaring a vector to hold the Face object(s).
```

#include <vector>

...

class Shape
{
public:
  Shape(size_t numberOfFaces);
  virtual ~Shape();
  const Face* getFace(size_t faceIndex);
  size_t getNumberOfFaces() const;
private:
  std::vector<Face*> faces;
};

Shape::Shape(size_t numberOfFaces)
{
  faces.resize(numberOfFaces);

  ...

  faces[0] = new Face(a, 4);
  ...
}

Shape::~Shape()
{
  for (std::vector<Faces*>::iterator it = faces.begin(); it != faces.end(); ++it)
  {
    delete *it;
  }
}

const Face*
Shape::getFace(size_t faceIndex)
{
  Face* face = 0;

  if (faceIndex < faces.size())
  {
    face = faces[faceIndex];
  }

  return face;
}

size_t
Shape::getNumberOfFaces() const
{
  return faces.size();
}

```

---

### Post by PaulM1985 on 2009-06-02
I have only started learning c++.  I thought that to create a new object I needed to do

MyObject *thing = new MyObject(args);

Is there a way to do:

MyObject thing = new MyObject(args);

so a pointer would not be needed?

Paul

Also,  I tried doing shape->get_number_of_faces() in  MyArea.cpp, to print out the number of faces and removed the line to get the faces and still get the same segfault.  I made the changes suggested in the above post to the Shape class and the errors still occurred.

---

### Post by mdawg414 on 2009-06-02
Oh no, you are correct. I did not see the "new" keyword. In C++, new will return the memory address so you will almost always want to use a pointer on the left side.

Do you always get the segfault when calling that method or only after deleting some faces? If it is the latter, then it is probably a problem with the destructor.

---

### Post by PaulM1985 on 2009-06-02
The problem seems to be whenever I try to do anything with shape in MyArea.cpp.  I have done std::cout << shape << std::endl and it returned a memory address so I am assuming shape is pointing at something, but when I call either of the two Shape functions (get_faces or get_number_of_faces) I get the segfault.

I am moving over from Java and so all of this stuff is new and different to me.

Paul

---

### Post by mdawg414 on 2009-06-02
Based on your first post, it doesnt look like the shape object is causing the segfault. Since it prints out "reading a face" it means that the function call of get_face is ok. Instead, it seems that the offset on the "faces" object is causing the segfault. Try printing out what "faces" is and make sure that is a valid memory address and not 0 or something and let me know what you find

---

### Post by Linteg on 2009-06-02
> **PaulM1985 said:**
> Is there a way to do:

MyObject thing = new MyObject(args);

so a pointer would not be needed?
There is:
```
MyObject thing(args);
```

---

### Post by dwhitney67 on 2009-06-02
> **PaulM1985 said:**
> I have only started learning c++.  I thought that to create a new object I needed to do

MyObject *thing = new MyObject(args);

Is there a way to do:

MyObject thing = new MyObject(args);

so a pointer would not be needed?

Paul
...

Sometimes it is necessary to allocate memory, other times it is not.  It depends on the needs of the application.  To answer your question above, one could instantiate a MyObject on the stack using:
```

MyObject thing(args);

// or, equivalently

MyObject thing = MyObject(args);

```

As you can see, this is trivial if doing it within a function; however, if this object is needed in a class, then one must approach the solution slightly differently.  Here's an example of how to do this:
```

class Foo
{
public:
  Foo(...);
private:
  MyObject thing;
};

Foo::Foo(...)
  : thing(args)
{
}

```
Note that one must construct 'thing' before the constructor body; otherwise, if MyObject has a no-arg constructor, it will automatically be constructed before the constructor body is entered.  This may have undesirable effects, including possible compilation errors (if the no-arg constructor is not defined) or performance hits during runtime.

Typically, allocation from the heap is warranted when you do not know ahead of time how many objects you may need to create; you only find out during runtime.  There are other cases when it useful, but always see if you can employ a solution that does not require you to allocate from the heap.

If you would like to look into advance topics of C++, look at the usage of smart-pointers, such as the C++'s tr1 shared_ptr or into Boost's version of the same, including scoped_ptr and a few other flavours.

Wrt your segfault, I suspect the reason no one has come forward to tell you exactly why the application is crashing is because you have not posted the complete code.  It is easiest to find the cause of a segfault when one can run the application.  Perhaps today, you can post your complete code, including the main() function, so that it can be compiled/linked.

---

### Post by MadCow108 on 2009-06-02
> **mdawg414 said:**
> Based on your first post, it doesnt look like the shape object is causing the segfault. Since it prints out "reading a face" it means that the function call of get_face is ok. Instead, it seems that the offset on the "faces" object is causing the segfault. Try printing out what "faces" is and make sure that is a valid memory address and not 0 or something and let me know what you find

It prints the "reading a face" message before accessing the array.
So it could still be the cause.
But we can't say without complete code.

---

### Post by dwhitney67 on 2009-06-02
> **MadCow108 said:**
> It prints the "reading a face" message before accessing the array.
So it could still be the cause.
But we can't say without complete code.

I agree 100%.  <edit> ... I should not be looking at code early in the morning.  :-)

---

### Post by MadCow108 on 2009-06-02
the whole loop is commented out :)

another thing I noticed is that the 2d array "a" is never deleted.
Another memory leak. (these things are a real pain in C, that why C++ has vectors, use them!)
To delete it:
for (i=0;i<size;i++) delete [] a[i]
delete [] a;
(except the faces class handles the deleting, which on the other hand would mean you have to watch that you don't try to access a in shape, because you can't know if it still exists (C++ Boost or TR1 has another solution for that: boost::shared_ptr))

---

### Post by mdawg414 on 2009-06-02
> **MadCow108 said:**
> It prints the "reading a face" message before accessing the array.
So it could still be the cause.
But we can't say without complete code.
Paul was under the impression that the shape object was causing the segfault. I am saying that the shape object seems to be OK since he was able to call a function from it. Instead, it seems the faces pointer is pointing somewhere it shouldnt be

---

### Post by PaulM1985 on 2009-06-02
Shape object was a null pointer.

When I was passing it in I was passing an empty index.

Thanks for everyone having a look at this.

I am going to go all the way through my code and make sure I guard against all of the stuff highlighted here.  Memory leaking etc.

Thanks again for all of your input.  Its much appreciated.

Paul

---


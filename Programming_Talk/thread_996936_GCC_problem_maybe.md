---
title: "GCC problem? maybe"
date: 2008-11-29
forum: Programming Talk
---

### Post by chris200x9 on 2008-11-29
Hi I have tried to write a program I developed for a school lab (this is not homework help) everyone else in the class uses windows and visual studio, the program works fine for them. I have written the following but it gives me the following error
```
 /tmp/ccujAOOq.o: In function 'main':
lab12.cpp:(.text+0xa5): undefined referance to 'Circle::Circle(int, int, int,int)'
collect2: Id returned 1 exitstatus
Compilation failed.

```

I went over this with my lab instructor and he couldn't figure this out either. Each section compiles fine but build messes up, also I can combine the object code via command line and get a functioning executable but on every IDE I get this error (I've tried geany and codebocks). 

here is my code 

lab12.cpp:
```


#include <string>
#include <iostream>
#include "Shape.h"
#include "Circle.h"// same

using namespace std;
int main(int argc, char** argv)
{
	//Circle a(3,1,2,3);
	//Shape(1,1,1);
	Shape *pointerToShape[4];
	pointerToShape[0] = new Circle( 3, 6, 9, 1);
	pointerToShape[0]->Print();

	return 0;
}

```

Shape.h:
```

#pragma once
class Shape	{
private:
    int	x;
    int	y;
    int	color;
public:
    Shape(int x, int y, int color);
    ~Shape();
    virtual void Print();
};

```

Circle.h
```

#include "TwoDimensionalShape.h"
class Circle: public TwoDimensionalShape{
private:
    int	radius;
public:
    Circle(int x, int y, int radius, int color);
	  ~Circle();
	
    void Print();
    int getArea();
    
};

```

Shape.cpp
```

#include "Shape.h"
#include <iostream>
using namespace std;

Shape::Shape(int x, int y, int color){
}
void Shape::Print()
{
	cout<<"I am shape";
}

Shape::~Shape() {
}

```

Circle.cpp 
```
 
#include "Circle.h"
  #include <iostream>
  using namespace std;  
    Circle::Circle(int x, int y, int radius, int color):TwoDimensionalShape(x,y,color)
    {
    }
    
    void Circle::Print()
    {cout<<"I am a Circle";
    }
    
    int Circle::getArea()
    {
    return 3.14*radius*radius;
    }


```


Please help I do not have access to windows or visual studio and I cannot afford to fail this lab. Thank you.

---

### Post by nebu on 2008-11-29
are you linking your header files when u are compileing with gcc???

your gcc compile statement should be something like 

gcc -l<path to header file> <something.cpp>

gcc does not know where ur custom header files are unless they are defined in the path......
so u hav to giv it the location....

just read the manual entry for gcc

---

### Post by wmcbrine on 2008-11-29
You don't link headers, you link libraries. There are no libraries involved here, and gcc has no problem finding header files in the current directory.

It looks like you're not linking the object files in the right order, but I don't know exactly, since you haven't explained that step. Also, I don't really understand why it matters whether or not you can build it in the IDE, if you can successfully build it from the command line. But then, I'm not an IDE guy. :)

I'm also not clear on how this isn't homework.

---

### Post by dexter on 2008-11-29
Make sure you use g++, not gcc when compiling c++ code files.
I've tried compiling your code and is works here (removed every refence to TwoDimensionalShape since it's not included). Try compiling your source this way:

1. make object files
g++ -c Circle.cpp -o Cirle.o
g++ -c Shape.cpp -o Shape.o
g++ -c lab12.cpp -o lab12.o

2. link everything together and build executable
g++ Cirlce.o Shape.o lab12.o -o Shapes

3. Run you program :)
./Shapes

---

### Post by chris200x9 on 2008-11-29
thanks all!

---


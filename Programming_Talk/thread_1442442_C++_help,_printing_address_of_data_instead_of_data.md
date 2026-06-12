---
title: "C++ help, printing address of data instead of data"
date: 2010-03-30
forum: Programming Talk
---

### Post by Hume's doona on 2010-03-30
Hi,

I'm just starting out with C++ and trying to get my head around objects.

I've written a simple program, but it has a really stoopid bug, in that it appears to print the memory address of the data I'm trying to output. Code is below:

Rectangle.h
```
class Rectangle{
	public:

    Rectangle();
	Rectangle(double, double);
	double setHeight(double);
	void setWidth(double);
	double getArea();
	double getPerimeter();
	double getHeight();
	double getWidth();

	private:

	double height;
	double width;
};
```

Rectangle1.cpp
```
#include "Rectangle.h"

Rectangle::Rectangle():height(4), width(2){}
Rectangle::Rectangle(double width, double height){
	setWidth(width);
	setHeight(height);
}
double Rectangle::setHeight(double height){
	if (height < 1){
		height = 1;
	}
	else {height = height;
	}
	return height;
}
void Rectangle::setWidth(double width){
	if (width < 1){
		width = 1;
	}
	else {width = width;
	}
}

double Rectangle::getArea(){
	double area = width * height;
	return area;
}
double Rectangle::getPerimeter(){
	return (2 * width)+(2 * height);
}
double Rectangle::getHeight(){
	return height;
}
double Rectangle::getWidth(){
	return width;
}
```

main.cpp
```
#include <iostream>
#include "Rectangle.h"
using namespace std;

//void printRectangle(Rectangle rec1);
//void printRectangle(Rectangle rec2);

int main(){
	Rectangle rec1(4, 40);
//	printRectangle(rec1);
	Rectangle rec2(3.5, 35.9);
	Rectangle rec3(1,2);
//	printRectangle(rec2);
	cout << "The area of the rectangle with width:height : " << rec1.getWidth() << ":" << rec1.getHeight() << " is : " << rec1.getArea() << endl;
	cout << "The perimeter is : " << rec1.getPerimeter() << endl;
    cout << "The area of the rectangle with width:height : " << rec2.getWidth() << ":" << rec2.getHeight() << " is : " << rec2.getArea() << endl;
	cout << "The perimeter is : " << rec2.getPerimeter() << endl;
//	cout << rec3.getWidth;
	cout << rec3.getHeight() << endl;
	return 0;
	}
```





And the output is:
```
The area of the rectangle with width:height : 0:6.95331e-310 is : 0
The perimeter is : 1.39066e-309
The area of the rectangle with width:height : 2.07323e-317:0 is : 0
The perimeter is : 4.14645e-317
6.93685e-310
```

Can someone please steer me in the right direction?

Cheers

---

### Post by Lux Perpetua on 2010-03-30
> **Hume's doona said:**
> I've written a simple program, but it has a really stoopid bug, in that it appears to print the memory address of the data I'm trying to output. Really? How do you figure?

```
double Rectangle::setHeight(double height){
	if (height < 1){
		height = 1;
	}
	else {height = height;
	}
	return height;
}
```What do you think **height = height;** does? (Hint: nothing useful.) Change the name of the parameter, or use **this->height** to refer to the object's data member.

---

### Post by Hume's doona on 2010-03-30
:lol: I di kinda figure that, not sure why I left it :redface:

---

### Post by Tony Flury on 2010-03-30
The same bug exists on the width - essentially your code is not printing the addresses - it is printing rubbish - i.e. non initialised attributes.

---

### Post by MadCow108 on 2010-03-30
better compile with -Wshadow
that warns about these kind of problems

---

### Post by dwhitney67 on 2010-03-30
Just to weigh in... it is not typical for a set-accessor to return a value.  Just have it perform the one operation it is intended to do, and that is store the given value.  For example:
```

void setHeight(double h)
{
   height = (h < 1 ? 1 : h);
}

double getHeight() const
{
   return height;
}

```

---


---
title: "C++ how to access non-overloaded function in derived class?"
date: 2007-07-11
forum: Programming Talk
---

### Post by c174 on 2007-07-11
Hello Everybody

I'm trying to do something very basic with classes in C++. However, I'm confused. Here's what I want to do:

1) Have a general class Shape which acts as a common interface to other class-functions  that specialize the Shape-class
2) The specialized classes can have extra functions not defined in class Shape. I want to acces those too, through the Shape-class.

I was thinking that the above could be done using inheritance of abstract classes. Here is a small test program for illustration

```
class Shape {
public:
	Shape() { cout << "shape constructor" << endl; }

	virtual int getSlope() = 0; // pure syntax enforces getSlope to be defined in both Line and Curve

	virtual int getLine() { return 0; } // why is this needed to access getLine through Line* ???
	virtual int getCurve() { return 0; } // why is this needed to access getCurve through Curve* ???
};

class Line : public Shape {
public:
	Line() { cout << "line constructor" << endl; }
	int getSlope() { return 1; }
	int getLine() {return -1; }
};

class Curve : public Shape {
public:
	Curve() { cout << "curve constructor" << endl; }
	int getSlope() { return 2; }
	int getCurve() { return -2; }
};

int main( int argc, char *argv[] ) {

	Shape* shape1 = new Line();
	Shape* shape2 = new Curve();

	cout << "shape1: getSlope " << shape1->getSlope() << endl; // prints "1"
	cout << "shape1: getLine " << shape1->getLine() << endl; // prints "-1"

	cout << "shape1: getSlope " << shape2->getSlope() << endl; // prints "2"
	cout << "shape2: getCurve " << shape2->getCurve() << endl; // prints "-2"

	cout << "shape1: getCurve " << shape1->getCurve() << endl; // prints "0" -- Oops!
	cout << "shape2: getLine " << shape2->getLine() << endl; // prints "0" -- Oops!

	delete shape1;
	delete shape2;
	return 0;
}
```

Running the code shows that the constructor of the derived classes get called  when shape1 and shape2 are created. However, if a remove the line "virtual int getLine() ..." and "virtual int getCurve()..." from the Shape class definition I cannot access those functions any more! The problem with having these extra virtual functions is illustrated in the last part of the program, where getCurve is called from a "pointer to a Line" -- I would like this to generate an error to avoid programming errors in a more complicated program.

I realize that my question must be rather basic. I would appreciate if someone could show me the right way to do it, or tell me if it is not possible to have this functionality in C++.

Thanks in advance :)

---

### Post by runningwithscissors on 2007-07-11
Classes derived from shape that do not want to implement the getCurve/getLine functions should override them and throw an Exception when the function is called.

Or, if you know the type at runtime you can do a cast to the derived type and access the relevant function, in which case, you do not need virtual functions in the base class. Which is kind of ugly and very cumbersome.

---

### Post by c174 on 2007-07-11
The Exception-idea is nice! :)

Casting would be ugly, yes, but it's not needed here since "getCurve" would not make sense anyhow for a "Line".

So, I guess Exceptions is the way to deal with it? It can only be caught at runtime? I think Java can do what I originally had in mind - but I'm not sure though.

Thank you runningwithscissors

---

### Post by runningwithscissors on 2007-07-11
> **c174 said:**
> I think Java can do what I originally had in mind - but I'm not sure though.
C++ can do Exceptions, no need to goto Java for that.
[http://www.cplusplus.com/doc/tutorial/exceptions.html](http://www.cplusplus.com/doc/tutorial/exceptions.html)

---

### Post by c174 on 2007-07-11
I guess I could put the error message (or exception) directly in the body Shape::getLine and Shape::getCurve. In this way I get an error if the functions are not overloaded - in this case I don't have to include a "getCurve" in the "Line"-class (which could become tedious if "Line" and "Curve" have a lot of functions that a not in common from "Shape").

There is no way of rearranging the classes to get the functionality at compile time?

---

### Post by runningwithscissors on 2007-07-11
> **c174 said:**
> I guess I could put the error message (or exception) directly in the body Shape::getLine and Shape::getCurve. In this way I get an error if the functions are not overloaded - in this case I don't have to include a "getCurve" in the "Line"-class (which could become tedious if "Line" and "Curve" have a lot of functions that a not in common from "Shape").That's a good idea, but any extra functions defined in the derived classes can then only be reached by casting.

> **c174 said:**
> There is no way of rearranging the classes to get the functionality at compile time?As far as I know, C++ does not allow modification of types at runtime. But, I am not a very proficient C++ programmer.

---

### Post by c174 on 2007-07-11
Ok, I'll stick to the current approach then, although it is a little bit clumsy.

Thank you for replying to this thread

---


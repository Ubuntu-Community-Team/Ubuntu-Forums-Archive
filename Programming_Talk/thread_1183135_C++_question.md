---
title: "C++ question"
date: 2009-06-09
forum: Programming Talk
---

### Post by Mirge on 2009-06-09
I have a question... see below in bold (public):

```

#include <iostream>

using namespace std;

class Polygon {
    protected:
        int width;
        int height;

    public:
        void SetValues(int width, int height);
};

class Rectangle : *_**public**_* Polygon {
    public:
        int GetArea();
};

// ##############################################
int main(int argc, char *argv[])
{
    Rectangle shape1;

    shape1.SetValues(5, 8);
    cout << "The area of shape1 is: " << shape1.GetArea() << endl;
    
    return 0;
}

// ##############################################
void Polygon::SetValues(int width, int height) {
    this->width = width;
    this->height = height;
}

// ##############################################
int Rectangle::GetArea() {
    return (this->width * this->height);
}

```

Output:
mike@mike-kubuntu:~/cpp$ ./class2
The area of shape1 is: 40
mike@mike-kubuntu:~/cpp$

```

class Rectangle : public Polygon {

```

This is the part I don't really understand. I know that I'm creating a new class called Rectangle, which inherits the properties & methods of Polygon... but what exactly does the "public" keyword there mean? Thanks!

---

### Post by SledgeHammer_999 on 2009-06-09
It is explained nicely [here](http://www.cplusplus.com/doc/tutorial/inheritance/). Take notice of the table.

---

### Post by Mirge on 2009-06-09
Thanks! Having a slightly difficult time understanding it, I'll have to play around with some code to catch on I think. Thanks again! :)

---

### Post by Jimleko211 on 2009-06-09
This is coming from a Java education, but from what I know is that public means that other objects can interact with it.  Private means that other objects can't interact with it, thus the "encapsulation" pillar.

---

### Post by Mirge on 2009-06-09
That helps as well, thanks :).

---

### Post by asbuntu on 2009-06-13
When you derive a (child) class from a (parent) class, any members of the parent class that are marked public are visible and usable in the child class as if they existed in the child class.

Any parent members that are marked private are inaccessible to the child class.  They don't exist in the child class.  Any manipulation of those (opaque) members must be through public members (methods).

Not sure I have this next part right, but I seem to recall that the middle ground is 'protected', which means that the member is available in the child class but can not be subsequently marked as public or protected.

Hope this helps.

---

### Post by Mirge on 2009-06-13
That helps clarify too, I'm pretty sure I get it now :) Thanks :)

---

### Post by asbuntu on 2009-06-13
You are very welcome.

I do want to correct something I said, however...

> **asbuntu said:**
> Any parent members that are marked private are inaccessible to the child class.  They don't exist in the child class.

The part about "they don't exist in the child class" is not quite correct.

They do exist in every instantiation of the child (or the parent) class.  They just can not be manipulated by any method other than one that belongs to the parent class.

You do seem to understand the original issue, so I will drop off at this point.  Re-post, however, and I can discuss opaqueness, data hiding, encapsulation, etc.

---

### Post by MadCow108 on 2009-06-13
I think your original question has not been answered directly (sorry if I overread it) and it my have been overlooked in the link.

the public statement after semicolon:
class daughter : public mother

means that all the public variables of the mother class are also public in the daughter class. private and protected are not changed.
You can also set other access flags.
e.g. protected would mean that all the public variables which daughter inherits from mother are protected no matter that they were public mother class.
example (will give compile error because of marked points):
```

#include <iostream>
class mother
{
	public:
	int var;
	private:
	int privatevar;
};

class son : public mother
{
	public:
	int othervar;
};

class daughter : protected mother
{
	public:
	int othervar;
};

using namespace std;
int main (int argc, char *argv[])
{
	mother cmother;
	//Ok var is public;
	cmother.var=1;

	son cson;
	//Ok var has been inherited with same access in son
	cson.var=1;
	//Not Ok privatevar is still inherited private, it can only be changed from within the class
	cson.privatevar=1;

	daughter cdaughter;
	//Not Ok var has been inherited as protected although it was public in mother
	cdaughter.var=1;
	return 0;
}

```

---


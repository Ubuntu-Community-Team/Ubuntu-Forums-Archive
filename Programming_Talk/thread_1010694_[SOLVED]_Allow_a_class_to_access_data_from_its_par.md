---
title: "[SOLVED] Allow a class to access data from its parent."
date: 2008-12-14
forum: Programming Talk
---

### Post by u-slayer on 2008-12-14
Okay I got class A (parent class) which creates an instance of class B (child class) inside of it. I want the methods in class B to access the data of class A. Is this possible? I've been reading the article on [Circular Dependency]("http://en.wikipedia.org/wiki/Circular_dependency"), but I want to do this without a mess of header files. 8-)

```
class B;

class A
{
	public:
		
	int qqq;
	B* child;
	
	A()
	{
		qqq = 32;
		child = new B(this);
	}
};

class B
{
	public:
	
	A* parent;
	
	B(A* p)
	{ parent = p; }
	
	void print()
	{
		cout << parent->qqq << endl;
	}
};

int main(void)
{
	A parent;
	parent.child->print();
}
```

and here are the errors:

```
error: invalid use of incomplete type 'struct B'
error: forward declaration of 'struct B'
```:guitar:

---

### Post by roelpeeters on 2008-12-14
Hi!

The usual approach to solve a circular dependency is to create a third (interface) class C which combines both A and B as pointers. This way they can be linked to eachother without knowing of each others existence.

Something like this:
```

class C {
public:
   C(A* a, B* b): a_(a), b_(b) 
   {} 
private:
   A* a_;
   B* b_;
};

```

Hope this helps,
Roel.

---

### Post by CptPicard on 2008-12-14
I guess it is "friend classes" that the OP is looking for...

---

### Post by geirha on 2008-12-14
The problem is that A's constructor is using B's constructor before B's constructor has been declared. One way to get around that is to only declare A's constructor in the class declaration, and define it after B's constructor has been declared.

```

class B;
class A
{
    ...
    A(); // declare constructor
};
class B
{
    ...  
};
A::A()   // define constructor
{
    qqq = 32;
    child = new B(this);
}

```

EDIT: Oh and don't forget to make a destructor that deletes the child.

---

### Post by dribeas on 2008-12-14
The error is unrelated to the title of the post. There is a limited amount of things you can do with a forward declared class (defining pointers, references or static member variables) and many things you cannot do until the full declaration of the class is presented to the compiler. (Read [this post]("http://http://ubuntuforums.org/showpost.php?p=6244789&postcount=1")'s comments)

```

class A;
class B;

class A // class declaration
{
public:
   A();
private:
   B* child_;
};

class B
{
public:
   B( A* parent ) : parent_(parent) {}
private:
   A* parent_;
};

A::A() : child( new B( this ) ) // ok B has been fully declared
{}

```

---

### Post by u-slayer on 2008-12-15
Okay thanks, geirha. I have been playing with this some more and it makes for an interesting demo on pointers.

These two statements are equivalent:
```
par.child->parent->quad();	
par.child->parent->child->parent->child->parent->child->parent->child->parent->child->parent->child->parent->quad();

```

I wonder what kind of performance hit the second statement takes:lolflag:

```
class A;

class B
{
	public:
	
	A* parent;
	
	B(A* );
	
	void print();
	
	//Hi refs nothing so it is fine here
	void hi()
	{ cout << "hi" << endl;}
};

class A
{
	public:
		
	int qqq;
	double* ddd;
	
	B* child;
	
	A()
	{
		cout << "Class A constructor: " << this << endl;
		
		qqq = 32;
		child = new B(this);
		
		//Create a gig of data in ram to prove that it is not duplicated
		ddd = new double[(int)1.25e8];
		for ( int x = 0; x < (int)1.25e8; x++ )
			ddd[x] = x;
	}

	//quad refs nothing so it is fine here
	void quad()
	{
		qqq *= 4;
	}
};

B::B(A* p)
{ 
	cout << "Class B constructor: " << this << endl;
	parent = p; 
	cout << "Parent = : " << parent << endl;
}


//Print References A therefore it needs to be after A
void B::print()
{
	cout << parent->qqq << endl;
}

int main(void)
{
	A par;
	par.child->print();
	par.child->parent->quad();
	//par A creates child B passing it A's address
	//B refs A which has function quad
	
	par.child->parent->child->parent->child->parent->child->parent->child->parent->child->parent->child->parent->quad();		//Same function as above
	
	par.child->print();
	par.child->hi();
	
	char c; cin >> c;	//Pause
	
}
```

---

### Post by u-slayer on 2008-12-15
> **u-slayer said:**
> 

```
par.child->parent->quad();	
par.child->parent->child->parent->child->parent->child->parent->child->parent->child->parent->child->parent->quad();
```
I wonder what kind of performance hit the second statement takes:lolflag:


I added a  for ( int x = 0; x < (int)1e9; x++)  before each statement to test it.

Above first statement = 4.868s
Above second statement = 10.832s

---


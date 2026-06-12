---
title: "Creating derived classes C++"
date: 2009-07-16
forum: Programming Talk
---

### Post by Benzaa on 2009-07-16
How would you create some derived classes given a choise??

In my case, I have something like this

```

class Reaction {
Reaction(void)
~Reaction(void)
.
.
}

class R1 : public Reaction {
R1(void)
~R1(void)
.
.
}

class R2 : public Reaction {
R2(void)
~R2(void)
.
.
}
```

And then, I use an "if" to create a library of reactions that I need. 

```

vector<Reaction*> library;

if ( ReactionName == "R1" ) 
   library.push_back( new R1 )

else if ( ReactionName == "R2" )
   library.push_back( new R2 )
.
.
.
}
```

I've done that for several reactions. 

Is there a more effective way to do it?
Is there a neat C++ trick that could help me with that??

---

### Post by dwhitney67 on 2009-07-16
What you have is fine.

If you plan to declare virtual methods in your base class, ensure that it also has a virtual destructor.

P.S.  There are other approaches, but simplistically what you have is fine.

---

### Post by smartbei on 2009-07-16
If you have a bunch of them, you may want to try using a map between the strings 'R1', 'R2', etc. to the function that creates the object, so that you won't have tons of ugly if... else. then you could also have a simple macro that registers a class in the map, and creates the creating function.

On second thought, you could just replace it with a switch...case and that would be just as well.

---

### Post by MadCow108 on 2009-07-16
when putting pointer to objects in containers you should consider using smart pointers like the boost::shared_ptr (and variants)

otherwise you have to take care to delete the objects of the vector "per hand" when the vector gets deleted.

---

### Post by Benzaa on 2009-07-16
What are the other approaches??

Will they help me to work with a lot of derived classes?

In my program I have something like 100 reaction classes, so, putting and "else if" everytime I create a new clase is a bit of a problem ( I think Im being lazzy )

---

### Post by Benzaa on 2009-07-16
> **MadCow108 said:**
> when putting pointer to objects in containers you should consider using smart pointers like the c++ standard auto_ptr or the boost::shared_ptr (and variants)

otherwise you have to take care to delete the objects of the vector "per hand" when the vector gets deleted.

How will you initialize the vector with auto_ptr??
would it be like

```

vector<auto_ptr<Reaction> > library;

```

---

### Post by MadCow108 on 2009-07-16
correction: the c++ standard auto_ptr should not be used for containers. because they aren't copyable

but the boost library has smart pointers which can be used in containers.
[http://www.boost.org/doc/libs/1_39_0/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/doc/libs/1_39_0/libs/smart_ptr/smart_ptr.htm)
it also has a special pointer container:
[http://www.boost.org/doc/libs/1_39_0/libs/ptr_container/doc/ptr_container.html](http://www.boost.org/doc/libs/1_39_0/libs/ptr_container/doc/ptr_container.html)

---

### Post by Zugzwang on 2009-07-16
Actually, whenever applicable, it is normally considered to be better style to store the objects itself in the container, rather than just its pointers.

```

vector<Reaction> library;

```

Note that this requires you to have a copy-constructor and an assignment operator, which will be constructed automatically for you (which is fine unless in turn you pointers or something else you what to handle explicitly in your class).

Note that here's another approach to your problem:
[PHP]
#include <string>
#include <iostream>
#include <vector>

class Base {
public:
	virtual void hello() = 0;
};

class A : public Base {
public:
	virtual void hello() { std::cout << "Hello from class A.\n"; };
	static Base* make() { return new A; };
};

class B : public Base {
public:
	virtual void hello() { std::cout << "Hello from class B.\n"; };
	static Base* make() { return new B; };
};

//=================[Creator]========================
class CreateListEntry {
private:
	std::string name;
	Base* (*make)(void);
public:
	CreateListEntry(std::string _name, Base* (*_make)(void)) : name(_name), make(_make) {};
	Base* apply(std::string _name) {
		if (name==_name) return make();
	}
};

class CreateList {
private:
	std::vector<CreateListEntry> creators;
public:
	CreateList() {
		creators.push_back(CreateListEntry("A",A::make));
		creators.push_back(CreateListEntry("B",B::make));
	}
	Base *getInstance(std::string name) {
		Base *which = NULL;
		for (int i=0;i<creators.size();i++) {
			which = creators[i].apply(name);
			if (which!=NULL) return which;
		}
	}
};


CreateList createList;
//=================[/Creator]========================

int main() {
	createList.getInstance("A")->hello();
	createList.getInstance("B")->hello();
}
[/PHP]

Here, you add all the classes you have *one* to a vector and then you can create instances using the identifiers provided.

---

### Post by Habbit on 2009-07-16
You could have a map of type identifiers (for example, the strings you were using, or integers, or whatever) to factory functions. A factory function is simple one that returns a new instance of the object (you cannot take a pointer to the constructor just like that). For example:```

typedef Reaction* (*ReactionFactory)()

// ...

class R1 : public Reaction {
public:
    static R1* makeR1() { return new R1(); }
}

// Fill the library
std::map<string, ReactionFactory> library;
library["R1"] = & R1::makeR1;

// Use the library
string ReactionName = getline(cin);
typename std::map<string, ReactionFactory>::iterator item = library.find(ReactionName);
if (item != library.end())
    return item->second(); // This invokes the appropriate factory function
else throw std::invalid_argument("Reaction not found");

```

---

### Post by Benzaa on 2009-07-16
I like these two techniques, I will use them.

Just one comment, it seems that all the reactions have to be loaded all the time. 

There are simulations when I dont use any reactions, so, I dont see the point of creating new objects (that is the reason for using the "if, else" structure). 

So, does it make any difference to have them all loaded or not?

I have the feeling that the program is a bit faster without having to create all the reactions objects.

Any comments??

---

### Post by Zugzwang on 2009-07-16
> **Benzaa said:**
> Just one comment, it seems that all the reactions have to be loaded all the time. 


No, that's not true. You only have a list of them loaded all the time which is used to create them when needed.

---

### Post by Benzaa on 2009-07-16
Ohh, I see it, it is storing the pointers to the "make" member functions.

Thanks for the help, I knew there was a neat trick to do this

---


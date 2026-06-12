---
title: "Help in understanding how C++ Destructors work in classes"
date: 2009-10-26
forum: Programming Talk
---

### Post by Deeack on 2009-10-26
Hi, I'm looking for help in trying to get my head around how class destructors in C++ deal with elements of their class, and I have a few questions I was hoping you could help me out with.

Consider the following example:

[PHP]
using namespace std;

class MyClass {
private:
    int myInt;
    vector<int> myVector;

public:
    MyClass() {
        // Do stuff
    }
    ~MyClass() {
        // Safe to leave empty in this situation?
    }
};

int main() {
    MyClass *example = new MyClass();
    delete MyClass;
}
[/PHP]

In the above example, when the delete is called, would the destructor for the vector be called as well, or do i need to somehow call the destructors of all the elements in the class in the classes destructor?

I'm of the belief that's what would happen but I'm fairly new to coding in C++, so I want to get into the habit of dealing with memory right early rather than have to try and get out of bad habits later!

Also am i right in saying that the abovie situation differs from the following: 

[PHP]
using namespace std;

class MyClass {
private:
    int myInt;
    vector<int> *myVector = new vector<int>;

public:
    MyClass() {
        // Do stuff
    }
    ~MyClass() {
        // Ensure myVector is deleted
        delete MyVector;
    }
};

int main() {
    MyClass *example = new MyClass();
    delete MyClass;
}
[/PHP]

Where if you declare a pointer to an new object you have to call delete on it manually? Does calling a delete on an object call it's destructor, and as such "myVector" should free any memory it's allocated for itself, or am I required to free the vectors allocated memory myself somehow?

Any help in clarifying this would be greatly appreciated!

---

### Post by MadCow108 on 2009-10-26
you are correct.
the first example will free the vector and its associated memory
as will the second case.

then a class gets deleted it calls the destructor of all its members. In your second example this will be the "destructor" of the pointer to the vector and not the vector itself, so you must delete the memory pointed to by the pointer per hand (as you did).

a delete of a an dynamically allocated vector will also delete the members of the vector.

if you want to learn how to handle memory in c++ early its best to read about RAII (resource acquisition is initialization).
That method is used to write exception safe code with very low risk of memory leaks. Its fundament is basically: never use new/delete
E.g. vector's should rarely be allocated with new, as it is a small structure which fits perfectly in stack (~12bytes in most implementations). The dynamics is all handled internally.

a very useful tool to find memory leaks is valgrind.
it can also detect other kinds of programming errors like segfault locations.

---

### Post by Deeack on 2009-10-26
Thanks a bunch for clearing that up for me! I'll have a look at RAII and valgrind!

---

### Post by dribeas on 2009-10-28
The second block of code would not compile, you cannot initialize in the place of member attribute declaration, but rather in the initialization list in the constructor (or in the constructor body, but the initialization list is the correct way of doing it).

Also note that it does not make any sense to hold STL containers (or strings) by pointer. They internally manage the memory they hold through pointers and have a small memory footprint themselves. That is, having a std::vector<> on the stack will not take much more space than holding it inside a pointer, and if a pointer is used, that space will probably be wasted by memory management code/RAII techniques.

---


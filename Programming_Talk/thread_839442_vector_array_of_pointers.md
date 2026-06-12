---
title: "vector array of pointers?"
date: 2008-06-24
forum: Programming Talk
---

### Post by Zeotronic on 2008-06-24
C++: I am making a game, and before I make my code too committed, I thought I should ask if there is any reason that I shouldn't have vector arrays of pointers. I know it doesn't work out making pointers to objects that are in vector arrays, so I thought I would merely make the vector arrays point to the information themselves (because the whole purpose of the arrays is to make the information accessible). For instance, I have an array:```
std::vector<Image_User*> iuser;
```
And I just want to make sure that wouln't error up in any unforseen ways.

---

### Post by henchman on 2008-06-24
iam writing currently ( "currently" ;) ) a gui class wrapper for the win32 api... I am doing it in exactly the same way and all "leaking analyzers" report no errors :)

you just have to make sure that if you delete objects from which pointers are stored in the vector, that you delete the pointer or set them to eg. NULL, so you don't accidentally try to access the objects of them.

---

### Post by Jessehk on 2008-06-24
Bad idea.

Either just store the objects (not pointers) in the vecter:
```

std::vector<Image_User> iuser;

```

or if you **must** store pointers, store a smart pointer like [boost::shared_ptr](http://www.boost.org/doc/libs/1_34_1/libs/smart_ptr/shared_ptr.htm) but **not** a std::smart_ptr as they have copying rules that make them incompatible with the STL containers.

---

### Post by Zeotronic on 2008-06-25
> Bad idea.

Either just store the objects (not pointers) in the vecter:
Code:

std::vector<Image_User> iuser;

or if you must store pointers, store a smart pointer like boost::shared_ptr but not a std::smart_ptr as they have copying rules that make them incompatible with the STL containers. 
Under the assumption that I may have trouble keeping track of my pointers (and what their pointing at), yes, I can see how this would be a bad idea... but I am pretty well confident that I can... so if perhaps you could expand on why its a bad idea, otherwise, I don't see the need to employ some new type of pointer.

---

### Post by Wybiral on 2008-06-25
Aside from managing memory, why would you possibly think it would cause problem? Pointers are just integers...

---

### Post by dwhitney67 on 2008-06-25
Smart Pointers can be useful when a pointer needs to be shared between two or more containers.  When the reference count (that is, the usage count) of the pointer reaches a count of zero, the memory is automatically deleted.  One does not need to worry about deallocating the memory manually and at the same time worry whether the other container(s) are done using the pointer.

If you plan to do it the traditional way, then that is fine too. Here are some examples that should be avoided though:

Example 1:
[PHP]std::vector< MyObject * > vec;
MyObject *obj = new MyObject();
vec.push_back( obj );
delete obj;    // inexperienced user may try to match every new with a delete[/PHP]
Example 2:
[PHP]std::vector< MyObject * > vec;
MyObject obj;
vec.push_back( &obj );   // obj will eventually go out of scope[/PHP]
To ensure careful allocation/management of pointers, consider this style:
[PHP]vec.push_back( new MyObject() );[/PHP]
Also consider creating your own self-cleaning vector object by expanding the std:vector object.  For example:
[PHP]class MyVector : public std::vector< MyObject* >
{
  public:
    MyVector() {}

    ~MyVector()
    {
      for ( unsigned int i = 0; i < this->size(); ++i )
      {
        delete this->at(i);
      }
    }
};[/PHP]

---

### Post by Zdravko on 2008-06-25
Nah, I'd rather do that for ensuring proper deletion of my objects:
[php]
std::vector<MyClass*> vmc;
/*...*/
template <class T>
void deleter(T*& p)
{
    delete p;
    p = 0;
}
/*...*/
std::for_each(vmc.begin(), vmc.end(), deleter<MyClass>);
[/php]Pure and elegant! Of course, in C++0x there will be shared_ptr and things will get even more elegant. But until then the above solution is the proper way! :)

---

### Post by dwhitney67 on 2008-06-25
Looks nice!  However, the deletion of the vector contents will not take place unless one explicitly calls std::for_each() function as you have shown.  Wouldn't it be nice if when the vector goes out of scope, that it's contents would be automatically destroyed when the vector's destructor is called?

No need to respond... I merely want you to think that perhaps there is more than one way to scale the mountain.

---

### Post by Zdravko on 2008-06-25
[dwhitney67]("http://ubuntuforums.org/member.php?u=322753"), that's right - having this algorithm automatically invoked would be better. You proposed inheriting from std::vector and define a proper destructor. This is not a good idea. std::-containers are not supposed to be used like that. They don't have virtual destructors. 
Sometimes, I have met reasonable uses of inheriting from a std::-container, but most of the time it was a failure.
What I use is the so called "embedding"/"layering" etc. technique - I make the container a member variable of another class - say MyClassController, that will take ownership and therefore full control of maintaing a set of MyClass objects. The destructor of MyClassController will then invoke the std::for_each algorithm - simple as possible!

---

### Post by Jessehk on 2008-06-25
> **dwhitney67 said:**
> 
[PHP]class MyVector : public std::vector< MyObject* >
{
  public:
    MyVector() {}

    ~MyVector()
    {
      for ( unsigned int i = 0; i < this->size(); ++i )
      {
        delete this->at(i);
      }
    }
};[/PHP]

No, don't do that either. the STL containers don't have virtual destructors which means that deriving from them is not a good idea.

---

### Post by dwhitney67 on 2008-06-25
Well 2 against 1... I lose.

Actually, the issue concerning STL containers not having virtual destructors is a valid point!

Perhaps it is time for me to retire from s/w development.

---

### Post by Zdravko on 2008-06-25
[Jessehk]("http://ubuntuforums.org/member.php?u=28447"), I already told him about that. He/she must be now truly convinced ;)

---

### Post by Jessehk on 2008-06-25
> **Zdravko said:**
> [Jessehk]("http://ubuntuforums.org/member.php?u=28447"), I already told him about that. He/she must be now truly convinced ;)

What's a minute between posts among friends?

---

### Post by Zdravko on 2008-06-25
> **dwhitney67 said:**
> Well 2 against 1... I lose.

Actually, the issue concerning STL containers not having virtual destructors is a valid point!

Perhaps it is time for me to retire from s/w development.
You don't need to feel frustrated. C++ is a great programming language that constantly evolves. Once diving into it, one can learn so many new things about programming at all. Just take your time and do program - coding will teach you best. Also, don't be afraid to ask questions. If you knock on a door, it will open.

---

### Post by Wybiral on 2008-06-25
> **Zdravko said:**
> C++ is a great programming language that constantly evolves. Once diving into it, one can learn so many new things about programming at all.

What kinds of things about programming do you learn from C++?

---

### Post by Zdravko on 2008-06-26
> **Wybiral said:**
> What kinds of things about programming do you learn from C++?
I learned how to organize and structure my application. I also learned techniques for large flexible and scalable software systems.

---


---
title: "C++/g++: Control order of constructors across multiple files?"
date: 2009-04-11
forum: Programming Talk
---

### Post by stair314 on 2009-04-11
Is there any way, writing in C++ and compiling with g++, to control the order of execution for constructors of objects, even if those objects appear in different .o files?
I'm working on a factory class for a library. The idea is that the factory class allocates objects and returns a T * to the client. The client requests object types using string identifier that specifies which subclass of T should be should be allocated.
The library comes with global variables instantiating the factory for a few different values of T. It also comes with a few different different subclasses of T, for each type T.
I'd like the client to be able to write their own new subclasses in their own code, and register them to my factory. That way they can extend the library's functionality without having to alter the code of the library itself.
That's all pretty easy so far. Here comes the hard part: I'd like to have
the subclasses automatically register themselves when the program launches, so that whoever writes function "main" doesn't need to manually
register anything. To do that, I made an "Autoreg" class. Whenever you
declare a subclass of T, you also declare an instance of Autoreg. The
arguments to the Autoreg object tell it how to register your class. Since anyone including the header file for the class also gets this Autoreg object, the class should automatically be registered when the Autoreg object constructor runs.
That works OK as long as just one object file uses the factory and the classes it makes, but the problem is our library code uses the factory, so if the client uses it too then we would get multiple copies of the
factory and all the autoreg objects. To get around that, I declared them
as extern in the headers, and then defined them in one .cpp file each.
Now when a client app runs, I get a seg fault in the _start() function.
Using gdb I verified that it happens because an autoreg constructor 
runs before the factory constructor. The crash happens when the registration method tries to enter the class's information into an std::map inside the factory that hasn't been constructed yet.
Does anyone know how to get this to work without dying? I've seen code
listings that do basically the same thing except not in library code
where extern was needed (e.g. [http://meat.net/2006/03/cpp-runtime-class-registration/](http://meat.net/2006/03/cpp-runtime-class-registration/) ) so I think this should be possible.
So far I have tried making sure that the .o file with the factory in it
appears first in the list of linker arguments, and that the .h file with
the factory in it appears first in the list of includes for all .cpp files
that use it, but that has not had any effect.
Does anyone have any ideas for how to get this to work? Is there some way
to force one constructor to run first? Or is there a more elegant solution?
Thanks in advance!

---

### Post by snova on 2009-04-11
> **stair314 said:**
> Is there any way, writing in C++ and compiling with g++, to control the order of execution for constructors of objects, even if those objects appear in different .o files?

No. C++ makes no guarantees, and I know of nothing GCC provides.

---

### Post by dribeas on 2009-04-11
You cannot control the order in which globals are instantiated. I kind of got lost in the long post, but this may be what you are looking for:

```

// Singleton
class Factory
{
private:
   Factory();
public:
   static Factory& instance();

   void register( std::string const & name, ConcreteFactory* factory ); // maybe*
   Element* create( std::string const & name ) const;
};
// implementation:
Factory& Factory::instance()
{
   static Factory factory;
   return factory;
}

```

Now, instead of using a global Factory object you can use the singleton to acquire the factory:

```

ConcreteFactory *cf = new SpecificConcreteFactory();
Factory::instance().register( "specific", cf );

```

Probably through the use of your AutoReg objects. Now, when the code above calls the instance() method for the first time, the internal static object is created and initialized. A reference to that newly created object is returned and the caller can execute the register operation.

---

### Post by stair314 on 2009-04-11
So the meat.net thing is just an unprincipled hack that happens to work in the 1-file case?
edit- nm, I was only replying to first post, second hadn't appeared yet.

---

### Post by dribeas on 2009-04-11
> **stair314 said:**
> So the meat.net thing is just an unprincipled hack that happens to work in the 1-file case?
edit- nm, I was only replying to first post, second hadn't appeared yet.

No, it is not. It uses the internal static variable to guarantee that the BaseFactory will exist at the time you call it. I had not read the link before, but it is just what I wrote before.

---

### Post by stair314 on 2009-04-11
Yeah, I figured out what you were saying. That is cool.
Is there not a "thank" button anymore? I haven't been on these forums in a long time.

---

### Post by dribeas on 2009-04-11
No, there is no thank button anymore. I believe it was misused and they determined to remove it. I have not been on these forums for a long time.

---

### Post by snova on 2009-04-11
> **stair314 said:**
> Is there not a "thank" button anymore? I haven't been on these forums in a long time.

They removed it a while back due to database issues (along with the Solved button).

---


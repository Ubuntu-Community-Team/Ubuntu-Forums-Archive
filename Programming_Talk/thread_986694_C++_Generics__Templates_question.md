---
title: "C++ Generics / Templates question"
date: 2008-11-18
forum: Programming Talk
---

### Post by Tadhg on 2008-11-18
Right, here's the deal!

I'm writing a program in which the first thing it needs to do is set up a GUI and allow the user to open either videos or images. Easy enough. It later will use these images and videos to do operations on. 

So I have a Image class and a Video class. I also have an Engine class. The Engine is an object which manages loading the images and videos, what images and videos are open at a certain time, and what to do to them. 

So in the engine, I have an image object array (an STL list actually) and a video object array (the same). 

At the moment, if I want to open an image, i call the load_image(file_path). If I want to open a video, I call the load_video(file_path). Each function loads the object into the correct array. This is obviously silly repitition of code. 

I want to have a single function called load_object(file_path) that can take a file path, figure out if it's a video or image (easy enough, check the extension) , load it, and figure out which array to insert it into. In java I know how to do this, but I can't see how to do it in c++. I know I should be using templates, but I don't really see how to actually implement it. 

Could some one set me straight?

---

### Post by Delever on 2008-11-18
I think you are misunderstanding what templates are for. Obviously, you need different code to create Image and Video objects, so code will be different.

However, you can write function to load an image or check file extension. But you don't need to know if file is image or video to check it's extension.

If you just want to learn templates, then it's another story :)

---

### Post by slavik on 2008-11-18
I'd say that you can have a base class call "media" or something with some basic behavior. then your engine can have a list of media* and video and image classes can inherit from media.

---

### Post by dribeas on 2008-11-19
> **Tadhg said:**
> Right, here's the deal!
[...]In java I know how to do this, but I can't see how to do it in c++. I know I should be using templates, but I don't really see how to actually implement it.

How would you do it in Java? Unless it implies storing unrelated elements in a container through the use of the Object base class, any other solution should work in C++.

From your description I would not use templates, I would write the load_object() that determines whether the file is one or the other and then internally calls the appropriate load_xxx() method.

On the other hand, as it was previously suggested by slavik, if both images and video have a common set of operations and it does make sense to have images and videos together, then you can consider defining a hierarchy with a base media file (and probably even a media factory that takes a file name, determines the type and returns a media* of the correct type, video or image).

---

### Post by Tadhg on 2008-11-19
Cool, yea I was thinking of creating a base class for media objects but the video and image objects aren't similar enough. 

In java (as I remember), I could create a method load_media(Object ob) and dynamically cast any object within the method (Video or Image). While I will still have to double code for images and video creation etc, it wont be as messy and I will only need one load_media method. This functionality doesn't carry over to C++ I take it?!

---

### Post by slavik on 2008-11-19
yes it does ... I described it in my previous post.

---

### Post by Zugzwang on 2008-11-19
> **slavik said:**
> yes it does ... I described it in my previous post.

But beware that in C++ classes must have at least one virtual method in order to be able to determine the type of an object at runtime. Furthermore all methods you overload/overwrite should be virtual if you use polymorphism.

---

### Post by dribeas on 2008-11-19
> **Tadhg said:**
> Cool, yea I was thinking of creating a base class for media objects but the video and image objects aren't similar enough. 

In java (as I remember), I could create a method load_media(Object ob) and dynamically cast any object within the method (Video or Image). While I will still have to double code for images and video creation etc, it wont be as messy and I will only need one load_media method. This functionality doesn't carry over to C++ I take it?!

You can do just the same in C++, instead of passing an Object pass a void* and do the appropriate casts. But I would not do it. The problem is that both in Java and C++ this solution takes away type safety.

If there is a shared interface between your two classes, I would define a base class and pass a reference of that type. If it cannot be done then you can refactor your code so that most of the shared parts are moved out of load_image/load_video and into some shared code.

```

class Engine
{
public:
   void load_resource( std::string const & name );

private:
   void load_image( std::string const & );
   void load_video( std::string const & );

   void common_code();

   bool is_image_( std::string const & ) const; 
   bool is_video_( std::string const & ) const;  
};

void Engine::load_resource( std::string const & name )
{
   if ( is_image_( name ) )
   {
      load_image( name );
   }
   else if ( is_video_( name ) )
   {
      load_video( name );
   }
// error, unknown resource type: !!!
}

void Engine::load_image( std::string const & name )
{
   common_code();
   // specific image code: create img
   images_.push_back( img );
}

void Engine::load_video( std::string const & name )
{
   common_code();
   // specific video code: create vid
   videos_.push_back( vid );
}

```

Assuming that both Video and Image can take a filename as constructor parameter. If loading the image or video requires more code, you can move that code into a private member method.

This will just push the two functions out of the interface and into the details of the implementation. Your java proposal is not simpler than this, as rather early you will have to determine whether the file is image or video and from there on the code will split in specific versions.

Now, what about templates?

```

class Engine { //...
   template <typename T>
   void load( std::string const & name, std::vector<T>& storage );
};

void Engine::load_resource( std::string const & name )
{
   if ( is_image_( name ) ) // ifs must be explicit, during compilation time you don't know what name is
   {
      load( name, images_ );
   } 
   else if ( is_video_( name ) )
   {
      load( name, videos_ );
   }
}

template <typename T>
void Engine::load( std::string const & name, std::vector<T>& storage )
{
   T t( name );
   storage.push_back( t );
}

```

Now, it can be a little simpler if your Image and Video classes share the same methods, that is, if all operations that take place inside load<> on the argument type T are equivalent in both Video and Image classes. In the example above only the constructor is used, and the requirement is that both media types have a constructor that takes a filename as argument. If at any time inside load<> you must use a functionality of one of the classes that is not present in the other you will have to fall back to splitting in two methods (either explicitly as above or implicitly with template specialization).

---


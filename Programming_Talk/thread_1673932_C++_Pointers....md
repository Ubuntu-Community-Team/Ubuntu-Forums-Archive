---
title: "C++ Pointers..."
date: 2011-01-23
forum: Programming Talk
---

### Post by Ravenshade on 2011-01-23
Hi, I got a quick puzzle. 

And it involves some SDL I'm not quite so sure how to go about it. 

My understanding of pointers so far is that... 

```
SDL_SURFACE *layer = NULL;
```

Layer is a surface and grabs all of its set up information from there. Whether or not that's correct I don't know. 

However I've got an issue (I'm trying to eliminate Globals and...well, I'm not having that much luck). So far I'm managing to contain the Globals to just one file effect. So for instance, I've split up my functions into different files and the globals in those files only affect those files. Usually it's because two or more functions want to give information to the same thing. (I imagine this'll get rather annoying when threads swing my way). 

Anyhow... I have a problem with one particular pointed. 

```
SDL_SURFACE *screen = NULL;
```

This is referenced from an init function, which I don't really want to seperate from my main file (I probably would if I could). It effectively just makes sure all systems are up to state and sets up the window size. 

The only place in main it is called from is by using the initialise() function, perhaps it should be inside initialise? 

However I then call another function called opening() which is at the moment in another file. This basically opens up a new sequence of events but unfortunately it involves affixing information from the images that are loaded inside opening() to the screen. 

Is the extern keyword a good way of getting out of this, or does someone have a better idea? 

Thanks for your time and any help would be really appreciated, I'm slowly getting my head around pointers...I think.

---

### Post by nvteighen on 2011-01-23
If you want to share information between functions, why don't you pass it as a parameter (or return it as return value)?

You're experiencing the need of good interfaces. Another reason why globals are considered evil is because the just patch bad design by making everything available to everyone without letting you know what does what to what... By avoiding globals, you commit yourself to make good design decisions, i.e. code that's reusable because you can combine it in smart ways with the provided interfaces.

EDIT: The extern keyword makes it possible to reference a variable across modules. But it is used this way: you place the extern declaration on those modules where you plan to use that variable. So, "extern" tells the compiler that the variable is declared outside the module. The classic example of this is the errno standard variable.

---

### Post by worksofcraft on 2011-01-23
> **Ravenshade said:**
> Hi, I got a quick puzzle. 

And it involves some SDL I'm not quite so sure how to go about it. 

My understanding of pointers so far is that... 

```
SDL_SURFACE *layer = NULL;
```

Layer is a surface and grabs all of its set up information from there. Whether or not that's correct I don't know. 

However I've got an issue (I'm trying to eliminate Globals and...well, I'm not having that much luck). So far I'm managing to contain the Globals to just one file effect. So for instance, I've split up my functions into different files and the globals in those files only affect those files. Usually it's because two or more functions want to give information to the same thing. (I imagine this'll get rather annoying when threads swing my way). 

Anyhow... I have a problem with one particular pointed. 

```
SDL_SURFACE *screen = NULL;
```

This is referenced from an init function, which I don't really want to seperate from my main file (I probably would if I could). It effectively just makes sure all systems are up to state and sets up the window size. 

The only place in main it is called from is by using the initialise() function, perhaps it should be inside initialise? 

However I then call another function called opening() which is at the moment in another file. This basically opens up a new sequence of events but unfortunately it involves affixing information from the images that are loaded inside opening() to the screen. 

Is the extern keyword a good way of getting out of this, or does someone have a better idea? 

Thanks for your time and any help would be really appreciated, I'm slowly getting my head around pointers...I think.

I'm not quite sure what you are doing here, but it sounds to me like you should put all these things in an object.

You can then make all your functions into methods of that object class and those methods will all have access to whatever you put in the object.

Having lots of global pointers is not such a good idea.

---

### Post by Ravenshade on 2011-01-23
> If you want to share information between functions, why don't you pass it as a parameter (or return it as return value)?

I would...but I'm not sure how. This isn't just a simple case of send information and get information. The reason why it's a global at the moment is because so many things require knowledge of the variable. 

How do I give multiple functions the knowledge of a pointer variable without making it global? 

For instance
> 
Function A: Requires to be able to apply information to 'Screen' and check if everything has gone okay with that process. This only needs to happen once. 

Function B: (I'm still debating whether I'll need this) will want to get rid of whatever is stored in Screen. This only needs to happen once. 

Function C: In another file. The function wants to access screen so that it can apply an image to it and then show it to the user. This needs to happen many times. 

That's my problem in a nutshell. 

> I'm not quite sure what you are doing here, but it sounds to me like you should put all these things in an object.

You can then make all your functions into methods of that object class and those methods will all have access to whatever you put in the object.

Having lots of global pointers is not such a good idea.

Agreed. A function is an object right >.> <.< right? 

I'm at the moment trying to get all of my globals into functions or at least...not so global, just so that they are specific to that task.

---
oh and thank you both for responding, you definitely gave me something to think about when looking at my code again.

---

### Post by worksofcraft on 2011-01-23
> **Ravenshade said:**
> 
Agreed. A function is an object right >.> <.< right? 


No, an object is an instance of a class.
A class can have data members which can include pointers.
A class also can have methods.

Methods are like functions, but they have access to all the members of the class.

you might want something like this:
[php]
struct my_app {
   // class data members
   SDL_SURFACE *layer;
   SDL_SURFACE *screen;

   // class methods
   init_screen();
   draw_layer_on_screen();
};
[/php]

You can then create instances of your application that each have their own screen and layer pointers and you can apply the methods to one like this:

[php]
   my_app sAppStruct;
   sAppStruct.init_screen();
   sAppStruct.draw_layer_on_screen();
[/php]

you can even make a constructor and a destructor that get called when the instance is created and when it is destroyed and so do your initialization simply by defining the instance.

---

### Post by Ravenshade on 2011-01-23
... where the hell were you three years ago? That's when I needed that kind of help dammit! 

Back then I was doing Java but that's not the point. 

Thank you very much, that's definitely opened up some possibilities. I'll look into structs, classes and methods as soon as I've had dinner, though I think you've pretty much hit the nail on the head with that!

---

### Post by nvteighen on 2011-01-24
> **Ravenshade said:**
> I would...but I'm not sure how. This isn't just a simple case of send information and get information. The reason why it's a global at the moment is because so many things require knowledge of the variable. 

How do I give multiple functions the knowledge of a pointer variable without making it global? 


Uh... making those functions accept a pointer as an argument and then pass the pointer you want as a parameter. Pointers are also variables the same way as any of the basic data types... Do it exactly as you'd pass an integer to a function, just state that the argument is of type SDL_SURFACE *.

```

int some_function(SDL_SURFACE *some_layer, int some_data)
{
    /* ... */
}

/* ... */
SDL_SURFACE *layer = NULL;
int something = some_function(layer, 78);
/* ... */

```

Anout objects: well, surely OOP will help with this, but you should first understand what I am telling you in order to do what worksofcraft is stating.

---

### Post by muteXe on 2011-01-24
You were doing java 3 years ago and you've never looked into classes and methods?

Google something like "OO design & analysis" for some good reading on code design.

---

### Post by Ravenshade on 2011-01-25
(Java + Me) * 3 years ago = I hadn't got a clue and I didn't understand. 

I still don't for the most part but I'm learning.

---


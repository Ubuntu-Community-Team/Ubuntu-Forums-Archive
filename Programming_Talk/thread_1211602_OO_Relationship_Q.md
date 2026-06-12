---
title: "OO Relationship Q"
date: 2009-07-12
forum: Programming Talk
---

### Post by weezerBo on 2009-07-12
If I have an object that performs a series of operations on data that needs to be primed/prepared would it generally be considered a good or bad idea to lump the series of functions that prepare/prime it with the ones that act on it?

Example: I have a Silhouette class that performs a series of silhouette operations, but a series of operations are required to determine the silhouette in the first place.

or

I have an Image class that performs a series of drawing operations on an existing file on the harddisk, should the class that performs the drawing operations also open the file, convert it to the right format? 

if the answers are no, what is the correct way to go about it? I understand Python and C++ if someone is kind enough to provide a simple / short examples on these types of problems.

---

### Post by pepperphd on 2009-07-12
If you need the image before and/or after the drawing operations, you should (or I would at least, and I'm quite the amateur) create a function or class to open and convert the image to the desired format that returns a pointer to your optimized image. Then I would make a second class (and third, and fourth, for each complete operation on an image) with functions that accept and return pointers to the image being worked on, which would take care of the actual silhouetting, etc.  This way you only have to open and close a given image once, not every time you perform a separate operation on it. 

I hope I could help :)

---

### Post by DougB1958 on 2009-07-12
There's probably no one-size-fits-all rule, but "put initializations in constructors" is pretty close. In other words, if you have things you need to do in order to prepare an object for use (e.g., opening the file that contains the image that the object represents), do those things in a constructor -- that's one of the major reasons modern OO languages provide constructors. Hope this is helpful, rather than just repeating something you already know, or misunderstanding your problem, or....

---

### Post by JordyD on 2009-07-12
I would make it so that you can either open and set to the correct format in the constructor or using the object's methods.

So if you have a class that makes a circle, you can do this (Python):
[PHP]class Circle:
    def set_diameter(self, diameter):
        # set the diameter

    def set_speed(self, speed)
        # set the speed

    def set_direction(self, direction):
        # set the direction

    def __init__(self, diameter=0, speed=0, direction=0):
        self.set_diameter(diameter)
        self.set_speed(speed)
        self.set_direction(direction)[/PHP]

So now we can create an instance like this:
[PHP]circle = Circle(10, 5, -1)[/PHP]

or like this:
[PHP]circle = Circle
# lots of code
Circle.set_diameter(10)
# lots of code
Circle.set_speed(5)
Circle.set_direction(-1)[/PHP]

Thus, you have a lot more flexibility this way. This is just how I would do it.

Using your Image example:
[PHP]class Image:
    def set_file(filename):
        # do stuff

    def set_format(format):
        # do stuff

    def __init__(self, file, format)
        self.set_file(file)
        self.set_format(format)[/PHP]

---

### Post by weezerBo on 2009-07-12
Just to clarify the image and silhouette were just examples, in much more general terms I mean anything that needs quite complex initialization before an object can use it. 

DougB1958: I'm usually tempted to go that route when it's just a matter of simply opening a file, but what if it's a much more complex, multi-step process? With the silhouette example it'd mean loading the file, scanning the image for blobs, recording the edges, I've done it before in C and it was about 13 different rountines seems kind of iffy dumping something like that all in the constructor, or am I wrong?

---

### Post by weezerBo on 2009-07-12
> **JordyD said:**
> I would make it so that you can either open and set to the correct format in the constructor or using the object's methods.

So if you have a class that makes a circle, you can do this (Python):
[php]class Circle:
    def set_diameter(self, diameter):
        # set the diameter

    def set_speed(self, speed)
        # set the speed

    def set_direction(self, direction):
        # set the direction

    def __init__(self, diameter=0, speed=0, direction=0):
        self.set_diameter(diameter)
        self.set_speed(speed)
        self.set_direction(direction)[/php]So now we can create an instance like this:
[php]circle = Circle(10, 5, -1)[/php]or like this:
[php]circle = Circle
# lots of code
Circle.set_diameter(10)
# lots of code
Circle.set_speed(5)
Circle.set_direction(-1)[/php]Thus, you have a lot more flexibility this way. This is just how I would do it.

Using your Image example:
[php]class Image:
    def set_file(filename):
        # do stuff

    def set_format(format):
        # do stuff

    def __init__(self, file, format)
        self.set_file(file)
        self.set_format(format)[/php]
would you put the routines that actually manipulate the image in the same class, or would you inherit or pass it to another?

---

### Post by JordyD on 2009-07-12
> **weezerBo said:**
> would you put the routines that actually manipulate the image in the same class, or would you inherit or pass it to another?

Depends. Do you want to have some things that share inheritance? Then I would say yes. Otherwise you don't really need to.

---

### Post by DougB1958 on 2009-07-13
> **weezerBo said:**
> DougB1958: I'm usually tempted to go that route when it's just a matter of simply opening a file, but what if it's a much more complex, multi-step process? With the silhouette example it'd mean loading the file, scanning the image for blobs, recording the edges, I've done it before in C and it was about 13 different rountines seems kind of iffy dumping something like that all in the constructor, or am I wrong?

That sounds like a big but reasonable constructor to me. What makes it "reasonable" in my mind is that it carries out initializations that are (presumably) necessary in order to have a meaningful silhouette that you can do other things with later. If there are other ways of initializing a silhouette (like you, I'll use "silhouette" as an example, these remarks apply to any class), you can write other constructors corresponding to them. Far more than the size of the code, the logic of the design is what matters -- making sure that you have constructors that put objects into meaningful initial states protects you from all sorts of bugs involving trying to do something with an incompletely initialized object later. If the size of the constructor bothers you, you can always write auxiliary methods (presumably private) to help the constructor.

---


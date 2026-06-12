---
title: "Java sizeof equivalent?"
date: 2009-09-28
forum: Programming Talk
---

### Post by Ferrat on 2009-09-28
So I've been working away on my project and it's going fairly well, a little trouble getting the Java OpenGL bindings to work but no matter, I'll get there.

But after a few hours of coding I'm getting to the save function of my program and I realize that there isn't a SizeOf function in Java? o.O 

Now I have been looking around and some people seem to think you don't need one, well I think I do but I can't seem to find any real way of getting one because it seems no matter how you do it you wont get it very precise or you have to read the ByteStream or something like that which seems like I would have to read and write to the file multiple times for one save to get the indexing I want?

The reason I want it is because I want to save to a binary file and it's going to be a fair amount of data and different object types in various quantities and I need to be able to "index" it to find stuff quickly and without hassle.

Lets say I have 5 objects 
Obj_1
Obj_2
Obj_3
Obj_4
Obj_5

I got 
30x Obj_1
53x Obj_2
1024x Obj_3
2x Obj_4
623x Obj_5

And amounts may change.

And on top of that I need a header on the file including some primitives and I don't want to sit down and calculate the size of every object, especially since their size might change if I change the Class and I might want to add Classes and so on.


Now since there is no SizeOf, is there any other way to do this in Java without the SizeOf?

---

### Post by geirha on 2009-09-28
In java, you generally serialize objects to write them to a file. See [http://en.wikipedia.org/wiki/Serialization](http://en.wikipedia.org/wiki/Serialization)

---

### Post by Ferrat on 2009-09-28
thanks, that worked :)

---


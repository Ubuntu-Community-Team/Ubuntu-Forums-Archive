---
title: "OO design question, database app"
date: 2009-05-23
forum: Programming Talk
---

### Post by badperson on 2009-05-23
Hi,
I'm writing a simple app that connects with a database. I have several objects that will need to be put into the database, the data will be read from an xml file, converted to objects and then put into the db. 

My question, is it best to have an interface, like storable, that every object that goes into the db will implement, or is it better to have a factory class that can take any object? 

thanks, 
bp

---

### Post by welshboy on 2009-05-23
Hey there,

What are the objects going to be?  Are they external objects like a file or an image, or is it from the program itself?

Your interface idea I'd go with, as you'd then have a controlled method of adding data to the data base.  As to putting the objects in to the data base, you may want to read up on Serialization (assuming it's an OOP language you're using.)

Hope that helps...(probably not but I thought I'd try.)

---

### Post by badperson on 2009-05-24
Hi,
it's being written in java, so it's OO for sure, I'll read up on serialization as you suggest. 

I think I will go for the "Storable" interface, but the only issue I have with that is I don't like the idea of SQL directly in the java classes....that has to violate OO principles. Maybe I'll find some way to abstract it. 

Oh, and the object are internal java objects to the app; not images or something. 
bp

---

### Post by unutbu on 2009-05-24
Hi badperson, just out of curiosity -- what is wrong with having SQL in a class definition?

---

### Post by badperson on 2009-05-24
It just seems to me to be sloppy OO design...if you change the db vendor or something, and changes need to be made, then you have to change all the code (which I suppose you would need to do anyway). 

I'm really just writing this dinky little app, so I'm probably overthinking all this stuff. I think I will just write the sql in those classes for now, and if I come up with a better way i'll change it later. 

bp

---

### Post by Quikee on 2009-05-25
Rather than this use an OR mapper like for example Hibernate or EclipseLink.

---


---
title: "Data Structure for C++ app for taking notes"
date: 2009-07-14
forum: Programming Talk
---

### Post by esaym on 2009-07-14
I am needing to write an app to use on my pda (nokia n810) to help me take notes and keep track of info.  I will mainly use this in church to keep track of info from bible studies, prayer requests,sermons ect.  I don't think I will need to make a gui for it, I think I will be able to use it just fine from the console.  My question is about what kind of data structures to use to keep track of all this?  I am thinking that for each kind of info (summaries from bible studies, prayer requests,sermons ect) I will just make a class for it.  Then make a class to create a linked list for each one of those objects.  So 3 linked lists.  Does this sound right?  I always liked using linked lists, I don't know why.  I guess the next issue would be how to save the data.  I am thinking just write each linked list to a separate file when the program closes and do the opposite when the app starts? Hmmm  

This all sounds pretty straight forward, I just want to make sure before I get started.

---

### Post by cabalas on 2009-07-14
Aside from the note itself how much extra data are you planning to store about the note?  if there isn't much why not use a [std::vector]("http://www.cppreference.com/wiki/stl/vector/start") or [std::list]("http://www.cppreference.com/wiki/stl/list/start") to store all the notes.  Using either the vector or the list also has the added bonus of you don't have to worry about the memory management for your notes.

---

### Post by c0mput3r_n3rD on 2009-07-14
> **cabalas said:**
> Aside from the note itself how much extra data are you planning to store about the note?  if there isn't much why not use a [std::vector]("http://www.cppreference.com/wiki/stl/vector/start") or [std::list]("http://www.cppreference.com/wiki/stl/list/start") to store all the notes.  Using either the vector or the list also has the added bonus of you don't have to worry about the memory management for your notes.

I agree, I am a big fan of vectors and say that's the way to go!

---

### Post by esaym on 2009-07-16
Yes I could use vectors or the stl but I want to do it the hard way so I can learn.  Looks like I am going to have to use curses to make a small text editor.

---

### Post by issih on 2009-07-16
Hmmn..theres a faint smell of unnecessarily created classes about your idea, but I'm not certain.

Simplistically, I'd say they are all text based notes. and really thats all you need, a class defining a text based note.

You then keep several vectors (or linked lists if you must) of these notes, one for prayers, one for sermons, whatever.

With a bit more thought I can see that the different types might have extra information that you may want to seperate from the bulk text, psalm number or whatever (I don't know the correct terminology, I'm afraid I'm pretty much a born and bred heathen).

In that case I'd stick to having an overall top level note class, and subclass it to hold those extra fields if necessary.

A nice implementation would then have a virtual method type() which the subclasses could override to return their exact type.

This would allow you to bung all your notes (typed as the top level class)into a single vector regardless of the actual type, and then search based on the type to retrieve your lists dynamically.

You could also have a time created method and indeed anything else you wanted to implement to sort/search by.

This version would give you a highly extensible and easily variable task management system, that could be used for almost anything.....


There I'll stop wibbling on now:)

---

### Post by esaym on 2009-07-16
> **issih said:**
> Hmmn..theres a faint smell of unnecessarily created classes about your idea, but I'm not certain.

Simplistically, I'd say they are all text based notes. and really thats all you need, a class defining a text based note.

You then keep several vectors (or linked lists if you must) of these notes, one for prayers, one for sermons, whatever.

With a bit more thought I can see that the different types might have extra information that you may want to seperate from the bulk text, psalm number or whatever (I don't know the correct terminology, I'm afraid I'm pretty much a born and bred heathen).

In that case I'd stick to having an overall top level note class, and subclass it to hold those extra fields if necessary.

A nice implementation would then have a virtual method type() which the subclasses could override to return their exact type.

This would allow you to bung all your notes (typed as the top level class)into a single vector regardless of the actual type, and then search based on the type to retrieve your lists dynamically.

You could also have a time created method and indeed anything else you wanted to implement to sort/search by.

This version would give you a highly extensible and easily variable task management system, that could be used for almost anything.....


There I'll stop wibbling on now:)

That is not a bad idea, I was thinking about messing around with inheritance on a couple of them.  Might as well just combine them all ay?  I have some small programs using inheritance and virtual methods, not sure how I could really use that here though.  Keep all the notes in one list and have make my search function check each virtual method to get the note type before returning it, ie search the whole list but only return a match if the data matches and the note type matches (note type would be virtual method).  Would that really be more efficient though?

---

### Post by issih on 2009-07-17
Not more efficient no...more adaptable, having to search to retrieve a list of a given type compared to storing that type in a seperate list is distinctly less efficient, it just opens up the possibility of doing more cunning things if you wish :)

---


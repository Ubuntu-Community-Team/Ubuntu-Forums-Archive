---
title: "Java string search"
date: 2010-08-19
forum: Programming Talk
---

### Post by liquidfunk on 2010-08-19
I'm at a loss of where to go with this, I need to write some Java code that will take an input, perhaps a name or an address, and print out everything that relates to it. 

I'm making an address book to practice my coding. I've got my code linked to a .txt file that will store all of my current addresses and phone numbers. 

Any suggestions of where to go? I can link my code so far if needed?

Thanks

---

### Post by Lootbox on 2010-08-19
Is your question how you should store all this information?

That'll depend on how you intend the program to be used. For example, if you want to look up an address entry given a name, that lends itself to storage in a Map.

Regardless of how you do it, you'll probably want to encapsulate all that information in a class that represents a single entry.

[edit] Upon re-reading your thread title, I assume you want to know how to tell if the entered input is, for example, a name or a phone number. I would look into the java.util.regex API.

---

### Post by liquidfunk on 2010-08-19
Thank you for your suggestions. I'll have a look into Maps.

I've got it roughly working like this so far.

EDIT: I didn't link the image - [http://twitpic.com/2g4rnr](http://twitpic.com/2g4rnr)

---

### Post by phrostbyte on 2010-08-21
Maybe look into using a relational database also. They are made for this sort of thing.

---


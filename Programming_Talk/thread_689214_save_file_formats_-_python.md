---
title: "save file formats - python"
date: 2008-02-06
forum: Programming Talk
---

### Post by aquavitae on 2008-02-06
Anyone have any suggestions of the best way to write a procedure in python to save data structures to a file?  By that I mean, when writing an app, how to write the save document procedure. I've considered using pickle, but I'd prefer a format I can also read fairly easily in a text editor.  The document structure itself is fairly complicated - lots of interlinking classes and I'd thought xml might be a good idea, but its quite  a lot of work to create it.  

Any good ideas?

---

### Post by pmasiar on 2008-02-06
You have contradictory requirements.

Pickle will serialize objects with links for you.
XML is (almost) editable, but it is obviously a lot of work to create custom XML, especially for a complicated structure. What is more important for you? 

If yo have complex interlinking, why you feel urge to edit it by hand?

---

### Post by SOULRiDER on 2008-02-06
You probably want to serialize your objects. I havnt done it in python, but as pmasiar mentioned (and google too) check this out:
[http://docs.python.org/lib/module-pickle.html](http://docs.python.org/lib/module-pickle.html)

---

### Post by aquavitae on 2008-02-06
What's contradictory about my requirements?  Unless you mean I want to acheive something complicated using a simple method?

Maybe pickle is the right way to do it though... I like text formats mainly for testing, but on the other hand the pickle model is (presumably) well tested so I shouldn't really need it.  My worry with pickle is how it might change in future versions of python, and therefore backward compatability with old pickled docs.  Maybe this is a baseless concern... but at least with a text format I have control over how it changes and if necessary can edit files by hand.

Another idea I had was to store a series of commands (i.e. from an undo framework) that can be used to build the document, but the trouble there is that the file could easily get filled with unnecessary commands. Or a similar option would be storing python code to create the doc, i.e. by x = eval(repr(x)) but this is also quite a bit of work.

---

### Post by Acglaphotis on 2008-02-06
I'd go with XML if you really want to read it in a text editor, but, as you put, its a lot of work. I would say that the work in this case would pay off.

---

### Post by pmasiar on 2008-02-06
I have this problem.... Yes I know I will use XML! 
Now I have two problems :-)

> **aquavitae said:**
> I like text formats mainly for testing, but on the other hand the pickle model is (presumably) well tested so I shouldn't really need it.  My worry with pickle is how it might change in future versions of python, and therefore backward compatability with old pickled docs.  Maybe this is a baseless concern... but at least with a text format I have control over how it changes and if necessary can edit files by hand.

I bet that pickle is better tested than your custom XML parser which you did not written yet! :-)

for simple printing of pickled objects for debugging, use pprint - pretty printing of objects.

I am not sure why you are afraid of changes in internal structure, but maybe you are right. Usually when such incompatible changes occur, either library is given different name, or "pickle upgrader" is hacked  together by someone with same problem like you have. 

Try asking on pickle developer mailing list if your fears make sense (I bet not), and please post the answer here - will be very interesting to know.

If this is an issue in upgrading between 2.6 and 3.0, and you are the first one who thought about it, you can get your 15 minutes of fame by reporting it as error - some volunteer will fix it for you, and will thank for it too. :-)

---

### Post by popch on 2008-02-06
I did a similar problem once, although it wasn't in Python nor - obviously - with Pickle. However, the principle still applies.

Saving an amazingly complex graph of objects was very easy with the built-in serialiser, and they provided any number of hooks to account for future changes in the serialiser supplied with the language.

What made using the built in serialiser more difficult than I had initially expected were changes in my own application. Since the serialiser restored the serialised (saved) objects exactly as I had saved them earlier, I managed to import objects from an older design into my more recent application. Not good at all.

Writing converters which converted the objects of all prior versions into the more recent ones turned out to be quite some challenge, even where that was possible at least in principle. I did not even attempt to do the reverse.

I think I ended up saving the stuff as valid XML and building separate utilities to convert the data between application formats.

---

### Post by aquavitae on 2008-02-06
> **pmasiar said:**
> 
I bet that pickle is better tested than your custom XML parser which you did not written yet! :-)
True
> 
I am not sure why you are afraid of changes in internal structure, but maybe you are right. Usually when such incompatible changes occur, either library is given different name, or "pickle upgrader" is hacked  together by someone with same problem like you have. 

Try asking on pickle developer mailing list if your fears make sense (I bet not), and please post the answer here - will be very interesting to know.

If this is an issue in upgrading between 2.6 and 3.0, and you are the first one who thought about it, you can get your 15 minutes of fame by reporting it as error - some volunteer will fix it for you, and will thank for it too. :-)
Just been going through the pickle docs... it seems they provide fairly good backward support.  When pickling, there's a variable you can set depending on how you want it pickled, 0 for old ascii, 1 for old binary, 2 for ascii, python 2.3 or later.  And I can see no reason why they shouldn't just add a number for python 3.0

I have no idea if its a issue for 3.0 though, probably not - I'm sure someone's thought of it by now! 

I'm more worried about how my own app will deal with it, like popch  says.  As it is I need to write an importer for a couple of files from a mockup I did earlier.  Fortunately those are nicely laid out xml so it'll be easy... but xml is so much more work! :(

Any comment on my other idea, about letting each object produce python code for its own creation?  Something like 
[php]
class A:
   def __init__(self, x)
      self.x = x
   def code(self):
      return 'A(%s)' % self.x
[/php]

---


---
title: "What is serialization ?"
date: 2009-11-05
forum: Programming Talk
---

### Post by dpux on 2009-11-05
Hello everyone !
I just came across the term serialization and its definition as follows..
> it is basically converting a class into binary form so that it can be read later on or sent over a network and then read out of the file or over the network as an object
thw wiki says it to be :
> [COLOR=#000000][FONT=Times New Roman][FONT=sans-serif] **serialization** is the process of converting an [object]("http://ubuntuforums.org/wiki/Object_%28computer_science%29") into a sequence of bits so that it can be persisted on a storage medium[/FONT][/FONT][/COLOR]

i have always supposed an object to be a sequence of bits in itself, because i have read objects as physical models of classes, their logical counterparts.
my doubt is, if an object is itself a bit sequence (though may not be linear), why do we need its conversion into "a sequence of bits" ...better called serialization ?

---

### Post by Arndt on 2009-11-05
> **dpux said:**
> Hello everyone !
I just came across the term serialization and its definition as follows..

thw wiki says it to be :


i have always supposed an object to be a sequence of bits in itself, because i have read objects as physical models of classes, their logical counterparts.
my doubt is, if an object is itself a bit sequence (though may not be linear), why do we need its conversion into "a sequence of bits" ...better called serialization ?

An object is represented using a specific layout of bits in memory, that's true, but the exact layout depends on the compiler and on the hardware - it's not something a programmer can rely on.

The bits comprising the serialized object, on the other hand, are well-defined. It can be moved around, and read in again on another hardware, or by another program.

---

### Post by Simian Man on 2009-11-05
The reason is that an object's representation in memory depends on a lot of things that are subject to change.  For example, the size of various fields on the machine you are running (eg ints can be 32 or 64 bits depending on your architecture, the endianness of the machine you are running on and furthermore the alignment the compiler chooses to use for structs.  By that I mean the compiler can choose to rearrange the fields in your structure and insert unused "padding".  Also if you, for example, add a minor field to your struct, then all of the serialized ones will be invalid if you try to load them back in this naive way.

Basically you can't make many assumptions about the way an object is represented in memory when using native code.  The purpose of serialization, then, is to write your class into a known format that can be loaded back reliably in the future - perhaps by a different type of machine altogether or a different version of your software.

---

### Post by dpux on 2009-11-05
Thank you for your replies !!
I have now a better understanding, but another doubt... This process seems to be same as "swapping" in-memory objects to hard-disk in context of operating systems. 
Can I assume the serialization mechanism and swapping mechanism to be the same ? Or is it that swapping needs serialization ?
What if an object/item is not serializable (for eg. i read primitive data types in java are not serializable)? cant we save those objects/items to hard-disk then ?

---

### Post by whoop on 2009-11-05
Hhhmm, the definitions confuse me a bit as I remember (at least I think I do) serializing objects to xml files, a couple of years back. The most certainly did not contain binary data.

The way I see it (at least how I use(d) it) is that serialization can save/store an instance (of an object) into serialized data (in different forms), the instance can then be (optionally) destroyed. You can then re-create/restore this instance using the serialized data.

SOAP comes to mind...

---

### Post by Arndt on 2009-11-05
> **dpux said:**
> Thank you for your replies !!
I have now a better understanding, but another doubt... This process seems to be same as "swapping" in-memory objects to hard-disk in context of operating systems. 
Can I assume the serialization mechanism and swapping mechanism to be the same ? Or is it that swapping needs serialization ?
What if an object/item is not serializable (for eg. i read primitive data types in java are not serializable)? cant we save those objects/items to hard-disk then ?

Swapping needs to be fast, and there is no need for any entity other than the original process to be able to interpret the object, so it's not changed in any way when swapped. The kernel only swaps whole memory pages anyway, not object by object (which may cross page boundaries, for that matter).

I don't know enough about Java primitive types to answer your question, other than perhaps the simple answer that not all types in Java are classes, and only classes have methods like the serialization method. An int has no methods.

---

### Post by Simian Man on 2009-11-05
> **whoop said:**
> Hhhmm, the definitions confuse me a bit as I remember (at least I think I do) serializing objects to xml files, a couple of years back. The most certainly did not contain binary data.

The way I see it (at least how I use(d) it) is that serialization can save/store an instance (of an object), the object can then be (optionally) destroyed. You can then re-create/restore this instance using the serialized data.

SOAP comes to mind...

You can use binary or textual serialization.  Binary is faster since the data is stored in a more concise form, but textual is easier to work with since you can inspect the serialized files with a text editor.  Also with binary you still need to worry about endianness if you are storing multi-byte values.  I usually compromise by using a textual encoding, but not one that is so bloated as XML.

[quote=dpux]
 Thank you for your replies !!
I have now a better understanding, but another doubt... This process seems to be same as "swapping" in-memory objects to hard-disk in context of operating systems.
Can I assume the serialization mechanism and swapping mechanism to be the same ? Or is it that swapping needs serialization ?
What if an object/item is not serializable (for eg. i read primitive data types in java are not serializable)? cant we save those objects/items to hard-disk then ?[/quote]

Swapping is done by the OS and it is similar in that your values are being moved from memory to disk, but different in that the OS doesn't need to worry about any of the portability issues I talked about it since it is only going to be swapped in/out on the same machine.

Either way, you don't need to do anything special to ensure that your program is swapped in and out of memory correctly.  It is handled transparently by the Operating System.  This actually wasn't always the case and programmers used to have to do this by hand.  Google "Overlays" if you're curious about this technique.

---

### Post by dpux on 2009-11-05
> **Simian Man said:**
> You can use binary or textual serialization.  Binary is faster since the data is stored in a more concise form, but textual is easier to work with since you can inspect the serialized files with a text editor.  Also with binary you still need to worry about endianness if you are storing multi-byte values.  I usually compromise by using a textual encoding, but not one that is so bloated as XML.


Thanks Simian and Arndt for making my basics clear, but you have aroused a new query...
What is textual serialization ? Whatever text we write is based on some encoding (mostly ASCII, UTF). Now what this encoding schemes do is to set a binary code for every character. So ultimately, all data is yet stored as a binary data....not as raw character data. Any binary data (if it uses any character encoding scheme) can be opened with a text editor.
So whats the difference between the 2 types of serialization...? what I "feel" is that its binary serialization that works at the core of textual serialization!

---

### Post by Simian Man on 2009-11-05
> **dpux said:**
> Thanks Simian and Arndt for making my basics clear, but you have aroused a new query...
What is textual serialization ? Whatever text we write is based on some encoding (mostly ASCII, UTF). Now what this encoding schemes do is to set a binary code for every character. So ultimately, all data is yet stored as a binary data....not as raw character data. Any binary data (if it uses any character encoding scheme) can be opened with a text editor.
So whats the difference between the 2 types of serialization...? what I "feel" is that its binary serialization that works at the core of textual serialization!

Yes you are right, it's all just bits.  Textual serialization just means that you use a character encoding.  In practice this usually means ASCII (or the ASCII subset of UTF-8).  So to serialize the number "17" textually you would write the two bytes 0x31 and 0x37.  To do so in binary you can write it as the byte 0x11 or the two bytes 0x0011 or 0x1100 and so on and so forth depending on your field's length and target endianess.

Sticking to ASCII text means it's easy to read, debug and you get portability "for free" which is not the case for binary.  Binary has the benefit of resulting in smaller files and hence quicker loading.  So like everything in programming, it's a trade-off :).

---

### Post by zippaplick on 2009-11-05
Serialization (also referred to as marshalling) is also used when sending objects between separate process, whether on the same machine or across the net. 

For example, say you've got a bunch of Spiffy class objects you want to pass to another process. You cant just hand off a pointer to a separate process. However, you could decompose the data in a Spiffy object to a bunch of strings, numbers or some other basic data, and write that out to a file or pipe. 

The other process could read the pipe and use the data to recreate the Spiffy objects, assuming it knows how. Serialization should encode (in whatever form) enough data to recreate the Spiffy object in the other process.

Similar concepts apply for sending objects over a network. A server could spit out serialized Spiffy data on some port. Clients could receive it, and deserialize it into identical objects within its own process space.

All I got for now. Hope that helps.

---

### Post by zippaplick on 2009-11-05
Article in wikipedia does a good job explaining it. has code sample too:
[http://en.wikipedia.org/wiki/Serialization](http://en.wikipedia.org/wiki/Serialization)

---


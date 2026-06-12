---
title: "[C] Write to a file some binary data, read some binary data from a file?"
date: 2008-11-12
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-12
As title says, how? Post me some tutorials please.

Can't find any with google or even dogpile.

---

### Post by issih on 2008-11-12
theres loads out there, google "c input output"

e.g. [http://www.cs.bu.edu/teaching/c/file-io/intro/](http://www.cs.bu.edu/teaching/c/file-io/intro/)

thinking about it google binary input output instead....

e.g. [http://www.cprogramming.com/tutorial/cfileio.html](http://www.cprogramming.com/tutorial/cfileio.html)

hope that helps

---

### Post by rbprogrammer on 2008-11-12
I would say you should get familiar with GNU's libtool.  You can find it out at [http://www.gnu.org/software/libtool/manual/](http://www.gnu.org/software/libtool/manual/) .... It may be hard to read at times in certain sections, but it is a great resource to learn about the C-Standard.

---

### Post by nvteighen on 2008-11-12
Have you read on fwrite() and fread()?

---

### Post by crazyfuturamanoob on 2008-11-14
I know how to save/load a single integer, but how to do it with a linked list, that might have hundreds of nodes?

---

### Post by dwhitney67 on 2008-11-14
I linked list generally has one or more data values, and a pointer link to the next node (and sometimes the previous node).

Storing the pointer (that is, the address) within a file to read at a later time is not practical because the application reading in the data will not be able to use the pointer (it may lay outside its program space).

Thus I recommend that you store only the data value(s), in a contiguous format within the binary file.  To do this, you will need to traverse your linked list from the beginning to the end.

If your data is represented by a structure, then it is easier to write the data to the file.  If they are independent fields, then a write may be needed for each field.  Similarly when it comes to read in the data.

P.S.  Concerning the write and read info above in the last paragraph, there are ways to write/read only the node to a file, minus the pointers.  Just use arithmetic when writing/reading.  For instance:

[php]
struct Node
{
  int          field1;
  int          field2;
  struct Node* next;
};

...

struct Node* myNode = ...;

write(fd, myNode, sizeof(struct Node) - sizeof(struct Node*));   // subtract the size of the field 'next'
[/php]

---

### Post by nvteighen on 2008-11-14
@dwhitney: Is there any advantage on using read()/write() compared to fread()/fwrite()?

---

### Post by dwhitney67 on 2008-11-14
> **nvteighen said:**
> @dwhitney: Is there any advantage on using read()/write() compared to fread()/fwrite()?

Not that I am aware of.  I am by no ways an expert at *nix internals.

---

### Post by scourge on 2008-11-14
> **nvteighen said:**
> @dwhitney: Is there any advantage on using read()/write() compared to fread()/fwrite()?

The only reason I'd ever use read() over fread() is because it has a non-blocking mode. But read() and write() are for UNIX only, where as fread() and fwrite() are part of the ANSI/ISO C standard.

---

### Post by Cracauer on 2008-11-14
> **nvteighen said:**
> @dwhitney: Is there any advantage on using read()/write() compared to fread()/fwrite()?

The f* stuff goes through C stdio. The !f* stuff works on Unix file descriptors.

That means it is buffered. Unsuitable for network sockets (unless you know how to control it). Generally faster for files, terminals and the like.

Serializing a Lisp in C is a pain, not to mention you need to serialize the objects that are inside the list, too. If they are all of the same non-pointer data type I'd convert the list to an array before saving it.

In general, if you have a list of complex objects that isn't easy to pack without pointers it's start to think about XML or SQL.

---

### Post by dwhitney67 on 2008-11-14
> **Cracauer said:**
> The f* stuff goes through C stdio. The !f* stuff works on Unix file descriptors.

That means it is buffered. Unsuitable for network sockets (unless you know how to control it). Generally faster for files, terminals and the like.

Serializing a Lisp in C is a pain, not to mention you need to serialize the objects that are inside the list, too. If they are all of the same non-pointer data type I'd convert the list to an array before saving it.

In general, if you have a list of complex objects that isn't easy to pack without points it's start to think about XML or SQL.

I have no idea what you mean by "points".

If disk space is an issue, then XML is a poor choice.  A lot of bloat is included with it.  Without a doubt, the overhead of XML vs. just packing data in binary format for a *homogeneous* system of computers, weighs in favor of the binary format.

If dealing with a *heterogeneous* system (i.e. the unknown), then sure, XML is useful.  But the OP has not mentioned such.

A database is useful for storing data that needs to be accessed in the "future".  For applications that toss around data in real-time (or near real-time), a database is useless, and in fact, reduces performance.


P.S.  If you know what an IPA is, then you realize I should not be posting the response above.

---

### Post by Cracauer on 2008-11-15
I mean pointers, I thought it's a pretty obvious typo.

There have been dozens of initiatives for standard binary formats in the last decades. None of them took off, I even format the name of what some boss in the 80ties wanted me to use. Why would IPA be any different? Why would I care?

XML you will of course gzip before storing it to disk. You get a large chunk of the bloat back, it's very huffman friendly. Not to mention that binary XML formats such as fast infoset get the size down even more but still allow you to use XML tools.

The tools are the critical part here. The original post has a non-flat chunk of data with a variable number of things in what might even be a variable number of dimensions. You gonna need a parser, sooner or later. Why reinvent the wheel?

Tools are the key. Do you really want the original poster to home-grow a parser for hierarchical binary data?

---

### Post by crazyfuturamanoob on 2008-11-15
How about converting the linked list into an array, then save the array?

And when loading, load the array, create some nodes and re-link the list?

---

### Post by Cracauer on 2008-11-15
> **crazyfuturamanoob said:**
> How about converting the linked list into an array, then save the array?

And when loading, load the array, create some nodes and re-link the list?

Suggested in posts 10 and 11 ;)

What do you do if the list points to user-defined data structures that have pointers in them?

---

### Post by crazyfuturamanoob on 2008-11-15
> **Cracauer said:**
> Suggested in posts 10 and 11 ;)

What do you do if the list points to user-defined data structures that have pointers in them?

For some reason I seem to have missed 10th post, and I don't see any references to 'array' in 11th post.

---

### Post by nvteighen on 2008-11-15
I'd like to know if maybe you could use a regular text file with some well-defined format instead of fiddling with binary data. As Cracauer has implied, if your structure has pointers and you just dump it into a binary file, you'll save the memory address where the data is, but not the data... and who assures you that exact memory address will be available to your program the next time?

---

### Post by pp. on 2008-11-15
> **nvteighen said:**
> if your structure has pointers and you just dump it into a binary file, you'll save the memory address where the data is, but not the data... and who assures you that exact memory address will be available to your program the next time?

That's not much of an issue if the structure is in contiguous memory. Just subtract the origin from each pointer, add the origin of the area where it's restored to after reloading.

Not that I'd recommend doing it that way. However, in some circumstances that might be the easiest solution. It's not robust in the sense that it might easily break by the most trivial of changes in the application producing the structure.

Another idea might be to assign a unique ID to each node (such as a running number). You then can replace each pointer to a node by the ID of the node being pointed to.

From there on, you can either put the nodes into an array (provided they are compatible enough to be placed into the same array) or you can serialize the stuff, for instance by designing an XML document type.

---

### Post by dwhitney67 on 2008-11-15
My God... the responses so far are wonderful, but what is so difficult about writing the contents of a linked list into a binary file?

For me it is a walk in the park.  To restore the link list would be just as easy.

Am I missing something here?  There is no need for an array or to place the data into any other secondary storage area.

I thought the example I provided earlier would suffice; the OP merely has to traverse his linked list (from start to end) and write the data of each node to a file.  When it is time to read it in, just parse the file, reading one data element (or structure) at a time.

I have been doing similar work in many of the projects I have supported where telemetry from a satellite was stored in a file (in binary) and had to be read.  The whole process is quite trivial.


P.S.  IPA is not a tool.  It is an acronym for "India Pale Ale".  I had the pleasure of drinking a few bottles of IPA last night.

---

### Post by nvteighen on 2008-11-15
> **dwhitney67 said:**
> 
For me it is a walk in the park.  To restore the link list would be just as easy.

Am I missing something here?  There is no need for an array or to place the data into any other secondary storage area.

And there comes my question: Why would you need a binary file to do that? Just fprintf() data separated by something and then retrieve it using fscanf(), fgets() or whatever...

> P.S.  IPA is not a tool.  It is an acronym for "India Pale Ale".  I had the pleasure of drinking a few bottles of IPA last night.

You're wrong. IPA is International Phonetic Alphabet (and also the International Phonetic Association): [http://www.arts.gla.ac.uk/IPA/](http://www.arts.gla.ac.uk/IPA/)

---

### Post by dwhitney67 on 2008-11-15
> **nvteighen said:**
> And there comes my question: Why would you need a binary file to do that? Just fprintf() data separated by something and then retrieve it using fscanf(), fgets() or whatever...

This is an option as well.  However ASCII data takes up more space than if stored in binary (that is, if the data being stored contains strings).  If just numbers are being stored, then as you pointed out, a field separator would be required.

> **nvteighen said:**
> 
You're wrong. IPA is International Phonetic Alphabet (and also the International Phonetic Association): [http://www.arts.gla.ac.uk/IPA/](http://www.arts.gla.ac.uk/IPA/)
My bad; the beer I drank clouded my judgment.

---

### Post by pp. on 2008-11-15
> **dwhitney67 said:**
> the integer value 1999 requires 4 characters, hence 16 bytes, if stored in ASCII.  If stored in binary, only 4 bytes are required, or less if the value is declared to be a short (2 bytes).

How so? ASCII encodes seven or eight bits per byte. The integer value 1999 consists of four digits and will therefore be stored in four bytes when encoded using the ASCII standard.

---

### Post by dwhitney67 on 2008-11-15
> **pp. said:**
> How so? ASCII encodes seven or eight bits per byte. The integer value 1999 consists of four digits and will therefore be stored in four bytes when encoded using the ASCII standard.
I edited my post; as with everyone else, I am entitled to make mistakes too.

---

### Post by pp. on 2008-11-15
> **dwhitney67 said:**
> I am entitled to make mistakes too.

Yes, indeed.

---

### Post by dwhitney67 on 2008-11-16
For whatever reason, this thread is still floating around in my thoughts.  So to convert my thoughts into code, I wrote a little test.

Assuming a Node structure is as follows:
[php]
struct Node
{
  int          value1;
  int          value2;
  struct Node* next;
};
[/php]
and that the linked-list insert function (e.g. addNode()) has been implemented, the following could be used to serialize and deserialize the linked-list data from a binary file.

[php]
void serialize(const struct Node* head, int fd)
{
  const struct Node* node = head;

  while (node != 0)
  {
    write(fd, node, sizeof(struct Node) - sizeof(struct Node*));

    node = node->next;
  }
}


struct Node* deserialize(int fd)
{
  struct Node* list = 0;
  struct Node  node;

  while (read(fd, &node, sizeof(struct Node) - sizeof(struct Node*)) > 0)
  {
    // got data; insert a new node into the list
    insertValues(&list, node.value1, node.value2);
  }

  return list;
}
[/php]

---

### Post by scourge on 2008-11-16
> **dwhitney67 said:**
> 
```

write(fd, node, sizeof(struct Node) - sizeof(struct Node*))
read(fd, &node, sizeof(struct Node) - sizeof(struct Node*))

```

That's pretty clever, but it's not platform-independent or even compiler independent, because the compiler may or may not add padding to the struct, and because of endianess.

I would always write and read the struct's contents one primitive at a time and flip the bytes if needed (eg. to convert from little-endian to big-endian).

---

### Post by dwhitney67 on 2008-11-16
> **scourge said:**
> That's pretty clever, but it's not platform-independent or even compiler independent, because the compiler may or may not add padding to the struct, and because of endianess.

I would always write and read the struct's contents one primitive at a time and flip the bytes if needed (eg. to convert from little-endian to big-endian).
+1.

However, if you read through the entire thread, I assumed that the OP was working on a single system.

If the data is to be shared within a heterogeneous group of systems, then using XML to store the data would probably be better.

---

### Post by scourge on 2008-11-16
> **dwhitney67 said:**
> +1.

However, if you read through the entire thread, I assumed that the OP was working on a single system.

True. But even then it's good to know about padding and endianess when you're messing with binary files. I should know, I posted a thread about it here a couple of years ago, when I noticed that my binary files which worked in Linux gave me garbage in Windows.


> If the data is to be shared within a heterogeneous group of systems, then using XML to store the data would probably be better.

If text files are the better choice for shared data, they're probably the better choice for private data as well. To me the only reason to use custom binary file formats is if the files are going to be big and/or require random access (binary search for example).

---

### Post by dwhitney67 on 2008-11-16
> **scourge said:**
> True. But even then it's good to know about padding and endianess when you're messing with binary files. I should know, I posted a thread about it here a couple of years ago, when I noticed that my binary files which worked in Linux gave me garbage in Windows.

Was this on the same architecture?  I ask merely out of curiosity.

---

### Post by scourge on 2008-11-16
> **dwhitney67 said:**
> Was this on the same architecture?  I ask merely out of curiosity.

Yes, on the same PC. Of course endianess was the same, but the GCC I used in Windows added more padding into the structs than the GCC in Linux.

---


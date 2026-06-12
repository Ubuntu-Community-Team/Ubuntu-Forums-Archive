---
title: "C++ - Adding data to the start of a file"
date: 2012-06-19
forum: Programming Talk
---

### Post by teward on 2012-06-19
Can anyone point me in the right direction as to how to add data to the *start* of a preexisting file with C++?

---

### Post by trent.josephsen on 2012-06-19
You can't insert data at the start of a file on disk. You need to read the entire file into memory, insert data at the beginning, and write the entire thing back to disk. (This isn't the only way, but given the file isn't too large, it's probably the best.)

---

### Post by teward on 2012-06-19
> **trent.josephsen said:**
> You can't insert data at the start of a file on disk. You need to read the entire file into memory, insert data at the beginning, and write the entire thing back to disk. (This isn't the only way, but given the file isn't too large, it's probably the best.)
 
Got any code examples?

---

### Post by trent.josephsen on 2012-06-19
I started to write a quick example of how to do it, but I was writing C -- don't know how one would use C++ instead. Probably using cin.getline() to populate a std::vector of strings.

---

### Post by dwhitney67 on 2012-06-19
> **Lord of Time said:**
> Got any code examples?

I do... actually, I could come up with one.  But what about you?

Trent already gave you the correct response (his first one).

If you insist on an example, I'm sure that someone will chime in with a nice shell script solution.  If it is C++ that you desire, which is not the easiest nor the most appropriate solution, then please make an attempt on your own such that others may critique (or praise) your solution.

---

### Post by dagoth_pie on 2012-06-20
> Trent already gave you the correct response (his first one).
Correction: **A** Correct response... :D
> which is not the easiest nor the most appropriate solution
A bit of a rash assuption, hypothetically speaking, for all we know he's written an entire game engine in C++ and is trying to figure out how add some data to the start of a savegame file.

Anyway, to the question at hand. 

The simplest solution has already been said. If it's a small file, just read the entire file into an std:string. Then write concatenate that onto the data you want to put out into the file and rewrite the entire file. It's a bit brute force, but it works.

Turns out I was wrong about being able to insert data it's not natively supported by fstream, I must have been thinking of a wrapper library, I guess it's been too long since I did much low level stuff. My apologies.

My new best recommendation is to follow what someone else said about using a temporary file, and with large files taking into consideration that you can't just drag the entire file through RAM, you can break it into lots of 100 characters shift from one file to the other. That way with a large file you won't fill up your memory.

Anyway, here's the link the fstreams reference, in case anyone still needs it.
[http://www.cplusplus.com/reference/iostream/fstream/]("http://www.cplusplus.com/reference/iostream/fstream/")

---

### Post by lisati on 2012-06-20
Another option is to create a new file with a temporary file name, write the data you wish to prepend, copy the original file after the prepended data, close the files, delete the original, and then rename the new file.

---

### Post by trent.josephsen on 2012-06-20
> **dagoth_pie said:**
> If you're wanting something a little more elegant, then you can use a filestream, here's a good reference: [http://www.cplusplus.com/reference/iostream/fstream/]("http://www.cplusplus.com/reference/iostream/fstream/")
Basically what you'll want to do, is open the stream, then you'll probably want to make sure the the stream pointer is at the start of the stream (I think it is by default, but I'm not sure off the top of my head) and then print stuff out to the stream.

I could be mistaken, but I believe the fstream output functions will overwrite the existing data in the file. I.e. if your file starts out with 'barbaz' and you insert 'foo' at the beginning using fstream, you will end up with 'foobaz' and not 'foobarbaz'.

Somebody correct me?

---

### Post by dwhitney67 on 2012-06-20
> **trent.josephsen said:**
> I could be mistaken, but I believe the fstream output functions will overwrite the existing data in the file. I.e. if your file starts out with 'barbaz' and you insert 'foo' at the beginning using fstream, you will end up with 'foobaz' and not 'foobarbaz'.

Somebody correct me?

The file contents will be overwritten with "foo"; all other contents are erased.

If one opens the file using append-mode, then the file pointer is placed at the end of the file.  One can attempt to move the pointer (to the beginning of the file), but it will not make a difference... data will still be appended at the end of the file.

P.S.  Actually you may be correct.  If one opens the file in both in and out modes, then perhaps new data can be written to overlay old data.

---

### Post by trent.josephsen on 2012-06-20
Seems you are right.
```
% cat insert.cxx 
#include <fstream>

int main()
{
	std::fstream fd("testfile", std::fstream::out | std::fstream::in);
	fd << "foo";
	fd.close();
}
% make insert
c++ -O2 -pipe  insert.cxx  -o insert
% echo 'barbaz' >testfile
% ./insert 
% cat testfile 
foobaz
```

---

### Post by dagoth_pie on 2012-06-20
Surely my memory can't be failing me, for some reason I'm thinking there's a second way to insert data to the filestream giving another parameter. It's late so I'll look into it tomorrow, in the meantime I'll put a warning on my original post that it might be wrong.

---


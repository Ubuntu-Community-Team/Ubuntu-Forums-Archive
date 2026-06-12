---
title: "What does 'fs' mean when dealing when reading files"
date: 2008-05-21
forum: Programming Talk
---

### Post by nite owl on 2008-05-21
Hi I have come across this notation a couple times now but when I google it I can't find anything that explains it to me. What does fs mean in these examples?
 ```

fstream fs("g:\orderbundle.txt", ios_base::in ); 

``` 
```

fs.open

```

....etc. Nowhere in the file input/output tutorials I have read does it cover the use of this 'fs' suffix???

Sorry I should have included in the title that its using C++

---

### Post by CptPicard on 2008-05-21
"File-Stream" :)

---

### Post by nite owl on 2008-05-21
> **CptPicard said:**
> "File-Stream" :)

lol of course :) thanks for that. However I am still confused by whats it do by being there??? i.e. whats its function?

---

### Post by CptPicard on 2008-05-21
Well, I/O is abstracted in terms of *streams* which are sequences of bytes. There are input and output streams. This one is a stream which reads a file, and is an input stream. Once you have the stream associated with a file and opened, the stream will produce the contents of the file when you read the stream, until stream reaches end-of-file.

There are also output streams for files that allow you to write into files, and for example input/output streams for network sockets, that let you use the same abstraction to read/write over the network. The first output stream you come across in C++ is the "cout" standard-out stream, which most C++ n00bs use without knowing what it is :)

---

### Post by dwhitney67 on 2008-05-21
'fs' is just the variable name of the object that happens to be, in your example, a file-stream.  If you feel more comfortable using 'foo' instead of 'fs', go for it.

---

### Post by Tuna-Fish on 2008-05-21
> **nite owl said:**
> Hi I have come across this notation a couple times now but when I google it I can't find anything that explains it to me. What does fs mean in these examples?
 ```

fstream fs("g:\orderbundle.txt", ios_base::in ); 

``` 
```

fs.open

```

It's just the name of the variable. Remember that c++ is object-oriented, and so is the library. Instead of calling library functions, you are creating a fstream object, and using it's methods.

[php]
//Just like you could do
std::string a_string("An example string created on stack");
// you can also do 
std::fstream a_fstream_object("/path/to/file", std::ios_base::in );
//what's nice about c++, is that when you exit the function, 
//all the objects created on stack in it will be cleanly removed. 
//That is, the file will be closed cleanly even if you never actually close it. 
//Alternatively, you could create the fstream on the heap, much like you'd do it in java.
std::fstream* fs = new std::fstream("/path/to/file", std::ios_base::in);
// the advantage is that you can return this from a function.
// but since there is no garbage collector in c++, you have to remember to do:
delete fs;
//somewhere, or you'll have a memory leak, and also you will leave the file open.
[/php]

---


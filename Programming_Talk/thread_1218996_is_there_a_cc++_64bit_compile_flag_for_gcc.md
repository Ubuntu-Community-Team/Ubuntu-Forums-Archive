---
title: "is there a c/c++ 64bit compile flag for gcc?"
date: 2009-07-21
forum: Programming Talk
---

### Post by schmendrick on 2009-07-21
Hey fellow programmers! 


is there some way to get check at compile time if it is a 64 bit machine? 
for runtime i can do a 

if(sizeof(char*) > 4)

above should even not have a performance impact when compiling the code optimized I guess, but i hazard there should be some compile flag that i can read out instead or isn't there? 


I think of myself being able to use google, but I cannot find an answer to this....

any ideas?

---

### Post by Sockerdrickan on 2009-07-21
```
uname -m
```

---

### Post by schmendrick on 2009-07-21
well thanks for the quick reply, but thats no preprocessor directive.

---

### Post by Sockerdrickan on 2009-07-21
Why would there be such a thing in the CPP? Use makefiles to define the arch and then ifdef your code

```
#ifdef X86_64
lol
#else
rofl
#endif

```

---

### Post by Keith Hedger on 2009-07-21
install the autoconf docs from the repos and look up "Specifying-Names" should be:"file:///usr/share/doc/autoconf-doc/autoconf.html#Specifying-Names"
Is this what you are looking for?

---

### Post by schmendrick on 2009-07-21
thanks for the link and the hint with the makefiles.

however, i think i am looking for what is described in the linked help:

> configure can usually guess the canonical name for the type of system it's running on. To do so it runs a script called config.guess, which infers the name using the uname command or symbols predefined by the C preprocessor.

(file:///usr/share/doc/autoconf-doc/autoconf.html#Specifying-Names)

i am looking for THAT C preprocessor symbols.

> Why would there be such a thing in the CPP? Use makefiles to define the arch and then ifdef your code

yeah, but i wondered if the compiler itself has any preprocessor directive i can use that tells me if its a compiler that compiles 64bit machine code or not.

ATM i have multiple computers, some running 64bit, some not. I want to be able to compile on all of them (compiling code for their architecture)  without having to manually set up my "makefile" (i am using scons though) specifically for each and every one of them.

---

### Post by Sockerdrickan on 2009-07-21
if you have 64 bit compiler you will get 64 bit objects automatically, what you describe is not always necessary and should not be in good code IMO

---

### Post by schmendrick on 2009-07-22
i found out two solutions now myself. 




first is, after digging a bit into dry gcc documentation, i now have some compiler flags that i sought. 

```

#ifdef __i386__
	printf( "__i386__!");
#endif

#ifdef __x86_64__
	printf("__x86_64__!");
#endif

```
  
second, as i am using scons for building i could do it like this, similar to what tuxor said

```

      if platform.machine() != 'x86_64':
          flags += 'DEFINE_IDENTIFIER_FLAG_i386'

```

but there are some reasons why i dissapprove this second solution.



so:    

case solved!




> 
if you have 64 bit compiler you will get 64 bit objects automatically, what you describe is not always necessary and should not be in good code IMO


it was not my question: "do i need it".
Yes, normally you shouldnt need it. 
But _I_ do. 
And thats why I asked. 


actually this is not part of the question, plus i dont have to justify why i need it but FYI i'll explain why i need the flag in this case anyway: 

i create code that shall be optimized for a powerpc processor with low processing power. it shall also run on normal PCs though. the code needs to be FAST, and if you want something fast then the code is not always looking nice.
The powerPCs have a variable number of generic "values" that can be ints, floats, strings, bools need to be packed and transported over the network with other data of various types and length. 
therefore i am going down on byte level and directly pack parts of the memory of the instance to a stream to later send it over the network. on the other side the data is directly de-packed into the there-created instance again. 
one struct that is a member of the class that is copied also contains a union with a pointer, a float, an int and a boolean.  packing that directly from memory is fast, but its not cross platform. 

so first i need to make sure that
a) the ints are always sent in big-endian, and 
b) the packed data is always the same size (which it wouldnt be on 64bit architectures, because the pointer is 8 byte there). the pointer is not interesting for me anyway when packing and de-packing data, so i can just omit where it is pointing to (transporting the data the ptr would be pointing to is done seperately).


so very simplyfied it comes down to something like this (if we disregard big/little endian issue):

```

if (sizeof(char*) > 4)//64 bit
   os.write( (char*)&data,sizeof(data)  - 4 );
else
   os.write( (char*)&data,sizeof(data)  );

```

or like i can do now: not at runtime but at compile time via the preprocessor.

so like you said: there ARE cases this is needed.

---

### Post by wmcbrine on 2009-07-22
The flag I use is "_LP64".

---


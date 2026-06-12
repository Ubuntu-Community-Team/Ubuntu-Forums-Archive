---
title: "Problem with make"
date: 2005-10-04
forum: Programming Talk
---

### Post by drgreborn on 2005-10-04
[IMG]http://i9.photobucket.com/albums/a51/drgreborn/compileerr.png[/IMG]
I'm rather new to make files. I was following the tutorial for CDT but I keep running into this error. Any idea how to fix this?

Ok i fixed the error. But there is no main.exe created.

---

### Post by thumper on 2005-10-04
Firstly remove hello.exe from the rm statement.

Add the -f flag to rm as this way rm doesn't complain if the file isn't there.

Remove the makefile: from the top of the file.

Then try ```
make
```

---

### Post by thumper on 2005-10-04
edit the main.o rule so it look like
```

main.o: main.cpp
      g++  -c -g main.cpp

```
There are generic build rules, but start with this.

Also the tutorials on the gnu site for make a quite good.

---

### Post by drgreborn on 2005-10-04
No dice mate. Still no main.exe file generated.

---

### Post by David Marrs on 2005-10-04
The file generated is called "hello". You run it by typing './hello' at the terminal. If you want it to be called main.exe you'll have to change the line:

hello: main.o

to 

main.exe: main.o

---

### Post by drgreborn on 2005-10-04
Ah I see. I shall try that. Just out of curiosity. Is what make is doing similar to what the Ant build files do?

Ok now I manage to run the ant file but it gives me some other errors. I think its got to do with my using the namespace.

/usr/include/c++/3.3/bits/basic_string.tcc:731: undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::basic_string[in-charge]()'

Any idea?

---

### Post by drgreborn on 2005-10-04
I've figured out whats wrong. Silly mistake. Should have used g++ insteaed of gcc.

Thanks thumper and David for the help.

---


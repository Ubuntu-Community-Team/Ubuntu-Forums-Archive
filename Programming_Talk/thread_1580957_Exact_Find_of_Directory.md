---
title: "Exact Find of Directory?"
date: 2010-09-24
forum: Programming Talk
---

### Post by huangyingw on 2010-09-24
Hello all,
      I want an exact find of a directory named "mirror" in "/" directory, but, just to ignore the .git, .svn, .hg directory, so I wrote following command
```

 find / -type d \( -name \.svn -o -name \.git -o -name \.hg \) -prune -name mirror
```
But I return me with nothing.
While the following one works, but without ignore:
```
find / -type d -name mirror
```
And this one would give me a lot of litters:(
```
find / -type d \( -name \.svn -o -name \.git -o -name \.hg \) -prune -o -name mirror
```

---

### Post by ibuclaw on 2010-09-24
> **huangyingw said:**
> And this one would give me a lot of litters:(
```
find / -type d \( -name \.svn -o -name \.git -o -name \.hg \) -prune -o -name mirror
```

^^ This is correct. You forgot one thing on the end though... (-print)

---

### Post by huangyingw on 2010-09-24
> **ibuclaw said:**
> ^^ This is correct. You forgot one thing on the end though... (-print)

Great thanks. This is quite curious:). For it works when finding file in such code:
```
find "$1" \( -name \.git -o -name \.svn -o -name \.hg \) -prune -type f -o -name "$2"

```
:))
BTW,is there existing shell for "finding". I am a newbie at linux programming. I always had to face a terrible task of finding a "main" entry in hundreds of *.c files:(. 
So, I wrote this shell:
```
find "$1" \( -name \.svn -o -name \.git -o -name \.hg \) -prune -o \( -name \*\.c -o -name \*\.cc -o -name \*\.h -o -name [m,M]akefile \) -exec grep -wnH "$2" {} \;
```

---

### Post by ibuclaw on 2010-09-24
> **huangyingw said:**
> 
BTW,is there existing shell for "finding". I am a newbie at linux programming. I always had to face a terrible task of finding a "main" entry in hundreds of *.c files:(. 


grep can cope with recursively searching through a directory...

Assuming your coding style is:
```

int
main (int argc, char** argv)
{
}

```
You can search for the file containing main with
```
grep "^main" -nlR /path
```
Note the use of '-R', you'll be needing that alot. :)

---

### Post by huangyingw on 2010-09-24
> **ibuclaw said:**
> grep can cope with recursively searching through a directory...

Assuming your coding style is:
```

int
main (int argc, char** argv)
{
}

```
You can search for the file containing main with
```
grep "^main" -nlR /path
```
Note the use of '-R', you'll be needing that alot. :)

Great, thanks a lot..

---

### Post by geirha on 2010-09-25
```
find . \( -name .svn -o -name .hg -o -name .git \) -prune -o \
      -type f \( -name \*.c -o -name \*.cc \) \
      -exec grep -l '^[[:blank:]]*\(int\)\{0,1\}[[:blank:]]*main[[:blank:](]' {} +
```

This should also capture cases where the return type is on the same line as the function```
int main(...
```

[http://mywiki.wooledge.org/BashFAQ/008](http://mywiki.wooledge.org/BashFAQ/008)
[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

---

### Post by huangyingw on 2010-09-26
> **geirha said:**
> ```
find . \( -name .svn -o -name .hg -o -name .git \) -prune -o \
      -type f \( -name \*.c -o -name \*.cc \) \
      -exec grep -l '^[[:blank:]]*\(int\)\{0,1\}[[:blank:]]*main[[:blank:](]' {} +
```

This should also capture cases where the return type is on the same line as the function```
int main(...
```

[http://mywiki.wooledge.org/BashFAQ/008](http://mywiki.wooledge.org/BashFAQ/008)
[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

Hello, I have tried your code
```
 find . \( -name .svn -o -name .hg -o -name .git \) -prune -o -type f \( -name \*.c -o -name \*.cc \) -exec grep -l '^[[:blank:]]*\(int\)\{0,1\}[[:blank:]]*main[[:blank:](]' {} \;
```
It only list the file name like bellow:
```
./searchroot/tools/one_search.cc
./codelab/babysitter/multi_thread_server.cc
./codelab/babysitter/simple_server.cc
./codelab/protobuf/main.cc
./codelab/libmemcached/test.cc
./codelab/build/hello.cc
./codelab/sstable/write.cc
./codelab/sstable/read.cc
./codelab/thrift/HelloBook_nb_server.cc
./codelab/parse_master/simple_y_parser_main.cc
./codelab/parse_master/parse_master_test.cc

```
Maybe that is not my intention.
Generally, I would like to search a certain key word in a certain directory. Your suggestion might not be my goal.

---


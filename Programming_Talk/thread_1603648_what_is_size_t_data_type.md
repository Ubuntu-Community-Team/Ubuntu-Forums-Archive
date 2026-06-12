---
title: "what is size_t data type"
date: 2010-10-23
forum: Programming Talk
---

### Post by c2tarun on 2010-10-23
hi friends
can anyone please explain me size_t data type.

---

### Post by simeon87 on 2010-10-23
Have you used Google to, for example, read [this]("http://en.wikipedia.org/wiki/Size_t") first?

---

### Post by phrostbyte on 2010-10-23
It's most often typedef'ed to "unsigned int".

---

### Post by c2tarun on 2010-10-23
hey i was reading the man page for getline and i read this line 
       ssize_t getline(char **lineptr, size_t *n, FILE *stream);

can you please explain me about the third parameter FILE??

---

### Post by c2tarun on 2010-10-23
> **phrostbyte said:**
> It's most often typedef'ed to "unsigned int".

i tried using unsigned int in place of size_t but compiler gave an error.

---

### Post by worksofcraft on 2010-10-23
> **c2tarun said:**
> i tried using unsigned int in place of size_t but compiler gave an error.

Yes, size_t is defined as either int or long depending on how big you can make things in memory, so on a 64 bit system you need a 64 bit size_t... i.e. it's going to be an unsigned long - well they not make negative sizes ;)

---

### Post by ender4 on 2010-10-23
FILE is a typedef to "struct _IO_FILE.  (see stdio.h).  Basically it is a handle that is returned by functions such as fopen, and passed to functions such as getline and fprintf. stdio.h defines three built-in files: stdin, stdout, and stderr.

The definition of struct _IO_FILE is in libio.h.

---

### Post by TheBuzzSaw on 2010-10-23
It's good to get into the habit of using size_t particularly when dealing with other size_t variables. For instance:

[php]
string s;
/// do lots of stuff to the string here
for (size_t i = 0; i < s.length(); ++i)
{
    // do stuff with s[i]
}
[/php]

If you attempt to find something in a string that isn't there, it will return string::npos, which I believe is a size_t.

Do not reduce to a mere typedef of an unsigned long. Learn to use size_t at the appropriate times.

---

### Post by nvteighen on 2010-10-23
You shouldn't care about what "size_t" is, but about what "size_t" means.

"size_t" is a type defined for sizes and I'm sure you'll understand why sizes should never be negative. So, when you want something to be not just a number but actually the size of something, "size_t" is the type you want.

The same goes for "FILE *". Don't care about what the "FILE" data structure is, but learn what it means. It is a handler for an open file: think of it as the abstract representation of a file you open with fopen() but, also, stdout, stdin and stderr, which are also files.

One should only care about the implementation of something if you're interested on the implementation, not on using it. I mean, of you're really curious, take a look on what FILE is and how it is implemented... My point is that abstractions are interfaces someone created for helping other coders to do their job more easily, so, unless you want to work on the abstraction itself (e.g. you think it's improvable), don't care about what such or such type actually is.

---


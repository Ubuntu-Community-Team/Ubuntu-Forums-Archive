---
title: "How To Create Your Own Programming Language on Ubuntu Linux (and other Linuxes)"
date: 2007-02-02
forum: Outdated Tutorials &amp; Tips
---

### Post by SuperMike on 2007-02-02
**[SIZE="4"]Background[/SIZE]**

[SIZE="2"]So you want to create a new scripting language entirely of your own design. This is not a problem if you're already somewhat of a programmer, and that's to whom this article is geared. Typically you would want to get a book on this and learn how to write three components -- a lexer, parser, and interpreter. Typically this takes the expertise of a C++ programmer and a few college courses on compiler and interpreter design.

Well, not any more. Now you can use the "Oku Trick" to make your own programming language in a shorter timeframe, and it will run super-fast. Time tests show a standard Fibonacci algorithm with this technique running about 100 times faster than Perl. Since time tests show Perl edging out PHP, Python, and Ruby, it looks like you might have an extremely fast language on your hands.

If you have Perl and GCC installed on the Linux PC, and have a 1 college semester understanding of C or C++, or have just curled up with a good book on C++ for a few weekends over a couple months, then you have the know-how to pull this off. It's not very hard, especially if you love programming.

This technique was invented by a Japanese guy named "Kazuho Oku" and I really have to give him a huge amount of credit here. With his technique, you could start small and invent a language that does nothing but namespaces, classes, methods, arrays, control structures, simple math, and standard I/O interaction, and then later on add other things like file I/O, etc., and grow it from there.

You have 3 choices with this technique below:

* Create your own C scripting language in exactly that, C. Not C-Like, not a dysfunctional C, not C Shell, but pure C just like it was compiled.

* Create your own C++ scripting language.

* [COLOR="Red"]Create a scripting language of your own liking by re-implementing C or C++ in your style, and then "breaking" those C or C++ features you don't want implemented in your code.[/COLOR]

Are you sold?


[SIZE="4"]**Installation steps:**[/SIZE]

1. Visit this URL that's basically got source and binary downloads for a compiled Perl script:

[http://labs.cybozu.co.jp/blog/kazuhoatwork/2006/02/c-0_05.php](http://labs.cybozu.co.jp/blog/kazuhoatwork/2006/02/c-0_05.php)

If you go the binary route with the RPM, download this RPM, run it through 'alien', and use 'dpkg -i' to install it.

$ wget 'http://labs.cybozu.co.jp/blog/kazuho/archives/c/C-0.05-1.i386.rpm'
$ alien C-*.rpm
$ dpkg -i c-*.deb

2. You may now use this new C command in /usr/bin or use 'mv' to change the name to something you find more agreeable.

3. Now read up on C pre-processor macros here:

[http://en.wikipedia.org/wiki/C_preprocessor](http://en.wikipedia.org/wiki/C_preprocessor)

4. And now you know how to re-implement C or C++ as your own super-fast scripting language, even faster than Ruby, Python, Perl, or PHP.

By default it already includes stdio and stdlib so that you can interact with Standard I/O, so here's a very simplistic example of re-interpreting C or C++ in your own language:
[/SIZE]
[SIZE="2"]```
#define println(s) printf(s "\n"); 
println("hello world");
```[/SIZE]

[SIZE="2"]In the above example, I invented "println" in my little "language". Now, using more advanced define (C preprocessor) statements, or adding in functions, you can create even more parts to your language. If you look at the small source code in step 1, where the #includes are being loaded with stdin and stdlib, you can have these statements preload before any program is run beneath it. The programmer sees nothing but a file in their own language that they run with your interpreter.

Happy programming on Ubuntu!!!

(Note: Standard GPL license restrictions apply here.)[/SIZE]

---

### Post by lsd33 on 2008-01-11
That looks f'in coooool... I am going to try that out.

---

### Post by IsotopeFission on 2008-10-08
I made my own language. Its like PHP and ColdFusion and used for website development. The website address is [www.xenutec.com](www.xenutec.com)

I used Visual Basic 6 to make the interpreter which many people told me that it wasnt possible with anything other than c++ or c# so basically the last 3 years I had a dream of creating my own programming language and found no documentation for it. Until I stublmbled upon my own idea of using command line for input and STDOUT for output.

My web programming language is in its infancy but it works with Windows Server 2000/2003/2008 - IIS 5/6/7

Just add my interpreter as a mapping with the line:

<FULL PATH TO MY FILE>\Isotope_CGI_IIS.exe "%s" %s

And create a Isotope Fission index file!!

Take a look at [www.xenutec.com](www.xenutec.com) if you feel you want to contribute email me at [email]isotope@xenutec.com[/email]

---

### Post by SuperMike on 2008-10-22
Here's how I used this to connect to a PostgreSQL database called 'names' with username 'names' password 'names' and table named 'names'.

First, you need to install the libraries you need. Start by installing the PostgreSQL server. Then, install libpgeasy. Now you're ready to begin.

Create a PostgreSQL server database called 'names', accessible with user 'names' by password 'names'. Then, open it and create a table 'names' and make it accessible by this username 'names'. The columns should be firstname varchar(30), lastname varchar(30). Then, insert some rows in there.

Now create a C script (name it /tmp/tester, for now) like so:
```

#!/usr/bin/C

#include <postgresql/libpq-fe.h>
#include <libpgeasy.h>

char firstname [30+1];
char lastname [30+1];
PGconn * connection;

connection = connectdb("dbname=names user=names password=names host=localhost");

on_error_stop();

doquery("SELECT * FROM names");

while ( fetch (firstname, lastname) != END_OF_TUPLES ) {
    printf("%s %s\n", firstname, lastname);
}

disconnectdb();

```

And now there's a special way you'll need to call this. Even though you have #!/usr/bin/C at the top, it won't work to simply call:

/tmp/tester

You'll end up with errors like:

source.c:(.text+0x2a): undefined reference to `connectdb'
source.c:(.text+0x32): undefined reference to `on_error_stop'
source.c:(.text+0x3e): undefined reference to `doquery'
source.c:(.text+0x6c): undefined reference to `fetch'
source.c:(.text+0x76): undefined reference to `disconnectdb'
collect2: ld returned 1 exit status

So, the fix is to run it like this:

C -cL/usr/lib/libpgeasy.so -clpgeasy /tmp/tester

To take this to another level, you could then use preprocessor directives like crazy to make this into your own mini "programming language" (of sorts) with database access.

Note that this script will run sort of slow on the first time, but on all subsequent hits, the script will run blazingly fast because it is compiled as a true C program.

As an added bonus, if you call this with exec() from PHP, you can speed up PHP to do various tasks that it might do slowly or ineffectively.

---

### Post by matmatmat on 2008-12-19
> * Create a scripting language of your own liking by re-implementing C or C++ in your style, and then "breaking" those C or C++ features you don't want implemented in your code.
What do you mean by "breaking"?

---

### Post by matmatmat on 2008-12-20
By breaking do you mean removing or not using (sorry for double post)

---

### Post by matmatmat on 2009-02-07
bump

---

### Post by matmatmat on 2009-02-07
Is breaking using undef?

---

### Post by SuperMike on 2009-02-07
> **matmatmat said:**
> Is breaking using undef?

Yes.

**EDIT:** This was wrong. I correct myself further down in the thread.

---

### Post by matmatmat on 2009-02-07
How would I use it?
```

#undef printf

```
?

---

### Post by SuperMike on 2009-02-07
Sorry, this thread was so old that I had to get my brain in gear, thinking back in C mode again instead of the PHP and jQuery that I normally work with. I was wrong with what I said about #undef.

In general, C has a very small set of reserved words:

[http://infinity.cos.edu/faculty/woodbury/Math18/reserved.html](http://infinity.cos.edu/faculty/woodbury/Math18/reserved.html)

Although you can't override those reserved words that I'm aware of, everything else comes from an added on library, and then you can rename and redo those functions in that library. For instance, printf comes from stdio.h, right?

So, by using #define, you create macros for your new language that build upon C's reserved words and libraries, and then you can include libraries and rework their interfaces in your mini-"language".

To me, that's faster than building your own interpreter the hard way with a lexer and parser.

---

### Post by roshanjose on 2009-02-07
Mind Blowing!!!

Must try it out

---

### Post by matmatmat on 2009-02-08
Thanks

---

### Post by iblis on 2009-06-26
You can essentially do this in plain C; take a look at the gnome library's source code some time - lots of macros. ;-)

It's great for a while, but it can and likely will become a pain to maintain. I found just using generic programming (ala C++) was less time consuming than writing a (pre)-preparser.

That, or check out Vala. C# syntax, C speed. Or Genie, which is a lot like Python or Boo.

This is not to say that I'd discourage attempting this as a fun learning experience. Once it evolves to the point of reference counting, though, I'd suggest not reinventing the wheel. :D

---


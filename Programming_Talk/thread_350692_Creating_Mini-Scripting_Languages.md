---
title: "Creating Mini-Scripting Languages"
date: 2007-01-31
forum: Programming Talk
---

### Post by SuperMike on 2007-01-31
Let's say you wanted to get a wild hair one day and, for fun, create your very own tiny scripting language? How would you do it?

Some potentials?
* Write a small C program that loads your code, converts it into #define pre-processor macros, and therefore C can run it like a normal C program?

* Write it in PIR. How, I don't know. PIR is like assembler for Parrot, which is a virtual machine and runtime for the future Perl6.

* Write it entirely in C or C++, using parsing libraries.

---

### Post by jblebrun on 2007-01-31
> **SuperMike said:**
> Let's say you wanted to get a wild hair one day and, for fun, create your very own tiny scripting language? How would you do it?

Some potentials?
* Write a small C program that loads your code, converts it into #define pre-processor macros, and therefore C can run it like a normal C program?

* Write it in PIR. How, I don't know. PIR is like assembler for Parrot, which is a virtual machine and runtime for the future Perl6.

* Write it entirely in C or C++, using parsing libraries.

Write in in Scheme or Lisp. They're a great base for domain specific languages.

Lex and Yacc (Flex and Bison) are worth checking out, if you want to work with tokenizing and parsing.

---

### Post by pmasiar on 2007-01-31
Another language *extremely* easy to extend in any direction is [Forth]("http://en.wikipedia.org/wiki/Forth_%28programming_language%29")

---

### Post by Wybiral on 2007-02-01
The parsing part really matters on how you want to structure the language. If it's simple enough, you might find it easier to not use a parsing library at all (for instance, ScripTur in my sig was easy enough to not use a parsing library/generator, it depends how complex you plan to make the language)

You might want to make a small virtual machine or maybe compile to machine code directly.

Maybe you would want to make it convert to GAS assembly since most linux users have the "as" assembler.

What kind of scripting language are you talking about here?

---

### Post by SuperMike on 2007-02-02
This was way-cool when I found it. This technique was invented by a Japanese guy named "Kazuho Oku" and I really have to give him a huge amount of credit here.

It requires Perl and GCC to be installed on the system, and many workstations and servers I know already have this installed on them.

All it takes is about a 1 college semester understanding of C or C++, or perhaps just curl up with a good book one summer on C++. You don't even need to learn how to write a parser! You could start small and invent a language that does nothing but namespaces, classes, and standard I/O interaction, and then later on add other things like file I/O, etc., and grow it from there.

You have 3 choices with this technique below:

* Create your own C scripting language in exactly that, C. Not C-Like, not a disfunctional C, not C Shell, but pure C just like it was compiled.

* Create your own C++ scripting language.

* Create a scripting language of your own liking by re-implementing C or C++ in your style, and then "breaking" those C or C++ features you don't want implemented in your code.

Sound cool? Well, what if I told you that a Fibonacci test of the source shows that it runs 100x faster than Perl? That would be quite a feat, right?

Installation steps:

1. Visit this URL and save the perl script in /usr/bin:

[http://labs.cybozu.co.jp/blog/kazuhoatwork/my_projects/c/C](http://labs.cybozu.co.jp/blog/kazuhoatwork/my_projects/c/C)

-OR-

Download this RPM, run it through 'alien', and use 'dpkg -i' to install it.

$ wget 'http://labs.cybozu.co.jp/blog/kazuho/archives/c/C-0.05-1.i386.rpm'
$ alien C-*.rpm
$ dpkg -i c-*.deb

2. You may now use this new C command in /usr/bin or use 'mv' to change the name to something you find more agreeable.

3. Now read up on C pre-processor macros here:

[http://en.wikipedia.org/wiki/C_preprocessor](http://en.wikipedia.org/wiki/C_preprocessor)

4. And now you know how to re-implement C or C++ as your own super-fast scripting language, even faster than Ruby, Python, Perl, or PHP.

By default it already includes stdio and stdlib so that you can interact with Standard I/O, so here's a very simplistic example of re-interpreting C or C++ in  your own language:

```
#define println(s) printf(s "\n");
println("hello world");
```

---

### Post by SuperMike on 2007-02-05
There's an even cooler way to do this if you're not a fan of having C or C++ as your scripting language, and are tired of declaring variables and so on. Here's how:

1. Install ngs-js from the Universe option of Ubuntu, via 'apt' or 'synaptic'. It's a nice little Javascript language interpreter, even in its incomplete form, that can allow you to do a lot of stuff in very little time. It's also extremely fast, I've found. It can be used for console I/O, CGI web stuff, using as the host language or your web server, interfacing with GTK2/+ and Swig, and a whole host of other cool things. It could replace your entire use of Perl, Python, or PHP, and with a way, way smaller disk footprint. IBM has recently also been interested in growing the Javascript language a great deal in the next decade. I believe you'll want to keep an eye on Javascript in the future.

2. The trick is to hook ngs-js into becoming your own programming language and deviating it a good bit from Javascript. Let's call this little language 'Z', below, for purposes of this example. Specifically, you'll want to:

* Automatically add boiler-plate code into the top of your Z language that's written in Javascript. This gives you the ability to encapsulate Javascript functions in other function names, or build things that you think the language should have had in the first place.

* Apply a sed script (pulling a bunch of RegExps from a text file) to your Z language file, switching Z language type clauses into Javascript clauses.

* If any includes are done, use an "include('myscript.z');" type syntax. Parse these with cat, grep, sed, echo, cut, tr, and so on to get 'myscript.z' out. Load this and also apply the sed script filter upon it.

* If you want to break certain items in Javascript that you don't want accessed in your little language, you can use 'sed' to break them into syntax errors in your Z program. Just don't 'sed' out your boilerplate code.

* If you want to do anything fancier than what sed and awk can't handle, then write a little Javascript program in ngs-js to parse your Z file and replace parts in a fancier way.

* Now what you end up with is:

- boilerplate Javascript (unedited)
- any include files that your script wants to include (edited through sed, awk, etc.)
- your little program script (edited through sed, awk, etc.)

* Now feed this to the ngs-js program via /usr/bin/js command and filter the output sort of like:

/usr/bin/js  /tmp/Z/myscript.z 2>/tmp/Z/err.txt;  cat  err.txt  |  sed  's/js:/Z:/g'

...with the sed on the end to make even the syntax errors reference your language instead of Javascript.

* Next, to make this run much faster, learn the cksum command. I used this to determine if my little script had changed. If it had, then I reran it through this filter. If it had not, then I reran the old one. By doing this, your scripts run about 1/4 second slower the first time you run them, and super fast for any time beyond that.


If you're a programmer, I think you should give this a try just for the fun of it. I found it pretty cool to convert Javascript into this other language entirely. I'm working on it still and it's called Polar. It will be available soon on code.google.com with project name of 'polar-lang'. Watch for it.

---

### Post by SuperMike on 2007-02-05
And for the even more advanced programmer, take the source of ngs-js, learn it, and modify it into something else entirely (as long as you follow the GPL restrictions).

---

### Post by SuperMike on 2007-02-05
> **Wybiral said:**
> ScripTur in my sig was easy enough to not use a parsing library/generator, it depends how complex you plan to make the language)

Scriptur....riiiight.

Hello World becomes:

(0,72,1,2)
(0,101,1,3)
(0,108,1,4)
(0,108,1,5)
(0,111,1,6)
(0,32,1,7)
(0,119,1,8)
(0,111,1,9)
(0,114,1,10)
(0,108,1,11)
(0,100,1,12)
(0,33,1,0)

---

### Post by Wybiral on 2007-02-05
Well, yeah... It's a turing machine, it's not meant to be a readable scripting language.

But you still haven't said what you want to use the scripting language for (if you have, then I apologize for missing that)

The use of the scripting language is what is important... ScripTur is meant to design turing machines... So yes... It's designed in a turing machine style syntax which is based on states and in/out values.

---

### Post by lnostdal on 2007-02-05
> **SuperMike said:**
> Let's say you wanted to get a wild hair one day and, for fun, create your very own tiny scripting language? How would you do it?

by using common lisp .. i'd have it up in an instant and it would be compiled to native machine code automatically via the lisp-compiler so it would have good runtime performance

---

### Post by Wybiral on 2007-02-05
If you're just wanting to embed a language in your program to allow for user scriptability... Try python. It's incredibly easy to embed and since it's a popular language a lot of users will already know it.

Here's a very simple example of a python console you could add to your app (keep in mind this is over-simplified and doesn't have any features other than executing python code)

```

#include <iostream>
#include <python2.4/Python.h>

int main()
{
   Py_Initialize();

   char code[1024];

   while(true)
   {
      std::cout << ">>> ";
      std::cin.getline(code, 1024);
      if(!strcmp(code, "exit"))
      {
         break;
      }
      PyRun_SimpleString(code);
   }

   Py_Finalize();
}

```

You just need the python dev files and you compile it with "g++ whatever.cpp -lpython2.4"

Python also has a simple interfacing for calling python functions from C/C++ and calling C/C++ functions from the python script. It also has a function that lets you load and execute an entire python script file.

---

### Post by SuperMike on 2007-02-05
> **Wybiral said:**
> But you still haven't said what you want to use the scripting language for

Oh, sorry. It was more of an FYI thing. In my particular case, I'm sort of like the guys who created Ruby. I just wanted something based on something else, but did it better and added this or that to it. For instance, I love PHP, but it does have its misgivings here or there:

* Large disk footprint. If you're wanting to get approval to make PHP your "scripting language" to manage your servers, and not use Perl, you might raise an eyebrow or two. Sure, it works great, but you can't beat that big disk footprint compared to say, a Perl or ngs-js installation.
* Nasty install on various forms of Linux -- have to get source and compile with a nasty set of configuration switches. (Unless you're on Ubuntu, tee hee.)
* Lack of namespace support.
* Having to use :: and -> all the time when a perfectly good "." will do (like in C#).
* Strange function names and function parameter order.
* Too many keywords in the global namespace.

So the idea behind Polar was to make it based on Javascript, but with a smaller base keyword set and be more straight-forward to use. Polar could not only be a good teaching language, but be a great language for general purpose business use. Anyway, it's a long road off, but that's the general idea. The idea was to get something up with a hooked ngs-js for now, and then later on rework it entirely through the original source of ngs-js in C. Besides, I need a fun diversion to think about from work sometimes.

---

### Post by SuperMike on 2007-02-05
> **lnostdal said:**
> by using common lisp .. i'd have it up in an instant and it would be compiled to native machine code automatically via the lisp-compiler so it would have good runtime performance

Yeah, I hear this a lot from people. A lot of Lisp guys say that. I just find it confusing to read Lisp programs. However, if what you say is true, I'd like to see a sample on the web where someone has built a decent parser, lexer, and interpreter for something small.

Take for instance a very tiny language that's smaller than Javascript. Break it on down to its bare minimums with console I/O, undeclared variables (everything's a variant), arrays, simple math, some simple string functions, one while loop, one for loop, and if/then, and the ability to have functions and parameters. So, given that, how does one use Lisp rapidly to pull that off? I'd like to see an example because you just might have me sold on Lisp since many people have spoken to me about Lisp for this sort of thing.

---

### Post by lnostdal on 2007-02-06
very quickly here -- something like this:

(edit: corrected some errors .. and simplified .. and simplified yet again; very simple now)

```

(defmacro myScript (code-string)
  "`code-string' is something else than lisp-code"
  (with-input-from-string (code-stream code-string)
    (let ((arg1 (read code-stream))
          (opr (read code-stream))
          (arg2 (read code-stream)))
      (format t "\"compiled\" from `myScript' to lisp-code: ~A~%" `(,opr ,arg1 ,arg2))
      ;; lisp-code is returned at macro-expansion time and then compiled to machine-code:
      `(,opr ,arg1 ,arg2))))


(defun test1 ()
  (myScript "3 + 4"))


;; we can extend it by adding lisp-functions:
(defun myScriptExtension (a b)
  (format nil "myScriptExtension: ~A ~A~%" a b))


;; use the newly added feature/extension:
(defun test2 ()
  (myScript "1234 myScriptExtension 4321"))


;; and it can somewhat get hold of data from the "lisp-side":
(defun test3 ()
  (let ((abc 1234) (def 4321))
    (myScript "abc myScriptExtension def")))



#|
cl-user> (test1)
7
cl-user> (test2)
"myScriptExtension: 1234 4321
"
cl-user> (test3)
"myScriptExtension: 1234 4321
"
cl-user> (myScript "3 + 4")
"compiled" from `myScript' to lisp-code: ((+ 3 4))
7
cl-user> (myScript "3 * 4")
"compiled" from `myScript' to lisp-code: ((* 3 4))
12
cl-user> (myScript "3 expt 4")
"compiled" from `myScript' to lisp-code: ((expt 3 4))
81
|#

```

..should give you an idea .. also see: [http://www.gigamonkeys.com/book/practical-an-html-generation-library-the-compiler.html](http://www.gigamonkeys.com/book/practical-an-html-generation-library-the-compiler.html)
 (and the chapter before on interpreting: [http://www.gigamonkeys.com/book/practical-an-html-generation-library-the-interpreter.html](http://www.gigamonkeys.com/book/practical-an-html-generation-library-the-interpreter.html) )

edit: note that infix in lisp is already available using a better method here: [http://plaza.ufl.edu/lavigne/infix.lisp](http://plaza.ufl.edu/lavigne/infix.lisp) .. but that's not really the point .. :)

edit2: also note that this expects string-literals .. it would however be no problem at all to read the "myscript"-code from a file (or whatever; point is shift from acquisition of data (or code) at compile-time to runtime) then compile it to lisp, then compile it to machine-code..  something like:
```

(funcall (compile nil `(lambda () ,(read-from-string (read-line)))))

```
(replace read-from-string with a function-version of myScript - i think; let me know if you want me to confirm this in detail by posting another example)

if you read from a file you can cache the compiled result and check for changes in script-file by using `file-write-date' .. very cool :)

---

### Post by SuperMike on 2007-02-06
Very interesting! I will have to give this some thought. I'm not too excited about using Lisp, but a lot of people have bragged about how one could knock out a command interpreter quickly with it, so I might forgo the grief and commit to it if it really can generate an interpreter for a "mini language" in record time.

---

### Post by SuperMike on 2007-02-07
> **lnostdal said:**
> <snip>Lisp</snip>

Inostdal - Some questions for you:

* What do I need to install to compile your example (apt-get install x)?

* Let's say I want to make a mini-language that's sort of like a Javascript-lite. And then I want to deploy that on servers. Do I need to include all the Lisp runtimes and compilers with that or can I just deploy my language interpreter and handful of my own libraries?

---

### Post by lnostdal on 2007-02-08
> **SuperMike said:**
> 
* What do I need to install to compile your example (apt-get install x)?


Any Common Lisp should handle the example. I use SBCL. I think the SBCL-version in Edgy is a bit old though. Feisty will have a 1.x-version included. 

You'll also need a proper front-end like Slime. Working directly against any Lisp from the console is not really feasible.

I've always had my Lisp-environment setup locally in my home-folder though. I find it has a couple of benefits as you can navigate freely to the latest version of things (and back) when required. If interested I could post a short tut on how to get up and running using this method. :)


[quote=SuperMike]
* Let's say I want to make a mini-language that's sort of like a Javascript-lite. And then I want to deploy that on servers. Do I need to include all the Lisp runtimes and compilers with that or can I just deploy my language interpreter and handful of my own libraries?
[/QUOTE]

Lisp requires some sort of runtime like any other language. Even C requires runtime support ( [http://en.wikipedia.org/wiki/Glibc](http://en.wikipedia.org/wiki/Glibc) ). The overhead and method varies between Lisp-implementations, and some support more than one method of distributing software.

Using SBCL I'd probably dump an image that contains a daemon that will provide runtime support for and compile the script-code you send/apply to it: [http://sbcl.sourceforge.net/manual/Saving-a-Core-Image.html](http://sbcl.sourceforge.net/manual/Saving-a-Core-Image.html)

I've used this [http://nostdal.org/~lars/programming/lisp/lisp-daemon/](http://nostdal.org/~lars/programming/lisp/lisp-daemon/) for handling startup of a simple backup-tool I wrote in Lisp. I can connect to the backup-tool and do direct changes in it at runtime from a remote computer via Slime. It totally rules. :)

---

### Post by SuperMike on 2007-02-08
Someone emailed me this:

[http://nekovm.org/](http://nekovm.org/)

However, it requires that you use a series of sed/awks or other regexps on your "language" to convert it to Neko, and then execute Neko. The advantage of using Neko over others, supposedly, is that it's supposedly cross-platform.

I couldn't get my glibc to the right version without royally screwing up my system, so I found the Debian unstable package and installed it with 'dpkg -i'. That made neko install with errors, but work. However, when trying to install anything else through apt after that, it recommended that I uninstall neko. Therefore, off neko went.

I then got to thinking, if this is all that neko wants, then my idea is just about the same but do it for the ngs-js interpreter instead of neko. So right now, this "Polar" language concept that I've come up with is running through ngs-js. I'm adding things to ngs-js that it doesn't have, as well as sed'ing out things I don't want ngs-js to have. It's working quite well.

---


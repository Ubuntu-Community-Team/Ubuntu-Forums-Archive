---
title: "[SOLVED] Would it be worth it?"
date: 2007-11-30
forum: Programming Talk
---

### Post by Majorix on 2007-11-30
Please don't flame me after reading this if you are a strong fan of Python. I started out just like you, but the language rejected me.

I have been getting only problems since the time I started using Python.

1. Strings weren't mutable. And some functions returned tuples (which in my opinion is not an absolutely necessary property for a language to have) which also were immutable. I like having the freedom when coding and want to explicitly declare variables immutable by declaring them as const. Python also doesn't have the const modifier.

2. Then, I couldn't design GUI's with wxPython due to a bug of the Boa Constructor IDE which affected Linux machines, and I have started a thread about this asking what could be done. But the thread consisted only of the original post and my bumps. I had to boot into Windows just to code with wxPython and that is not what I want. I use Windows only rarely.

3. As far as I know, it is not easy to write regex'es with Python (actually there is no "regex'ing" under Python, only templating), due to lack of some stuff, and I believe that regex'ing is an essential value for a scripting language.

4. Python lacked good documentation. The tutorials are poorly written, except for the first one.

5. And I will most likely be moving to Japan or South Korea or another Far-Eastern country after I graduate; and I hear Ruby is more popular in that part of the world. Did I hear right?

6. My final problem so far is that the library failed on me by not retrieving a webpage fully. I also had to type in this "realm" and "host" parameters, of which I have no idea what they could be, and they aren't explained or sampled in the thousand-pager library reference. In my opinion it must be really easy to connect to webpages and retrieve their content, but with Python it wasn't.

The point of thread is, would it be worth my time and efforts continuing with Python? Or should I just go the Ruby way? I have already started with "Programming Ruby" from Pragmatic Programmers, which is like the official book for Ruby, and so far I like what I see. But Ruby isn't as popular as Python from what I read and hear, and that got me pondering.

---

### Post by smartbei on 2007-11-30
Regexing is possible in python through the re module. See [http://www.amk.ca/python/howto/regex/](http://www.amk.ca/python/howto/regex/).

In the case of the failed webpage retrieval you were using the wrong function for the job. You did not need basic http authentication, what you should have used was the basic urlopen function with certain parameters passed using POST.

Lastly, there are good reasons for strings being immutable, read things like [http://c2.com/cgi/wiki?ImmutableValue](http://c2.com/cgi/wiki?ImmutableValue). Google for more information if you are interested.

As for tuples - I am not sure why tuples bothered you so much:
```

x, y, z = func_that_returns_a_tuple()

```

As for your question: Ruby can indeed be a good (useful) language to learn, and you may or may not like it better - I guess that is up to personal preference.

---

### Post by Majorix on 2007-11-30
@smartbei:
In the official tutorial I read it didn't even mention about the re module. Thanks for providing me with information regarding it.

I believe I needed authentication in my case, because in the examples page they used only that HTTPBasicAuthentication() method WITH username and password parameters. Anyways I will look into that more.

And about the tuples.. Once while I was debugging a Python code it said that I was trying to modify an immutable tuple value. I didn't have any tuples in the code as far as I remember though, so I thought it must have something to do with the return value of a function. I know I am not being clear enough here, but I wasn't paying much attention to that while I was debugging, so it isn't that clear in my mind either. But I know one thing: Lists are enough.

Thanks for the reply :)

---

### Post by pmasiar on 2007-11-30
> **Majorix said:**
> In the official tutorial I read it didn't even mention about the re module. 

Not so, see Tutorial, 10.5 String Pattern Matching.

> And about the tuples..  I didn't have any tuples in the code 

it is easy to confuse list and tuples: (a,b) is tuple, [a, b] is list.

> I know one thing: Lists are enough.

And you know it wrong!:-)  Sometimes you **do want** immutable sequences. Even C has struct, which is basically tuple: 'grouped' values of different classes (list with values of different classes is possible, but not very useful).

If you thought about it a little (or had experience in low-level programming, like C or ASM), it would be obvious that strings **cannot** be immutable: any change requires reallocation of memory in heap.

There are many badly written Python tutorials, because too many people without deep understanding of the language feel qualified to express strong opinions about the language :-)

---

### Post by smartbei on 2007-11-30
I believe pmasiar meant:
> **pmasiar said:**
> 
If you thought about it a little (or had experience in low-level programming, like C or ASM), it would be obvious that strings **cannot** be **mutable**: any change requires reallocation of memory in heap.


With the obvious point being that other languages simply hide away this immutability, whereas python leaves it as is.

---

### Post by Majorix on 2007-11-30
I have this:
> Differences
Unlike Python, in Ruby,...

    * Strings are mutable.
from [http://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-python/](http://www.ruby-lang.org/en/documentation/ruby-from-other-languages/to-ruby-from-python/)

I was reading it to see what are the differences between Ruby and Python.

---

### Post by tyoc on 2007-11-30
I dont see why ASM or C show inmutability?

```
int main(){
    char a[4]; //int a[5];...
    for(int i = 0; i< sizeof(a); i++){
        a[i] = 0;
    }
    return 0;
}
```In asm there is **stos b, w, ...** thus I cant see why they are not mutable?, in fact they should be mutable, there is no enought capacity for all objects in memory to be unmutable.

Reallocating or resizing is other thing that has 1 connection with "mutability"... but I will call that more "extend the content" not the mutability like change of value in the own constrains (change of value of the data).

I dont get the thing of saying that asm and C have unmutable strings.

---

### Post by Majorix on 2007-11-30
I didn't claim anything about C. This thread was created with Python in mind. Please don't go off-topic.

---

### Post by CptPicard on 2007-11-30
What is the problem with immutable strings? They are efficient from implementation standpoint for example. Java has immutable strings too,  and it never troubled me. Anyway, isn't it easy to play with character arrays in Python if you need to?

---

### Post by LaRoza on 2007-11-30
You studied Python for a very short time, shopping for a "perfect" language will get you no where.  

[http://norvig.com/21-days.html](http://norvig.com/21-days.html)

As for tuples and lists, you can convert a type to a list (and a list to a tuple) with the list() and tuple() methods.

If such language features drove you away from Python, Ruby will likely show just as many flaws. Python is designed the way it is for a reason, and your objections to it are not part of the core of the language, Ruby will probably have features that annoy you as well.

---

### Post by tyoc on 2007-11-30
yea... also if you dont like unmutable filling, never go near of Haskel and related family.

[http://pleac.sourceforge.net/pleac_python/strings.html](http://pleac.sourceforge.net/pleac_python/strings.html)

You havent cleam nothing about C, yea. But there was a point about asm and C that I can't get or understand.

---

### Post by Majorix on 2007-11-30
You guys have added to my pondering... Everybody says to stick with Python...

But most of the problems I described in the OP are still there :( Some of them aren't even talked about yet.

---

### Post by tyoc on 2007-11-30
Enumerate the problems 1 by 1, I think they are almost all already answered.

Lack of documentation? (you even see that there is re and other things... how you can say that they are not there, only because you dont see it?), problem about not mutable? I give a link where if you really want, it is show how to do it with array of chars. But if you gona use a RAD, then you are tied to it (ie BOA dont working in linux??, dont know boa myself)... and other things... ie, I remember if Im not wrong that you say something that why auth and ubuntuforums doesnt work?? (thought in fact I only skim in that thread). If I where learning to use wxPython, I will not use BOA, intead try ```
[http://del.icio.us/soytyoc/dev:python:wx](http://del.icio.us/soytyoc/dev:python:wx)
``` or other useful links that request hand coded GUI (yea, I know you will like something RAD). 

>  The point of thread is, would it be worth my time and efforts continuing with Python?> You guys have added to my pondering... Everybody says to stick with Python...
 
 But most of the problems I described in the OP are still there :sad: Some of them aren't even talked about yet.You have stated the main point of this discussion :P.

---

### Post by Majorix on 2007-11-30
OK I enumerated the Q's as you requested. Should have done that the first time I posted. Anyways...

You got one of my points wrong. Bad documentation means that the author can't teach well, or you can't learn from it.

And why should I do it with an array of char's when there is the builtin class string and its methods?

And yes, I want a RAD, it is not called *Rapid* Application Development for nothing :)

---

### Post by Wybiral on 2007-11-30
> **Majorix said:**
> 1. Strings weren't mutable. And some functions returned tuples (which in my opinion is not an absolutely necessary property for a language to have) which also were immutable.

2. Then, I couldn't design GUI's with wxPython due to a bug of the Boa Constructor IDE which affected Linux machines, and I have started a thread about this asking what could be done.

3. As far as I know, it is not easy to write regex'es with Python (actually there is no "regex'ing" under Python, only templating), due to lack of some stuff, and I believe that regex'ing is an essential value for a scripting language.

4. Python lacked good documentation. The tutorials are poorly written, except for the first one.

5. And I will most likely be moving to Japan or South Korea or another Far-Eastern country after I graduate; and I hear Ruby is more popular in that part of the world. Did I hear right?

6. My final problem so far is that the library failed on me by not retrieving a webpage fully. 

1. Some things are immutable because they should be, however since Python supports strong generic features, converting an immutable to a mutable is trivial (and it expresses the code more explicitly). What function returns are you talking about?

2. wxPython is just a library. Try Gtk (glade works just fine).

3. There are re libraries for Python. I don't know what you're talking about.

4. Seriously? I think Python has TONS of great documentation (in book and online)

5. Not sure about this, but it probably depends what you want to do and what companies you want to work with.

6. Once again, that it's Python the language, that is a problem with a library. Try another one.

---

### Post by Majorix on 2007-11-30
#3 is solved. Sorry about the confusion, I must have been reading too fast.
#4 is doubtful. I have not come across any. Links?
#5, I want to work as an application dev in a serious IT company.
#6 can't be done with another built-in library. Do I have to download extra libraries? Can you link me to a page where I can find module downloads?

Thanks for the reply.

---

### Post by Majorix on 2007-11-30
> 
2. wxPython is just a library. Try Gtk (glade works just fine).


Sorry about the fast reply.

Is GTK cross-platform?

---

### Post by tyoc on 2007-11-30
del>  #4 is doubtful. I have not come across any. Links?In the links of the guys that like Python, I also have some here

```

[http://del.icio.us/soytyoc/dev:python](http://del.icio.us/soytyoc/dev:python)

```
Also search related like dev:python:wx in the page, because delicios dont know the way I manage catecories with ":" (like a wiki I have used little).

>  #5, I want to work as an application dev in a serious IT company.Any company that can give you a contract and pay you is enought serious I think.

> #6 can't be done with another built-in library. Do I have to download extra libraries? Can you link me to a page where I can find module downloads?Im not versed in this, but from what I remember skimming your original thread some time a go, you where trying to use an auth handler for connect to this forum and authenticate yourself, If Im not Wrong, that is a fail of concept, and http auth handler is for manage the authentication before get any content of the server, not the PHP based authentication also via sessions (dont know how many cokies relate to the PHP sessions...).

>  Is GTK cross-platform?From what I know, Linux & windows, I **suppose** also is OSX. But from what I know some of the demos are outdated (by instance see one related to HTML viewer or some like that, it dont catch the ENTER key when you press it on a URL, you should modify that little thing).


Also wich tuts are you reading? (that are not good, and which 1 is the good)

---

### Post by Majorix on 2007-11-30
@tyoc:
#4, thanks for the link. I will be checking the links from there and see if they are good enough. Also, what printed books are good?
#5, with serious I mean they have to have big goals and a good large staff.
#6, I don't quite get you. Could you please for instance post what you would do (in that thread if you would like)?

And I was reading the tuts from the official python docs page.

---

### Post by tyoc on 2007-11-30
[http://ubuntuforums.org/showthread.php?p=3858114](http://ubuntuforums.org/showthread.php?p=3858114)

mmm, I dont know exactly what are you trying to do (or if your first aproach was OK to what you want to do), but I will try to explain the difference,between authenticate HTTP and this board autenthication.

Example, suppose you connect to an FTP server, then you are prompt to user/passwd, you download a file, open it, and have a password.

The first user/password is part of the protocol, the second is part of the protection to the file you have just downloaded.

auth handlers are HTTP handler for the protocol authentication (like the user/pass for FTP), this board has an authentication (provided outside the HTTP protocol via PHP/sessions and dont know how cockies enter here exactly, but they are, all this is not part of the HTTP protocol) is more like the authentication of the file you just downloaded.


Hope this serve to you, for see that there is a difference between user/password at protocol level, and user/password at application level (like this board, that will require POST or some like that), like I have said, Im not well versed in this matter, perhaps later with more time I will look into it.

By instance, I dont know if you are trying to authenticate to a page that has authentication via HTTP (you are normally prompted with a poppup window before it even download anything from the server) or if you want to authenticate to a site like this (they are different things).

---

### Post by Majorix on 2007-12-01
> **Majorix said:**
> Please don't flame me after reading this if you are a strong fan of Python. I started out just like you, but the language rejected me.

I have been getting only problems since the time I started using Python.

1. Strings weren't mutable. And some functions returned tuples (which in my opinion is not an absolutely necessary property for a language to have) which also were immutable. I like having the freedom when coding and want to explicitly declare variables immutable by declaring them as const. Python also doesn't have the const modifier.

2. Then, I couldn't design GUI's with wxPython due to a bug of the Boa Constructor IDE which affected Linux machines, and I have started a thread about this asking what could be done. But the thread consisted only of the original post and my bumps. I had to boot into Windows just to code with wxPython and that is not what I want. I use Windows only rarely.

3. As far as I know, it is not easy to write regex'es with Python (actually there is no "regex'ing" under Python, only templating), due to lack of some stuff, and I believe that regex'ing is an essential value for a scripting language.

4. Python lacked good documentation. The tutorials are poorly written, except for the first one.

5. And I will most likely be moving to Japan or South Korea or another Far-Eastern country after I graduate; and I hear Ruby is more popular in that part of the world. Did I hear right?

6. My final problem so far is that the library failed on me by not retrieving a webpage fully. I also had to type in this "realm" and "host" parameters, of which I have no idea what they could be, and they aren't explained or sampled in the thousand-pager library reference. In my opinion it must be really easy to connect to webpages and retrieve their content, but with Python it wasn't.

The point of thread is, would it be worth my time and efforts continuing with Python? Or should I just go the Ruby way? I have already started with "Programming Ruby" from Pragmatic Programmers, which is like the official book for Ruby, and so far I like what I see. But Ruby isn't as popular as Python from what I read and hear, and that got me pondering.

I am trying to one by one eliminate the problems.

So far I eliminated #3 (it was my mistake, there is a re module to work with regex'es), #2 (I got wxGlade to work, and am currently working on it and learning wxPython), and #6 (do I have to use POST?)

Half eliminated, half to go (#1, #4, #5). I feel excited. Will I be able to get back to the most popular scripting language?

Thanks for all your help.

---

### Post by LaRoza on 2007-12-01
> 
1. Strings weren't mutable. And some functions returned tuples (which in my opinion is not an absolutely necessary property for a language to have) which also were immutable. I like having the freedom when coding and want to explicitly declare variables immutable by declaring them as const. Python also doesn't have the const modifier.

4. Python lacked good documentation. The tutorials are poorly written, except for the first one.

5. And I will most likely be moving to Japan or South Korea or another Far-Eastern country after I graduate; and I hear Ruby is more popular in that part of the world. Did I hear right?


1. The reasons why strings aren't mutable and why tuples exist are good, and Python doesn't have a "constant" modifier, if you want a value of a variable to be immutable, don't change it. Also, you can follow the convention of naming constants in all capital letters.

4. Python has the best documentation I have seen. The documentation is available online, and for download [http://docs.python.org/download.html](http://docs.python.org/download.html)

5. Learn Ruby or Python doesn't exclude the other. Learn both.

---

### Post by Majorix on 2007-12-01
@LaRoza:
1. I think I will have to start living with the fact that strings and tuples are immutable. Does list() successfully create a list from a tuple so that I can happily work with the list without worrying about immutability?
4. I have liked the tut.pdf (the first, introductory tutorial) from there, however when I tried reading the ext.pdf (the tutorial for extending Python with C/C++) I failed to learn. The first few pages got me puzzled so I left it. I had found another tutorial (unofficial), probably I should look into that. That looked more friendly to me.
However, the lib.pdf (library reference) didn't have too many examples. It could have contained an example for each function and class in the library. Is there another reference I can look at?
5. I am reading Programming Ruby as we speak, and am trying GUI programming with wxPython. So yeah, I am learning both. No problem for me, I have lots of empty storage space in my brain :p
Is there a wxRuby? In my RAD called wxGlade there is no option to generate Ruby code, but to generate Python, Perl, Lisp, C++ and XRC (is that a programming language?). Is there any tool that can create wxRuby (if the toolkit exists in the first place)

Thanks a lot :)

---

### Post by CptPicard on 2007-12-01
Seriously, even mentioning #5 does not reflect well on your competence or your ability to learn. I mean... are you honest to God serious that you're worried about learning the "wrong" language based on the idea that Ruby is winning some kind of a popularity contest in... uh... *Asia?* 

Do you have any idea how many coders there are in that part of the world, and how many different languages they make use of? For as long as you're flexible enough, you'll find plenty of work. And considering it an issue with Python that Ruby's popularity is higher in Japan than in the rest of the world (because that's where it originated from) just means you're avoiding the necessary work of knowing multiple languages...

---

### Post by Majorix on 2007-12-01
You are so kind in style that I can only thank you.

---

### Post by CptPicard on 2007-12-01
No hard feelings but your argument is just bs, so I might just as well call you on it ;)

---

### Post by SunnyRabbiera on 2007-12-01
well if you feel ruby is better go for it, both ruby and python are open source.
I find pearl pretty good too, I actually used it once or twice and found it pretty easy.
I did python once too, its not that hard but I see where you can have issues

---

### Post by ghostdog74 on 2007-12-01
> **Majorix said:**
> 
The point of thread is, would it be worth my time and efforts continuing with Python? Or should I just go the Ruby way? I have already started with "Programming Ruby" from Pragmatic Programmers, which is like the official book for Ruby, and so far I like what I see. But Ruby isn't as popular as Python from what I read and hear, and that got me pondering.

Can you help me?
I started drinking Pepsi, would it be worth my time continuing to drink Pepsi, or should i drink Coca Cola. I heard Pepsi is not as popular as Coca cola, and that got me pondering.

---

### Post by pmasiar on 2007-12-01
#5 who uses Python?

See [http://python.org/](http://python.org/) : NASA, ILM, Honeywell uses Python, not mentioning Google. Big enough? :-)

If you want to be a **professional** programmer, be prepared to learn many more languages - there is no silver bullet. Start learning SQL now :-)

---

### Post by Majorix on 2007-12-01
I know beginner level Python, Java, and just started out with Ruby.
I know intermediate C and C++.
I know somewhat advanced C# and SQL. There is not much to know to SQL anyways, a simple cheatsheet reference kept by does the job :D

I consider myself to be a student coder; still learning, but in the right path hopefully :)

---

### Post by LaRoza on 2007-12-01
> **Majorix said:**
> @LaRoza:
1. I think I will have to start living with the fact that strings and tuples are immutable. Does list() successfully create a list from a tuple so that I can happily work with the list without worrying about immutability?
4. I have liked the tut.pdf (the first, introductory tutorial) from there, however when I tried reading the ext.pdf (the tutorial for extending Python with C/C++) I failed to learn. The first few pages got me puzzled so I left it. I had found another tutorial (unofficial), probably I should look into that. That looked more friendly to me.
However, the lib.pdf (library reference) didn't have too many examples. It could have contained an example for each function and class in the library. Is there another reference I can look at?
5. I am reading Programming Ruby as we speak, and am trying GUI programming with wxPython. So yeah, I am learning both. No problem for me, I have lots of empty storage space in my brain :p
Is there a wxRuby? In my RAD called wxGlade there is no option to generate Ruby code, but to generate Python, Perl, Lisp, C++ and XRC (is that a programming language?). Is there any tool that can create wxRuby (if the toolkit exists in the first place)

Thanks a lot :)

1. list() does that, it takes a tuple, returns and returns a list.

4. I am not sure exactly what kind of documentation you need, but browse my wiki: [http://laroza.pbwiki.com/Python](http://laroza.pbwiki.com/Python). The best way to understand a function, if you don't fully understand the docs, is to try it. The python interactive sessions are great for this.

5. [http://wxruby.rubyforge.org/wiki/wiki.pl](http://wxruby.rubyforge.org/wiki/wiki.pl)      [http://www.wxcommunity.com/modules.php?op=modload&name=Downloads&file=index&req=viewdownload&cid=1](http://www.wxcommunity.com/modules.php?op=modload&name=Downloads&file=index&req=viewdownload&cid=1)

---

### Post by Majorix on 2007-12-02
#1, thanks, I will use that from now on.
#4, I need a documentation that would explain about extending Python with C or C++.
#5, I couldn't find any IDE for wxRuby (I have a thread here asking about one too) so I am currently looking into fxRuby. I will let you know how it goes.

Thanks :)

---

### Post by Wybiral on 2007-12-02
> **Majorix said:**
> I need a documentation that would explain about extending Python with C or C++.

Assuming you're an experienced C programmer, you shouldn't need much more than this: [http://docs.python.org/api/api.html](http://docs.python.org/api/api.html)

---

### Post by Majorix on 2007-12-02
#5 is fixed. I am from now on using fxRuby, FreeRIDE, Geany, and FoxGUIb to build GUI applications with Ruby.

@Wybiral:
Isn't that a reference guide? Is it good to learn from a reference? Aren't there any tutorials instead? Thanks for caring.

Only #4 is yet to be fixed. Others are done with.

---

### Post by Majorix on 2007-12-05
*bump*

---

### Post by Wybiral on 2007-12-05
Since my last post I've had a pretty enlightening experience with [SWIG]("http://www.swig.org/Doc1.3/Python.html"). If you plan to wrap C or even C++ code into Python, don't waste your time with the Python-C API. Use something like SWIG instead. It will save you tons of migraines, and do a ton of work for you.

---

### Post by tyoc on 2007-12-05
And it has athe plus that it also work for other langs... thus worth it.

---

### Post by Majorix on 2007-12-05
> **Wybiral said:**
> Since my last post I've had a pretty enlightening experience with [SWIG]("http://www.swig.org/Doc1.3/Python.html"). If you plan to wrap C or even C++ code into Python, don't waste your time with the Python-C API. Use something like SWIG instead. It will save you tons of migraines, and do a ton of work for you.

I have actually gone and fetched myself the whole documentation, and I will try to read it as soon as possible. Thanks for the tip :)

---

### Post by Majorix on 2007-12-07
A little status update I felt like posting:

I am in the midst of a Python RegEx-Howto.
I am also reading "Programming Ruby" from Pragmatic Programmers.
I have downloaded the SWIG tutorial but I am yet to start reading it. But it looked promising enough.
I have tried programming with fxRuby and FoxGUIb, but FoxGUIb kept crashing on me. Now that I am upgrading to Hardy on the said computer, things may or may not change. We shall see. I will update you again.
I have learned how to live with Python's immutable strings and tuples.

For now I am marking this as solved.

I am back to business with Python. Thanks to all who helped.

Maj-

---


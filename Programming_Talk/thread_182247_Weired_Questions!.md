---
title: "Weired Questions!"
date: 2006-05-25
forum: Programming Talk
---

### Post by Isoss on 2006-05-25
Well .. I feel weired to ask such questions being a php programmer! ... 

Just no body taught me and I've just started asking myself these questions as I took some geek pills to help being a faster-growing geek so I can develop and improve my web programming skills faster for the sake of better job performance.

And these questions are:

1. I know computer is based on - correct me if I am wrong - on 111100010100011 ... then comes the assebly then - I guess - ASCII and then the programming languages that we are here for. So, in general, how programming languages are usually built so thier applications "or environments" would comprehend the scripts. I need to know that for PHP in particular. I mean like ( how did 

2. In what laguages web applications are built? like those applications built for php programming.

3. What is .list ? as for sources.list I can see the comment hash ( # )  which gives me the impression that something like "  deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted " is a programming function! so to what programming language does .list refere?


Enough 4 now ... I'll continue posting my questions after I get these answers answered. 
I am really happy to be here. Ubunutu is really "Humanity for others" and that's how I reallt feel here. ppl are very helpfull and encouraging.

Thanks in advance.

---

### Post by kingmonkey on 2006-05-25
> how programming languages are usually built so thier applications "or environments" would comprehend the scripts.

Scripts is a list of programs.
Programs are written in languages that are compiled into binary.

Hope that helps a bit - Im no expert.

> What is .list ? as for sources.list I can see the comment hash ( # ) which gives me the impression that something like " deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted " is a programming function! so to what programming language does .list refere?

.list means nothing its just a label for you to know its a list
# at the begining of a line tells the program to ignore that line when it reads it.

> In what laguages web applications are built? like those applications built for php programming.

Could be any language under the sun really. C++ or python is most likely though.

---

### Post by siminone on 2006-05-25
I'll try to answer your question to be the best of my abilities:

I. Computer languages are split into two different types, compiled and intrepreted. Compiled languages convert the source code you type in into machine code (ie 1's and O's). This machine code is then executed as programs.

Intrepreted languages (some are also known as script langauges like PHP) on the other hand convert the source code to machine code and when you finish running, it 'disapears'.  

You will always need an intrepreter to run your source code every time whereas compiled code is independent of the language compiler.

For PHP, the intrepreter is embedded into the server ie Apache. When your server encounteres a PHP file, it calls the PHP Intrepreter to convert the PHP file into HTML code so it can be displayed.

2) PHP is a web language, as well as python, perl, asp, java, javascript, AJAX (a framework of Javascript and XML). The list goes on.

In terms of .list files, they are just text files that contains addresses of all Ubuntu repositories. The # (as you said a programming function) is used as comments and is ignored by apt.

---

### Post by Isoss on 2006-05-25
> **kingmonkey]Scripts is a list of programs.
Programs are written in languages that are compiled into binary.

Hope that helps a bit - Im no expert.
[/QUOTE]
Thanks. but this still needs more clear to me. I was kinda froze wondering how could this be?? that scripts are programs!!! I mean, talking with php ... when I go like <?php
function func($var)
{
  if ($var == value)
  { 
    return "$var" said:**
> 
.list means nothing its just a label for you to know its a list
# at the begining of a line tells the program to ignore that line when it reads it.


Good ... I was thinking that it might be something like .inc which we include into a php file like configs and stuff. so .. I guess .list is the same ... it should be included into some file, mabe built with C++ and the # is for commentting used by C++ or whatever ...

[QUOTE=kingmonkey]
Could be any language under the sun really. C++ or python is most likely though.[/QUOTE]
I've just started thinking of Paython ... and by the way ... I've never heard of it before I entered these forums.

Thanks a lot. Still waiting for some answers before I post my new questions.

---

### Post by Isoss on 2006-05-25
[QUOTE=siminone]I'll try to answer your question to be the best of my abilities:

I. Computer languages are split into two different types, compiled and intrepreted. Compiled languages convert the source code you type in into machine code (ie 1's and O's). This machine code is then executed as programs.

Intrepreted languages (some are also known as script langauges like PHP) on the other hand convert the source code to machine code and when you finish running, it 'disapears'.  

You will always need an intrepreter to run your source code every time whereas compiled code is independent of the language compiler.

For PHP, the intrepreter is embedded into the server ie Apache. When your server encounteres a PHP file, it calls the PHP Intrepreter to convert the PHP file into HTML code so it can be displayed.

2) PHP is a web language, as well as python, perl, asp, java, javascript, AJAX (a framework of Javascript and XML). The list goes on.

In terms of .list files, they are just text files that contains addresses of all Ubuntu repositories. The # (as you said a programming function) is used as comments and is ignored by apt.[/QUOTE]

I guess with the help of you guys things got more clear. By the way. I studied these stuff long time ago but I was very young and interested in some other stuff ... so I just forgot the compiler and the interpreter stuff ...

So I guess I'll just continue my questions right here in the following reply post.

---

### Post by Isoss on 2006-05-25
Here I come to the rest ... I dunno whether the list's gonna be long or not but that depends on the questions that I might just come up with during this discussion or maybe they could be shortened by spontenous answers.

4. Let's say I want to invent a programming language. Do I need to konw assembly in order to do that? ofcourse I am not going to or not even thinking but who knows??? I believe God created our brains with the same abilities but it just depends on HOW these abilities are implemented and improved and directed the right way ... and I guess that's what I am doing here ... directing my thoughts ... just to be familiar with everyhthing.

5. What are the main differences between PHP and the other web programming languages that functions just the same. I mean languages like ASP and Perl ... I know PHP is an open source ... which is my moto my computers and internet life. (That's why I chose to fly with linux) ... ASP is MS and I just abhor it therefor! ( no hard feallings ha? you can be free to abhor open source as well ;) ) so I just dunno what can ASP do which PHP can't do! 

6. What is the most dynamic language in web page performance? could C++ and C# be written into a webpage under some certain environment which compiles them with the other web programming laguages (My questions is based on something I heard) ... is this what is called ASP.NET or  PHP.NET ? and if yes, is this the answer to the "dynamicism", if I can call it like that, which this question is all about?

---

### Post by Kvark on 2006-05-25
I am far from an expert when it comes to low level stuff, hope I don't make a fool out of myself while trying to answer this...

To invent a programming language you need to know any existing programming language.

For example let's say you make a game where the players submit simple programs in an easy language you invented that moves robots around in a virtual world. You can make PHP loop through each line in a text a user submitted and perform actions depending on what each lines say. A switch statement like this could be responsible for making your PHP script understand the code the players submit. The functions this statement calls would just manipulate the game database.
```
switch ($line) {
case "move forward":
   move_forward($robot_id);
   break;
case "turn left":
   turn_left($robot_id);
   break;
case "turn right":
   turn_right($robot_id);
   break;
}
```

If you want to know how computers actually think in binary then build a calculator circuit one transistor at a time. Perhaps a virtual one with klogic which is in the repos. After building circuits that can compute simple calculations (such as "add two binary numbers given by pushing a row of buttons and display the result in binary by lighting a row of leds" so you need to know how to read and write numbers in binary which is easier then it sounds) and reading up on how the transistors and other components in a circuit works it might feel a little bit less like a mystery that computers can think in binary.

To bridge the gap from binary to text languages. Imagine that you would write a program in binary. A sequence of binary numbers that will be fed to a circuit to cause it to perform a sequence of calculations. You could write a binary program that performs calculations on the binary ascii codes in a text file and produces a new sequence of binary numbers, a new pogram. Now you can use assembly instead of binary because you have an assembler and even if you want to make a new assembler you don't need to use binary because your old one can put the new one together. From there on repeat the same proccess to invent higher level languages, write a C compiler in assembly and so on all the way up to the parser written in PHP to invent the simple robot game language.

---

### Post by Isoss on 2006-05-25
Thanks ... that really helps. that encourages me to go and google for more study materials but now I have some specificatios to use for my search ... Thanks again. 

Still waiting for some answers ... Thanks guys

God bless

---

### Post by unbuntu on 2006-05-25
> 4. Let's say I want to invent a programming language.Do I need to konw assembly in order to do that?
Yes and no.  It depends on to what extent you mean by "programming language".  For us to use a certain language, it takes source code, which is no more than a file consisting of strings and lines, and the rules to interpret these strings and lines that makes a computer understand our intention.  The first component maps to the semantic side of a language, and second the compiler side.  You definitely need assembly if you're writing a compiler, but not so for the semantics part...that's my understanding anyways...

> 5. What are the main differences between PHP and the other web programming languages that functions just the same.
No language nowadays can claim that there are things it can do but absolutely impossible for another language.  Therefore, for the functional side, not much is different from languages to languages.  It comes down to personal preference(or company preference) and other features.  Most people choose PHP because it's efficient under apache, it's open-source, and suits very well the needs of small-medium scaled web applications.

> 6. What is the most dynamic language in web page performance? could C++ and C# be written into a webpage under some certain environment which compiles them with the other web programming laguages...
For ASP.NET you can use any language (I think) that is under the ".NET umbrella", which includes C#.  Yes, ASP.NET compiles source code into binaries and it comes with the concept of "Web components" which PHP doesn't have native support for. (at least for PHP4, not sure about PHP5 tho)

---

### Post by Isoss on 2006-05-25
Hmmm ... every word is interesting! stiring up more questions though ...

So ... There is no such thing as PHP.NET? I heard it from someone but still not sure. I need more explaination on this: 
[quote=unbuntu]Yes, ASP.NET compiles source code into binaries and it comes with the concept of "Web components" which PHP doesn't have native support for. (at least for PHP4, not sure about PHP5 tho)[/quote] what do u mean by native support? ... In short .. is there an environment for PHP like the .NET ubmrella concept? I also wanna know how to to distinguish a compiled-languages based website ... I mean like direct me to a website that just gives these dynamic features that only .NET compiled-languages can do. Is it something like mircosoft website?

---

### Post by unbuntu on 2006-05-25
[QUOTE=Isoss]
So ... There is no such thing as PHP.NET? I heard it from someone but still not sure. 
[/quote]
There is such thing as PHP.NET...[www.php.net :p](www.php.net :p) 
But I never heard dot net's version for php, and googling around didn't give me anything either...
> 
I need more explaination on this: 
 what do u mean by native support? ... In short .. is there an environment for PHP like the .NET ubmrella concept? 
Native support: for instance, in ASP.NET you can develop a web page as if you are developing a desktop application.  The web components are just like components (or "control" in old-day VB term) for desktop application from a textbox, button, to more complicated components like Calendars and Validators...The support of these use are built-in in ASP.NET, meaning you can get the component (usually in DLL but I could be wrong), set up the project property, import the namespace, and then go ahead and use them.  But there's no equivalent for these in PHP4.  
> 
I also wanna know how to to distinguish a compiled-languages based website ... I mean like direct me to a website that just gives these dynamic features that only .NET compiled-languages can do. Is it something like mircosoft website?
Well...if you see a URL that points to some aspx file, that's a clear clue that it's using ASP.NET...much of the "dynamic" features on Microsoft.com are results of using web components I believe.

---

### Post by Isoss on 2006-05-25
Cool infos. I just wish there could be like ASP.NET for PHP in the future. I'm more concerned in web programming and even if I can learn the other languages used for desktop applications I don't think that I would one day leave the web programming. Any way .. I just seek to introduce higher and better perormance through websites and internet. 

One last thing before I get to sleep cuz I am yawning already!
I noticed something wiered: when I go to [www.joker.com](www.joker.com) it can see that the index extension is .joker!!! like this: [https://joker.com/index.joker](https://joker.com/index.joker)  ... 
What is that? I also have seen a website one day with the extension index.index ... what are these? programming languages or what?
like did joker invent a programming language for websites and is using it alone? 
LMAO ...
no ... really what is this?

---

### Post by KLineD on 2006-05-25
I'll try to explain the best I can, because this is a field that interests me a lot.

[QUOTE=Isoss]1. I know computer is based on - correct me if I am wrong - on 111100010100011 ... then comes the assebly then - I guess - ASCII and then the programming languages that we are here for. So, in general, how programming languages are usually built so thier applications "or environments" would comprehend the scripts. I need to know that for PHP in particular. I mean like ( how did[/QUOTE]

You've got half of it right. First there is binary and that's the only thing a computer understands. Assembly language is just a set of mnemonics (instructions) and data. Assembly can be considered as a basic programming language. With it you have direct access to the processor, it's internal registers and so on. Now ASCII has nothing to do here, ASCII is just a standar that defines certain values with certain character, let's say the value (in hex) 0x41 represents the character 'A' (not 'a', that's a different hex value) why 0x41 and not another? it's just because that's the way it's defined.

Now, as I understand your post, you mentioning "programming languages" actually means "high level programming languages". These, as said by siminone, can be interpreted or compiled. Interpreted ones need another program (an interpreter) that takes the program you wrote, reads it instruction by instruction, and executes the appropiate action. Examples of interpreted languages are Python and Perl.

Compiled languages need a compiler (hence the name) to convert the source code you wrote to binary data (that the computer understands). Then, the OS can execute the program, allocating any resources it needs, etc.

So, in order to invent a new language you need two things: define the structure (grammar, features, etc) of the language and create a compiler for that language. There are tools that aid in the creation of new languages, being the most popular (by me anyway) [bison]("http://www.gnu.org/software/bison/").

[QUOTE=Isoss]2. In what laguages web applications are built? like those applications built for php programming.[/QUOTE]
In many actually! you mentioned PHP, but there are more, like ASP or JSP. Now a very popular "technique" is making use of asynchronous Javascript + XML otherwise known as AJAX.

[QUOTE=Isoss]3. What is .list ? as for sources.list I can see the comment hash ( # )  which gives me the impression that something like "  deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted " is a programming function! so to what programming language does .list refere?[/QUOTE]
Well, the extension has nothing to do with the file, the same way a text document can have .txt or .readme or no extension at all. sources.list is a text file with a defined grammar so a program (apt) can read it, parse it, understand it and then execute some instructions with the info contained there. The makers of apt defined the pound symbol (#) so when apt encounters this at the beginning of a line, that line is ignored. But it's not like that is a binary instruction or anything.

I hope I can help you understand a little better these questions.

---

### Post by unbuntu on 2006-05-25
[QUOTE=Isoss]
One last thing before I get to sleep cuz I am yawning already!
I noticed something wiered: when I go to [www.joker.com](www.joker.com) it can see that the index extension is .joker!!! like this: [https://joker.com/index.joker](https://joker.com/index.joker)  ... 
What is that? I also have seen a website one day with the extension index.index ... what are these? programming languages or what?
like did joker invent a programming language for websites and is using it alone? 
LMAO ...
no ... really what is this?[/QUOTE]

The extension of a file doesn't really matter for a computer...it's for human readability or whatever.  Don't know what their server is but I know on Tomcat you can set up URL redirection (or something like that...I forgot the term), and then you have this dummy index.joker "file", which may not even be a file. But everytime you hit this url, you got redirected by the servlet that's actually processing this url.

---

### Post by Isoss on 2006-05-26
Perfect ... thanks a lot guys you've been very helpful. things are more clear now, they need more study of me though ... so I'll try to get some e-books as much as I can to establish a full understing of these basics. And your answers got me more interested.

It was my dream to study something like computer sience but never could! But thank God for the internet with which you can bring the whole world and every knowlegde into your house ... 

I'll google arround and at the same time I hope that you'd help me find some good e-books (HTML manuals and e-books are preferable) about:
1. How Binaries are created as (on - off) positive and negative charges. and How does the computer understand it. I mean like everything about electronics in computer and the way birnaies are created.
2. Everything about the Assembly language.
3. How compilers and interpreters work together.

I need to study one of the computer programming languages that will help me write db-based programs that work with something like mysql. something that is pretty close to PHP in the way it functions.
I am working on an arabic bible study website using PHP of course. let's say I want to create an arabic bible study software ... something that is pretty similar to what I'm doing in PHP. What programming language do u suggest?

Now here I have a question.

In softwares, what is the language that functions the same as HTML for building webpages? I mean languages that can create templates and frames for programs? 
For example, if I need to build a website, I need HTML, CSS, (sometimes JS), PHP, MySQL, SQL ... 
Now in softwares, let's say I need to use Paython, or perl, or C++ ... I wish that you'd list each programming langauge with the languages it works with to create a software program.

Thanks a bunch guys.

God bless you all.

---

### Post by Kvark on 2006-05-26
A programmer really doesn't need to know how the electronics in a computer works. But if you are curious the [wikipedia article]("http://en.wikipedia.org/wiki/Digital_circuit") on digital circuits should give an overview of the topic. [These lessons]("http://www.ibiblio.org/obp/electricCircuits/index.htm") looks like they go through the topic with the same detail as you'd get when reading electronics in school. No matter what material you read you'll need to experiment as much as possible in klogic or another circuit simulator to really understand what they are talking about.

Personally I'd recommend Python for writing software. For the user interface (which PHP users html+css for) I perfer wxWidgets because it uses GTK widgets on Linux so it's just as good on Linux as PyGTK but it can also use the native widgets on Windows or OSX instead so it's cross platform without extra work. To use wxWidgets you can either write Python code that adds stuff to the GUI (code that says "create menubar, add menu to menubar, add menu item to menu" and so on), write an xml file(similar to html, it's structured tags instead of a long row of "add this, add that, add some more" that is usually used to define software GUIs) that defines the interface or drag and drop widgets in a graphical GUI maker such as wxglade.

---

### Post by KLineD on 2006-05-26
[QUOTE=Isoss]1. How Binaries are created as (on - off) positive and negative charges. and How does the computer understand it. I mean like everything about electronics in computer and the way birnaies are created.[/QUOTE]
To understand that you need to have a deeper understanding of how electronics work. The things you are asking go way down inside the processor, where transistors live. The transistor used in digital electronics function as a very tiny electric switch, that change states (on and off) when current passes through them (it's a lot more complicated than that but then I'd need to explain about solid state phisics and that's another story). Transistors are also used in analog electronics to make amplifiers, filters, etc.

[QUOTE=Isoss]2. Everything about the Assembly language.[/QUOTE]
Assembly is really a fascinating languge, but a very though one too. It's generally not recommended to develop in assembly unless you absolutely need to because of speed, size or other constrains or because you are cross developing for a microcontroller with no high level language. Take a look at [the art of assembly]("http://webster.cs.ucr.edu/AoA/index.html") if you want to learn something about assembly for the x86 the easy way. Thou the author of the book adds some extensions to x86 assembly to make it easier to start programming, it's a great book and a great learning experience.

[QUOTE=Isoss]3. How compilers and interpreters work together.[/QUOTE]
Well, they dont. A language (tipically) is either compiled or interpreted. Maybe I'm missing the point of your statement here but it seems to me that you have the (wrong) idea that both a compiler and an interpreted are needed to produce a program.

[QUOTE=Isoss]I need to study one of the computer programming languages that will help me write db-based programs that work with something like mysql. something that is pretty close to PHP in the way it functions.
I am working on an arabic bible study website using PHP of course. let's say I want to create an arabic bible study software ... something that is pretty similar to what I'm doing in PHP. What programming language do u suggest?[/QUOTE]
PHP can do what you want and more, but it's not the only language that can connect to databases. You can use for example, Java and JDBC to connect to any database with a JDBC connector like mysql, postresql, sql server, oracle, hsqldb and more. With Java (and servlets/JSPs or any of its many web frameworks like struts, tapestry, JSF)

[QUOTE=Isoss]Now here I have a question.

In softwares, what is the language that functions the same as HTML for building webpages? I mean languages that can create templates and frames for programs? 
For example, if I need to build a website, I need HTML, CSS, (sometimes JS), PHP, MySQL, SQL ... 
Now in softwares, let's say I need to use Paython, or perl, or C++ ... I wish that you'd list each programming langauge with the languages it works with to create a software program.

Thanks a bunch guys.

God bless you all.[/QUOTE]
Now, I find this question very interesting. Someone mentioned wxWidgets, but generally there isn't a language to create presentation per se. In desktop programming, you have something like a toolkit, or widgets that are provided so a programmer can use those widgets and create a user interface. Examples of widgets are buttons, text boxes, check boxes, scrollbars. Some toolkits offer a series of hooks so different programming languages can be used (GTK for example can be used in conjunction with Python, C or Java) but others only allow for one programming language. So to make a story short, there isn't a standar language to describe application layout, but it sure is a hell of an idea (and I think it's somewhat implemented with toolkits that provide XML description of user interface)

---

### Post by siminone on 2006-05-27
Might I suggest you look at mod_python. It is a python intrepreter embedded into the Apache server. It is still under developmet but has a number of advantages over PHP -

1) You can access all the modules (libraries) of the Python language.
2) Access to Apache internals like handlers (these are parts of the server software that 'handles' the processing of a webpage). It can be configured to process certain webpages differently.
3) It seperates code from presentation. You have webpages of code that calls HTML pages. This is a matter of taste but I've had a look at PHP and mod_python and find code more logical to understand if it is all in one place rather than scattered around webpages.

As to comment made in earlier post about the need to know other programming languages when creating a new one, I'm not so sure about that.

This is going off on a tangent but as computers become more powerful and evolve like biolgoical and quantum computing, there will be new ways to interact and communicate with them. 

Can this be best done with the programming languages today that are based on mathematics?

---

### Post by Isoss on 2006-05-27
Thanks to you all guys ... valuable information and links. I am really encouraged to learn about assembly and Paython. I will work hard learing, and I trust that you would help me. I'd also help with the stuff I know, whether in PHP or anything related to web development. I am really glad here. Ubuntu turned my programming "instincts" on lol.

Thanks to all of you.

---

### Post by Kvark on 2006-05-27
I haven't used a circuit simulator since switching to Linux but this thread made me actually try a bunch of different circuit simulators for Linux. I discovered that me mentioning klogic earlier was a mistake, it's ok but tkgate which is also in the repos is a much better alternative. When you start tkgate it displays an excellent tutorial that will get even complete newbies started. That tutorial is the best quick intro to circuits I can find. Other advantages is that it displays circuits in a very clear way (well, clear once you get used to the symbols) and working with them is easier then in most other simulators. There, now I have corrected the bad advice I gave earlier on which simulator to practice with if you care about how digital electronics works.

Back to the programming topic. Learning assembly or any language for that matter might be good just to learn programming in general from a new perspective but you hopefully won't ever have to use assembly for any real project. High level languages are far more productive.

---


---
title: "FAQ: Scripting Languages"
date: 2008-02-10
forum: Programming Talk
---

### Post by LaRoza on 2008-02-10
This thread help your write and run various scripting languages, if you have another language to add, post it, and I will update this post.

[size=+1][color="blue"]Languages:[/color][/size]
* Perl
* PHP
* Python 
* Ruby
* Tcl
* ECMAScript
* Shell
* C

[size=+1][color="blue"]Common to all:[/color][/size]

There are two ways to run a script, one by invoking the interpreter on the command line, and the other is to run it as a normal executable. 

To mark a file as executable, use this command:

```

chmod +x <filename>

```

To let the system know which interpreter to use, use the **shebang** ( #! ). It must be the first line of the script. It should point to the interpreter with the correct options.

To run a script, run it like a normal program, if the script isn't in your $PATH variable, specify the path. 

The packages to be install, an example program, and the running of it are given here.

```

./<filename>

```

Will run a script or program in your current working directory.

[size=+1][color="blue"]Perl:[/color][/size]

You don't need to install anything.

[php]
#!/usr/bin/perl
#Save as "hw.pl"
print "Hello world!";
[/php]

Mark it executable, and run.

[php]
chmod +x hw.pl
./hw.pl
[/php]

[size=+1][color="blue"]PHP:[/color][/size]

You will need to install the php-cli package.

```

sudo aptitude install php5-cli

```

Example program:

[php]
#!/usr/bin/php
<?php
// Save as hw.php
    echo "Hello world\n";
?>
[/php]

Mark it as executable and run.

[size=+1][color="blue"]Python:[/color][/size]

Python is already installed.

Example program:

[php]
#!/usr/bin/python
#Save as "hw.py"
print "Hello world!"
[/php]

Mark it as executable and run.

[size=+1][color="blue"]Ruby:[/color][/size]

Install with:
```
sudo aptitude install ruby
```

Example program:

[php]
#!/usr/bin/ruby
# Save as "hw.rb"
puts "Hello world!";
[/php]

Mark as executable and run.

[size=+1][color="blue"]Tcl:[/color][/size]

Tcl is installed.

Example program:

[php]
#! /usr/bin/tclsh
# Save as "hw.tcl"
puts "Hello World!"
[/php]

Mark it as executable and run.

[size=+1][color="blue"]ECMAScript[/color][/size]

Note: ECMAScript isn't normally used this way.

You will need to install spidermonkey, which is the ECMAScript interpreter used by Firefox.

```

sudo aptitude install spidermonkey-bin

```

Example program:

[php]
#!/usr/bin/smjs
//Save as "hw.js"
print("Hello world");
[/php]

Mark as executable and run.

[size=+1][color="blue"]Shell Scripts[/color][/size]

Obviously, you have a shell installed.

Example program:

```

#!/bin/sh
# Save as "hw.sh"
echo "Hello world"

```

Mark as executable and run.

[size=+1][color="blue"]C:[/color][/size]

Surprise! C is normally compiled, see [FAQ: Compiling your first C or C++ programs]("http://ubuntuforums.org/showthread.php?t=689635") if you want to learn how to use C. There is a very good C interpreter which you can use. It is also a compiler, and may be better than gcc in some cases.

You will need to install [Tiny C Compiler (tcc)]("http://fabrice.bellard.free.fr/tcc/"), use:

```

sudo aptitude install tcc

```

Example program:

[php]
#!/usr/bin/tcc -run
#include <stdio.h>

int main(int argv, char ** argv) 
{
    printf("Hello World\n");
    return 0;
}
[/php]

Mark it as executable and run it.

[size=+1][color="blue"]Final Notes:[/color][/size]

Although these languages look similar with these examples, they are very different when your programs are more than one line.

If you are using Windows, you don't need to specify the path when it is in the current working directory, and you don't need the shebang. Windows uses file extensions to determine what is executable.

C is not normally run this way, so if you are learning C, you might want to familiarize yourself with gcc, and compiling.

To learn more, see [Learn to Program wiki]("http://laroza.pbwiki.com")

---

### Post by ghostdog74 on 2008-02-10
should C be here?

---

### Post by LaRoza on 2008-02-10
> **ghostdog74 said:**
> should C be here?

You caught me in middle of an edit, yes, it should.

(Read it :))

---

### Post by ruy_lopez on 2008-02-10
Since you are introducing the shebang, you might as well introduce shell scripting:

```
#!/bin/sh

echo "Hello world"


```

I know PHP code blocks look nice and colorful, but there *is* a PHP example. Having the other examples titled "PHP Code:" might confuse some people.

---

### Post by LaRoza on 2008-02-10
> **ruy_lopez said:**
> Since you are introducing the shebang, you might as well introduce shell scripting:

```
#!/bin/sh

echo "Hello world"


```

I know PHP code blocks look nice and colorful, but there *is* a PHP example. Having the other examples titled "PHP Code:" might confuse some people.

Yeah, but I don't want only one to have syntax highlighting, and I am using the [ code ] for commands. They will get over it, probably.

Good idea, I will add shell now.

---

### Post by RIchard James13 on 2008-02-10
BASIC -> Gambas is the one I hear the most about, but I don't know if it runs from the shell.
JAVASCRIPT -> whatever the current version is runs in your web browser. You can embed it in html or load it separately.

[PHP]<html>
<head>
<script type="text/javascript">
<!--
document.write("<h1>Hello World</h1>");
// -->
</script>
</head>
<body>
</body>
</html>[/PHP]

Shove that into a empty file. Name the file something.html and double click on it.

---

### Post by ghostdog74 on 2008-02-10
how about awk too ? Its a language on its own, interpreted as well.
```

# awk 'BEGIN{print "hello world"}'
hello world

```
awk script
```

#!/usr/bin/awk -f
BEGIN{print "hello word"}

```

---

### Post by LaRoza on 2008-02-10
That is a very bad way to use ECMAScript, so I won't do that.

There are JavaScript (and JScript) interpreters, if anyone can post a good one for Ubuntu, I will consider adding.

---

### Post by LaRoza on 2008-02-10
> **ghostdog74 said:**
> how about awk too ? Its a language on its own, interpreted as well.
```

# awk 'BEGIN{print "hello world"}'
hello world

```
awk script
```

#!/usr/bin/awk -f
BEGIN{print "hello word"}

```

Interesting, but then I would be doing one for dc, bash, dash, etc.

(etc isn't a language.)

I don't think awk is used that way, perhaps you can do one for sed and awk? (A different thread)

---

### Post by ghostdog74 on 2008-02-10
> **LaRoza said:**
> 
I don't think awk is used that way,
you have to know it to [believe it.]("http://doc.cat-v.org/henry_spencer/amazing_awk_assembler/") :). Also, if Perl is considered here, then its "father" awk should be too. :)

---

### Post by LaRoza on 2008-02-10
> **ghostdog74 said:**
> you have to know it to [believe it.]("http://doc.cat-v.org/henry_spencer/amazing_awk_assembler/") :). Also, if Perl is considered here, then its "father" awk should be too. :)

Sorry, I see it now.

But it seems more specific in use than the ones here. Perhaps you could write one for such tools? I think I am going over my original intent by having shell scripting and C.

"FAQ: The other scripting languages"

---

### Post by ghostdog74 on 2008-02-10
doesn't matter :). shell scripting (with *nix tools ) will suffice.

---

### Post by RIchard James13 on 2008-02-10
> **LaRoza said:**
> That is a very bad way to use ECMAScript, so I won't do that.

Yeah it is an ugly hack to write the document using javascript. You could use an alert to pop-up Hello World, but most uses of javascript are different. If you take javascript out of the browser it fails to have much meaning. Kinda like taking awk out of the shell. Maybe some Java interpreter might be better.

---

### Post by RIchard James13 on 2008-02-10
"SpiderMonkey is a standalone JavaScript/ECMAScript interpreter"

sudo apt-get install spidermonkey-bin

[PHP]#!/usr/bin/smjs

print ("Hello World");
[/PHP]

---

### Post by LaRoza on 2008-02-10
> **RIchard James13 said:**
> "SpiderMonkey is a standalone JavaScript/ECMAScript interpreter"

sudo apt-get install spidermonkey-bin

[PHP]#!/usr/bin/smjs

print ("Hello World");
[/PHP]

Just what I was looking for :) Thanks.

---

### Post by lnostdal on 2008-02-10
Common Lisp using the CLISP implementation .. i'll post another post for SBCL later if i'm not too lazy

```

lars@ibmr52:~/programming/lisp/clisp$ cat script.lisp
#!/usr/bin/env clisp

;; http://clisp.cons.org/impnotes.html#quickstart-unix

(defun mkstr (&rest args)
  (with-output-to-string (s)
    (dolist (a args) (princ a s))))

(defun main ()
  (princ
   (mkstr "*load-truename*: " *load-truename* #\Newline
          "*load-pathname*: " *load-pathname* #\Newline
          "ext:*args*: " ext:*args* #\Newline))

  (princ "Type in your name: ")
  (format t "Your name was ~A~%" (read-line)))

(main)

lars@ibmr52:~/programming/lisp/clisp$ chmod +x script.lisp
lars@ibmr52:~/programming/lisp/clisp$ ./script.lisp this is the arguments
*load-truename*: /home/lars/programming/lisp/clisp/script.lisp
*load-pathname*: script.lisp
ext:*args*: (this is the arguments)
Type in your name: Lars
Your name was Lars
lars@ibmr52:~/programming/lisp/clisp$ 

```

---

### Post by lnostdal on 2008-02-10
ok, for Common Lisp using the SBCL implementation: 
[http://www.sbcl.org/manual/Unix_002dstyle-Command-Line-Protocol.html](http://www.sbcl.org/manual/Unix_002dstyle-Command-Line-Protocol.html)

*~/.sbclrc* is a suitable place to put the initialization code mentioned in that writing btw.

to get hold of the command line arguments you can use *sb-ext:*posix-argv** in the same way as shown in the CLISP example above

---

### Post by mridkash on 2008-02-10
Anything about Actionscript?
Can I run it (or compile it) in some way on ubuntu. of-course without using wine.

---

### Post by LaRoza on 2008-02-10
> **mridkash said:**
> Anything about Actionscript?
Can I run it (or compile it) in some way on ubuntu. of-course without using wine.

ActionScript is based on the ECMAScript specification for Flash.

---

### Post by pmasiar on 2008-02-10
maybe you should define what "scripting" is and how it is different from "programming", if any.

Also, how "scripting" is related to dynamically typed, late binding languages? Is List "scripting" language? Why or why not? Why C is and why not Java? Is there different areas where different scripting language is more appropriate?

Also, printing "hello world" is such a trivial example that it hardly shows any real usage of the language. "99 bottles of beer" is IMHO much better example of language expressiveness. And you don't have to write that all, just link to good resources on the web.

IMHO, of course, YMMV. Any FAQ is better than no at all.

---

### Post by scruff on 2008-02-10
I've been seeing a lot of nice FAQ's for beginners popping up in my Google reader as I subscribe to this forums RSS feed. 

I was just curious - are these going to become stickies? I think that would be awesome. Anyone who follows this forum knows that "search" is rarely used by absolute beginners asking which IDE or language to use ;)

---

### Post by LaRoza on 2008-02-10
> **pmasiar said:**
> maybe you should define what "scripting" is and how it is different from "programming", if any.

Also, how "scripting" is related to dynamically typed, late binding languages? Is List "scripting" language? Why or why not? Why C is and why not Java? Is there different areas where different scripting language is more appropriate?

Also, printing "hello world" is such a trivial example that it hardly shows any real usage of the language. "99 bottles of beer" is IMHO much better example of language expressiveness. And you don't have to write that all, just link to good resources on the web.


This isn't meant to show how to use the language, but how to get it working. Defining "scripting" is difficult, and I trust non experts to use this FAQ, and they will not care about such distinctions.

Good idea, I will link to the 99 page for each language, so they can see what code looks like.

---

### Post by LaRoza on 2008-02-10
> **scruff said:**
> I've been seeing a lot of nice FAQ's for beginners popping up in my Google reader as I subscribe to this forums RSS feed. 

I was just curious - are these going to become stickies? I think that would be awesome. Anyone who follows this forum knows that "search" is rarely used by absolute beginners asking which IDE or language to use ;)

A sticky will link to them.

---

### Post by reed026 on 2008-02-26
LaRoza, you may want to update the cli command to the following
# sudo aptitude install php5-cli
from 
# sudo aptitude install php-cli

---

### Post by pedro_orange on 2008-02-26
GJ on all these informative posts LaRoza. Way to go saving time!

---

### Post by Verminox on 2008-05-17
> **LaRoza said:**
> There are JavaScript (and JScript) interpreters, if anyone can post a good one for Ubuntu, I will consider adding.

```
sudo apt-get install rhino
```

I'm currently using Rhino to embed JavaScript into my Java application. Me likes. No, loves. :)

---

### Post by sephiroth124 on 2008-09-18
i'm guessing i'm pretty screwed being a vb6 programer just starting to delve into linux programing. the only language i see posted i have experiance in is php. any tips on how to start in C or C++ ,  like where to find editors and compilers for one of the two?

---

### Post by scruff on 2008-09-18
sephiroth124 - by all means, learn C and C++ if you want, but if you're a VB guy already you'll get up to speed and accomplish a lot more if you start with something like Python or Perl. Python being my first choice, though I come from more of a Perl background...

Check out [Dive Into Python]("http://diveintopython.org/"): free book to get you started. LaRoza has a wiki somewhere in his sig that has a bunch of info also.

Python is pre-installed on all Linux distros and any editor will work. I use VIM. Kate, & Gedit are nice GUI based editors if you aren't into VIM.

---

### Post by sephiroth124 on 2008-09-18
well i'm not sure about python but i know that a hacker freind of mine told me i'd never end up using perl so if i might acomplish more with python i think i'll go for it the thing is how do i compile my programs to distrubute them and can they be compiled for windows users? on occasion i do have my friends test things for bugs and most if not all of them use windows .... the reason i wanted to go with C or C++ was cause i've used a C++ editor on windows just never got the hang of it so i know with the source and a compiler any of my windows friends can run the programs. for now i'm gonna learn a bit of python while i wait on another reply and hope you can answer my questions

---

### Post by scruff on 2008-09-18
Well I'm not sure what your buddy is talking about regarding Perl, but...

You don't compile Python programs. Its an interpreted language, meaning you write the code and run it, and the Python interpreter handles the rest. Python (interpreter, libraries, etc) can be installed on any platform including Windows so your code can be run on any platform if you are so inclined to make the effort (some system level stuff requires slightly diff approach on diff platforms). 

Spend a couple hours playing around in Python and I'm sure many of your questions will become clear on their own. You'll also learn enough to write useful code in that amount of time :)

---

### Post by kknd on 2008-09-18
Lua

[PHP]
#! /usr/bin/env lua

print("Hello World!")
[/PHP]

---

### Post by pmasiar on 2008-09-18
> **sephiroth124 said:**
> how do i compile my [Python] programs to distrubute them and can they be compiled for windows users? 

Python **is** compiled (automagically when you try to run code which was not compiled yet, or changed after compiled) into .pyc files, and you can distribute those if you want to, but there are tools to restore sources (comments are lost of course).

Instead of compiling Python for every platform, you install platform support (once) and then run your code. 

Use download Python installer from ActiveState.com (standard windowsy installer, download and click 5 times), it is better than python.org version: it also sets environment variables (it is documented in readme, but why not let installer to do it 8-) )

See wiki in my sig for links to free books and training tasks.

---

### Post by Kadrus on 2008-09-18
Just saw this thread,and I wanted to add Objective CAML to the languages,as it can be used as a scripting language as well.
[Ocaml Script]("http://martin.jambon.free.fr/ocamlscript.html")
```

#! /usr/bin/env ocamlscript
 ...code...

```

---

### Post by sephiroth124 on 2008-09-18
i'll have to remember where to find the python installer incase a freind decides i've created somthing useful and they want to use it (perhaps i should recreate my hacker freinds rynOS lol ) but right now i'm running linux and all i really need for linux is a decent ide or editor. i tried installing the sugested VIM ( someone in the thread sugested it i'm sure ) and i can't find it to run the thing so i'm downloading somthing called eclipse witch is supposed to have a plugin achetecture for the support of multiple languages witch for me would be quite useful as i wouldn't have to change programs to change languages i could just change the language setting. so hopefully this will be the last time you hear from me for a while

---

### Post by LaRoza on 2008-09-18
> **sephiroth124 said:**
> i'll have to remember where to find the python installer incase a freind decides i've created somthing useful and they want to use it (perhaps i should recreate my hacker freinds rynOS lol ) but right now i'm running linux and all i really need for linux is a decent ide or editor.
It isn't hard. Google "Python installer", however I recommend the activePython version (see pmasiar's sig and wiki if you ever forget where to get it. My wiki also has the link).

> 
i tried installing the sugested VIM ( someone in the thread sugested it i'm sure ) and i can't find it to run the thing so i'm downloading somthing called eclipse witch is supposed to have a plugin achetecture for the support of multiple languages witch for me would be quite useful as i wouldn't have to change programs to change languages i could just change the language setting. so hopefully this will be the last time you hear from me for a while

Vim is a command line editor ;) 

If you want a good editor for Python with lots of plugins but no bloat, just use gedit and its plugins. Gedit is called "text editor" in the menu.

---

### Post by sephiroth124 on 2008-09-18
so to start vim i need to run it from the terminal right? i think i'll just stick to C and C++ cause i have an editor i should be able to use ( its the C/C++ version of eclipse ) the problem is in vb usually when you start a new project it creates a file for the form and right clicking it opens up a code file for it but in C/C++ it doesn't do that so i'm confused as to where to start...... i like this community your all generaly pretty helpful i wish i had saught after help when my video card didn't want to work properly ( its working now after playing with settings for a bit and turning on the driver ) i could've solved that issue in minutes rather than days if i could've seen the page to post

---

### Post by LaRoza on 2008-09-18
> **sephiroth124 said:**
> so to start vim i need to run it from the terminal right?
You don't just start it in the terminal, it runs there ;) It is the best editor.

> 
i think i'll just stick to C and C++ cause i have an editor i should be able to use ( its the C/C++ version of eclipse ) the problem is in vb usually when you start a new project it creates a file for the form and right clicking it opens up a code file for it but in C/C++ it doesn't do that so i'm confused as to where to start......
Learn how to write C and C++ then. ;)

---

### Post by sephiroth124 on 2008-09-18
the question i need answered to really delve into it is after i start a project do i add a source file to it or is there somthing else i need to add to it ? ( C/C++ )

---

### Post by pmasiar on 2008-09-18
> **sephiroth124 said:**
> the question i need answered to really delve into it is after i start a project do i add a source file to it or is there somthing else i need to add to it ? ( C/C++ )

And you think that best place to ask it is to hijack FAQ thread about scripting languages? How very thoughtful of you :-)

---

### Post by LaRoza on 2008-09-18
> **sephiroth124 said:**
> the question i need answered to really delve into it is after i start a project do i add a source file to it or is there somthing else i need to add to it ? ( C/C++ )

A few issues, this is a FAQ about scripting languages, so you should start your own thread.

Also, you might want to try to write more grammatically correct sentences and use punctuation and proper capitalisation. I really can't tell what you are saying.

What do you mean by "project"? Is this in project as a concept, ie, the sysres project. A project as a version control point of view (adding a file to a project needs to be done explicitly) or an IDE issue?

And which language? C or C++? 

These are all points to keep in mind when you make your own thread.

---

### Post by pmasiar on 2008-09-19
+1. Before providing answers, read "how to ask questions" in my sig 8-)

---

### Post by YourSurrogateGod on 2008-09-30
Anyone know of a good Perl book? I have Oreilly's Programming Perl 3rd Edition. It seems to be good, but when I started out reading it, got a problem on something and posted it here, someone was quick to point out that I wasn't using use strict and use warnings in Perl. Now I'm beginning to have doubts as to whether this is a book that does a good job of teaching you from the start on how to become a good Perl programmer.

---

### Post by slavik on 2008-10-01
the book is good, the use strict; use warnings; is more of a good style, but the book teaches Perl well.

---

### Post by LaRoza on 2008-10-01
> **slavik said:**
> the book is good, the use strict; use warnings; is more of a good style, but the book teaches Perl well.

So, you see a book which forsakes good style from the beginning as good at teaching Perl? The rumours are true...

Good style, IMO, should be taught first, in any language.

---

### Post by YourSurrogateGod on 2008-10-02
> **slavik said:**
> the book is good, the use strict; use warnings; is more of a good style, but the book teaches Perl well.

The reason why I ask is because if it teaches you less than good programming style and gets you to become careless at times, it can give you nasty surprises. I didn't want to go down a wrong route at the outset.

---

### Post by karlmp on 2009-08-20
**m4**

[PHP]define(`yoo',`Hello World!')
I say this: yoo[/PHP]


Put this line into a file, called hwm4 and run it with m4:

```
m4 hwm4

I say this: Hello World!

```

---

### Post by Mirge on 2009-08-20
Hurray for thread necromancing

---

### Post by karlmp on 2009-08-21
> **Mirge said:**
> Hurray for thread necromancing

this thread is in the stickies

---

### Post by nvteighen on 2009-08-22
Hm... what I don't get is what that post is supposed to mean...

---

### Post by Aikar on 2011-03-05
> **LaRoza said:**
> That is a very bad way to use ECMAScript, so I won't do that.

There are JavaScript (and JScript) interpreters, if anyone can post a good one for Ubuntu, I will consider adding.
There is one now.
Node.JS
Instructions (note: DO NOT USE APT-GET! The package on apt is very old and not the latest stable... compile from source.):
```

apt-get install build-essential git-core libssl-dev
mkdir -P ~/local/src/node
cd ~/local/src/node
git clone [EMAIL="git@github.com:joyent/"]git@github.com:joyent/[/EMAIL]node.git .
./configure
#replace 4 with # of CPU cores you have.
JOBS=4 make
sudo make install

```then 'node'

example: server.js
```

#!/usr/bin/env node
var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(8124, "127.0.0.1");
console.log('Server running at [http://127.0.0.1:8124/](http://127.0.0.1:8124/)');

```then 
```

node server.js
#or
./server.js

```
and open browser to [http://127.0.0.1:8124/](http://127.0.0.1:8124/)

---


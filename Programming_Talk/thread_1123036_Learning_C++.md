---
title: "Learning C++"
date: 2009-04-11
forum: Programming Talk
---

### Post by Qwertylol on 2009-04-11
[COLOR="Black"]OK so I'm sure this gets asked a thousand million times: but I really want to learn C++. I know JavaScript very well (the only thing they have in common is the syntax but it's a start).

Basically I want to make my own very very basic programming language (I know this may seam too advanced and pointless) to display web pages. I do not want to use the languages like PHP, rather I want to make my own (more fun!). It will be simple: playing variables against each other, language construct functions and including files, with its own basic syntax. No object inheritance, classes or prototypes- probably not even a switch statment. so like (just random example):

[PHP]
$allowed_pages = (array) array("index","page");
    if(isset($_GET['page'] && in_array($_GET['page']))){
        include $_GET['page'] . ".txt";
    }
else{
    echo "no page specified";
}
}

// will go to something like

$allowed_pages:array = "index":string , "page":string ;

if((get $page).inArray($allowed_pages)){ // hmm this is a 
prototype but w.e
    paste file get $page;
}
else{
    print "no page specified";
}
[/PHP]

I know this is very insecure, languages like PHP and the like are very good but it's for the education and hobby (bored of using programming languages).

I know nothing about C++ but going to Uni next year (though not doing computer science) I can choose up to 50 credits in computing modules (I'd rather not "waste" those modules on something irrelevant to my degree though) so I can learn there. 

what's the best compiler to use? what's the difference between C++ for windows/linux? to do with code libraries? I haven't a clue!

I know something like this is way out of the league of a beginner: but this is my goal so I want to learn what is relevant for me to do this. That's why I posted a new topic rather than looking at the millions posted on the web!

Thanks if you can help!

also I can't afford books until September when I get my student loan so online resources will be better right now - but if you know a good book by all means recommend it !
[/COLOR]

---

### Post by slavik on 2009-04-11
You need much more knowledge of C++ than you have in order to do something like this. Sorry, but you will have to wait until you know more.

---

### Post by Qwertylol on 2009-04-11
> **slavik said:**
> You need much more knowledge of C++ than you have in order to do something like this. Sorry, but you will have to wait until you know more.Yea man, it's a big task! I just want some advice as to the best things to focus on learning to do this. I defiantly don't plan on being able to do this even in the next 12 months!

Right now I'm working my way through Thinking in C++, anything else to read?

---

### Post by samjh on 2009-04-11
> **Qwertylol said:**
> Right now I'm working my way through Thinking in C++, anything else to read?

Good.

After that, you should probably look at [Programming Language Pragmatics, 2nd ed.](http://www.amazon.com/Programming-Language-Pragmatics-Second-Michael/dp/0126339511/ref=sr_1_3?ie=UTF8&s=books&qid=1239496608&sr=1-3)

> what's the best compiler to use? what's the difference between C++ for windows/linux? to do with code libraries? I haven't a clue!On Linux, the usual compiler for C++ is g++.  Install it (and other essential build tools) with:
```
sudo apt-get install build-essential
```
Focus first on standard C++ libraries.

There are many differences between Windows and Linux, which are not yet relevant at your stage of study.

---

### Post by Xender1 on 2009-04-11
also, coding c++ on linux it is nice to use an IDE. such as eclipse or netbeans. fool around with both to see which you like, personally i prefer netbeans (with g++ compiler)

---

### Post by samjh on 2009-04-11
> **Xender1 said:**
> also, coding c++ on linux it is nice to use an IDE. such as eclipse or netbeans. fool around with both to see which you like, personally i prefer netbeans (with g++ compiler)

At this stage of his learning, he would be better served using a simple text editor like Gedit, and compiling via the command-line.

---

### Post by Peasantoid on 2009-04-12
I've created all manner of toy programming languages, but designing one that's actually *useful* is a **huge** undertaking. You'll need to implement:

* A tokenizer : Converts text into "tokens" the interpreter can understand
* ... : Any number of intermediate steps. Generally not necessary for a simple language.
* An interpreter : Reads in the tokens and does stuff with them.

It's best to try this with a scripting language such as Python and then repeat the process a few times. That'll teach you the fundamentals.

---

### Post by defaultusername on 2009-04-12
Read "The C++ Programming Language" by its creator, Bjorn Stroustrup. That should teach you a thing or two without too much fluff. IIRC it also offers exercises that help solidify the concepts behind C++.

Interpreters aren't that hard to write, but it involves more programming theory than you'd want to deal with while learning C++. If there's one thing I've learned in my time, it's to avoid being too ambitious and getting nothing at all done in the end. However, if you still wish to undertake that project ...

[http://en.wikipedia.org/wiki/Interpreter_(computer_software](http://en.wikipedia.org/wiki/Interpreter_(computer_software))
[http://en.wikipedia.org/wiki/Lisp_(programming_language](http://en.wikipedia.org/wiki/Lisp_(programming_language))

A popular long-standing challenge presented to beginner/intermediate programmers involves writing a LISP interpreter. That should keep you occupied for some time.

---

### Post by mmix on 2009-04-12
IMHO, your basic programming language similar like perl.

---

### Post by Jiraiya_sama on 2009-04-12
I started and am still learning C++ from "C++ Primer 4th ed."

---

### Post by Fixel on 2009-04-12
Geany is a great text editor, much more sexy than gedit! It compiles and runs the stuff you write, but doesn't have all the overwhelming features that for instance Eclipse or NetBeans has.

Using it to do most of my basic work.

---

### Post by simeon87 on 2009-04-12
While I fully agree with the above comments on the complexity of writing your own compiler/interpreter, the OP doesn't have to implement a very complex language. For example, most esoteric programming languages have a few elements, each representing a particular operation, such as pushing a value on the stack, et cetera. This should be achievable for a beginning programmer.

---

### Post by slavik on 2009-04-12
> **simeon87 said:**
> While I fully agree with the above comments on the complexity of writing your own compiler/interpreter, the OP doesn't have to implement a very complex language. For example, most esoteric programming languages have a few elements, each representing a particular operation, such as pushing a value on the stack, et cetera. This should be achievable for a beginning programmer.
And with this comment, I suggest looking into implementing Brainfuck. [http://en.wikipedia.org/wiki/Brainfuck](http://en.wikipedia.org/wiki/Brainfuck)

The wikipedia page even has some code to test your code with.

---

### Post by nvteighen on 2009-04-12
A besides note, just FYI. If you want to create your own language, you can easily do that with Lisp. Well, actually, Lisp development usually means to create a new language for some problem to solve... :) This languages will  also be Lisp dialects and will share all its propierties.

This is because Lisp is really easy to parse, because of it's constant prefix notation *(proc arg1 arg2 ...)* syntax. Another easy to parse language, but somewhat esoteric, is Forth, which uses postfix notation *3 4 + 5 * 1 - 4 **... which in infix notation is the much "harder" 4 * (1 - 5 * (3 + 4)). Look at Wikipedia for more information... maybe your language could take a Forth-like shape.

But C-like (or ALGOL-like) languages are a pain to parse. I personally have no idea how to do it, but I imagine the syntax tree should really be very complex compared to Lisp's (which actually writes everything in syntax trees...). Don't event mention languages like Perl, where you also have to determine the so-called "contexts" to know what to do with a certain variable...

---


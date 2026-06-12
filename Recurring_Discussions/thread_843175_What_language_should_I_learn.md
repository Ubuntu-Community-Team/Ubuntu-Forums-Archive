---
title: "What language should I learn?"
date: 2008-06-28
forum: Recurring Discussions
---

### Post by Papenco on 2008-06-28
Hello.

I know Pascal, a little C, C++, some Delphi and a bit of Java Programming. I'm looking forward to create applications such as audio players and that type of things. 

Which language should I learn or keep improving?

Thanks.

---

### Post by LoneWolfJack on 2008-06-28
You will find C is widely used in the Linux world. Use Java if you want to have programs running natively on all common platforms (even though C/C++ can do that too, of course).

A C programmer myself, I'd always suggest C of course. Using GTK you can write decent applications (GIMP is using GTK), but if you already know Java, you might want to proceed on that path so you don't have to deal with the "low-levelness" of C.

Now wait for the army of Python programmers singing their song... ;)

---

### Post by neoAnderson on 2008-06-28
Indeed there's lately been a lot of programming talk on the forums these days and I constantly hear people being almost religious about Python (and lately Ruby). 

The following site gives an overview of the most popular languages currently. 

[http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html](http://www.tiobe.com/index.php/content/paperinfo/tpci/index.html)

---

### Post by Papenco on 2008-06-28
Thanks, and by the way, what's Python and all that?
I've heard of it many times, but never asked.

---

### Post by wdaniels on 2008-06-28
I'd suggest either Python or C#. Python is both easy and powerful, with a slightly different syntax to what you're used to if you fancy a change. [Exaile]("http://www.exaile.org/") is a good example of an audio player written in Python.

C# is always a useful language to know, for obvious reasons, and for this you could use [Banshee]("http://banshee-project.org/") as an example.

There are loads of other interesting languages to learn of course, and everyone has their favourites. Personally, I like Python for quick, simple things, C# for anything more strongly 'architected' and PHP for web development.

C/C++ are used for most of the underlying programs in Linux, so they're always good to know for fixing stuff, but since you're already familiar with these, I'd go for something more high-level (it tends to be more fun when you get stuff done faster). I seem to manage to fix the odd driver and most other stuff I need to do with fairly limited C/C++ skills :D

Java has always been a love/hate thing for me personally. In theory it seems like it could be the best of all possible worlds, but in practice I find it to be ugly and troublesome, which is why I use C# in preference despite it's connections to Microsoft. Note that Python is also cross-platform.

---

### Post by Papenco on 2008-06-28
Thanks for all this help.
And now I've made some conclusions, which is a good Python-learning web page or a Python/Programming forum?

---

### Post by LoneWolfJack on 2008-06-28
It's a programming language without curly braces... do I have to say more? ;)
Consider Perl without said braces and instead of figuring out cryptic commands, you spend more time counting whitespace than programming. ;-)

Seriously, people claim that Python is a good beginners language and that it comes with a lot of bindings. From my perspective, it is not a good beginners language because of the weird notation. Also, again, personally, I wouldn't want to waste time learning a programming language that has no special purpose and end up having to learn another programming language to do things right.

Yet Ubuntu's internals are largely written in Python so you can expect many developers around here using it,

---

### Post by wdaniels on 2008-06-28
> **LoneWolfJack said:**
> I wouldn't want to waste time learning a programming language that has no special purpose and end up having to learn another programming language to do things right.

Yet Ubuntu's internals are largely written in Python so you can expect many developers around here using it,

Having lots of bindings and lots of examples is more important than a funny notation. I like learning languages with a funny notation, it's more interesting. Who has ever "had to" learn another programming language to "do things right"? Python has it's limitations just the same as any language, but unless you want to write a kernel module or a high-performance decoder or something, none so bad that you would have to go and learn a different language! :D :D

As always, it's horses for courses and so far as learning to program goes, it has more to do with learning all the relevant libraries than any particular language syntax; you will learn almost as much about the design and functionality of GTK or GStreamer (for example) whether you use them through the Python bindings or the native C APIs.

---

### Post by Papenco on 2008-06-28
Ok, I'm gonna learn Python, which compiler should I use?

---

### Post by wdaniels on 2008-06-28
> **Papenco said:**
> Ok, I'm gonna learn Python, which compiler should I use?

You don't need to worry about compiling - you just run it interpreted and it will automatically compile the bytecode (and save it) as you go. The only time you may need to do it manually is for deployment, because the program will normally be deployed in a location where the interpreter (running as a standard user) will not normally be able to write to the install location. But packaging is another matter entirely that can get quite complicated, so you should worry more about writing your programs first!

The 'standard' reference implementation of Python is known as CPython and I recommend you stick with that - don't worry about the various alternatives like IronPython (for Mono/.NET) and Jython (for Java) - there's no reason for you to get involved with those when getting started (or probably ever).

---

### Post by spirit2 on 2008-06-28
[http://www.diveintopython.org/toc/index.html](http://www.diveintopython.org/toc/index.html)

---

### Post by lisati on 2008-06-28
> **spirit2 said:**
> [http://www.diveintopython.org/toc/index.html](http://www.diveintopython.org/toc/index.html)
Contrary to what the site says, SOME Windows machines come with a version of Python preinstalled - my Compaq (HP) machine did, but I've never used it in the 3 years I've had the machine.

---

### Post by stokedfish on 2008-06-28
Japanese.

Coz it's sexy.

---

### Post by LaRoza on 2008-06-28
> **lisati said:**
> Contrary to what the site says, SOME Windows machines come with a version of Python preinstalled - my Compaq (HP) machine did, but I've never used it in the 3 years I've had the machine.

HP and Compaqs come with it, but I still recommend using the ActivPython installer.

---

### Post by Diabolis on 2008-06-28
An example of a music player written in Java would be [Jajuk]("http://www.jajuk.info/index.php/Main_Page").

---

### Post by pmasiar on 2008-06-28
on windows, use ActiveState Python (comes with IDE called IDLE). On Linux, it is already installed, pick your editor.

Every time someone mentions Python's 'significant whitespace' as a problem, I feel sorry for the guy/gal: Python is just language where proper indent structure **is** syntax structure, no more and no less. If you do not want to indent your code, I don't want to read it, ever, sorry.

Big difference between Python and static languages (C/C++/Java etc) is not indent, but dynamic typing, which many blub programmers cannot appreciate (by definition, [blub programmer](http://www.paulgraham.com/avg.html) cannot appreciate features of more advanced language which s/he does not grok).

---

### Post by Can+~ on 2008-06-28
> **Papenco said:**
> Ok, I'm gonna learn Python, which compiler should I use?

It's interpreted.

Ubuntu/MacOS/Some_Linux_Distros:
```
python myfile.py
```

Windows:
-Download [interpreter](http://www.python.org/download/)
-I think double clicking, but I'm not sure if this compiles or just executes, some windows guy can confirm ?

---

### Post by LaRoza on 2008-06-28
> **Can+~ said:**
> It's interpreted.

Ubuntu/MacOS/Some_Linux_Distros:
```
python myfile.py
```

Windows:
-Download [interpreter](http://www.python.org/download/)
-I think double clicking, but I'm not sure if this compiles or just executes, some windows guy can confirm ?

If the file extension is associated with the Python interpreter, yes it will. (Not all people who use Windows are guys)

For GUI apps in Windows, use the .pyw extension so you don't get the terminal window.

On Linux, if the file has the shebang line and is marked executable you can run it like any other program.

---

### Post by nvteighen on 2008-06-28
> **pmasiar said:**
> 
Every time someone mentions Python's 'significant whitespace' as a problem, I feel sorry for the guy/gal: Python is just language where proper indent structure **is** syntax structure, no more and no less. If you do not want to indent your code, I don't want to read it, ever, sorry.

A thought: Why do we C/C++ people never complain on significant whitespace in Makefiles? Ah, but Python is evil for having it...

I'm full of these irrelevant discussions; and I try to avoid them as much as I can. It's more senseful to discuss and value programming languages from their features, libraries, portability, goals, etc. If someone said "I don't like Python because its standard library has this x, y, z problems" or "I don't like it because it's inconsistent in this point", I'd really respect that as a technical point of view and as an attempt to see things in a more serious way, even if that opinion is proven to be wrong.

A bit of common sense, please!

---

### Post by Can+~ on 2008-06-28
> **LaRoza said:**
> If the file extension is associated with the Python interpreter, yes it will. (Not all people who use Windows are guys)


Sorry.

"Windows humans or borgs"

Fixed. :KS

---

### Post by CptPicard on 2008-06-28
> **pmasiar said:**
> 
Every time someone mentions Python's 'significant whitespace' as a problem, I feel sorry for the guy/gal:

But... but... I still dislike the significant whitespace, although I otherwise have mostly come around to Python in parts I didn't initially "get" :(

The "use tools" argument sounds slightly hypocritical, because even Java becomes tolerable with the use of (huge) tools, and there the need for tools seems to be an negative...

Significant syntactical elements should be visible and language should essentially be a stream of characters. The one biggest, hugest issue with significant whitespace is that each line actually contains global structural information in the form of a *global* amount of whitespace preceding other elements. So when you cut and paste and mangle your code, the local block structure is not explicit enough and global structure is always carried with it until you fix it, and you better get it right. In other languages you can just hit the equivalent to Emacs M-q to "make it look nice".

---

### Post by LoneWolfJack on 2008-06-28
> Every time someone mentions Python's 'significant whitespace' as a problem, I feel sorry for the guy/gal: Python is just language where proper indent structure **is** syntax structure, no more and no less. If you do not want to indent your code, I don't want to read it, ever, sorry.

You know, I won't fall for this flamebait. In fact, I believe that everyone who is reading this stuff will ask him or herself "if he is so religious about python, what shortcomings are there he doesn't want to tell me about?".

Indicating that my programs are not structured enough because I don't use Python simply makes me laugh.

In fact, your Python-preference mixed with personal attacks against people who don't like it probably qualify you for this "blub programmer" thing you have been referring to.

---

### Post by CptPicard on 2008-06-28
Frankly, to me the aggression and name-calling against high-level-language advocates just shows that the blub programmers who pride themselves on knowing nothing but C or Java and not ever planning on using anything else just lash out because they don't like facing up to their own limitations and incompetence and lack of experience. It's nice to imagine you're leet and know something, until someone suggests you actually don't -- and that worse yet, all that "manual labour" you are putting into your low-level coding is actually mostly useless, and that you can't expect to be particularly revered for doing ... jus that.

Nothing new there really. One would be well served to remember that being a geek is all about learning stuff as you go, all the way from cradle to grave.

---

### Post by pmasiar on 2008-06-28
> **LoneWolfJack said:**
> Indicating that my programs are not structured enough because I don't use Python simply makes me laugh.

If you are used for code to have correct indent structure, why it is a problem if Python requires what you do anyway?

---

### Post by LoneWolfJack on 2008-06-28
Because I am not going to be forced to use a indent style that tries to make things as hard to read as possible while you keep counting whitespaces.

You seriously call this readable?
```

a = ['cat', 'window', 'defenestrate']
for x in a:
    print x, len(x)

print "\n"

for x in a[:]:
    if len(x) > 6: a.insert(0, x)
print a

print "\n"

for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
	    print n, 'equals', x, '*', n/x
            break
    else:
        print n, 'is a prime number'

print "\n"

def fib(n):
    a, b = 0, 1
    while b < n:
        print b,
        a, b = b, a+b
fib(2000)

```

All taken from the official documentation. Setting up the blocks alone takes 78 whitespaces.

You can program Python to your heart's content, no problem. But don't claim it being superior because of its indent style, which actually is a mess and not that far away from Perl as claimed. It's not easier to learn as PHP or Ruby as well. Also, considering its pretty unique indent style, I would dare to claim that people who just know Python will have a harder time learning other languages as the bulk of them is related to C in style.

And no, I did not just copy and paste that stuff. Being a C programmer, not a language evangelist, it doesn't take much for me to learn a new language.

Also, I don't mind high-level programming languages at all. Compare above code to the "pythonized" PHP code:

```

$a = array('cat','window','defenestrate');
foreach($a as $x)
	{echo $x.' '.strlen($x)."\n";}

echo "\n";

foreach($a as $val)
	{
	if(strlen($val)>6)
		{array_unshift($a,$val);}
	}

print_r($a);

echo "\n";

foreach(range(2,9) as $n)
	{
	$a = '';
	foreach(range(2,$n) as $x)
		{
		if($x==$n)
			{continue;}

		if($n%$x == 0)
			{
			$a = "$n equals $x * ".($n/$x)."\n";
			break;
			}
		}

	if(strlen($a))
		{echo $a;}
	else
		{echo "$n is a prime number\n";}	
	}

echo "\n";

```

---

### Post by LaRoza on 2008-06-28
> **LoneWolfJack said:**
> Because I am not going to be forced to use a indent style that tries to make things as hard to read as possible while you keep counting whitespaces.

Counting? I never had to count, tab key works wonders...

> 
You seriously call this readable?


Well, the syntax is, although the code itself isn't the most explicit, but then again, that code wouldn't be any more clear with another syntax.

I don't get the problem with the whitespace. You don't have to think about it, it is what you probably do anyway, and it just means you don't have to type extra characters. No big deal here...

---

### Post by rlameiro on 2008-06-28
Well, I am in no means a expert programmer. Just a hobby coder that started to program for pc about a month ago. I am learning python, but let me say to you that I prefer the python example over the PHP one. Why? It is clean. clear and with logic. why do you need to have this"{  }" if you can indent your function? Less characters are easy to read. I am a professional(at least I think :))classic musician and to read an ugly score full of unnecessary information slows down your response, even if it is for your help.
About this matter I think this flamewares are so lame... Everyone that are pro coders flame other languages instead of learn more thing ... I feel that the people just loose precious time talking bad things about other languages for purely personal reasons. 
People when you think that read python is harder to read than C or even PHP... well maybe never programed in assembly....lol When I studied electronics one of myfinal exams (digital systems) ad a problem: multiply a thing in the register XY with the thing in XX and put the result in YX- I cannot recall for sure but I think I needed something like 8-10 code lines to do a multiplication. LLOLL WAKE UP Hi level langs are good for most the things...  I made a simple hardware control via serial port software, with python in 3 days!!! of course it is not yeat fully tested or bug free but I just started to program a month ago... and before knew Assembly for microcontrollers....

Well continue withe flame war:lolflag:

---

### Post by LoneWolfJack on 2008-06-29
Let me repeat this again: I am NOT saying "don't learn Python". I am saying "stop claiming Python is superior".

There are many fascinating languages around. If Python fits your needs and your way of thinking, go with it. 

Yet looking at it as someone who understands probably more than a dozen programming languages (of course, there are only two that I have mastered to a very high degree, but you knew that, right?) and knows several different indent styles, I feel I can claim that the ones based on C are the most readable.

Also, like I said before, there's nothing Python can do that another language couldn't do better. Python is like Perl without braces probably sums it up pretty well. If I am wrong here name the one thing that Python can do best. 

No bashing there, absolutely not. I suppose that many of the little games in the repos are written in Python and I happily use them; the more programmers there are, the more free applications get made, which is a good thing. Even if they insist on programming them in Python.

As for the whitespaces... finally got Python to accept tabs if I set them to the equivalent of 4 whitespaces... interesting.

---

### Post by pmasiar on 2008-06-29
You do not need to count whitespace - just align them 'by eye' - start each line **of the same block** at the same position. So you can do ie:

[php]
def fib(n):
  # only 2 spaces for this block
  a, b = 0, 1
  while b < n:
        # 6 more spaces for this block
        print b,
        a, b = b, a+b
[/php]

etc. same block starts in same column, that's all. Exactly like your PHP example. I am in complete loss why this is a problem, sorry.

And most editors (above pico I guess) will do smart syntax-aware indent for you - and if your editor does not, get another better, they are all free.

---

### Post by LaRoza on 2008-06-29
> **LoneWolfJack said:**
> Let me repeat this again: I am NOT saying "don't learn Python". I am saying "stop claiming Python is superior".
[quote]

No one says that, just that it is good as a first language and good as a multipurpose language.


[quote]
Yet looking at it as someone who understands probably more than a dozen programming languages (of course, there are only two that I have mastered to a very high degree, but you knew that, right?) and knows several different indent styles, I feel I can claim that the ones based on C are the most readable.


To you, because you are used to them. Someone who uses Lisp mostly (there are people like that) find such languages messy and hard to read.

---

### Post by ghostdog74 on 2008-06-29
> **LoneWolfJack said:**
> 
As for the whitespaces... finally got Python to accept tabs if I set them to the equivalent of 4 whitespaces... interesting.
its usually recommended not to use tabs, but manually type in 4 spaces. However, you can use 1 space too if you don't like extra work
```

def fib(n):
 a, b = 0, 1
 while b < n:
  print b,
  a, b = b, a+b  

```

---

### Post by pmasiar on 2008-06-29
> **LoneWolfJack said:**
> Let me repeat this again: I am NOT saying "don't learn Python". I am saying "stop claiming Python is superior".

But I never did. Everybody who knows me knows very well that the most superior language of them all IMHO is Forth :-)

I just keep repeating that Python:
- is best first language for any beginner
- might be the only language needed for non-professional programmer, like a scientist
- is substantially more productive (for me and many others) than any statically typed language, 
- fast enough that I would gladly burn some CPU cycles for dynamic type checking
- easier to read than other competing dynamically typed languages like Perl, PHP, Ruby (that includes Python culture)

C is faster. Java/C# is more widely used, sadly, etc etc. What is your definition of 'superior'?

> Yet looking at it as someone who understands probably more than a dozen programming languages 

Me too :-)

> I feel I can claim that the ones based on C are the most readable.

Well I read enough misaligned Perl code not to believe indent - and always reformat other's code. And {} waste lines on my screen :-)

> Also, like I said before, there's nothing Python can do that another language couldn't do better. Python is like Perl without braces probably sums it up pretty well. If I am wrong here name the one thing that Python can do best. 

No, you have to substantiate claim that another language does whatever better :-)

Of course Python has no superior ideas - all dynamic languages are like that. But it is more readable.

Python is first language optimized to communicate between humans, not with computer. Your understanding of needs of human-to-human communication is biased by too many un-natural languages you learned. Python is different than all of them ==> so it is strange ==> so it needs to be rejected. I was trapped in same trap before I embraced Python.

---

### Post by LoneWolfJack on 2008-06-29
> **pmasiar said:**
> But I never did. Everybody who knows me knows very well that the most superior language of them all IMHO is Forth :-)


No wonder you're not missing them braces.

> **pmasiar said:**
> 
I just keep repeating that Python:
- is best first language for any beginner


PHP is exactly as good or bad as a beginner's language as Python.

> **pmasiar said:**
> 
- might be the only language needed for non-professional programmer, like a scientist


Ok. But so is Perl. And with some limitations even PHP.

> **pmasiar said:**
> 
- is substantially more productive (for me and many others) than any statically typed language, 


Which is something it has in common with every high level programming language... that's what they are there for, after all.

> **pmasiar said:**
> 
- fast enough that I would gladly burn some CPU cycles for dynamic type checking


Yup... same goes for PHP. In fact, Debian stats say that PHP is about 5 to 10% faster than Python. Haven't checked myself though.

> **pmasiar said:**
> 
- easier to read than other competing dynamically typed languages like Perl, PHP, Ruby (that includes Python culture)


Perl, ok. Ruby perhaps. PHP? Not a chance.

> **pmasiar said:**
> 
C is faster. Java/C# is more widely used, sadly, etc etc. What is your definition of 'superior'?


What a fascinating question... given some though I'd say it would have to be as fast as Fortran, as powerful as C, as easygoin as PHP and it would have to provide me with the choice of low or high level programing just as I see fitting.


> **pmasiar said:**
> 
Well I read enough misaligned Perl code not to believe indent - and always reformat other's code. And {} waste lines on my screen :-)


You would be surprised how well placed braces make your life so much easier.


> **pmasiar said:**
> 
No, you have to substantiate claim that another language does whatever better :-)


You're the one telling the young impressionable minds (as someone put it) that Python is the way to go. So you tell me why.

> **pmasiar said:**
> 
Of course Python has no superior ideas - all dynamic languages are like that. But it is more readable.


I disagree with the more readable part.

> **pmasiar said:**
> 
Python is first language optimized to communicate between humans, not with computer. Your understanding of needs of human-to-human communication is biased by too many un-natural languages you learned. Python is different than all of them ==> so it is strange ==> so it needs to be rejected. I was trapped in same trap before I embraced Python.

I would really give something for a language that would allow me to build applications as efficient as in C but in much less time. Python can do the latter (so can PHP with GTK), but I'm not dropping the efficiency and ruin my companies reputation.

Sorry for the quotation mess.

---

### Post by LaRoza on 2008-06-29
> **ghostdog74 said:**
> its usually recommended not to use tabs, but manually type in 4 spaces. However, you can use 1 space too if you don't like extra work

Most editors (any editor worth using) lets you set a tab as a set amount of spaces.


> **LoneWolfJack said:**
> 
PHP is exactly as good or bad as a beginner's language as Python.

I wouldn't say that. PHP is almost always used on a server, which makes it "good" for people who already know XHTML and CSS, but using it that way is hard to do well (people keep mixing code and markup...).

> 
You would be surprised how well placed braces make your life so much easier.

They do? The first thing I do when I get code off the forum is to move the braces to how I use them, so I can read the code. I read Python from the get go.


> 
You're the one telling the young impressionable minds (as someone put it) that Python is the way to go. So you tell me why.

He has. If you need stats, check out the sticky. There is a poll which found the people who voted on this forum thought Python was the best place to start (C was second I think).

Also there is a why to Love/Hate Python thread for you to read and find anything new to post (why repost it here?)

> 
I disagree with the more readable part.

C syntax isn't inheritly more readable, you are just used to it (it seems). Lisp programmers find other syntaxes (if that is a word) confusing and messy. 

> 
I would really give something for a language that would allow me to build applications as efficient as in C but in much less time. Python can do the latter (so can PHP with GTK), but I'm not dropping the efficiency and ruin my companies reputation.

Many companies got a good reputation from using such languages. Python, Lisp, Perl etc can be secret weapons against the people who think C++, Java etc are the only way to go. I don't know what your company does though.

---

### Post by pmasiar on 2008-06-29
> **ghostdog74 said:**
> its usually recommended not to use tabs, but manually type in 4 spaces. 

Zillions of free editors let you to set tab as 4 spaces, and replace tabs with spaces. If yours does not, use real editor - they are a dime a dozen. 

Or set editor to replace 8 spaces with tab - the only thing which will screw you is to mix tabs and spaces . Mixing them will emit syntax warning in Py3K.

I never count spaces, use tab=4 and del/backspace at indent level will go -4 spaces in any good programmer's editor. Never had any problems (unless mixed tabs and spaces). SciTE will even show you mixed levels with tabs/spaces as error.

---

### Post by wdaniels on 2008-06-29
> **LoneWolfJack said:**
> Yet looking at it as someone who understands probably more than a dozen programming languages (of course, there are only two that I have mastered to a very high degree, but you knew that, right?) and knows several different indent styles, I feel I can claim that the ones based on C are the most readable.

Let's hope you don't use such ill-reasoned assumptions in your code :p

> **LoneWolfJack said:**
> Also, like I said before, there's nothing Python can do that another language couldn't do better. Python is like Perl without braces probably sums it up pretty well. If I am wrong here name the one thing that Python can do best.

Again, I find your logic both odd and unhelpful. You seem to have assumed that people here are telling the OP that Python is inherently better than other languages, which so far as I can see, nobody has. What has been said is that it could be a good choice for what he/she wants to do.

As with all aspects of life, everybody has their own preferences based things like experience, influences, nature and personal values. And these are constantly weighed in relation to our immediate and long-term goals. Choosing a programming language for a particular project or purpose is no different, so there's not much sense in trying to force your opinion too heavily on people. Merely expressing preferences, (well-)reasoned or not, may be helpful, or not...you never can tell unless you know the OPs mindset pretty well. But you seem to have come to the discussion with the express purpose of dissuading the world from using Python on the flimsy basis that you don't get on with the syntax and can't see any unique benefits.

I think all the points for and against Python have been adequately covered (yet again) in this thread (none of which are highly significant either way in my opinion) so now it's getting personal :D It's funny how whenever this happens, all the participants quietly groan to themselves then proceed to have the flame war anyway...I can't say a lot about that since I'm doing the exact same thing myself, only that it might make for a more interesting discussion on human nature :D :D

---

### Post by ghostdog74 on 2008-06-29
> **pmasiar said:**
> Zillions of free editors let you to set tab as 4 spaces, and replace tabs with spaces. If yours does not, use real editor - they are a dime a dozen. 

seriously, i know about that. which do you prefer, having to change editor settings every time you port code and use different editors, or just sit back and relax and don't have to worry about that?

---

### Post by LaRoza on 2008-06-29
> **ghostdog74 said:**
> seriously, i know about that. which do you prefer, having to change editor settings every time you port code and use different editors, or just sit back and relax and don't have to worry about that?

Well, I am not expert, but I think my editors will remain configured to my liking (just copy the .vimrc, and Gedit and Crimson Editor are already set)

As for projects, I think there will be standards, and if a project is using Python, there is most likely a standard for indenting (four spaces seems to be the "standard" for it)

---

### Post by ghostdog74 on 2008-06-29
> **LaRoza said:**
> Well, I am not expert, but I think my editors will remain configured to my liking (just copy the .vimrc, and Gedit and Crimson Editor are already set)

well, one thing you should understand is, not every environment has the same editors as you. and not every one is a developer.
> 
As for projects, I think there will be standards, and if a project is using Python, there is most likely a standard for indenting (four spaces seems to be the "standard" for it)
like i said, if code is indented 4 spaces (not tabs set to 4 spaces), you don't have to worry about Python code getting messed up in different environment.

---

### Post by pmasiar on 2008-06-29
> **ghostdog74 said:**
> seriously, i know about that. which do you prefer, having to change editor settings every time you port code and use different editors, or just sit back and relax and don't have to worry about that?

I know you know that - I just don't see need to count spaces. Many editors recognize 'Python  mode' and behave sanely.

---

### Post by LaRoza on 2008-06-29
> **ghostdog74 said:**
> one thing you should understand is, not every environment has the same editors as you. and not every one is a developer.

Well, all of **my** environments do :-)

> 
like i said, if code is indented 4 spaces (not tabs set to 4 spaces), you don't have to worry about Python code getting messed up in different environment.
No, I think you misinterpreted what was written. You press tab, but it puts in four spaces as if you typed it.

```

set tabstop=4
set expandtab

```

---

### Post by ghostdog74 on 2008-06-29
> **LaRoza said:**
> Well, all of **my** environments do :-)

No, I think you misinterpreted what was written. You press tab, but it puts in four spaces as if you typed it.

```

set tabstop=4
set expandtab

```

i think you don't get my point, but it doesn't matter. I am going to stop here.

---

### Post by LaRoza on 2008-06-29
> **ghostdog74 said:**
> 
i think you don't get my point, but it doesn't matter. I am going to stop here.

I can't tell if you are saying tabs should be used, or four spaces. If you are saying to use tabs, that is a portable way to code, but can lead to weird looks in other editors. Using four spaces is also portable, and will look consistant, but anyone else adding code will also have to use four spaces.

---

### Post by lisati on 2008-06-29
While looking at a thread that has more to do with gaming than programming, I  remembered a programming language I was once exposed to, "RPG". If memory serves, it stands for "Report Program Generator". I wonder if anyone still uses it!

---

### Post by ghostdog74 on 2008-06-29
> **LaRoza said:**
> I can't tell if you are saying tabs should be used, or four spaces. If you are saying to use tabs, that is a portable way to code, but can lead to weird looks in other editors. Using four spaces is also portable, and will look consistant, but anyone else adding code will also have to use four spaces.
tabs should not be used.  Use 4 spaces, press the space bar 4 times. that's what i meant. you are right. anyone else adding code , especially for developers, would have to follow this 4 spaces (not tabs) standard. this should ensure consistency across other environment.

---

### Post by LaRoza on 2008-06-29
> **ghostdog74 said:**
> tabs should not be used.  Use 4 spaces, press the space bar 4 times. that's what i meant. you are right. anyone else adding code , especially for developers, would have to follow this 4 spaces (not tabs) standard. this should ensure consistency across other environment.

Well, I do the same (odd, we agree :-))

However, I have the tab key set to insert four spaces (not a four space tab) so I use that when I am on my computers.

---

### Post by ghostdog74 on 2008-06-29
> **LaRoza said:**
> Well, I do the same (odd, we agree :-))
:)

> 
However, I have the tab key set to insert four spaces (not a four space tab) so I use that when I am on my computers.

that should be fine. :)

---

### Post by LoneWolfJack on 2008-06-29
> **LaRoza said:**
> 
I wouldn't say that. PHP is almost always used on a server, which makes it "good" for people who already know XHTML and CSS, but using it that way is hard to do well (people keep mixing code and markup...).


I'll have to give you that.

> **LaRoza said:**
> 
They do? The first thing I do when I get code off the forum is to move the braces to how I use them, so I can read the code. I read Python from the get go.


Yes, they do indeed. But I know that where to exactly place the braces is another thing people keep fighting over.

> **LaRoza said:**
> 
He has. If you need stats, check out the sticky. There is a poll which found the people who voted on this forum thought Python was the best place to start (C was second I think).


If C really is second, I would start questioning the reliability of this poll ;)

> **LaRoza said:**
> 
Also there is a why to Love/Hate Python thread for you to read and find anything new to post (why repost it here?)


Whether I like or dislike Python is not what I am trying to advocate. I'm trying to make the point that Python is not necessarily the best beginner's choice.

> **LaRoza said:**
> 
C syntax isn't inheritly more readable, you are just used to it (it seems). Lisp programmers find other syntaxes (if that is a word) confusing and messy. 


Judging from my experience especially with Assembler and Cobol, braces save the day. Lisp's sole purpose is to catch elephants.

> **LaRoza said:**
> 
Many companies got a good reputation from using such languages. Python, Lisp, Perl etc can be secret weapons against the people who think C++, Java etc are the only way to go. I don't know what your company does though.

Can't go into too much detail in an open forum, so let's just say we work for several pretty well known companies. We start where others give up (which is a slogan I would like to use but that would be too obvious :) ).

The more important part is that we're not just building applications that work, we build applications that work and that are as efficient as possible. Like I said in another post, 0.05 seconds processing time per page on an average server is what we consider acceptable for websites.

The same philosophy goes for GUI software. As much as I would like to take it easy and go with PHP/GTK for example, this is not what our customers expect from us (and what they are paying for). So basically, Python is not an option because it's too slow (so is PHP and Perl).

---

### Post by pmasiar on 2008-06-29
> **LoneWolfJack said:**
> > Python is best first language for any beginner
PHP is exactly as good or bad as a beginner's language as Python.

Disagree. And BTW we had a poll (as unscientific as those polls go) Python won and PHP did not. So your opinion is in minority, just FYI.

PHP is not good match for simple scientific calculations, or just massaging file system. PHP is for webpages, and it feels so. And Python library has modules, not 5000 functions in global namespace without consistency.

> > Python might be the only language needed for non-professional programmer, like a scientist

> Ok. But so is Perl. And with some limitations even PHP.

Perl does not have that gentle nudge to write clear code - and has many quirks, killing occasional user. 

> > Python is substantially more productive (for me and many others) than any statically typed language,

> Which is something it has in common with every high level programming language... that's what they are there for, after all.

Yes. Just Python has that edge, as I said before.

> > Python is fast enough that I would gladly burn some CPU cycles for dynamic type checking

> Yup... same goes for PHP. In fact, Debian stats say that PHP is about 5 to 10% faster than Python. 

But non CompSci dyed-in-wool C/Perl haxor can **read the code** faster and with less knowledge - code is more obvious, because it uses less special characters/operators which make sense for sysadmin who knows bash but not non-programmer.

OK so you like PHP. I still disagree that PHP is better for total beginner, especially if beginner is not focused on creating dynamic webpages fast - and even then, Django might be still better more future-proof and scalable choice.

But you cannot claim with straight face that PHP is better general programming language for user with simple needs than Python. One glimpse on the code will show the difference. Just ask any beginner with no programming experience and no plans to become CompSci expert. I did.

> What a fascinating question... given some though I'd say it would have to be as fast as Fortran, as powerful as C, as easygoin as PHP and it would have to provide me with the choice of low or high level programing just as I see fitting.

Forth, obviously! :-)

> You would be surprised how well placed braces make your life so much easier.

I program in Java for living. 

> So you tell me why.

Of course all dynamic languages are close enough and I prefer any of them (well, not PHP :-) ) to Java. But I prefer Python style the most. 

Python has flexibility of Perl without the readability problems. PHP lacks structure as result of it's wild growth. Ruby is too close to Perl.

> I disagree with the more readable part.

... and we live in free country: we can keep our opinions, and suggest and reader compare Python and PHP code and make own opinion.

I would really give something for a language that would allow me to build applications as efficient as in C but in much less time. Python can do the latter (so can PHP with GTK), but I'm not dropping the efficiency and ruin my companies reputation.

And why you cannot compile Python? Or if you cannot, recode 5% of time critical code in C?

---

### Post by LaRoza on 2008-06-29
> **LoneWolfJack said:**
> 
If C really is second, I would start questioning the reliability of this poll ;)


I also happen to recommend Python, C and Lisp (see my site). If you don't see the reasoning for learning C, then I don't think you quite get Linux programming...

> 
Whether I like or dislike Python is not what I am trying to advocate. I'm trying to make the point that Python is not necessarily the best beginner's choice.

The point wasn't made. Instead of attacking Python, give reasons why another is better.

> 
Lisp's sole purpose is to catch elephants.


I don't get it; you don't get Lisp. Most hackers of note seem to think Lisp is worth learning, if only for the experience. (Some programmers do their majority of code in Lisp, and seem to be successful)

> 
Can't go into too much detail in an open forum, so let's just say we work for several pretty well known companies. We start where others give up (which is a slogan I would like to use but that would be too obvious :) ).


No information but with claims? Not worth paying attention on the internet. I could say that I am a tall, good looking red head with a 42" chest with hair to a 27" waist, but without proof or more information you have to assume I am not (the above stats are true, but "good looking" is a little subjective)

---

### Post by NovaAesa on 2008-06-29
Well here's my take on Python vs. other languages debate.

Great things about Python: 1) Indentation is part of the block syntax. This makes things a heck of a lot easier both when reading code and writing code (compared curly bracket languages). 2) It's great to learn, very easy to get a hang of.

Bad things about Python: 1) The typing system. I *think* it's called dynamic typing, but in any case it really really annoys me. I much prefer to explicitly decide what type a certain variable is going to be.

Now what I really wish for is a version of C++ and Java that have indenting to decide where the blocks are rather than brackets. There have been too many times where I have to move brackets around because someone insists that they should go like this:
```

block heading
{
    block body
}
```
rather than this:
```

block heading {
    block body
}
```

---

### Post by LoneWolfJack on 2008-06-29
> **pmasiar said:**
> Disagree. And BTW we had a poll (as unscientific as those polls go) Python won and PHP did not. So your opinion is in minority, just FYI.


Do the same poll on a community site that is based around PHP and see totally different results...

> **pmasiar said:**
> 
PHP is not good match for simple scientific calculations, or just massaging file system. PHP is for webpages, and it feels so. And Python library has modules, not 5000 functions in global namespace without consistency.


It's true that PHP functions sometimes lack consistency in naming and order of parameters. Yet I am sure if you look close enough, you'll find this in Python as well.

> **pmasiar said:**
> 
Perl does not have that gentle nudge to write clear code - and has many quirks, killing occasional user. 


Don't really like Perl myself, so no argument there.

> **pmasiar said:**
> 
Yes. Just Python has that edge, as I said before.


Now what do you do with the army of PHP programmers on this world that claim that PHP has "that" edge?

> **pmasiar said:**
> 
But non CompSci dyed-in-wool C/Perl haxor can **read the code** faster and with less knowledge - code is more obvious, because it uses less special characters/operators which make sense for sysadmin who knows bash but not non-programmer.


Still disagree with code readability.

> **pmasiar said:**
> 
OK so you like PHP. I still disagree that PHP is better for total beginner, especially if beginner is not focused on creating dynamic webpages fast - and even then, Django might be still better more future-proof and scalable choice.


Didn't say PHP was better. However, I have seen many times where Python was recommended to someone who wnated to learn web-programming without even mentioning PHP and leaving the impression on the newbie that PHP programmers are apparently a bunch of queers who don't know what they're doing.

> **pmasiar said:**
> 
But you cannot claim with straight face that PHP is better general programming language for user with simple needs than Python. One glimpse on the code will show the difference. Just ask any beginner with no programming experience and no plans to become CompSci expert. I did.


Still disagree with the readability. But if you tell the rest to the aforementioned newbie, I am almost happy. All that I'm asking for is that Python isn't introduced as the holy grail of programming. 

> **pmasiar said:**
> 
Forth, obviously! :-)


Doesn't have braces so that's the end of that. :)

> **pmasiar said:**
> 
I program in Java for living. 


I can now see that there is no hope for you. You have already been consumed by the dark side. ;)


> **pmasiar said:**
> 
Of course all dynamic languages are close enough and I prefer any of them (well, not PHP :-) ) to Java. But I prefer Python style the most. 

Python has flexibility of Perl without the readability problems. PHP lacks structure as result of it's wild growth. Ruby is too close to Perl.


There's one of those magic words... tell the newbie that you *prefer* Python and you won't have me complaining ever again... ;)

> **pmasiar said:**
> 
And why you cannot compile Python? Or if you cannot, recode 5% of time critical code in C?

We have been thinking about that (yet using PHP/GTK instead), but so far there wasn't a real chance to actually do it. Also, I'd like to test this with one of our inhouse projects first.

---

### Post by LaRoza on 2008-06-29
> **LoneWolfJack said:**
> Do the same poll on a community site that is based around PHP and see totally different results...

This community is not based on any language, but on Ubuntu Linux.

---

### Post by LoneWolfJack on 2008-06-29
> **LaRoza said:**
> I also happen to recommend Python, C and Lisp (see my site). If you don't see the reasoning for learning C, then I don't think you quite get Linux programming...


Yet according to your own posting, the poll question was what is the best place to start, not what language is best for programming under Linux...


> **LaRoza said:**
> 
The point wasn't made. Instead of attacking Python, give reasons why another is better.


I'm not "attacking" it at all. I'm trying to pull the magic off it that some try to instill.

> **LaRoza said:**
> 
I don't get it; you don't get Lisp. Most hackers of note seem to think Lisp is worth learning, if only for the experience. (Some programmers do their majority of code in Lisp, and seem to be successful)


First, you should read this to see the wisdom behind what I typed... ;)
[http://www.ggi-project.org/mailinglist/sep98/103.html]("http://www.ggi-project.org/mailinglist/sep98/103.html")

Secondly, I don't consider myself a hacker. Nor do I want to become one. I prefer having a life over being a "real hacker". ;)

> **LaRoza said:**
> 
No information but with claims? Not worth paying attention on the internet. I could say that I am a tall, good looking red head with a 42" chest with hair to a 27" waist, but without proof or more information you have to assume I am not (the above stats are true, but "good looking" is a little subjective)

If you promise not to give out this information, I can provide you with company website and my personal Xing profile should that really be necessary.

---

### Post by Frak on 2008-06-29
Oh, Python. A.K.A. Your guide to good programming etiquite (python is the best way IMHO to learn proper code formatting, such as whitespaces and whatnot).

---

### Post by LaRoza on 2008-06-29
> **LoneWolfJack said:**
> Yet according to your own posting, the poll question was what is the best place to start, not what language is best for programming under Linux...

It doesn't matter, programming is programming. Since most people use Ubuntu on this forum, it is just added sugar.

> 
Secondly, I don't consider myself a hacker. Nor do I want to become one. I prefer having a life over being a "real hacker". ;)

I am not sure what you are trying to say. Are you saying the favourite past time of many people on this forum (including me) is a waste of time?

> 
If you promise not to give out this information, I can provide you with company website and my personal Xing profile should that really be necessary.

Not really. I don't care. Also, if it is a public site then it should be no secret, if for some reason you don't want to be associated with this company/site, then you shouldn't tell me. I am not trustworthy that way.

---

### Post by LoneWolfJack on 2008-06-29
> **LaRoza said:**
> It doesn't matter, programming is programming. Since most people use Ubuntu on this forum, it is just added sugar.


I am not sure your reply is on the same subject. Also, I would call "programming is programming" a pretty bold claim.

> **LaRoza said:**
> 
I am not sure what you are trying to say. Are you saying the favourite past time of many people on this forum (including me) is a waste of time?


Not at all. Your time, your choice. It is not my place to judge this.

> **LaRoza said:**
> 
Not really. I don't care. Also, if it is a public site then it should be no secret, if for some reason you don't want to be associated with this company/site, then you shouldn't tell me. I am not trustworthy that way.

Which is, as much as I hate to say this, what I suspected, or I would have just sent you that information.

Both sites are not secret but I can't have my private forum accounts associated with my business for everyone who can use google. After all, I need some privacy.

Also, I feel somewhat reluctant to provide a profile just to prove the truth of what I'm saying.

---

### Post by LaRoza on 2008-06-29
> **LoneWolfJack said:**
> 
Which is, as much as I hate to say this, what I suspected, or I would have just sent you that information.

Also, I feel somewhat reluctant to provide a profile just to prove the truth of what I'm saying.

What did you suspect? That I don't care about it?

Then you shouldn't have brought it up :-) I have refrained from making points about subjects if it would involve something I didn't want to get into in more depth.

---

### Post by xlinuks on 2008-06-29
Let the flames go on :)
LoneWolfJack is the winner so far :))

---

### Post by LaRoza on 2008-06-29
> **xlinuks said:**
> 
LoneWolfJack is the winner so far :))

Then I don't want to be a winner ;)

(Every person will think their own side is "winning" when in observation by the way)

---

### Post by nvteighen on 2008-06-29
> **NovaAesa said:**
> 
(...)
```

block heading {
    block body
}
```

My eyes hurt!!

(Again, C people discussing curly braces, as usual).

---

### Post by xlinuks on 2008-06-29
> **LaRoza said:**
> Then I don't want to be a winner ;)

(Every person will think their own side is "winning" when in observation by the way)

Ok, you at least acknowledged you're involved in flaming discussion :)

---

### Post by wdaniels on 2008-06-29
> **nvteighen said:**
> My eyes hurt!!

(Again, C people discussing curly braces, as usual).

It's funny, I always hated the curly braces in C, but they don't seem to bother me at all in PHP :confused:

Anyone else find that the same things that bother them in some languages, don't in others?

---

### Post by |{urse on 2008-06-29
Ive seen amazing things done with c/C++/C#/Ruby/Perl/Python/Whatever compiled/interpreted It's silly to sit around and tell someone what language they should learn when you haven't even ascertained exactly how that individual learns.. If they are better with spatial logic vs. visual logic then those people would get on with curly braces better etc. etc. I think tech is at the point where even something with horrendous whitespace issues will run reasonably fast. did any of you take into account what exactly the beginning programmer wanted to do with his newly learned language? If it was simply to make vb type office apps or was it hardcore C++ + maya 3d rendering? It's like opening a toolbox with every tool imaginable and fighting over which tool is the best.

---

### Post by LaRoza on 2008-06-29
> **xlinuks said:**
> Ok, you at least acknowledged you're involved in flaming discussion :)

Civilized discussion about a possible stale topic. Flaming, true flaming, is against the CoC.

---

### Post by lisati on 2008-06-29
I don't have a problem with braces/brackets/parentheses of any kind as part of a programming language - properly used, they can help with clarity, showing which statements belong together as a group, without the need for getting the indentation precisely right. 

BTW, I took my first programming steps on a system where proper indentation mattered: get things in the wrong column and you were likely to get either a pile of error messages or a seriously misinterpreted piece of code.

---

### Post by lisati on 2008-06-29
> **xlinuks said:**
> Ok, you at least acknowledged you're involved in flaming discussion :)

Flaming? I see a healthy difference of opinion where everyone can end up winners - it helps keep these forums interesting.

---

### Post by cardinals_fan on 2008-06-29
Ruby is really fun

---


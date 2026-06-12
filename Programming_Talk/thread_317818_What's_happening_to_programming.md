---
title: "What's happening to programming?"
date: 2006-12-13
forum: Programming Talk
---

### Post by Wybiral on 2006-12-13
When programming as we know it started, it seriously was implemented using 0's and 1's (machine code)... But, people got tired of having to write like that and more readable languages popped up like assembly (which is like a masked version of machine code). Later FORTRAN, COBOL, and Pascal came into view to make things even more readable and manageable (because 0's and 1's weren't cutting it anymore). I would say that things really kicked into gear after C and especially after C++

But, the underlying theme between all of this progress was... Readability and manageability.

But lately I have seen hundreds of programmers and programs hellbent on writing the most complex piece of art they can write looking something vaguely similar to this...
```

def d(#!&):()()#!#*iu++29(*){}{}#@%%0!022101*()#**2**3{}

```
That was an exaggeration, of course... But why are so many people beginning to revert back to unreadable, unmanageable code??? It seems like regression to me. And the weirdest part is that people are calling code like that "elegant"... ??? Yeah if you have a thing for funny unreadable symbols I can see how that would look elegant.

Anyway, am I the only one who is seeing this?

---

### Post by 23meg on 2006-12-13
Can you cite some examples from the FOSS world? With most FOSS code I'm seeing the exact opposite; almost all code I've looked into is well annotated and easy to maintain. That's an inherent trait of distributed development in general, since otherwise it would be very hard to work on the code together.

---

### Post by Wim Sturkenboom on 2006-12-13
Why not give some real world examples? So we are able to actually comment on your statement.

---

### Post by samjh on 2006-12-13
There are some in the hacking underground who tend to write ridiculously terse code, but I've yet to come across really bad examples from collaborative open-source projects.

Somtimes it can be amusing and fun to write terse code: take a look at the weekly programming challenge thread for examples.  But for serious programming, I think terse code is more frowned upon than ever before.

---

### Post by Kieranties on 2006-12-13
There are many aspects to programming, and typically many ways of implementing those aspects.

The reason why we can have more "humane" languages these days is because hardware is starting to catch up with what we really want it to do.  We no longer have to be as explicit or terse with coding as by and large the compiler/interpreter will clean things up for us.  A prime example is garbage collection.

What you have to remember is that you are still talking to the computer in 1s and 0s, but it has to go through more translation now then it did before.  Have you ever tried writing a compiler?  Give it a go in lex and yacc, it can be incredibly dificult.

Back on topic... The more humane and readable you make your code, the more translation it must go through...therefore the more time (often) it will take to execute (though this isn't always the case).  Using terse short, often unreadable code can be a life saver when your trying to optimise a project.

Of course it does look odd, but that's where the quality of the programmer comes in, and it is up to them to write good comments/documentation

---

### Post by asimon on 2006-12-13
> **Wybiral said:**
> When programming as we know it started, it seriously was implemented using 0's and 1's (machine code)... But, people got tired of having to write like that and more readable languages popped up like assembly (which is like a masked version of machine code). Later FORTRAN, COBOL, and Pascal came into view to make things even more readable and manageable (because 0's and 1's weren't cutting it anymore). I would say that things really kicked into gear after C and especially after C++

But, the underlying theme between all of this progress was... Readability and manageability.

I think we can say that it's all about increasing productivity. And readability and manageability are important parts of it.

> **Wybiral said:**
> 
But lately I have seen hundreds of programmers and programs hellbent on writing the most complex piece of art they can write looking something vaguely similar to this...
```

def d(#!&):()()#!#*iu++29(*){}{}#@%%0!022101*()#**2**3{}

```
That was an exaggeration, of course... But why are so many people beginning to revert back to unreadable, unmanageable code??? It seems like regression to me.

And the weirdest part is that people are calling code like that "elegant"... ??? Yeah if you have a thing for funny unreadable symbols I can see how that would look elegant.

Actually I think most of the time such code is not very elegant but the result of rather bad programmers. But of course there are cases where it makes sense to accept rather unreadable code when it saves a couple of CPU cycles. For example there are some very popular functions in 3D graphics which are very unreadable and don't show easily what they compute, but they are very fast, which is sometimes more important than readable, elegant, and maintainable code.

As Wim Sturkenboom said, without concrete examples, no one can say if the code you saw is clever and very efficient or just bad hacking.

---

### Post by Verminox on 2006-12-13
I'd say I disagree with the OP. If you go to any programming websites, forums, tutorial sites, etc. you will find a lot of stress on readability and managing of code. Very rarely does anyone encourage making complex and un-reusable code, with the exception of "Who can make the weirdest/most complex snippet" type of competitions. Full scale applications, especially open source ones (because they should be modifiable) are usually written well, unless the programmer isn't good in the first place.

---

### Post by pmasiar on 2006-12-13
> **Wybiral said:**
> But lately I have seen hundreds of programmers and programs hellbent on writing the most complex piece of art they can write looking something vaguely similar to this...
```

def d(#!&):()()#!#*iu++29(*){}{}#@%%0!022101*()#**2**3{}

```

Anyway, am I the only one who is seeing this?

you mean stuff like  [this]("http://en.wikipedia.org/wiki/Perl#Fun_with_Perl")?

I suggest you make following exercise:
[LIST=1]
[*]start python shell: >python
[*]type 'import this' (without quotes)
[*]enjoy the zen wisdom of python
[/LIST]

Do you like it? :-)

Python was designed to be readable as foremost goal: "perl is executable line noise. Python is executable pseudocode"

You may want to read also Paul Graham's essay [The hundred-year language]("http://www.paulgraham.com/hundred.html") about how languages evolve and what increase in CPU speed migh bring us.

---

### Post by asimon on 2006-12-13
> **pmasiar said:**
> Python was designed to be readable as foremost goal: "perl is executable line noise. Python is executable pseudocode"
Of course the question if that design goal was met is debatable. :twisted:

---

### Post by Wybiral on 2006-12-13
To pmasiar, I am a python user, and I love it. I think the two most efficient and readable languages are python and C++. Well, assembly is readable, but hardly manageable. And yeah, that link is a good example, I have noticed alot of that kind of code in forums and in code compo's and stuff. It's like people are trying to write the most difficult to follow code possible and the newer scripting languages are allowing it.

Also, I read that "hundred year language" essay a few day's ago and it is very good. I disagree with a number of things in it though... I see scripting languages becoming very popular and I've noticed that people are wanting to write in interpreted languages instead of compiled. While I believe that compiled is a better option for speed, I think in a few years computers will be so fast that it wont matter... So, here's my theory...

Operating systems wont be a bunch of programs, they will be a really powerful interpreter. And, here's the kicker... I think this interpreter operating system will be hardware! It would allow for maximum speed (kindof like the first early computers, or calculators!) And if possible, because I have seen a large amount of AI speech recognition programs... It's very possible that the interpreters language will be close to a natural language.

Anyway, thats just me theory. "Paul Graham" brought up some good points, but I still think a natural language interpreter will allow non-programmer type people to use computers the way us programmers do.

---

### Post by ssalman on 2006-12-13
[FONT=Arial][SIZE=3]Allow me to throw a twist.... :)

try to compile the below code in C, and run it... and marvel at the out put!!

[/SIZE][/FONT]```
#include <stdio.h>
 
main(t,_,a )
char * a;
{
return! 0<t? t<3? main(-79,-13,a+ main(-87,1-_, main(-86, 0, a+1 )
+a)):  1, t<_? main( t+1, _, a ) :3, main ( -94, -27+t, a )
&&t == 2 ?_ <13 ? main ( 2, _+1, "%s %d %d\n" )
:9:16: t<0? t<-72?
main( _, t,
"@n'+,#'/*{}w+/w#cdnr/+,{}r/*de}+,/*{*+,/w{%+,/w#q#n+,/#{"
"l+,/n{n+,/+#n+,/#;#q#n+,/+k#;*+,/'r :'d*'3,}{w+K w'K:'+}e"
"#';dq#'l q#'+d'K#!/+k#;q#'r}eKK#}w'r}eKK{nl]'/#;#q#n'){)#}"
"w'){){nl]'/+#n';d}rw' i;# ){nl]!/n{n#'; r{#w'r nc{nl]'/#{l,"
"+'K {rw' iK{;[{nl]'/w#q#n'wk nw' iwk{KK{nl]!/w{%'l##w#' i; :"
"{nl]'/*{q#'ld;r'}{nlwb!/*de}'c ;;{nl'-{}rw]'/+,}##'*}#nc,',#n"
"w]'/+kd'+e}+;#'rdq#w! nr'/ ') }+}{rl#'{n' ')# }'+}##(!!/")
:
t<-50? _==*a ? putchar(31[a]): main(-65,_,a+1) :
main((*a == '/') + t, _, a + 1 ) : 0<t?
main ( 2, 2 , "%s") :*a=='/'||
main(0,
main(-61,*a, "!ek;dc i@bK'(q)-[w]*%n+r3#l,{}:\nuwloca"
"-O;m .vpbks,fxntdCeghiry")
,a+1);}


```[FONT=Arial][SIZE=3]
Bad code can be written by everyone, bu[/SIZE][/FONT][FONT=Arial][SIZE=3]t [/SIZE][/FONT][FONT=Arial][SIZE=3]Obfuscated code can only be written by an ellite few.... see for yourself in this [link]("http://www.ioccc.org/")!![/SIZE][/FONT][FONT=Arial][SIZE=3]
[/SIZE][/FONT][FONT=Arial][SIZE=3]

[/SIZE][/FONT]

---

### Post by Wybiral on 2006-12-13
Thats a good example of what I mean. It works very well for little competitions like that, but not in real world programming. That was a cool example though.

> 
Bad code can be written by everyone, but Obfuscated code can only be written by an ellite few....


I disagree, anyone could make a program like that if they used another program to generate the source code.

---

### Post by Mickeysofine1972 on 2006-12-13
> **Wybiral said:**
> When programming as we know it started, it seriously was implemented using 0's and 1's (machine code)... But, people got tired of having to write like that and more readable languages popped up like assembly (which is like a masked version of machine code). Later FORTRAN, COBOL, and Pascal came into view to make things even more readable and manageable (because 0's and 1's weren't cutting it anymore). I would say that things really kicked into gear after C and especially after C++

But, the underlying theme between all of this progress was... Readability and manageability.

But lately I have seen hundreds of programmers and programs hellbent on writing the most complex piece of art they can write looking something vaguely similar to this...
```

def d(#!&):()()#!#*iu++29(*){}{}#@%%0!022101*()#**2**3{}

```
That was an exaggeration, of course... But why are so many people beginning to revert back to unreadable, unmanageable code??? It seems like regression to me. And the weirdest part is that people are calling code like that "elegant"... ??? Yeah if you have a thing for funny unreadable symbols I can see how that would look elegant.

Anyway, am I the only one who is seeing this?

I have to agree but with a little twist.

I think people are writing stupid and unreadable code because its easier than making it open  to others. This is a mark of a truly open source coder. i fyou want to make it OSS then make it really 'open' by making you source 'human' readable.

thats my 2 pennys worth anyway, right or wrong

Mike

---

### Post by dwblas on 2006-12-13
I've always wondered what kind of code is written by people who post messages like "If u r riting code".  If they are too lazy to key in "you"???  Anyway, bad code is like bad drivers, IMHO, they both get a disproportionate amount of attention, i.e. you don't hear anyone complain about the programs that are easy to modify.

---

### Post by shining on 2006-12-14
> **Wybiral said:**
> When programming as we know it started, it seriously was implemented using 0's and 1's (machine code)... But, people got tired of having to write like that and more readable languages popped up like assembly (which is like a masked version of machine code). Later FORTRAN, COBOL, and Pascal came into view to make things even more readable and manageable (because 0's and 1's weren't cutting it anymore). I would say that things really kicked into gear after C and especially after C++

But, the underlying theme between all of this progress was... Readability and manageability.

But lately I have seen hundreds of programmers and programs hellbent on writing the most complex piece of art they can write looking something vaguely similar to this...
```

def d(#!&):()()#!#*iu++29(*){}{}#@%%0!022101*()#**2**3{}

```
That was an exaggeration, of course... But why are so many people beginning to revert back to unreadable, unmanageable code??? It seems like regression to me. And the weirdest part is that people are calling code like that "elegant"... ??? Yeah if you have a thing for funny unreadable symbols I can see how that would look elegant.

Anyway, am I the only one who is seeing this?

I see it as a challenge, or as an exercise of style.
Like the [The International Obfuscated C Code Contest]("http://www.ioccc.org/") which was already mentioned above.

Beyond this scope, I don't see why source code would be obfuscated. For GPL softwares, it isn't very clear, but I'm not sure it's allowed.

That's in the section 3:
> 
The source code for a work means the preferred form of the work for making modifications to it.


As for proprietary softwares, you can't even see the code. Though I believe obfuscation can still be used there, for making reverse engineering harder.

Anyway, as far as I know, the tendency is still the same, trying to make the code as readable as possible. That helps debugging and maintaining a lot.

---

### Post by Burgresso on 2006-12-14
I think that when many people write esoteric code they are just trying to look smart.

Or they aren't very good or experienced.

One or the other :)

---

### Post by Klipt on 2006-12-14
> **Wybiral said:**
> Operating systems wont be a bunch of programs, they will be a really powerful interpreter. And, here's the kicker... I think this interpreter operating system will be hardware!

Isn't that what [Lisp Machines](http://en.wikipedia.org/wiki/Lisp_machine#Initial_development) were?

---

### Post by Hendrixski on 2006-12-14
> **Wybiral said:**
> 
But lately I have seen hundreds of programmers and programs hellbent on writing the most complex piece of art they can write looking something vaguely similar to this...
```

def d(#!&):()()#!#*iu++29(*){}{}#@%%0!022101*()#**2**3{}

```


Anyway, am I the only one who is seeing this?

No, you're not alone.  I have seen my share of TERRIBLY written, undocumented, illegible code.  Less so in large open source projects, though I have met many open source nerds who think that if people can't understand their code that the reader surely must be stupid.  It's more common in proprietary code that's only maintained by one person, and suddenly guess what, others need to use it but there's no directions as to how.

---

### Post by rplantz on 2006-12-14
> **Wybiral said:**
> When programming as we know it started, it seriously was implemented using 0's and 1's (machine code)... But, people got tired of having to write like that and more readable languages popped up like assembly (which is like a masked version of machine code). Later FORTRAN, COBOL, and Pascal came into view to make things even more readable and manageable (because 0's and 1's weren't cutting it anymore). I would say that things really kicked into gear after C and especially after C++

But, the underlying theme between all of this progress was... Readability and manageability.


I don't agree that programmers were any better back then.

I started my programming in an academic environment. I got my first programming job in industry in 1977 with a company that made CT scanners. My first assignment was to port the code from a Data General Nova to Eclipse. (For the younger people, the Eclipse had more features.) It was all assembly language. Thousands of lines of code. The only comments the previous programmer had made where "Data follows" every once in a while. The fact that it was a data segment was immediately obvious to anyone who could read the assembly language, so the comment was redundant. In one place, it took me two days to figure out why three instructions multiplied by thirteen. (The scanner had twelve Xray detectors, plus one for reference.) There was no multiply instruction; he had used a series of add and shift instructions. It was very clever code, but the original programmer made no attempt to make the code readable nor manageable.

I have seen many more similar examples throughout my career.

---

### Post by Hendrixski on 2006-12-14
> **Burgresso said:**
> I think that when many people write esoteric code they are just trying to look smart.

Or they aren't very good or experienced.

One or the other :)
[SIZE="6"][B]
EXACTLY!!!! [/B][/SIZE][SIZE="1"]*but don't tell them that it really makes them look stupid.[/SIZE]

---

### Post by dwblas on 2006-12-14
> I got my first programming job in industry in 1977So did I.  The thing I appreciate most about programming now, after databases, is descriptive variable names.  At that time you were limited to 6 or 8 bytes depending on the compiler, because of limited memory.  It's nice to see bollinger_band_upper = 1 instead of bobu=1.

---

### Post by rplantz on 2006-12-14
> **dwblas said:**
> So did I.  The thing I appreciate most about programming now, after databases, is descriptive variable names.  At that time you were limited to 6 or 8 bytes depending on the compiler, because of limited memory.  It's nice to see bollinger_band_upper = 1 instead of bobu=1.

I heard about a guy who wrote a C program where he used only the characters one, zero, lower-case ell, and upper-case oh to make up all his variable names. For example, OO01l011.

Reminds me of the Dilbert cartoon about the Y2K "bug." Dogbert is given the task of locating all occurrences of a year in the company's software. After six weeks of investigation, he announces the good news that their code only has ones and zeros in it.

---

### Post by dwblas on 2006-12-15
This is off topic as well, but if whoever has the sig "There are 10 kinds of people, those who understand binary and those who don't" dies, I'm gonna steal it.  I know the variable name was a joke, but how would you like to try and figure out a variable name with the letters oh-oh-zero-el-one.  I might write myself a reminder for April 1st and give someone some custom code to debug.

---

### Post by lnostdal on 2006-12-15
> **Wybiral said:**
> I've noticed that people are wanting to write in interpreted languages instead of compiled. 


No; people want _interactive_ languages and environments. There is a common fallacy that "interactive" exclusively means "interpreted" - which just isn't true.

As I type this into my interactive session:

```
(defun hello-world () (write-line "Hello World!"))
```

..and press enter - the function `hello-world' is compiled to native machine code at once#1. I can do this multiple times and it will be re-defined interactively at run-time. The lines between "times" are blurred.

#1: [SBCL](http://www.sbcl.org/)

---

### Post by pmasiar on 2006-12-15
> **Wybiral said:**
>  I see scripting languages becoming very popular and I've noticed that people are wanting to write in interpreted languages instead of compiled. 

It is not about interpreted - you can compile python code if you insist. It is about dynamically typed. Duck typed, garbage-managed languages. Agile: easy to write prototype.

>  operating system will be hardware! It would allow for maximum speed 

OS in the ROM? LOL. Why? Apple tried it long time ago.

We don't need **maximum **speed. We need **enough speed, and enough flexibility** to do what we need to do today, finish today (and not wait for tomorrow). And also make possible  what we will need to do tomorrow.

> a large amount of AI speech recognition programs... It's very possible that the interpreters language will be close to a natural language.

Anyway, thats just me theory. "Paul Graham" brought up some good points, but I still think a natural language interpreter will allow non-programmer type people to use computers the way us programmers do.

Ambiguos natural languages for noob programming? Yeah right! :-)

See? Id I agreed with you or not? :-P How computer can tell?

If I need to choose my side, sorry Wybiral, you are ubuntista  - but I side with Pau Graham ;-)

---

### Post by Wybiral on 2006-12-15
No, I was saying... If they created an interpreter that could act off of natural language, so that you could speak a "program" into existence, and I don't think this is far from possible. I have seen some INCREDIBLY intuitive AI and sure you would have to speak clearly and be careful how you phrase things, but the interpreter could also ask what you meant if you say an ambiguous phrase. It sounds really scifi-ish but AI is really picking up these days.

And then I kindof figured... If there WERE an interpreting program that everyone used and was very popular... Why not hardwire it as the computer? Technology is also picking up and making this very possible and even cheap. This would allow for MAXIMUM speed and size efficiency.

This is all just me throwing around idea's, I'm just saying it IS possible.

---

### Post by pmasiar on 2006-12-15
yeah right :twisted:

---

### Post by Wybiral on 2006-12-15
Ok, I forgot I was talking to a psychic here... If only I knew as much about the future as you, oh great one.

All I'm saying is that no one knows... You can make theories, but... What kind of crazy theories did they have 100 years ago for the year 2000... And it was nothing like that. Just as early as the 50's people still had crazy theories of the year 2000. I'm just saying, technology has always caught people off guard... You may be surprised.

---

### Post by rplantz on 2006-12-15
> **Wybiral said:**
> No, I was saying... If they created an interpreter that could act off of natural language, so that you could speak a "program" into existence, and I don't think this is far from possible. 

And this will lead to "lawputer" chips that will argue the meaning of the words I say into the interpreter. And, of course, good lawputers will be very expensive.

This will lead to "politiputers", which will be used to design lawputers, and then we are all in trouble.  :)

---

### Post by pmasiar on 2006-12-16
> **Wybiral said:**
> Ok, I forgot I was talking to a psychic here.

I said "yeah right" as prime example that you cannot rely on computer to understand natural language 100%. Resulting misunderstanding only underscored my point: if human have problems to understand each other, how they can hope automate this understanding? I cannot see the future, but past failures (40 years of failures in understanding natural language) are good predictor of the future ones :-)

---

### Post by Wybiral on 2006-12-16
Thats nonsense... Before computers we spent centuries without computers and they still happened... Those years weren't foretelling anything. And, like I said, you would have to speak clearly... Sarcasm obviously wouldn't work. But it IS possible. Go read up on some pattern recognition algorithms. I'm not saying it WILL... But it COULD.

---

### Post by jmc1024 on 2006-12-16
[QUOTE=Wybiral;1881881]To pmasiar, I am a python user, and I love it. I think the two most efficient and readable languages are python and C++.

You've got to be kidding!  C++ readable!?!?

    Goober a;
    Goober b;
    cout << a + b;

With constructors and operating overloading no one knows what this code really
does without sufing the code and piecing it all together.

Oh, yes I do have professional C++ experience - 6 years.  I'll go with C any day.

Mark

---

### Post by Wybiral on 2006-12-16
Um... It makes absolute sense to me.

Step 1. Know your standard library!
Step 2. Don't use ambiguous labels like "goober"
Step 3. Know any resources you are using.

cout is the console-out function.
"<<" is an OPERATOR, it's very clear how it works, it just accepts anything after it as a parameter for the function "cout"

Alot of languages have constructors and operator overloads (python for instance). Maybe it's object oriented programming that you find unreadable... Not just C++

If it's a project you're working on, then I assume you should know what the function of "goober" is and what members belong to it. You should also know what the operator overload "+" means for the goober class. If not, then you either don't have very good communication with your team or you are using resources that you know nothing about and you will have this problem with all languages. Even in C I could write an ambiguous function name and you could have no idea exactly what that function does. Just like those operator overloads and the "goober" class. I hope no one is out there trying to program without knowing the resources they are using, that would be a problem in all languages!

---


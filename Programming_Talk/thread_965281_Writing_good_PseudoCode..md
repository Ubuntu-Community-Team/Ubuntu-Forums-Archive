---
title: "Writing good PseudoCode."
date: 2008-10-31
forum: Programming Talk
---

### Post by brian77095 on 2008-10-31
Correct me if I am wrong....

PseudoCode is not really any lang.  It is suppose to be like an outline of what you want the real program to do.

If that is the case do you write it differently for different programing lang.?

Do you write it mainly for your self or do you make it so that anyone can read it and understand it?

Thanks for the tips!!

---

### Post by sshuber on 2008-10-31
Pseudo code is one of those things that is almost 100% dependent on what yourself and your target audience wants. I don't believe there is any standard at all for it. You could use words or make stuff up if you wanted as long as you can understand what it means.

It's really just meant to be an outline of a program/algorithm with no emphasis on correct syntax unless you want to.

So my code in C for something to add all numbers from 1-50 may be: 

```
int i,temp,size;
i=1; temp=0; size=50;
while(i<=size)
{
   temp+=i;
   i++;
}
```

and the psuedo code could be:
```
initialize vars
set i=1,temp=0,size=50
while i is less than size add i to temp
```
This would be completely valid and I personally could read my psuedo code and understand what actual code I need to write. I think in code so I picture syntax when I'm planning things in my head but others may find just simple words more useful.

The advantage of using words and writing out things like I did in my pseudo code above is that it is not language specific. You could read that and since it uses common programming ideas, take it and code it in any language.

Moral of the story is whatever goes as long as the target audience can understand it.

---

### Post by pmasiar on 2008-10-31
Python is called "executable pseudocode" - because for anyone knowing one or more C-like language, it is almost as readable as pseudocode.

---

### Post by drubin on 2008-10-31
> **brian77095 said:**
> Correct me if I am wrong....

PseudoCode is not really any lang.  It is suppose to be like an outline of what you want the real program to do.

If that is the case do you write it differently for different programing lang.?

Do you write it mainly for your self or do you make it so that anyone can read it and understand it?

Thanks for the tips!!

If you want to learn how to write pretty neat PseudoCode learn [Pascal]("http://en.wikipedia.org/wiki/Pascal_programming_language") it is pretty much PseudoCode  :)

But I mostly code in comments first and then turn the comments into code as I go along. That way I know the program flow and if some one else had to pick it up it is already in the code as comments to what I was planing to do.

---

### Post by brian77095 on 2008-10-31
[QUOTE]

pmasiar  	
Re: Writing good PseudoCode.
Python is called "executable pseudocode" - because for anyone knowing one or more C-like language, it is almost as readable as pseudocode. 


[QUOTE]

Could your go in to a bit more detail?  Or provide a link??

---

### Post by drubin on 2008-10-31
> **pmasiar said:**
> Python is called "executable pseudocode" - because for anyone knowing one or more C-like language, it is almost as readable as pseudocode.

I would disagree with this. I am working with python now and although the language is pretty neat and enjoying it. The whole () [] {} and functions that return value,value2 can be quite confusing. So I would consider it to much of a high level lang to consider it PseudoCode(see point about pascal)

---

### Post by cmay on 2008-10-31
i think wikipedia books hs a book about algoritms that are written using only pseudo code.
maybe that could be of some use for you. i am really dog tired right now so please exuse me for not providing link. i am getting old so i need my sleep .i just figured i would point you in that direction .

---

### Post by pmasiar on 2008-10-31
Don't get me started about Pascal. BEGIN/END as integral part of pseudocode?

Of course it is matter of taste. That is the whole point: pseudocode does not have formalized syntax. 

If someone has hard time to comprehend powerful literal expressions, big part of Python power is missed. It's your loss, not mine.

Links: [http://www.google.com/search?q=python+executable+pseudocode](http://www.google.com/search?q=python+executable+pseudocode)

---

### Post by nrs on 2008-10-31
> **brian77095 said:**
> 
Do you write it mainly for your self or do you make it so that anyone can read it and understand it?
Well, it depends on the reasons you're writing it. Generally the only time I use pseudo-code is when I'm bouncing ideas off of people or inquiring about something, so it's pretty vital everyone be able to comprehend it.

Mine tends to be Python-like, I don't use straight python because even that has its eccentricities.

---

### Post by drubin on 2008-10-31
> **pmasiar said:**
> If someone has hard time to comprehend powerful literal expressions, big part of Python power is missed. It's your loss, not mine.

Yes I agree with missing the Python power... but this is PseudoCode that is supposed to be non-language specific and most others don't have the same syntax/features at Python.

You are a Python developer so thus programming PseudoCode would make more sense to you in Python. yes and the point each to his own is very important with this discussion else it is going to turn out to be a full on war.

---

### Post by fiddler616 on 2008-10-31
I think that PseudoCode is:
a) Very dependent upon the person doing it
b) Very dependent on the level of thoroughness desired--be it a rough outline, or a program-without-correct-syntax.
c) Very dependent on the PseudoCoder's first language. My PseudoCode is very Pythonic--but then again I'm a Pythoneer (or try to be :P ) Wikipedia's PseudoCode looks a bit more C/C++/C#/Java -ish (including braces, for one) because braces are a much more common convention than indentation.

I'm assuming we all know about: [http://en.wikipedia.org/wiki/Pseudocode](http://en.wikipedia.org/wiki/Pseudocode)

...my $.02

---

### Post by nvteighen on 2008-10-31
This is something I'm interested (being someone studying Linguistics, that's logical, isn't it? 8)).

Actually, there cannot be something as a "Pseudo-code"... Whatever code you write in some coherent language will be a program; maybe the language used is only known by yourself or resembles algorithmic mathematical notation or it is Python or Java... **You can't write code outside a programming language**.

Of course, using ASM as Pseudo-code is not very useful, as what you seek in "Pseudo-coding" is that people have a clearly readable and concise expression of your algorithm. You can of course use ASM, but Python or any high-level language will do it better as they tend to privilege expressiveness and clarity.

Whether there is an computer implementation or not of the language you use is absolutely irrelevant. Lisp was born a sort of "Pseudo-code" and was implemented as a programming language; Python is a programming language and Wikipedia increasingly uses it as "Pseudo-code". I could write "Pseudo-code" even in Spanish, though it may not be a very clever decision (there's a reason why natural languages are not used in this kind of areas.)...

So, do you want to write good "Pseudo-code"? Write code in some coherent formal symbolic system (i.e. a language) that has some good amount of expressiveness to quickly give people (or yourself) an idea on what you're trying to do.

---

### Post by lisati on 2008-10-31
IMO, pseudo-code is just one of many tools available to help programmers; it should be tailored to suit the programmer's style and any corporate standards that might be applicable.
The rare occasions I've used pseudo-code have been as a stepping stone while I'm refining my ideas on how to achieve a particular task.

---

### Post by samjh on 2008-10-31
> **brian77095 said:**
> Correct me if I am wrong....

PseudoCode is not really any lang.  It is suppose to be like an outline of what you want the real program to do.

If that is the case do you write it differently for different programing lang.?

Do you write it mainly for your self or do you make it so that anyone can read it and understand it?

Thanks for the tips!!

It depends on what the pseudocode is meant to do.

You can even write it in ordinary prose.  I tend to do it this way initially, by putting each step in numbered format.

Example:
```
1. Generate random number, put into variable x.

2 Ask user to guess the number.
2.1. Get user input.
2.2. Compare input to x.
2.3. If x > input then say "Your guess was too low."; Go to step 2.
2.4. If x < input then say "Your guess was too high."; Go to step 2.
2.5. If x = input then say "Your guess was right."; Go to step 3.

3. Exit program.
```

I've actually seen someone use poetry. :confused:  Very clever, but ultimately not too useful. :KS

As your pseudocode becomes more detailed, it will resemble a programming language more and more.  Try to make it gradually transform into the target programming language, but not too much that it becomes the language. ;)

Another thing you can do is draw flowcharts, and then write simple pseudocode inside the little processes in the flowchart.  This is really only recommended for massively complex projects, preferably with CASE (Computer Aided Software Engineering) tools.

---

### Post by CptPicard on 2008-10-31
The idea really is just to get the point across concisely and clearly, without having to worry about the language being "real" enough that a computer could handle it.

Python is actually very, very close to the kind of pseudocode I used to write in exams at university when describing algorithms. What you essentially need is functions, control structures (for, if, while) and some convention for describing data structure access... so that when you have something like a queue in your algorithm, you can do "for item in Queue" (like Python does). 

In addition to the above, I would just use mathematical notation to describe, for example, set operations on a very high level (Python does some of this too, in list comprehensions!)... most of the time in algorithmics you really don't need to specify all the dirty details of how exactly you do something like set intersection in practice -- it's assumed you can :)

---

### Post by winkyloCC on 2008-11-28
In a statement such as

Declare Number As Integer

Can someone explain what this statement is asking?

Also, where is a good starting point or template when turning a problem into a design for a program? For an assignment I am trying to create menu type program for foriegn currency conversion. Altough I am also having troulbe getting this project off the ground, the most difficult part is making sure all of the details needed are included. In other words Im finding it difficult to expand the modules I have created.

---

### Post by brian77095 on 2008-11-28
> **winkyloCC said:**
> In a statement such as

Declare Number As Integer

Can someone explain what this statement is asking?

Also, where is a good starting point or template when turning a problem into a design for a program? For an assignment I am trying to create menu type program for foriegn currency conversion. Altough I am also having troulbe getting this project off the ground, the most difficult part is making sure all of the details needed are included. In other words Im finding it difficult to expand the modules I have created.



First Welcom to the Forum!!  I hope you experience here will be as fruitful as mine has been so far!

As for your first question.

That statement is telling you to tell the computer that the number or "thing" is a number not just another character.  Once declared you can now tell the computer to add or subtract ect. with other integers...

example 

int = a        this is declaring "a" to be an integer.

Hope that helps and hope that right!!

If not I am sure the others will expound or correct me..

---

### Post by Tony Flury on 2008-11-28
To me that statement could be either :

1) a Pseudo code statement that says you need an integer variable called Number - in whatever language you might be using. 
in C that would be : 
```

int Number;

```
in python - it would not be anything - variables are not strongly typed - the type is defined when it gets its first value.

2) or it could actually be a statement in a high level language, which tells the language that you are creating Variable called Number which is an Integer. I actually vaguely recognise the language (i think) but i am not 100% sure what it is.

---

### Post by slavik on 2008-11-28
since this discussion is about pseudo code and not about languages.

when I write pseudo code, I tend to write it in Perl terms like send a list, for list, etc. I usually write down the more important formulas that come up in my head that I think I might forget.

the idea of pseudo code is to get the important/difficult pieces, the simple stuff you probably already know like the back of your hand.

---

### Post by pmasiar on 2008-11-28
> **Tony Flury said:**
> in python - it would not be anything - variables are not strongly typed - the type is defined when it gets its first value.

wrong and wrong.

1) Python is **strongly** typed language. It's typing is just dynamic, and methods are checked at runtime (late binding), but ie 2 + "3" is not valid (in Perl, which **is** weakly typed, result is 5).

2) Type is not defined with first value. Variable's name just binds name to object of certain type, but type is associated with target (value), not the name. Later you can rebind name to object of different type: all type info (methods etc) is resolved at runtime.

---

### Post by bobbocanfly on 2008-11-28
My pseudo-code is basically just Python, which often means I just skip pseudocode and dive into the Python (this has mixed results, especially when coding when [tired,drunk]). I have even started taking notes in school in Python (this pisses my teachers off greatly).

---

### Post by pp. on 2008-11-28
> **bobbocanfly said:**
> I have even started taking notes in school in Python (this pisses my teachers off greatly).

You might want to learn APL, then.

---

### Post by winkyloCC on 2008-11-28
Thanks for the warm welcome everyone I will be returning here often.

OK, I have seen  the term "int" around a lot and am not sure what it means. I have assumed it is an abbreviation for initialize? Believe it or not the term popped up in my book and nowhere in the book does it define what the term means. It assumes one should know that. My teacher also hates pseudocode but can not change the curriculum. He has suggested submitting assignments in java and he will except it the same. I just don't want to waste time trying to learn something new this late in the course.

I will look at APL however and see if I can make better since out of it.

---

### Post by CptPicard on 2008-11-28
> **winkyloCC said:**
> 
OK, I have seen  the term "int" around a lot and am not sure what it means.

"Integer". Pretty much the most basic data type after booleans/bits :)

> 
I will look at APL however and see if I can make better since out of it.

APL? Oh.. no. Don't go there. :)

---

### Post by pp. on 2008-11-29
> **winkyloCC said:**
> OK, I have seen  the term "int" around a lot and am not sure what it means.

'Int' is short for "integer (number)". An integer number is a number with no digits after the decimal point (and, in fact, no decimal point). In the context of computer programming, there usually are further constraints as to the maximum and minimum values allowed for variables of that type.

> **winkyloCC said:**
> I will look at APL however and see if I can make better since out of it.

Do not look at APL at this point in your curriculum. I suggested using APL to the person who uses Python for the lecture notes just in order to annoy the teachers. APL looks a bit like Greek to most non-Greeks except that it's not that easily readable. It was a joke.

---

### Post by winkyloCC on 2008-12-06
I sometimes see in some pseudocode examples, in parenthesis, the term "floating point". What does this term mean?

---

### Post by nvteighen on 2008-12-06
I guess, some kind if type casting "à la C". In other words: if 'a' is of type 'x' and you want it to be of type 'y' for some context, you'd write: (y) a. That would make the computer interpret 'a' as of type 'y' just for that place.

---

### Post by pp. on 2008-12-06
> **winkyloCC said:**
> the term "floating point". What does this term mean?

It's some kind of number. In contrast to the 'integers' mentioned earlier in the thread, they do have decimals. Think of those much like the numbers used and displayed by your electronic calculator when it's set to 'scientific mode'.

Pocket calculators are still in use nowadays, are they?

BTW, I think it a bit unexpected that you apparently take some programming lessons and do not yet know the most elementary terms for numeric data types.

---

### Post by winkyloCC on 2008-12-06
> **pp. said:**
> It's some kind of number. In contrast to the 'integers' mentioned earlier in the thread, they do have decimals. Think of those much like the numbers used and displayed by your electronic calculator when it's set to 'scientific mode'.

Pocket calculators are still in use nowadays, are they?

BTW, I think it a bit unexpected that you apparently take some programming lessons and do not yet know the most elementary terms for numeric data types.

Thats because the school (University of Phoenix) I attend explain very little. The reading material they provide throws these kinds of terms into the curriculum without any explanation where they came from. The class I am in, noone has a clue expect for people who already work in the field. Even the instructer hates the curriculum. Or so he says. The class is so much of a joke that whenever I go to search engines for help with assignments almost all of the questions are posted on the internet somewhere, word for word. The problem with that is most people who post these questions are only looking for someone to do their homework for them. I am actually trying to get an understanding for the material. Thats why you won't see me posting a homework question but will post for answers to questions I don't know.

---

### Post by pmasiar on 2008-12-07
> **winkyloCC said:**
> explain very little. The reading material they provide throws these kinds of terms into the curriculum without any explanation where they came from. 

You certanly heard about wikipedia: why not to use it? 

ie: [http://en.wikipedia.org/wiki/Floating_point](http://en.wikipedia.org/wiki/Floating_point)

Also, check wikiversity for more consistent curriculum, and howStuffWorks.com for explaininf basic concepts in simple terms.

It's a plus that you really try to learn instead of getting someone to do your homework, but wikipedia has most (all?) the answers for that kind of questions. Good luck!

---

### Post by YankeeRose33 on 2009-05-01
Can anyone help explain the whole psuedocode/algorithm logic thing? I am in a fundamentals of programming class, and find this particular topic rather difficult to grasp. I have absolutely NO knowledge of any programming, and this is the first exposure that I have had so far to this concept. 
I have spent the last 10 years or so doing construction, fabrication and manufacturing, but am now forced to change career path due to disability from that work.

---

### Post by samjh on 2009-05-01
Pseudo-code is "false code".  It's a kind of fake programming language used to describe programming logic without being tied up with the specific features or rules of any particular programming language.

The simplest form of pseudo code is to literally translate normal English into something that looks vaguely like code.

Example:
```
IF person's age > 18 THEN
    bartender can serve alcohol = true.
```

A programmer can then use that information to turn it into proper code for a programming language.  I could take the above example and translate it into C programming language...
```
if (person.age > 18) {
    bartender.servealcohol = 1;
}
```
... or the Python programming language...
```
if person.age > 18:
    bartender.servealcohol = true
```
... and so on.

Pseudo-code gives programmers the ability to express the way an algorithm works in a semi-structured manner, in a way that is clearer than using natural English, but more flexible and easy to read than a real programming language.

---


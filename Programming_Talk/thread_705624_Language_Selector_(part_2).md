---
title: "Language Selector (part 2)"
date: 2008-02-23
forum: Programming Talk
---

### Post by Fbot1 on 2008-02-23
Same idea as
[http://ubuntuforums.org/showthread.php?t=701278](http://ubuntuforums.org/showthread.php?t=701278)

but with a simple set theoretic approach instead. Fill free to change it or suggest something.

(If you have Firefox (any version I think), you can copy this into your url bar and press go to run it)
```

javascript:

var i,j,m;
var ASM,HLA,c,csharp,cpp,d,java,javascript,pascal,perl,python;
m=ASM=HLA=c=csharp=cpp=d=java=javascript=pascal=perl=python=0;

i = prompt('What kind of interface?\nx for windowed,\ng for normal 3D graphics,\ne for 3D graphics by a specalized engine,\nanything else skips it.', '');
if(i=="x"){
	m++;c++;csharp++;cpp++;d++;java++;pascal++;perl++;python++;
	i = prompt('Do you want to use both Gtk and Qt portably? y for yes, anything else skips it.', '');
	if(i=="y"){m++;pascal++;}
}
else if(i=="g"){m++;c++;cpp++;perl++;}
else if(i=="e"){}

i = prompt('Do you want to access the hardware directly? y for yes, n for no, anything else skips it.', '');
if(i=="y"){m++;ASM++;c++;cpp++;d++;HLA++;pascal++;}
else if(i=="n"){m++;csharp++;java++;javascript++;perl++;python++;}

i = prompt('Should it be popular? y for yes, n for no, anything else skips it.', '');
if(i=="y"){m++;c++;csharp++;cpp++;java++;javascript++;perl++;python++;}
else if(i=="n"){m++;ASM++;d++;HLA++;pascal++;}

i = prompt('Should it be C-like? y for yes, n for no, anything else skips it.', '');
if(i=="y"){m++;c++;csharp++;cpp++;d++;HLA++;java++;javascript++;}
else if(i=="n"){m++;ASM++;pascal++;perl++;python++;}

i = "The following are suggested:";
do{
	if(ASM==m){i=i+"\nAssembly"}
	if(HLA==m){i=i+"\nHigh level assembly"}
	if(c==m){i=i+"\nC"}
	if(cpp==m){i=i+"\nC++"}
	if(csharp==m){i=i+"\nC#"}
	if(d==m){i=i+"\nD"}
	if(java==m){i=i+"\nJava"}
	if(javascript==m){i=i+"\nJavascript"}
	if(pascal==m){i=i+"\nPascal"}
	if(perl==m){i=i+"\nPerl"}
	if(python==m){i=i+"\nPython"}
	i=i+"\n--";
	m--;
}while(m != 0);
alert(i);

```

---

### Post by Fbot1 on 2008-02-23
No one has anything to suggest? :(

---

### Post by LaRoza on 2008-02-23
I will get back to this. I am going to use it for a more standard approach.

---

### Post by Fbot1 on 2008-02-23
> **LaRoza said:**
> I will get back to this. I am going to use it for a more standard approach.

What do you mean?

---

### Post by LaRoza on 2008-02-23
> **Fbot1 said:**
> What do you mean?

I am going to make it usable from a web page. (Nothing big, just click a button to start it)

The javascript: protocol doesn't always work, and it would be easier for me to test it (I don't use Firefox) though a browser.

---

### Post by Fbot1 on 2008-02-23
> **LaRoza said:**
> The javascript: protocol does always work

neat

---

### Post by LaRoza on 2008-02-23
> **Fbot1 said:**
> neat

Sorry, I mean't **doesn't**

I rewrote the code, but changed no logic, just semantics.

[php]
        var i;
        var ASM,HLA,c,csharp,cpp,d,java,javascript,perl,python;
        ASM=HLA=c=csharp=cpp=d=java=javascript=perl=python=true;

        i = confirm('Do you want to access the hardware directly? Ok for yes, Cancel for no.', '');
        i ? csharp=java=javascript=perl=python=false : ASM=c=cpp=d=HLA=false;;

        i = confirm('Should it be popular? Ok for yes, Cancel for no.', '');
        i ? ASM=d=HLA=false : c=csharp=cpp=java=javascript=perl=python=false;

        i = confirm('Should it be C-like? Ok for yes, Cancel for no.', '');
        i ? ASM=perl=python=false : c=csharp=cpp=d=HLA=java=javascript=false;

        i = "The following are suggested:";
        ASM==true ? i+="\nAssembly" : false;

        HLA==true ? i+="\nHigh level assembly" : false;
        c==true ? i+="\nC" : false;
        cpp==true ? i+="\nC++" : false;
        csharp==true ? i+="\nC#" : false;
        d==true ? i+="\nD" : false;
        java==true ? i+="\nJava" : false;
        javascript==true ? i+="\nJavascript" : false;
        perl==true ? i+="\nPerl" : false;
        python==true ? i+="\nPython" : false;
        alert(i);
        return false;
[/php]

I am going to upload it, so it can be tested by others and yourself.

[http://laroza.freehostia.com/prog/](http://laroza.freehostia.com/prog/)

---

### Post by Fbot1 on 2008-02-23
> **LaRoza said:**
> Sorry, I meant **doesn't**
Okay

> **LaRoza said:**
> 
I rewrote the code, but changed no logic, just semantics.
[php]
...
        i = confirm('Do you want to access the hardware directly? Ok for yes, Cancel for no.', '');
...
        i = confirm('Should it be popular? Ok for yes, Cancel for no.', '');
...
        i = confirm('Should it be C-like? Ok for yes, Cancel for no.', '');
...
[/php]


The reason I used prompt instead was so they could skip the question if they didn't care. So in that way it's a little different.

---

### Post by LaRoza on 2008-02-23
> **Fbot1 said:**
> Okay



The reason I used prompt instead was so they could skip the question if they didn't care. So in that way it's a little different.

Ideally, there should be a three button prompt. I could code that, but not on the spot.

---

### Post by Fbot1 on 2008-02-24
No one has anything to add?

---

### Post by seventhc on 2008-02-24
If you choose *y, y, n *or from the page **LaRoza** put up *ok, ok, cancel*
it doesn't offer a language selection.
I was trying to see the different outcomes based on my selections, choosing differently each time.

---

### Post by Fbot1 on 2008-02-24
> **seventhc said:**
> If you choose *y, y, n *or from the page **LaRoza** put up *ok, ok, cancel*
it doesn't offer a language selection.
I was trying to see the different outcomes based on my selections, choosing differently each time.

There doesn't seem to be one.

---

### Post by seventhc on 2008-02-24
Oh, OK...I thought it would give back *Python* as a selection.

---

### Post by LaRoza on 2008-02-24
It doesn't give anything for the original (Y,Y,N) either.

I like the idea, though.

@Fbot1 Perhaps you want to refine the questions and logic?

---

### Post by Fbot1 on 2008-02-24
> **LaRoza said:**
> Perhaps you want to refine the questions and logic?

What do you suggest?

---

### Post by LaRoza on 2008-02-24
> **Fbot1 said:**
> What do you suggest?

I suggest questions and languages that come up on the forum.

Perhaps you can use the languages on my selector (and the ones you have) and make it more precise.

Mine is for learning, your script seems to be for chosing a language for the task. It might make a good combo.

---

### Post by seventhc on 2008-02-24
> It doesn't give anything for the original (Y,Y,N) either.
I know, I mentioned both. but maybe the way I worded it doesn't look right.
But I was mentioning for both. 
here it is again, with the 'or' in bold. ;)
> If you choose y, y, n **or** from the page LaRoza put up ok, ok, cancel

---

### Post by LaRoza on 2008-02-24
> **seventhc said:**
> I know, I mentioned both. but maybe the way I worded it doesn't look right.
But I was mentioning for both. 
here it is again, with the 'or' in bold. ;)

Oh, my code is the same as the other, just using booleans. The logic is exactly the same, for practicle purposes.

---

### Post by slavik on 2008-02-24
this is what I call hacking, nice one :)

how about "javascript in the address bar"

---

### Post by LaRoza on 2008-02-24
> **slavik said:**
> this is what I call hacking, nice one :)

how about "javascript in the address bar"

It is taking advantage of the "javascript:" protocal, which isn't standard.

You usually only see:

```

<a href="javascript:popup(this);" title="See me">Click This</a>

```

But you can put as many statements in there as one likes for browsers that can do that.

---

### Post by scourge on 2008-02-24
> **Fbot1 said:**
> No one has anything to add?

There's a lot that can be added. For example:

- Do you want to develop cross-platform applications?
- Do you want to create a graphical user interface?
- Do you need OpenGL (i.e. for a game)?
- Are there heavy performance requirements (not the same thing as access to hardware)
- Should the language be object-oriented?

---

### Post by Wybiral on 2008-02-24
What if it scores them instead of making them go away (some question will increase the score, others may decrease the score) then you can sort them by relevance at the end. That way there is never a case where NO language is suggested, they are just shown from most likely to least likely.

---

### Post by slavik on 2008-02-24
how about organising the languages into a tree?

---

### Post by Fbot1 on 2008-02-25
> **scourge said:**
> There's a lot that can be added. For example:

- Do you want to develop cross-platform applications?
- Do you want to create a graphical user interface?
- Do you need OpenGL (i.e. for a game)?
- Are there heavy performance requirements (not the same thing as access to hardware)
- Should the language be object-oriented?
I avoided object-orientation and the term cross-platform because they really aren't very telling.

> **Wybiral said:**
> What if it scores them instead of making them go away (some question will increase the score, others may decrease the score) then you can sort them by relevance at the end. That way there is never a case where NO language is suggested, they are just shown from most likely to least likely.
The newer one does this (well, kinda).

> **slavik said:**
> how about organizing the languages into a tree?
I'll do it when it's appropriate.

---

### Post by sznurek on 2008-02-26
My turn :) I give examples in pseudocode - i don't know Javascript.
[PHP]
class Language:
    string name
    string description

class Python extends Language:
    name = "Python"
    description = "1337 l4ngu4g3!!111"

class Question:
    string name
    string description
    function pointsFor(Language l, Boolean b):
        if typeof(l) == Python:
            return b ? 2 : -2

class DumbQuestion extends Question:
    name = "Dumb"
    description "Yes, no, nothing...?"
    function pointsFor(Language l, Boolean b):
        if typeof(l) == Python:
            return b ? 2 : -2
        // etc...

[/PHP]

Now we need to organize questions some way:
[PHP]
class Node:
    Question q
    Node forYes
    Node foNo
    Node forNothing // All nodes is references
[/PHP]

Then we can make a question tree:
[PHP]
Question q1 = new PortabilityQuestion()
Question q2 = new SpeedQuestion()
Question q3 = new DumbQuestion()
Node yesNo = new Node()
yesNo.q = q2
Node nothing = new Node()
nothing.q = q3
Node parent = new Node()
parent.q = q1
parent.forYes = parent.forNo = yesNo
parent.forNothing = nothing
[/PHP]
OK, now we have question tree :) The rest:
[PHP]
class Analyser:
    array_of_all_languages langs
    Hash points // hash : keys is languages, values is points
    Node questionTree
    function do_the_job():
        Node current = questionTree
        result = show_question(current.q)
        if result != CANCEL:
            for_each_language l:
                points[l] += current.q.pointsFor(l, result)
        show_next_question() // I don't have time to write all :)
        sort_by_points(points)
        return hash
// Then you simply print the first 5 :)
        
[/PHP]

I hope you get the point :) Maybe it is too complicated for this simple app, but I like apps coded this way. Maybe it IS wrong. I've warned you.

I'm curious it is good design of classes - can somebody check it out and post reply?

But javascript don't have classes... right?

Bless.

---

### Post by LaRoza on 2008-02-26
> **sznurek said:**
> 
But javascript don't have classes... right?



ECMAScript does have objects, but **doesn't** use classes. It uses prototypes.

---


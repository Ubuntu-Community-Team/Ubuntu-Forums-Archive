---
title: "perl or python"
date: 2008-10-24
forum: Recurring Discussions
---

### Post by muteXe on 2008-10-24
Afternoon,
I admit i've not done much research yet, so don't take my head off please.  I'm wanting to learn a new language and i'm thinking either perl or python.  I'd like a language I can quickly test out functions that i'd go on to write in c# or c++.
Any ideas would be great thank you,

Tom

---

### Post by ghostdog74 on 2008-10-24
> **muteXe said:**
> Afternoon,
I admit i've not done much research yet

then please do so.
> 
Any ideas would be great thank you,

Tom

type "Perl vs Python" in google search.

---

### Post by LaRoza on 2008-10-24
> **ghostdog74 said:**
> 
type "Perl vs Python" in google search.

See these threads: [http://ubuntuforums.org/showthread.php?p=4716120](http://ubuntuforums.org/showthread.php?p=4716120)

Since nothing good can come of this thread, moved to Recurring Discussions.

---

### Post by sheto on 2008-10-25
I say Python. Easier, faster, smarter.

---

### Post by Canis familiaris on 2008-10-25
Or both? I plan to learn both, just for fun. Currently Python though.

---

### Post by LaRoza on 2008-10-25
> **Anurag_panda said:**
> Or both? I plan to learn both, just for fun. Currently Python though.

I tried that.

It is very hard to get far if you know one. Python/Perl/Ruby are sort of in the same niche, although they are each different.

Once you know one, it is hard to learn the others, mainly because it is boring.

---

### Post by ghostdog74 on 2008-10-25
> **LaRoza said:**
> 

Once you know one, it is hard to learn the others, mainly because it is boring.

it will not be boring when you are paid to solve problems in each of those languages.

---

### Post by loell on 2008-10-25
both.. the more you code in python the more you wished you could make it shorter, hence you'd be wanting to venture in perl.

---

### Post by LaRoza on 2008-10-25
> **ghostdog74 said:**
> it will not be boring when you are paid to solve problems in each of those languages.

Almost anything is worthwhile if one is getting paid.

---

### Post by y-lee on 2008-10-25
A few months ago I decided to get back into programming after 8 years of not programming at all. and out of the several languages I wanted to learn or learn better, I chose python as to the language to focus on. It is easy to learn and incredibly powerful and very expressive. I certainly recommend it over perl which is powerful and expressive but hardly on anyones list as easy to learn.

> **loell said:**
> both.. the more you code in python the more you wished you could make it shorter, hence you'd be wanting to venture in perl.

I disagree with this statement for several reason. First and foremost conciseness is hardly a virtue in programming, it is far more important for your code to be understandable. And secondly Python can be every bit as concise and also sadly hard to understand as Perl if not more so. It might be unpythonic to code like that but rest assured it can be done. Consider the below permutation function as an example:

```
>>> perm = lambda x: reduce(lambda r, a: [p[:i] + [a] + p[i:] for p in r for i in range(len(p)+1)], x[1:], [x[:1]])
>>> print perm(['a', 'b', 'c'])
[['c', 'b', 'a'], ['b', 'c', 'a'], ['b', 'a', 'c'], ['c', 'a', 'b'], ['a', 'c', 'b'], ['a', 'b', 'c']]
>>>

```

Concise to the point and hardly easy to understand. Now compare this with one of my first permutation algorithms in python:

```
def perm(p):
    result = []
    # Stop recursion if length p = 1
    if len(p) == 1:
        result.append(p)
        return result
    # recursively generate permutations of p[1]...p[n]
    simpler = perm(p[1: ])
    # for each permutation, add the first element in all possible positions
    for permutation in simpler: 
        additions = insert(p[0], permutation)
        for a in additions:
            result.append(a)
    return result
    

def insert(ch, s):
    result = []
    # insert ch in every position in list s and add to result
    for i in range(len(s) + 1):
        inserted = s[0: i] + [ch] + s[i: ]
        result.append(inserted)
    return result   

print perm([0, 1, 2])    

```

Which would you rather try to read, debug or modify? And btw neither of these  are particularly great ways to generate permutations, well sorta they are same algorithm. But they are simple to understand and the first illustrates my point that one can be incredibly concise programming in python, I could have gave an even more complex example but programming like that to me is the height of stupidity. It is not particularly bad in the perm example above but if one takes it to extremes one produces code one will not even understand a month later.

---

### Post by loell on 2008-10-25
lamba is hardly considered concise yet readable, 

in python where is the switch statement without resorting to dictionaries? and where is the ternary operator?.. you know, little things like this that make conditionals concise yet readable, would want to make you check back on perl or ruby.

---

### Post by LaRoza on 2008-10-25
> **loell said:**
> lamba is hardly considered concise yet readable, 

You reject the abilities of Python while attacking what it lacks, really not worth debating.

---

### Post by loell on 2008-10-26
> **LaRoza said:**
> You reject the abilities of Python while attacking what it lacks, really not worth debating.

you already put the thread in recurring, so debating on what's worth debating is not worth debating. 

it is my impression that this is what's recurring for.

---

### Post by ghostdog74 on 2008-10-26
what's there to argue and debate about? You all can argue till the cows come home but it will all be just one ultimate conclusion. There will no real answer because its all to each his own.

---

### Post by loell on 2008-10-26
> **ghostdog74 said:**
> what's there to argue and debate about? You all can argue till the cows come home but it will all be just one ultimate conclusion. There will no real answer because its all to each his own.

there is none, its just the way people responds back and forth, you bite, they bite back, at the end every laughs smile or smear  at least.

---

### Post by y-lee on 2008-10-26
> **loell said:**
> lamba is hardly considered concise yet readable, 

in python where is the switch statement without resorting to dictionaries? and where is the ternary operator?.. you know, little things like this that make conditionals concise yet readable, would want to make you check back on perl or ruby.

Come on at least know what you are talking about. How is a **switch** statement different than a **if...elif...elif ...else** in anything other than name?

However in my opinion long switch statements and/or long if then else statements are a sign your code needs refactored amd probably should be replace with something else, like an array of function pointers to use C terminology.

But regardless of that your second point: ternary operator? Yeah python has it:
```

x = 3 if (y == 1) else 2
```

Both perl and python are great languages and both have faults and perhaps lack this or that that another language may provide. Both being turing complete languages they of course are capable of doing anything one can do in any other language (In theory).  But imho I think python is easier to learn and any claims that python is not as concise as perl are misfounded and probably the result of someone not knowing python well.

And btw I was hardly claiming complex lambda expressions are readable, they are if you are used to it but for a beginner they are best left alone.

---

### Post by cardinals_fan on 2008-10-26
Perl: there is no substitute!

Seriously, it depends on what you want to accomplish.  When you want to pull information off a website and parse out the details you need, Perl can't be beat.  For other things, Python might be better.

---

### Post by LaRoza on 2008-10-26
> **y-lee said:**
> Come on at least know what you are talking about. How is a **switch** statement different than a **if...elif...elif ...else** in anything other than name?


A switch statement will execute all of the conditions and won't do an "else" by default and requires use of "breaks", essentially, switches are contained goto's.

And lambdas can be good for beginners.

> **cardinals_fan said:**
> 
Seriously, it depends on what you want to accomplish.  When you want to pull information off a website and parse out the details you need, Perl can't be beat.  For other things, Python might be better.
Um... It is trivial in Python as well. Also, Perl would be using RE probably, unlike the html and xml parsers of Python.

---

### Post by cardinals_fan on 2008-10-26
> **LaRoza said:**
> 
Um... It is trivial in Python as well. Also, Perl would be using RE probably, unlike the html and xml parsers of Python.
Yes, but Perl has always struck me as the best language for sorting through text files (or web pages, which essentially **are** text files).  There's a reason it earned the acronyms Practical Extraction and Report Language and Pathologically Eclectic Rubbish Lister.

In the end, it all comes down to personal experience, which in turn comes down to personal opinion.

---

### Post by y-lee on 2008-10-26
> **LaRoza said:**
> A switch statement will execute all of the conditions and won't do an "else" by default and requires use of "breaks", essentially, switches are contained goto's.

And lambdas can be good for beginners.


Hmm what you have described LaRoza is the standard C version of a switch case statement that allows "fall throughs." Not all languages implement switch in such a manner, as an example of one that does not the [programming language]("http://en.wikipedia.org/wiki/RPL_programming_language") on my HP 48 calculator. And yeah I consider it a real language (I like it too I think it is a cute language :))

But anyway my point was that in the classic and most used form of a switch statement in some C like language:

```
switch (value) {
    case 'a':
        result = x * 5;
        break;
    case 'b':
        result = x + 7;
        break;
    case 'c':
        result = x - 2;
        break;
}

```

in python is nothing more than

```
if value == 'a':
    result = x * 5
elif value == 'b':
    result = x + 7
elif value == 'c':
    result = x - 2
```

Situations involving more complex switch statements, including fall throughs can also be  achieved using a combination of *if ,if elif* and so on. One also has [other options]("http://stackoverflow.com/questions/60208/replacements-for-switch-statement-in-python") in python aside from this solution.

But since this is discussion of the virtues of perl vs python I find it ironic switch was even mentioned as perl currently has no switch statement. It is my understanding that this is going to be added to perl 6.0, but now perl users either use hash tables, if statements or a switch module. As to a switch module one could easily write a switch module for python, [in python even]("http://code.activestate.com/recipes/410692/").

And as to the "*And lambdas can be good for beginners.*" If I were teaching *an introduction to programming* college class using python lambdas and functional programming techniques would be covered toward the end of the semester. assuming I was teaching absolute beginners. But if the python class was for students already familiar with programming in one or more languages lambdas would be introduced much earlier. And btw I did used to teach programming classes in college, it has been a while tho :)

> **cardinals_fan said:**
> In the end, it all comes down to personal experience, which in turn comes down to personal opinion.

Precisely language wars are ridiculous :)

---

### Post by LaRoza on 2008-10-27
> **y-lee said:**
> But anyway my point was that in the classic and most used form of a switch statement in some C like language:

Ah, that is true, the effect of them is the same (although, I have used fall throughs many times).

> 
And as to the "*And lambdas can be good for beginners.*" If I were teaching *an introduction to programming* college class using python lambdas and functional programming techniques would be covered toward the end of the semester. assuming I was teaching absolute beginners. But if the python class was for students already familiar with programming in one or more languages lambdas would be introduced much earlier. And btw I did used to teach programming classes in college, it has been a while tho :)

It would depend on the class. MIT when they used Scheme almost certain used lambdas from the near beginning. An intro using C++ wouldn't even consider the concept.

---


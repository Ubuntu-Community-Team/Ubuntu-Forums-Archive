---
title: "Fortan 77 Programming Help"
date: 2008-02-11
forum: Programming Talk
---

### Post by DivineNuker on 2008-02-11
I don't know how to do this please i need serious help.

THe question is as follows:

The square of the sine function can be represented by the following:

sin^2x = x^2 - (2^3* x^4)/ (4!) + (2^5 * x^6)/(6!) -..... = SUM OF ((-1)^(n+1) * 2^(2n-1) * x^2n) / (2n)!

Write a program to evaluate this series for an input value, x, printing the results after 2,4,6,8,......14 terms and comparing each sum to the true solution. Note that the term for n=1 is x^2 and that all consecutive terms can be obtained by multiplying the previous term by
 -(2x)^2/ (2n(2n-1))

The Output should have the following form:

                    [b][center] Comparison of Values of Sine Squared[/center]

[left]Number of Terms[/left]  [center] Series Summation                        Intrinsic Function[/center] [right]  Difference[/right]
[left]2[/left]  [center]  xx.xxxx     xx.xxxx [/center]  [right]          xx.xxxx[/right]
[left]4[/left] [center]xx.xxxx       xx.xxxx  [/center]  [right]         xx.xxxx[/right]
[left].
.
.
14[/left]

*** NOTE Series Summation and Intrinsic Functions are two different columns. I did my best with Bbcode formating :D *** 

[/b]
I have a little bit of the program written by for the love of god I cant figure out how to do it. The format of the output is one of the many things i cant figure out how to do. I don't even understand the question completely.

THis program is to be written in Fortran 77 of course

I would be eternally grateful if someone can help me out with it

THANKS>

---

### Post by aks44 on 2008-02-11
[http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2](http://www.parashift.com/c++-faq-lite/how-to-post.html#faq-5.2)

[QUOTE=C++ FAQ Lite]If I did your homework for you, then you might pass your class without learning how to write a program like this. Then you might graduate and get your degree without learning how to write a program like this. You might become a professional programmer without knowing how to write a program like this. Someday you might work on a project with me without knowing how to write a program like this. Then I would have to do you serious bodily harm.[/QUOTE]

---

### Post by DivineNuker on 2008-02-11
I don't want you to write the exact source code... i want HELP on "HOW" to do this... Explain what the question actually is asking because I do not understand it.. And help me on what needs to be done.. I AM NOT ASKING you to write the source code so i can copy it.... I dont want that.. i have a test in a few days i Need to learn this stuff. 

If you do not want to help me.. then don't post plz..

---

### Post by aks44 on 2008-02-11
> **DivineNuker said:**
> I don't want you to write the exact source code... i want HELP on "HOW" to do this... Explain what the question actually is asking because I do not understand it.. And help me on what needs to be done.. I AM NOT ASKING you to write the source code so i can copy it.... I dont want that.. i have a test in a few days i Need to learn this stuff. 

If you do not want to help me.. then don't post plz..

That's not a problem of "not wanting to help you" but the tone of your post implied that you were expecting to be spoon-fed ("Write a program that..."). We get so many queries for doing people's homework here (without them actually willing to understand anything) that we get quite defensive. Especially when this is someone's first post on this forum.


Sooo... I can't really help you with FORTRAN, but here's the big picture:

- have a function that takes the input value and the number of terms as arguments, which will calculate the polynomial sum.

- have a loop (2...14) that calls that function, calculate the difference with built-in **sin(x)^2** and display the results accordingly.


Hope this helps.

---

### Post by DivineNuker on 2008-02-11
Thanks that helped a lot

About the "Write a program" i apologize for that but i was just copying the question that I was asked i never thought it would be taken as I was asking this forum community to write a program..

Thanks

Im trying it out.. i think i got it but it has a few problems

THanks for help

---

### Post by aks44 on 2008-02-11
One more advice: don't focus on the presentation (columns, ...) right now. Just make it work correctly, you'll add the "bells and whistles" later. ;)

---

### Post by DivineNuker on 2008-02-11
Hey aks44,

 ok i got most of it done.. heres the only problem..

U said use the built-in (intrinsic) sinx^2 funciton.. but the problem is that that built in function has X as its only argument.. so how would i do it do it accounts for each TERM N from 2 - 14 (increment 2)

The actual polynomial sum without the intrinsic function had both X and N so that was easy.. but the sinx^2 only has X so ... it will spit out the same value for the same X for each different N

Please can you explain/help me on this

thanks

EDIT:: Wow nvm.. i think i got it T_T

---

### Post by happysmileman on 2008-02-11
> **DivineNuker said:**
> 
U said use the built-in (intrinsic) sinx^2 funciton.. but the problem is that that built in function has X as its only argument.. so how would i do it do it accounts for each TERM N from 2 - 14 (increment 2)

I might misunderstand what you're saying, but if you mean what I think you mean, there's probably a FOR statement in fortran:

```

for (x=2; x<=14; x+=2)
{
    //Do whatever, x will have value of two, then it'll repeat this for 4, then 6, 8, 10, 12, 14
}

```

Would be how you do it in C/C++, so assuming there's an equivalent FOR statement in FORTRAN77 (almost all programming languages have one) you should be able to use it very similarly.

---

### Post by LaRoza on 2008-02-11
> **happysmileman said:**
> I might misunderstand what you're saying, but if you mean what I think you mean, there's probably a FOR statement in fortran:


[http://www.tat.physik.uni-tuebingen.de/~kley/lehre/ftn77/tutorial/loops.html](http://www.tat.physik.uni-tuebingen.de/~kley/lehre/ftn77/tutorial/loops.html)

You can also use goto's for looping.

---

### Post by aks44 on 2008-02-11
> **DivineNuker said:**
> The actual polynomial sum without the intrinsic function had both X and N so that was easy.. but the sinx^2 only has X so ... it will spit out the same value for the same X for each different N

And (besides the pure programming part) the goal of the whole homework is to...? :-s


Looks like you're not only having trouble with the technical (FORTRAN) part, but also with the mathematical approach of the question?

---

### Post by DivineNuker on 2008-02-11
oK I got the program done..

just  need help on formatting

Does anyone happen to know... how can i make a table like structure.. like

[left]Heading1[/left]      [center]heading 2[/center]
[left]blah1 [/left]              [center]blah1[/center]
[left]blah2    [/left]          [center] blah2[/center]
[left]blah 3  [/left]          [center] blah 3[/center]

Basically LEFT Center Right justification.. anyone got any idea to do it in Fortan 77? 

Thanks

---

### Post by LaRoza on 2008-02-11
I suggest talking to your teacher for help. It seems you don't understand the math or language.

See [http://www.tat.physik.uni-tuebingen.de/~kley/lehre/ftn77/tutorial/](http://www.tat.physik.uni-tuebingen.de/~kley/lehre/ftn77/tutorial/) although I assume you have book on it.

How to format output: [http://www-teaching.physics.ox.ac.uk/Unix+Prog/hargrove/tutorial_77/17_format.html](http://www-teaching.physics.ox.ac.uk/Unix+Prog/hargrove/tutorial_77/17_format.html)

It is this forum's policy not to do homework. If you have trouble with Fortran on Ubuntu or want someone to check your answer, then you can ask.

---

### Post by DivineNuker on 2008-02-11
Ok fine

---

### Post by LaRoza on 2008-02-11
You wan't help, but not the code. I gave links to what you need, that should be enough.

---


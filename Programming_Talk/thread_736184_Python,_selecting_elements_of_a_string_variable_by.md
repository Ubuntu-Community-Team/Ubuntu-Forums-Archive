---
title: "Python, selecting elements of a string variable by type"
date: 2008-03-26
forum: Programming Talk
---

### Post by clanky on 2008-03-26
I am trying to write a python program which solves quadratic equations, to do so I need to take a quadratic equation entered by the user in the form of

y=ax**2+bx+c

where a, b and c are integers, and extract them from the string for use in a formula.  Is there a simple way to do this?  I can work round it by asking for inputs of each element individually, but I feel that the first approach would be a bit more polished.

---

### Post by WW on 2008-03-26
If I had to use your program more than twice, I would not want to have to type the variables and plus signs every time.  Simply asking for a, b, and c is a better interface, IMHO. I have to type less, and there is less chance of making a mistake.

If you stick with the idea of parsing the string, how flexible will your code be?  Are all of the following acceptable:  "4 x^2 - 7 x +1", "4x-8", "14", "-4 x**2 + 10", "13 - 8x + -8x^2" ?

---

### Post by Lord Illidan on 2008-03-26
I too am in the favour of doing it in the a b c format, it leaves less space for error, and it's also easier to code.

---

### Post by clanky on 2008-03-26
Thanks guys, I am really only writing it as a way of learning the language, I see your point about being easier from the users point of view, but in terms of learning what python can do, would it be possible to extract an integer from a string variable and use it in a calculation?

---

### Post by nanotube on 2008-03-26
> **clanky said:**
> Thanks guys, I am really only writing it as a way of learning the language, I see your point about being easier from the users point of view, but in terms of learning what python can do, would it be possible to extract an integer from a string variable and use it in a calculation?

using regexps (the re module) is probably your best bet and would produce the most robust and flexible code. check it out in the docs. :)

---

### Post by WW on 2008-03-26
> **clanky said:**
> [...] learning what python can do, would it be possible to extract an integer from a string variable and use it in a calculation?
Yes, and it's a good exercise for learning how to work with strings (and possibly "regular expressions", if you choose to use that tool).  How much code you'll have to write depends on how much freedom you'll allow the user when entering the formula.

---

### Post by bvmou on 2008-03-26
Here is a way to do what you want, in a way that only uses language basics.  I added a step to remove whitespace if you get input like "y = x**2 + 2x + 1"  All the variables are sequential from 'm', so 'm' is the first step, 'n' is the second, etc.

```

Python 2.5.2 (r252:60911, Mar 12 2008, 13:36:25) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> m = raw_input()
y = 12x**2 + 123x + 1234
>>> m
'y = 12x**2 + 123x + 1234'
>>> n = m.split("=")
>>> n
['y ', ' 12x**2 + 123x + 1234']
>>> o = n[1]
>>> o
' 12x**2 + 123x + 1234'
>>> p = o.split("+")
>>> p
[' 12x**2 ', ' 123x ', ' 1234']
>>> q = []
>>> for item in p:
...     r = item.replace(" ", "")
...     q.append(r)
... 
>>> q
['12x**2', '123x', '1234']
>>> a = q[0][:-4]
>>> a
'12'
>>> a = int(a)
>>> a
12
>>> b = q[1][:-1]
>>> b
'123'
>>> b = int(b)
>>> b
123
>>> c = q[2]
>>> c
'1234'
>>> c = int(c)
>>> c
1234

```

---

### Post by LaRoza on 2008-03-26
It is best to take the values, and not the equation. The above program snippets makes a lot of assumptions (integers, the use of '+', the existance of terms) as it is just a demonstration. To make something that can read the human equation and not be fragile would be much more work than to write something that can solve quadratic equations. 

Here is the one I wrote a while ago (just for learning, I haven't looked at it since).
[php]
c PROGRAM TO SOLVE QUADRATIC EQUATIONS        
        program hw
        real A, B, C, D

        write (*,*) 'General form: Ax2 + Bx + C = 0'

c GET THE VALUES

        write (*,*) 'Enter A, B, C '
        read (*,*) A, B, C

c FIND OUT IF IT IS LINEAR, QUADRATIC, OR TRIVIAL

        if (A .eq. 0) then
c SOLVE A LINEAR EQUATION
            if (B .eq. 0) then
                if (C .eq. 0) then
                    write (*,*) 'Is trivial'
                else
                    write (*,*) 'Is impossible'
                end if
            else
                write (*,*) 'X = ', -C/B
            end if
C SOLVE A QUADRATIC EQUATION
        else

            D = B**2 - 4*A*C
            if (D .ge. 0) then
                if (D .gt. 0) then
                    write (*,*) 'Has two solutions'
                    write (*,*) 'X(1) = ', (-B + D**.5)/(2*A)
                    write (*,*) 'X(2) = ', (-B - D**.5)/(2*A)
                else
                    write (*,*) 'Has one solution'
                    write (*,*) 'X = ', -B/(2*A)
                end if
            else 
                write (*,*) 'Has two complex solutios'
                write (*,*) -B/(2*A), ' + or - ', (-D)**.5/(2*A), ' *I'
            end if
        end if

        stop
        end
[/php]

---

### Post by bvmou on 2008-03-26
Yes, that is not so much a program as food for thought.  You can substitute float(a) in the above, for example, where necessary.  The question as I understand it is more to do with turning the user's long string input into something useful, to learn how to do it, rather than evaluating the equation itself, which is clearly better done with another kind of input.  The useful stuff in that case are things like 'replace', so if you get, for example - rather than +, you can pop in something like:

```
>>> m
'y = 12x**2 + 2x -6'
>>> n = m.replace("-", "+ -")
>>> n
'y = 12x**2 + 2x + -6'
>>> 
```

---

### Post by WW on 2008-03-26
> **bvmou said:**
>  [...] if you get, for example - rather than +, you can pop in something like:
```
>>> m
'y = 12x**2 + 2x -6'
>>> n = m.replace("-", "+ -")
>>> n
'y = 12x**2 + 2x + -6'
>>> 
```

Be careful;  the formula "-12x**2 + -2x - -6" should be considered legitimate input.  (Of course, what the program considers to be valid is up to the designer, as long as the user knows the rules, too.)  Another issue to consider: If a=0, does the user have to enter "0x**2+..."?  Likewise for a=1, and for the other coefficients.

---

### Post by clanky on 2008-03-26
Guys, thank you all very much, fantastic help.

I am off back to sea for 3 months on 7th April, so I want to get my head around as much of Ubuntu and Python as I can before i go, because after that it will just be me and a book!

---

### Post by pmasiar on 2008-03-26
Get [Martelli's Python Cookbook](http://www.buy.com/prod/python-cookbook-2nd-edition/q/loc/106/30893191.html) - will show you all kinds of tricks. Get also other O'Reilly's books (Learnig Python etc), if it's only you and book, you want couple books (showing the same thing from multiple angles). Check also website in my sig, it has many training tasks for beginners, so you will have something to code.

Good luck, looks like you live interesting life!

---

### Post by mssever on 2008-03-26
> **LaRoza said:**
> Here is the one I wrote a while ago (just for learning, I haven't looked at it since).

Which language is that? I don't recognize it.

---

### Post by pmasiar on 2008-03-26
> **mssever said:**
> Which language is that? I don't recognize it.

Fortran?

---

### Post by LaRoza on 2008-03-26
> **mssever said:**
> Which language is that? I don't recognize it.

> **pmasiar said:**
> Fortran?

Fortran 77

---

### Post by mssever on 2008-03-27
> **LaRoza said:**
> Fortran 77
Well, that destroys what I thought I knew about Fortran. I had thought that it was based on code being in specific columns (perhaps due to punchcard influence), but apparently I'm wrong.

---

### Post by clanky on 2008-03-27
> **pmasiar said:**
> Get [Martelli's Python Cookbook](http://www.buy.com/prod/python-cookbook-2nd-edition/q/loc/106/30893191.html) - will show you all kinds of tricks. Get also other O'Reilly's books (Learnig Python etc), if it's only you and book, you want couple books (showing the same thing from multiple angles). Check also website in my sig, it has many training tasks for beginners, so you will have something to code.

Good luck, looks like you live interesting life!

Thanks for that, I have just got lots of book tokens for my birthday, so i am off shopping today for some linux and python books to take back to sea with me.

As for an interesting life, at times it is interesting in the sense that I get to go to fantastic places, i get to manage a fantastic bunch of people and I can come home to a fantastic wife and children, at other times it is interesting in the sense of the old Chinese curse - ""may you live in interesting times"

---

### Post by LaRoza on 2008-03-27
> **mssever said:**
> Well, that destroys what I thought I knew about Fortran. I had thought that it was based on code being in specific columns (perhaps due to punchcard influence), but apparently I'm wrong.

It is based on columns.

0-6 Comments at column one, labels at 2-5
7-72 Code here
72-80 Don't know what goes here

That is why all comments (lines beginning with a "c") start at column 0, and all the code is indented. You can further indent, as I did, to keep it readable.

---


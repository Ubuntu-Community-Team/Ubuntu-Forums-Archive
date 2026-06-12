---
title: "Trigometric Equation Solution"
date: 2008-05-27
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-05-27
This isn't a homework question but a PreCalculus Test Question that I couldn't answer for lack of understanding

```

Write sin^3(x) in first degree cosine ( cos(?) )

```
I tried to use this formula but failed
```

(1-cos(2x))/2=sin^2(x)

```

fractions are ok and leave anwser in calculator ready

Please no high level calculus answers i am in precalculus and only understand to about calc 1

By the way i want the steps and an explanation not just
[INDENT]cos(13x -2)/2[/INDENT]

---

### Post by Can+~ on 2008-05-27
[http://en.wikipedia.org/wiki/List_of_trigonometric_identities#Power-reduction_formulae](http://en.wikipedia.org/wiki/List_of_trigonometric_identities#Power-reduction_formulae)

---

### Post by ifross on 2008-05-27
Not sure that answered the question as he asked it in terms of cosine... Seems quite hard, are you sure that that is the question?

With my limited maths knowledge, I think that it would be tough getting it in terms of just first order cosines (short of saying cos(x) = sin(x+(pi/2))

---

### Post by CptPicard on 2008-05-27
There *is* a formula for sin^3 in terms of sines as I think was on the Wikipedia page... but frankly, I have been messing with it for an hour now and can't coerce it into cosines... I would be prone to agree with the previous poster and suggest that you may have misunderstood the question?

---

### Post by ConMan318 on 2008-05-27
It seems like the answer would be
```

sin^3(x) = (1 - cos^2(x))^(3/2)

```

I don't know how it would end up being what you wrote it was, unless I read your original post wrong; is what you wrote there: "cos(13x -2)/2", the correct answer?

I've never heard of needing something to be "first-degree" cosine, does that mean that there can't be any squares/exponents besides one?

---

### Post by geirha on 2008-05-27
> **ConMan318 said:**
> It seems like the answer would be
```

sin^3(x) = (1 - cos^2(x))^(3/2)

```

That does not seem to be right. Try drawing the graphs with [gnuplot](apt:gnuplot):
```

$ gnuplot
gnuplot> plot sin(x)**3, (1-cos(x)**2)**(3/2)

```
You'll see they don't match.
> **ConMan318 said:**
> 
I've never heard of needing something to be "first-degree" cosine, does that mean that there can't be any squares/exponents besides one?
That is what it means, yes. 

Can+~ has allready posted the formula which will give you the answer in first degree sine:
```

sin^3(x)= (3sin(x)-sin(3x))/4

```
and converting between sine and cosine is simple: 
```

cos(x) = sin(pi/2-x)
and
sin(x) = cos(pi/2-x)

```
So the answer is ...

---

### Post by OpenFish on 2008-05-28
last time i checked

sin**3(x)
sin**2(x) * sin (x)
(1 - cos**2(x)) * sin(x)
(1 - cos**2(x)) * cos(x - 90)
cos(x - 90) - cos**2(x)cos(x - 90)

every line should be the same
and the last two lines both express sin**3(x) in turmes of cos(x)

is this what ur looking for ?? calc says they are the same any way

there will be a way of simplifing it down a lot but i cant remember

---

### Post by shifty2 on 2008-05-28
Just curious, what level is precalculus? ie age? 

It seems like quite a lame question tbh, not a particularly nice answer. Did they want the answer in terms of cos(x) rather than having cos**y(x)? Don't know what level you are, but using de moivre would get it into single powers of cos and sine and from there you could just use a lot of cos(x-90)=sin(x) to get it into single powers of cosine.

---

### Post by OpenFish on 2008-05-28
```
cos(x - 90) - cos**2(x)cos(x - 90)
```

well im sorry

```
cos(x - 90) - cos(x)*cos(x)*cos(x - 90)
```

or 

```
cos(x - 90)*cos(x - 90)*cos(x - 90)
```

and 

```
cos(A+-B) = cosAcosB +- sinAsinB
```

i love trig it just gose round and round in ever more complicated circles 

by the way have u seen the matrix opengl uses for giving orientations it dosen't have any identity's in it but it keeps us on are toes

yes i do think there is a simple er way to show it but i havnt needed it so dont know it 
but the curve that sin**3(x) isn't a linia transformation of sin(x) so it cant just be maded from cos(x*A)*B (i think!)

---

### Post by OpenFish on 2008-05-28
sorry i hadn't read all of ur post

```
(3*cos(x-90)-cos(3*x - 90))/4
```

and yes yes this is better but the point of this post is to prove how u get hear and i cant explain how u get to this!!

although it is quite pretty

see what i mean about circles!!

---

### Post by Mr.Macdonald on 2008-05-28
The age levels of this class is Junior in High School (15 - 17) but this teacher makes the class about college level.

The indented formula on my first post is psuedo and just an example.

Maybe I did misunderstand it because that test was brain rattling and I may have misread it. Wikipedia has power reduction formulae but none for that question. The Teacher also didn't teach us the formulae after 2nd power. Ill ask his and release the solution privately (by email at my discretion) as to avoid academic dishonesty. All i hope is that their was a typo and i will get credit.

---

### Post by galileon on 2008-05-28
sine cubed x is also sine squared x times sine x

sine squared x is half ( 1 - cosine x )

sine x itself is cosine of ninety degrees minus theta

does that make sense?

> **Mr.Macdonald said:**
> This isn't a homework question but a PreCalculus Test Question that I couldn't answer for lack of understanding

```

Write sin^3(x) in first degree cosine ( cos(?) )

```
I tried to use this formula but failed
```

(1-cos(2x))/2=sin^2(x)

```

fractions are ok and leave anwser in calculator ready

Please no high level calculus answers i am in precalculus and only understand to about calc 1

By the way i want the steps and an explanation not just
[INDENT]cos(13x -2)/2[/INDENT]

---

### Post by unutbu on 2008-05-28
As has been previously noted, sin(x) = cos(x- pi/2). So if we can get sin^3(x) written in terms of first degree sines and cosines, then we are home free.

Important formulas for trig reduction are

> sin(A+B) = sin(A)cos(B) + sin(B)cos(A).
cos(A+B) = cos(A)cos(B) - sin(A)sin(B).

Two particular cases of this are
> sin(2x)=sin(x)cos(x)+sin(x)cos(x)=2sin(x)cos(x)
cos(2x)=cos(x+x)=cos^2(x)-sin^2(x)=(1-sin^2(x))-sin^2(x)=1-2sin^2(x).

Notice from the main trig reduction formulas there seems to be a way to "translate" from things like sin(3x) to products of sines and cosines ... things like sin^3(x). We're interested in sin^3(x), and we are interested in getting it down to something like sin(3x), so there is reason to pursue this line of thinking.

> sin(3x)=sin(x+2x)=sin(x)cos(2x) + sin(2x)cos(x)
 = sin(x)*(1-2sin^2x) + 2sin(x)cos(x)cos(x)
 = sin(x)*(1-2sin^2x) + 2sin(x)cos^2(x)
 = sin(x)*(1-2sin^2x) + 2sin(x)(1-sin^2(x))
 = sin(x)*(1-2sin^2x) + -2sin^3(x)+2sin(x)
 = sin(x)-2sin^3(x) + -2sin^3(x)+2sin(x)
 = -4sin^3(x) + 3sin(x)

So

> 4 sin^3(x) = 3sin(x)-sin(3x)
 sin^3(x) = (3sin(x)-sin(3x))/4 = (3cos(x-pi/2) - cos(3x-pi/2))/4

```
% gnuplot
gnuplot> plot sin(x)**3, (3*cos(x-pi/2)-cos(3*x-pi/2))/4

```

---


---
title: "c program to compute PI"
date: 2012-04-11
forum: Programming Talk
---

### Post by DaviesX on 2012-04-11
```

#include <stdio.h>
#include <math.h>

// Fascinating number - PI
int main ( int argv, char *argc[] )
{
    double a = 1.0;
    double b = 1.0/sqrt ( 2.0 );
    double t = 1.0/4.0;
    double x = 1.0;
    double y;

    int i;
    for ( i = 0; i < 4; i++ )
    {
        y = a;
        a = (a + b)/2.0;
        b = sqrt ( b*y );
        t -= x*(y - a)*(y - a);
        x *= 2;
    }

    double pi = (a + b)*(a + b)/(4*t);
    printf ( "%.15f\n", pi );

    return 0;
}

```
It was so fast, but I'm trying to understand why it could work :mad:

---

### Post by davetv on 2012-04-11
It uses this method

[http://en.wikipedia.org/wiki/Gauss%E2%80%93Legendre_algorithm](http://en.wikipedia.org/wiki/Gauss%E2%80%93Legendre_algorithm)

---

### Post by DaviesX on 2012-04-11
Still not quite understand how to get the limits when A0 = 1 and B0 = cos &#966;. Why it is PI/2K(sin &#966;) &#65311;

---

### Post by davetv on 2012-04-12
I looked at it and played with it on paper for a few hours, tried forward/backwards and I can't see a proof to that either.

Anybody know?

---

### Post by Majorix on 2012-04-12
This is called Numerical Analysis and is taught at most engineering schools. You could get a book and read on it, there are lots of other useful stuff. And, don't bother about understanding the formula, most of the time it is very complicated :)

---

### Post by muteXe on 2012-04-12
Davetv: I may have a look at it tonight before i start drinking.

---

### Post by davetv on 2012-04-12
Had a few to drink - looked at it again - gave up. No need to understand the mathematics of a wheel to know it rolls.

---

### Post by muteXe on 2012-04-12
Yea but i'm curious. Used to do a lot of this stuff at uni, but that was a long time ago.

---

### Post by davetv on 2012-04-12
If you figure it, please post your results, I am keen to learn. Good luck :) - (I finished uni 28 yrs ago myself)

---

### Post by DaviesX on 2012-04-12
Proof of both arithmetic mean and geometric mean has the same limit
An+1 = (An + Bn)/2
Bn+1 = sqrt ( An*Bn )
when n->infinite lim An = lim Bn

1. arithmetic mean always greater or equal to geometric mean when a and b is greater than 0
(a + b)/2 >= sqrt ( a*b )
a/2 - sqrt ( a*b ) + b/2 >= 0

because (sqrt (a/2) - sqrt (b/2))^2 >= 0 is always true when a > 0 and b > 0
So the proposition is proved.

then to explore An - Bn > An+1 - Bn+1 when n >= 1
An - Bn > (An + Bn)/2 - sqrt ( An*Bn )
An - 3Bn > -2*sqrt ( An*Bn )       #1

Use the theory we found in 1
(An + Bn)/2 >= sqrt ( An*Bn )
An + Bn >= 2*sqrt ( An*Bn )        #2
We plus #1 and #2, 
2*An - 2*Bn > 0
An > Bn
means arithmetic mean is greater then geometric mean
which is always true when n >= 1 and An > 0, Bn > 0

So An - Bn > An+1 - Bn+1 > An+2 - Bn+2 > ....
and when n->infinite lim An - Bn = 0
which means lim An = lim Bn

That all what I can do...:-), I can't come up with that integral when A0 = 1, B0 = cos x

---

### Post by davetv on 2012-04-13
Thanks for that DaviesX ... pretty much my proof of the converging limit ... tis the suddenly introduced trig function I don't get as same as you. The wiki article shows it, but doesn't show why/how it was arrived at.

I give up ... programmer not a mathematician ... just knew the gauss-legendre algorythm for PI offhand when I saw your question.

Interesting discussion. :) Time for a beer!

---

### Post by DaviesX on 2012-04-13
Yeah, and I have found out more about gauss-legendre. It is not only an algorithm, but a trick for writing an integrating function. It comes out much faster because it produces very high rate of convergence (The precision of the decimal doubles every time ! So I think it is worthy finding it out ). 

Even more I have got that a value between arithmetic-geometric mean is called M(An, Bn)
which can be expressed as following
M(An, Bn) = Pi/4 * (An + Bn)/K{ [(An - Bn)/(An + Bn)]^2 }

I would like to post the proof about this after I can found out :-), I think it is the key point to understand this identical equation. After that, I think it is easy to follow the steps that wiki given. ^_^

---

### Post by DaviesX on 2012-04-15
> **DaviesX said:**
> Yeah, and I have found out more about gauss-legendre. It is not only an algorithm, but a trick for writing an integrating function. It comes out much faster because it produces very high rate of convergence (The precision of the decimal doubles every time ! So I think it is worthy finding it out ). 

Even more I have got that a value between arithmetic-geometric mean is called M(An, Bn)
which can be expressed as following
M(An, Bn) = Pi/4 * (An + Bn)/K{ [(An - Bn)/(An + Bn)]^2 }

I would like to post the proof about this after I can found out :-), I think it is the key point to understand this identical equation. After that, I think it is easy to follow the steps that wiki given. ^_^

Finally ! I found out the proof for the limit of arithmetic-geometric  mean. I was been found by a genius Mathematician - Gauss. This proof  have to be written in 2 papers (So complex and ingenious :mad: ), let me try generate the  formulas in some pictures, so that I would be able to post it :KS

---

### Post by DaviesX on 2012-04-16
Gauss theorem:
 

let 
[IMG]https://public.bay.livefilestore.com/y1pBF0DAItuV10EPL9y7IVRwvy-BBU_2SJZ9ucfGI_vCPLPT9LzuJF__fiiGhvNqhProlP-fC0ZF7E205E0lZ_USQ/Selection_001.png?psid=1[/IMG]
 then
[IMG]https://public.bay.livefilestore.com/y1pBF0DAItuV10oFxmlDKShKfB2HsZcp9KCTzhv5u3GGp0beTzs4X9_h_6H0AAMiiAalP4zsPtbsFmqdP3l9-hV6g/Selection_002.png?psid=1[/IMG]

  where M (1+x, 1-x ) is the limit of arithmetic-geometric mean and K(x) is the complete elliptic integration of of the first kind.  
 

 In case we can prove this formula, hopefully M(1+x, 1-x) can be expressed as a function.
 So we are going to change the integrand in term of a and b which are defined as follow
[IMG]https://public.bay.livefilestore.com/y1p5a0AuS52VC2kyh71QB12O-aeA6woVdMgFkzAkjcXJV9Xfy8M7WjSOq17E4dp0k9-HSlN6m4W0DuOTthAsSA0qQ/Selection_013.png?psid=1[/IMG]

  

 let 

[IMG]https://public.bay.livefilestore.com/y1pBF0DAItuV13woNxZPxh-ld1JfXGRI22HHHfMq-xSNracU5ymPaLRDLZGErAVtIpVwaiZQomShY0jiGguprh0-A/Selection_003.png?psid=1[/IMG]

 

K(x) become
[IMG]https://public.bay.livefilestore.com/y1pBF0DAItuV12AMzyMbdlxXewadoXBFlp1K_lNZ40MoBwFLGSJQYkODNmZMmH74zWarpiDzmkwIDLkY2LV2SKnhw/Selection_004.png?psid=1[/IMG]

  And let
[IMG]https://public.bay.livefilestore.com/y1pExzZ3qQ_DAds-QUSuSYhiz7klAnjVdWo3ecw7V3-JH3cikokBjGbYh9JaHy5T7xlmHrQaaOOxqxJA3hLgaPwPA/Selection_005.png?psid=1[/IMG]

 

 Now the formula becomes more decent, and what we are going to do is to  
 prove the equality between:  
  [IMG]https://public.bay.livefilestore.com/y1pBF0DAItuV10oFxmlDKShKfB2HsZcp9KCTzhv5u3GGp0beTzs4X9_h_6H0AAMiiAalP4zsPtbsFmqdP3l9-hV6g/Selection_002.png?psid=1[/IMG]
The formula above should be M(An, Bn) = PI/2 * I(An, Bn), I messed up...

 [IMG]https://skydrive.live.com/redir.aspx?cid=debfb1a1543a0abd&resid=DEBFB1A1543A0ABD%21403&parid=DEBFB1A1543A0ABD%21399[/IMG]

---

### Post by DaviesX on 2012-04-16
As I was mentioned just now, we hope the limit that An and Bn converged to can be expressed as a function. M(1+x, 1-x) is an even function because x in the integrand above is power 2, so Gauss assumes that the function is: 

 [IMG]https://public.bay.livefilestore.com/y1pbDcuIFdXEy6kfo2KWifVXXWoek86tr0fOldNPVWNDx0jEM50BLvoj7krArUGuuS1jkPrJQjHwR_g2796cGLDgA/Selection_008.png?psid=1[/IMG]
 

   then we make the substitution like:  
   [IMG]https://public.bay.livefilestore.com/y1pbDcuIFdXEy4bOfZyb5guveGoRuOxk3O6pEogjSfdOKFCEkom70ydvYx_KKG9ckj_mPcF316Ign-CjpSxcMTN2A/Selection_009.png?psid=1[/IMG]
 

  magically,  
   [IMG]https://public.bay.livefilestore.com/y1pbDcuIFdXEy4QZKp-5MyDicRCecLImPPJHm3rO5SeFflE3PPC3tElxvVlZA2RsyyA40tMq-pgSYHOm4iSpQ_R3A/Selection_010.png?psid=1[/IMG]

 

  Because M(a, b) is the limit of An and Bn,  
  So, it has the following properties
  [IMG]https://public.bay.livefilestore.com/y1pC-1A10oPWNKjItUgvuidjyhrjDlifSGvgCj7EF4TOkdLJ2aar6cRS1UWIM8tK0fXZSBzbc2l1OriB0F-0WSloQ/Selection_011.png?psid=1[/IMG](1)
   	 	 	 	 	 	 	 	   
 [IMG]https://public.bay.livefilestore.com/y1p19R2kV0CS-QnPeKzwUoI9xUpVAb-5aIhzm74kz-OqeENwmL2kwEUoLotrCBdfP4aw1smZX_kA3KWBmePxkCrHA/Selection_014.png?psid=1[/IMG](2)
 

 If we enforce property 2 for M
  [IMG]https://public.bay.livefilestore.com/y1p19R2kV0CS-SRxyu9EcUr5qh4LW954RZ1J0TcPcw1aKPY1h0Oh5FSTV6wXjJsX3aGGI2CVToMP4dd0Q78bBMi_A/Selection_015.png?psid=1[/IMG]



 Then we use property 1 for M
[IMG]https://public.bay.livefilestore.com/y1p19R2kV0CS-QA1PCQtJFWjrK4OfqSHr3hTQFRlG0lYfz7KcGrh_9nTwEgj7pXFOpRyWZhFSHoLG2U9rimOd9yFQ/Selection_016.png?psid=1[/IMG]


So
[IMG]https://public.bay.livefilestore.com/y1p19R2kV0CS-SbqYx61qGi5C2gCpNSBw_uFYND3UgP6pGLUsLhmTkDbZQrxGHKtfuqNXpgkmh3RTwLpYgNN5qoRA/Selection_017.png?psid=1[/IMG]

---

### Post by DaviesX on 2012-04-16
Therefore, the function assumed by Gauss become an equation !
  [IMG]https://public.bay.livefilestore.com/y1pCRZ5z5td-8IXMR0wDMsf8JugQ15RXi0aoIzLMlJUe4-CRJo6pqOwKSAPOf-x3_OeLzA68GiSzva_PlXnw4IfGw/Selection_018.png?psid=1[/IMG]



 now what we are going to do is to solve the coefficient Ak, then it is the function that expressed the limit of An and Bn. In order to solve A0, A1, A2, &#8230; we can expand the equation by using binomial theorem, then equating the coefficient of x that are in the same power. Because A0 is followed with x to the power 0, we can find A0 by the fact that M(1, 1) = M (1 + 0, 1 &#8211; 0) = 1, where x = 0.                                    So A0 = 1

---

### Post by lisati on 2012-04-16
My head hurts, it has been a very long time since it has tried to cope with anything quite like this! :D

---

### Post by DaviesX on 2012-04-17
Yeah, it's pretty hard, Gauss expand the binomial using 3 pieces of paper ! I think I am not going to copy that...
[IMG]https://public.bay.livefilestore.com/y1pOnPT4IlATTLsmuyrAu-68d2-CmDUK5uHol08zwg1RpZYcaVBj3tgGwnVUDN_OYclWQ25dPZqktOmxK308T0RVA/Selection_023.png?psid=1[/IMG]

---

### Post by DaviesX on 2012-04-17
Expanding the binomial is a very harsh thing, I didn't do it =,= instead, I copy the result from someone's blog
[IMG]https://public.bay.livefilestore.com/y1pFMiUQNjJC-v6l6jJ4QvzPhrHnynjLJAPog5_tVy0xM5PmOj3OZZfHhYrLVZ_2CQuggTNABD1x06bcVEKORukhw/Selection_019.png?psid=1[/IMG]

  

 Maybe we can discover that the regular pattern of this sequence is:  
  [IMG]https://public.bay.livefilestore.com/y1pFMiUQNjJC-tHiezvY0EttgEdfGMmLJCeJ8vFURKllbmK1wiWv7upMR7CCi3S0BQ5LbRNNdW_tAud20vTcCZSIw/Selection_020.png?psid=1[/IMG]



 let's do this (1) x (2) x (3) x (4) x &#8230; x (n), and we get
[IMG]https://public.bay.livefilestore.com/y1pFMiUQNjJC-tk5MSwI62WoUTA5AYIAWeoB_91VMSUm0YTryTh8O_uRLa9cH_NIJ__OtIyMyYngLrp6W1iaP_nFg/Selection_021.png?psid=1[/IMG]



  We can complete the function for the limit of An and Bn now, 

[IMG]https://public.bay.livefilestore.com/y1pkQTVuwvIrTpphjTK5aUx6ZI8wLUop-9dzY641q-09vF--KGPFZnT5ifrwY8pXDzxesY7enjrlwWfMDWQa-wXlg/Selection_022.png?psid=1[/IMG]

---

### Post by DaviesX on 2012-04-17
So tiring, I would like to finish the rest of the proof later on ...

---

### Post by iamanidiot123 on 2012-04-17
There's a simpler way.

Still include math.h

```
double pi = 4.0 * atan( 1.0 );
```

This works because the units are radians by default (2 radians = 360 degrees)
The arctangent of one is 1/4 pi
Just multiply 1/4 pi by 4 and you get pi ^.^

---

### Post by lisati on 2012-04-17
> **iamanidiot123 said:**
> There's a simpler way.

Still include math.h

```
double pi = 4.0 * atan( 1.0 );
```

This works because the units are radians by default (2 radians = 360 degrees)
The arctangent of one is 1/4 pi
Just multiply 1/4 pi by 4 and you get pi ^.^

Yes, for odrinairy mortals set with a real-world problem to solve, that would be a good solution.

As I understand it, this thread is about one way someone coming up with a working trigonometric function such as atan() might work it out. :D

---

### Post by DaviesX on 2012-04-17
Yeah, there are dozen of way to solve PI, but compare to that method, if you want to get millions or billions of decimals, it's kind of slow. Because calculate atan itself may use Taylor expansion. its rate of convergence can not be as fast as that method. This is why it attracts me to try to find information about it.

Pn = An - Bn = ( sqrt(An) + sqrt(Bn) )( sqrt(An) - sqrt(Bn) )
Pn+1 = An+1 - Bn+1 = (An + Bn)/2 - sqrt ( An*Bn ) = 1/2 * ( sqrt(An) - sqrt(Bn) )^2

When n->infinite, let's find
lim (Pn+1)/ (Pn)^2 = lim 1/2 * 1 / ( sqrt(An) + sqrt(Bn) )^2 = lim (1/2) * 1/ 4*M (a, b) = 1/(8 M ( a, b ))
So that it becomes a constant, 
Pn+1 ~ C* (Pn)^2
Therefore, every iteration could produce double precision of decimal then last time ! which is really fast ! :-)

---

### Post by DaviesX on 2012-04-17
Oh, I may forget it should use sqrt, which uses Newton's iterating theorem, it's slow too when the number of decimal has become skyrocketing, though it has double convergence. Maybe there are some other ways to speed up sqrt, but I don't know about that ...

---

### Post by zobayer1 on 2012-04-17
> **DaviesX said:**
> Oh, I may forget it should use sqrt, which uses Newton's iterating theorem, it's slow too when the number of decimal has become skyrocketing, though it has double convergence. Maybe there are some other ways to speed up sqrt, but I don't know about that ...

Fast Fourier Transformation can be used, I could not understand the solution but it is available on internet. This problem is a good place to test how fast the convergence is and how many digits can be computed accurately within time limits.
[http://www.spoj.pl/problems/PIVAL/]("http://www.spoj.pl/problems/PIVAL/")
And as far as I know, many of the best solutions are implementations of FFT.

---

### Post by DaviesX on 2012-04-17
Thanks for your post, but I don't think I can write a program that can compute millions of digits of PI, I think it's hard, will it ?
I just know how to write a c program without making syntax error for the time being ...

---

### Post by 11jmb on 2012-04-17
> **DaviesX said:**
> Thanks for your post, but I don't think I can write a program that can compute millions of digits of PI, I think it's hard, will it ?
I just know how to write a c program without making syntax error for the time being ...

One of the easier problems holding you back from many digits will be floating-point precision. I think IEEE 754 only gives you about 50 bits of precison for 64-bit doubles, which is about 15 decimal digits. if you're using C99, you can get just over twice as many digits out of a long double.

Check out GMP, which allows you to use arbitrary-precision numbers in C

[http://gmplib.org/](http://gmplib.org/)

I know this isn't the main question you're trying to answer, but this might be useful as you move forward.

---

### Post by DaviesX on 2012-04-18
Thank you ! :-)

---


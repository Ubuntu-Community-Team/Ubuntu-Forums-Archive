---
title: "how to convert float value to int value in C"
date: 2012-05-01
forum: Programming Talk
---

### Post by prismctg on 2012-05-01
how to convert float value to int value in C ? example : input is : 12.04 and output is 1204

---

### Post by muteXe on 2012-05-01
your example doesn't match your question really.

i.e. i'd expect the int value of 12.04 to be 12.

---

### Post by prismctg on 2012-05-01
actually i found this problem in my exam . Here is the question  "Write a program to read the price of an item in decimal form (like 15.95) and print the output in int form  ( like 1595 )

---

### Post by muteXe on 2012-05-01
ah that's different.
can't you just multiply the float by 100 and then convert to an int?
the question's kind of asking you to convert from pounds to pence.

---

### Post by r-senior on 2012-05-01
What have you written so far?

---

### Post by codemaniac on 2012-05-01
> **prismctg said:**
> actually i found this problem in my exam . Here is the question  "Write a program to read the price of an item in decimal form (like 15.95) and print the output in int form  ( like 1595 )

If that is exactly the question in the examination , i would love to cheat as muteXe suggested . ;)
```

#include<stdio.h>
#include<unistd.h>

int main()
{
float x = 15.95;
int i =(x * 100);
printf("%d\n",i);
}
```

---

### Post by prismctg on 2012-05-01
[codemaniac]("http://ubuntuforums.org/member.php?u=997189") you are great :) and thnx a lot ..  and also thnx to every one :)

---

### Post by codemaniac on 2012-05-01
> **prismctg said:**
> [codemaniac]("http://ubuntuforums.org/member.php?u=997189") you are great :) and thnx a lot ..  and also thnx to every one :)

:lolflag: It was the lamest piece of code in the whole wide world .

---

### Post by muteXe on 2012-05-01
lol @ 'cheating' :)

---

### Post by prismctg on 2012-05-01
> **codemaniac said:**
> :lolflag: It was the lamest piece of code in the whole wide world .
ya may be but I m new in programming world :)

---

### Post by Bachstelze on 2012-05-01
Nice try, but no.

```
firas@dhcp-v033-031 ~ % cat test2.c                                 
#include <stdio.h>

int main(void)
{
    float x = 35.01;
    int n = x*100;
    printf("%d\n", n);
}
firas@dhcp-v033-031 ~ % gcc -std=c99 -pedantic -Wall -Wextra test2.c
firas@dhcp-v033-031 ~ % ./a.out                                     
3500
```

---

### Post by PeterP24 on 2012-05-01
yeah, I wanted to post something like "but what if the price float value has more than 2 decimal after the comma, i.e. 15.0144" but than I figured that since a price can only be expressed in dollars and cents it wouldn't make sense. However, I would like to know if in C, a float value with an arbitrary decimals after the coma can be "converted" to an int in the manner described by the OP. Multiplying with a power of ten would help only if you knew in advance the number of decimals after the comma to be recovered.
Sorry for hijacking the thread - if necessary I would open another one with this question.

---

### Post by PeterP24 on 2012-05-01
> **Bachstelze said:**
> Nice try, but no.

```
firas@dhcp-v033-031 ~ % cat test2.c                                 
#include <stdio.h>

int main(void)
{
    float x = 35.01;
    int n = x*100;
    printf("%d\n", n);
}
firas@dhcp-v033-031 ~ % gcc -std=c99 -pedantic -Wall -Wextra test2.c
firas@dhcp-v033-031 ~ % ./a.out                                     
3500
```

Use double instead of float?:
```
 /* bch.c*/
#include <stdio.h>

int main(void)
{
    double x = 35.01;
    int n = x*100;
    printf("%d\n", n);
}
```

With the output:
```
pts@hal9000:~/cwork$ gcc bch.c
pts@hal9000:~/cwork$ ./a.out
3501

```

---

### Post by Bachstelze on 2012-05-01
> **PeterP24 said:**
> I would like to know if in C, a float value with an arbitrary decimals after the coma can be "converted" to an int in the manner described by the OP.

You can always convert a float value to an int, but if the value is very close to an integer value, you might get unexpected results.

---

### Post by Bachstelze on 2012-05-01
> **PeterP24 said:**
> Use double instead of float?:
```
 /* bch.c*/
#include <stdio.h>

int main(void)
{
    double x = 35.01;
    int n = x*100;
    printf("%d\n", n);
}
```

With the output:
```
pts@hal9000:~/cwork$ gcc bch.c
pts@hal9000:~/cwork$ ./a.out
3501

```

I was waiting for someone to say that. :)

```
firas@dhcp-v033-031 ~ % cat test2.c 
#include <stdio.h>

int main(void)
{
    double x = 10.03;
    int n = (int)(100*x);
    printf("%d\n", n);
}
firas@dhcp-v033-031 ~ % gcc -std=c99 -pedantic -Wall -Wextra test2.c
firas@dhcp-v033-031 ~ % ./a.out                                     
1002

```

---

### Post by PeterP24 on 2012-05-01
> **Bachstelze said:**
> I was waiting for someone to say that. :)

```
firas@dhcp-v033-031 ~ % cat test2.c 
#include <stdio.h>

int main(void)
{
    double x = 10.03;
    int n = (int)(100*x);
    printf("%d\n", n);
}
firas@dhcp-v033-031 ~ % gcc -std=c99 -pedantic -Wall -Wextra test2.c
firas@dhcp-v033-031 ~ % ./a.out                                     
1002

```

Aaah - I didn't know that. My question, related to my previous posts can be then reformulated: given an float value, can you recuperate an arbitrary number of decimals after the comma in the C language?

Since my skills with C are not so strong, I don't know how to give an answer to the above question. There must be an hack around the way the C language converts float values and displays them. I know for certain that C would work with very precise floats and display them using printf and appropriate precision modifiers, if only they were not converted to int. 

```

```

---

### Post by Bachstelze on 2012-05-01
> **PeterP24 said:**
> Aaah - I didn't know that. My question, related to my previous posts can be then reformulated: given an float value, can you recuperate an arbitrary number of decimals after the comma in the C language?

Since my skills with C are not so strong, I don't know how to give an answer to the above question. There must be an hack around the way the C language converts float values and displays them. I know for certain that C would work with very precise floats and display them using printf and appropriate precision modifiers, if only they were not converted to int. 

Very precise does not mean arbitrarily precise. Some values cannot even be represented as a float (or a double) to begin with. 10.03 is one of them:

```
firas@dhcp-v033-031 ~ % cat test2.c
#include <stdio.h>

int main(void)
{
    double x = 10.03;
    printf("%.100lf\n", x);
}
firas@dhcp-v033-031 ~ % gcc -std=c99 -pedantic -Wall -Wextra test2.c
firas@dhcp-v033-031 ~ % ./a.out 
10.0299999999999993605115378159098327159881591796875000000000000000000000000000000000000000000000000000

```

---

### Post by Bachstelze on 2012-05-01
Just for kicks: for how many values between 10 and 100 with 0.01 increment do you think the program fails with a double?

*EDIT:* Perhaps surprisingly, it's just a tiny bit less than with a float.

*EDIT2:* Also, almost all values that work with a float do not work with a double, and vice versa.

---

### Post by DaviesX on 2012-05-01
I have a defect thought about it :)
```

float decimal = xx.xxx...
int integer;
 
while ( fabsf (decimal - (int)decimal) > ERROR_BOUND )
{
    decimal *= 10;    
}
 
integer = (int)decimal;

```
 
But it has many problems like overflowing

---

### Post by Bachstelze on 2012-05-01
It's actually very simple, but you need to think outside the box. :)

---

### Post by DaviesX on 2012-05-01
I think it is a problem related to IEEE floating point format ...
Actually I don't know that, though :mad:

---

### Post by PeterP24 on 2012-05-01
> **DaviesX said:**
> I think it is a problem related to IEEE floating point format ...
Actually I don't know that, though :mad:

Yeah - here is what I always thought about floating points representation as integers:
[sign][integer representing some number before the comma].[integer representing some number coming after the comma ]

I might be wrong - got to check some technical papers I found on IEEE floating point formats. 

I didn't knew that C can represent 10.03 as 10.0299999... until now. After all, the numerical methods courses warns you that you may loose some precision during arithmetic floating point operations. I never thought you can loose precision during simple representation of the floating point variable. It must be something obvious and hidden in the same time - the thing that makes you say: ahaa - I knew that, but you can only say that after some expert reveals it to you or you find it on your own.

---

### Post by Bachstelze on 2012-05-01
> **PeterP24 said:**
> 
I didn't knew that C can represent 10.03 as 10.0299999... until now.

When you think about it a little, it makes sense. You know how some seemingly simple numbers like 1/3 are impossible to represent in decimal? If we counted in base 3 instead of base 10, 1/3 would be 0.1. But because 3 doesn't match well with our base 10, we can't represent 1/3.

Likewise, a number like 1003/100 seems simple to us because we have numbers that fit with our natural base 10, but it is impossible to represent in base 2, which is how (current) computers store numbers. Hence it is impossible to store the value 1003/100 as a float, just like it is impossible to write the number 1/3 in base 10 on a piece of paper.

---

### Post by DaviesX on 2012-05-01
> **PeterP24 said:**
> Yeah - here is what I always thought about floating points representation as integers:
[sign][integer representing some number before the comma].[integer representing some number coming after the comma ]

I might be wrong - got to check some technical papers I found on IEEE floating point formats. 

I didn't knew that C can represent 10.03 as 10.0299999... until now. After all, the numerical methods courses warns you that you may loose some precision during arithmetic floating point operations. I never thought you can loose precision during simple representation of the floating point variable. It must be something obvious and hidden in the same time - the thing that makes you say: ahaa - I knew that, but you can only say that after some expert reveals it to you or you find it on your own.

That sort of representation is not floating point, instead, it is fixed point. Because there is no way to know where the comma would be :mad:

single precision floating point format is
```

1        | 8             | 23
sign bit | exponent bits | decimal bits

```
But to encode floating point is more complicated. There are 3 sort of condition, I can't figure out why it should be like that

---

### Post by Bachstelze on 2012-05-01
> **DaviesX said:**
> 
But to encode floating point is more complicated.

Fun stuff: implement the four floating-point arithmetic operations using only bit-level operators. :D

---

### Post by DaviesX on 2012-05-01
There is a formula to represent a binary number in decimal form.

```

a binary: ...B5 B4 B3 B2 B1 B0 = 

B0*2^0 + B1*2^1 + B2*2^2 + ... + Bn*2^n


```

The sum of that polynomial is the actual decimal number.

I don't know if it work for floating point, because that would become negative exponent...

---

### Post by PeterP24 on 2012-05-01
> **DaviesX said:**
> That sort of representation is not floating point, instead, it is fixed point. Because there is no way to know where the comma would be :mad:

single precision floating point format is
```

1        | 8             | 23
sign bit | exponent bits | decimal bits

```
But to encode floating point is more complicated. There are 3 sort of condition, I can't figure out why it should be like that

Thanks - I admit that the secrets of floating point are hidden from me. Not to say that I wouldn't search this topic further, This thread has been very fruitful for me in terms of knowledge I gained from @Bachstelze and you. Its like you both know kung-fu and I only know the name of the moves :D. I have to retreat now - @Bachstelze has raised several problems with I must try now in order to gain more knowledge.

---

### Post by DaviesX on 2012-05-01
:) We are both learner actually ...
I start learning this language maybe 2 years ago

---

### Post by DaviesX on 2012-05-01
I use this program to test several numbers, But I can find any clue from it
```

#include <stdio.h>

void itoa ( unsigned int val, char *string )
{
    unsigned int decimal[32] = {0};
    int i = 30;

    for ( ; val && i; --i, val >>= 1 )
        decimal[i] = val & 1;

    int j = 0;
    string[0] = '0';

    for ( i++; i < 31; i++, j++ )
        string[j] = "01"[decimal[i]];

}

int main()
{
    float ftNumber;
    scanf ( "%f", &ftNumber );
    unsigned int format = (int&)ftNumber;

    char sign[1 + 1] = {0};
    char exponent[8 + 1] = {0};
    char decimal[23 + 1] = {0};

    itoa ( format >> 31, sign );
    itoa ( (0XFF) & format >> (32 - (8 + 1)), exponent );
    itoa ( (0X7FFFFF) & format, decimal );

    printf ( "%s ", sign );
    printf ( "%s ", exponent );
    printf ( "%s\n", decimal );

    return 0;
}

```

---

### Post by Bachstelze on 2012-05-01
FYI, it fails on 504 values with a double, and 507 with a float. For a double, the values are:

```
10.03
10.04
10.12
10.20
16.06
16.08
16.15
16.24
16.31
16.33
16.40
16.49
16.56
16.58
16.65
16.74
16.81
16.83
16.90
16.99
17.06
17.08
17.15
17.24
17.31
17.33
17.40
17.49
17.56
17.58
17.65
17.74
17.81
17.83
17.90
17.99
18.06
18.08
18.15
18.24
18.31
18.33
18.40
18.49
18.56
18.58
18.65
18.74
18.81
18.83
18.90
18.99
19.06
19.08
19.15
19.24
19.31
19.33
19.40
19.49
19.56
19.58
19.65
19.74
19.81
19.83
19.90
19.99
20.06
20.08
20.15
20.24
20.31
20.33
20.40
32.05
32.12
32.16
32.23
32.30
32.37
32.41
32.48
32.55
32.62
32.66
32.73
32.80
32.87
32.91
32.98
33.05
33.12
33.16
33.23
33.30
33.37
33.41
33.48
33.55
33.62
33.66
33.73
33.80
33.87
33.91
33.98
34.05
34.12
34.16
34.23
34.30
34.37
34.41
34.48
34.55
34.62
34.66
34.73
34.80
34.87
34.91
34.98
35.05
35.12
35.16
35.23
35.30
35.37
35.41
35.48
35.55
35.62
35.66
35.73
35.80
35.87
35.91
35.98
36.05
36.12
36.16
36.23
36.30
36.37
36.41
36.48
36.55
36.62
36.66
36.73
36.80
36.87
36.91
36.98
37.05
37.12
37.16
37.23
37.30
37.37
37.41
37.48
37.55
37.62
37.66
37.73
37.80
37.87
37.91
37.98
38.05
38.12
38.16
38.23
38.30
38.37
38.41
38.48
38.55
38.62
38.66
38.73
38.80
38.87
38.91
38.98
39.05
39.12
39.16
39.23
39.30
39.37
39.41
39.48
39.55
39.62
39.66
39.73
39.80
39.87
39.91
39.98
40.05
40.12
40.16
40.23
40.30
40.37
40.41
40.48
40.55
40.62
40.66
40.73
40.80
40.87
40.91
64.07
64.10
64.21
64.24
64.32
64.35
64.46
64.49
64.57
64.60
64.71
64.74
64.82
64.85
64.96
64.99
65.07
65.10
65.21
65.24
65.32
65.35
65.46
65.49
65.57
65.60
65.71
65.74
65.82
65.85
65.96
65.99
66.07
66.10
66.21
66.24
66.32
66.35
66.46
66.49
66.57
66.60
66.71
66.74
66.82
66.85
66.96
66.99
67.07
67.10
67.21
67.24
67.32
67.35
67.46
67.49
67.57
67.60
67.71
67.74
67.82
67.85
67.96
67.99
68.07
68.10
68.21
68.24
68.32
68.35
68.46
68.49
68.57
68.60
68.71
68.74
68.82
68.85
68.96
68.99
69.07
69.10
69.21
69.24
69.32
69.35
69.46
69.49
69.57
69.60
69.71
69.74
69.82
69.85
69.96
69.99
70.07
70.10
70.21
70.24
70.32
70.35
70.46
70.49
70.57
70.60
70.71
70.74
70.82
70.85
70.96
70.99
71.07
71.10
71.21
71.24
71.32
71.35
71.46
71.49
71.57
71.60
71.71
71.74
71.82
71.85
71.96
71.99
72.07
72.10
72.21
72.24
72.32
72.35
72.46
72.49
72.57
72.60
72.71
72.74
72.82
72.85
72.96
72.99
73.07
73.10
73.21
73.24
73.32
73.35
73.46
73.49
73.57
73.60
73.71
73.74
73.82
73.85
73.96
73.99
74.07
74.10
74.21
74.24
74.32
74.35
74.46
74.49
74.57
74.60
74.71
74.74
74.82
74.85
74.96
74.99
75.07
75.10
75.21
75.24
75.32
75.35
75.46
75.49
75.57
75.60
75.71
75.74
75.82
75.85
75.96
75.99
76.07
76.10
76.21
76.24
76.32
76.35
76.46
76.49
76.57
76.60
76.71
76.74
76.82
76.85
76.96
76.99
77.07
77.10
77.21
77.24
77.32
77.35
77.46
77.49
77.57
77.60
77.71
77.74
77.82
77.85
77.96
77.99
78.07
78.10
78.21
78.24
78.32
78.35
78.46
78.49
78.57
78.60
78.71
78.74
78.82
78.85
78.96
78.99
79.07
79.10
79.21
79.24
79.32
79.35
79.46
79.49
79.57
79.60
79.71
79.74
79.82
79.85
79.96
79.99
80.07
80.10
80.21
80.24
80.32
80.35
80.46
80.49
80.57
80.60
80.71
80.74
80.82
80.85
80.96
80.99
81.07
81.10
81.21
81.24
81.32
81.35
81.46
81.49
81.57
81.60
81.71
81.74
81.82
81.85

```

---

### Post by DaviesX on 2012-05-01
You mean that test code ?

---

### Post by Bachstelze on 2012-05-01
No, I mean codemaniac's suggestion on the first page.

---

### Post by DaviesX on 2012-05-01
How does it fail ? It looks work ?.?

---

### Post by DaviesX on 2012-05-01
Oh, I know....

---

### Post by DaviesX on 2012-05-01
Do you think this one could work ?
```

#include <stdio.h>
#include <math.h>

int main()
{
    float decimal = 507.05;
    int integer;

    while ( fabsf (decimal - (int)decimal) > 1e-2 )
    {
        decimal *= 10;
    }

    integer = (int)decimal;
    printf ( "%d\n", integer );

    return 0;
}

```

---

### Post by Bachstelze on 2012-05-01
No.

```
firas@dhcp-v056-159 ~ % cat test4.c 
#include <stdio.h>
#include <math.h>

int main()
{
    float decimal = 73.67;
    int integer;

    while ( fabsf (decimal - (int)decimal) > 1e-2 )
    {
        decimal *= 10;
    }

    integer = (int)decimal;
    printf ( "%d\n", integer );

    return 0;
}
firas@dhcp-v056-159 ~ % gcc -std=c99 -pedantic -Wall -Wextra test4.c
firas@dhcp-v056-159 ~ % ./a.out 
73669992

```

---

### Post by Bachstelze on 2012-05-01
P.S.: With a double, it fails as well. Wrong result for 10.01, and even an infinite loop for 10.02.

---

### Post by DaviesX on 2012-05-01
73.67f just can't be stored precise enough, it's inevitable except using fixed point...

So just get rid of the box as you said :)
```

#include <stdio.h>

int main()
{
    char number[12] = {0};
    char output[12] = {0};

    gets ( number );

    for ( int i = 0, j = 0; number[i] != 0; i++ )
        if ( number[i] != '.' )
            output[j++] = number[i];

    puts ( output );

    return 0;
}

```

---

### Post by tjwilli on 2012-05-01
Back to the OP. This isn't a numerical solution, but why not get the integer part and fractional part of the number, concatenate them as a string (sprintf), and then convert that string into an int with sscanf?

---

### Post by DaviesX on 2012-05-01
Because as we have found before, IEEE floating point is an approximate number, some can't be express like 73.67 for single, 10.01 for double :mad:

This only way to store them is using fixed point, then that is almost the same idea as using a string...

---

### Post by muteXe on 2012-05-02
This has been a most educating thread for me. Cheers all.

---

### Post by lisati on 2012-05-02
I was going to suggest that we *string* together a solution but then saw post 38. :)

My $0.02: How is the "float" value actually stored - as a float or double variable, or as text somewhere e.g. as input from the keyboard or from a file?

---

### Post by codemaniac on 2012-05-02
Oh My god a lot of things has been happened here ..Lemme swallow all ..

---

### Post by DaviesX on 2012-05-02
> **muteXe said:**
> This has been a most educating thread for me. Cheers all.

And it stimulates me to implement an encode algorithm although it's not perfect :)

---

### Post by kevinharper on 2012-05-02
Insane how a simingly simple question can turn into a doctorial thesis.

Makes me want to drive to the Grand Canyon and see if my computers can fly! :P

As for representation of 1/3: That's why they invented that little bar that goes above the first repeating # sequence. :D Looks like everyone is essentially searching for the C equivalent.

---

### Post by ifross on 2012-05-03
I have a method which works for every value between 0.01 and 99.99. It is quite simple and basically instead of multiplying by 100 as suggested before, multiply by 1000 and make this an int. Then add 5 and divide by 10 which essentially causes the value to be rounded to the nearest value, which accounts for any floating point errors.

```

#include <stdio.h>


int main()
{
    int i;
    float x = 10.03;
    i = (((int)(x*1000)) + 5)/10;
    printf ("%d\n", i);
    return 0;
}
```

---

### Post by DaviesX on 2012-05-03
Excellent ! 
But how about those which doesn't have a fraction, for example, 10.00

---


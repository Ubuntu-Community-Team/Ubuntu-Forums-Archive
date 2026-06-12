---
title: "Some C Clarification"
date: 2008-12-30
forum: Programming Talk
---

### Post by CLomax on 2008-12-30
> #include <stdio.h>
main()
{
	int n,i=1,j,c;
  printf("Number Of Terms Under 1000: \n\n");
		n=1000;
		 while(i<=n)
		 {
		    c=0;
		    for(j=1;j<=i;j++)
		    {
              if(i%j==0)
		c++;
 		    }
           if(c==2)
           printf("%d  ",i);
           i++;
        }
}

For a university entrance scholarship I am likely to be asked to write an algorithm which produces the first 1000 prime numbers. This is the code I have written which seems to work fine (FYI, I gathered some ideas/snippets of code from parts of the internet).

The problem I'm having is that it isn't pseudo code. I can "translate" most of it but there are certain areas I'm having trouble with...

E.G > if([COLOR="Red"]i%j[/COLOR]==0)
    What exactly is the red portion of the formula actually doing?

By the way, my indentation is far better than what the quote is showing :P.

Thank you for your time.

---

### Post by samjh on 2008-12-30
It's the modulo operator, which calculates the remainder of i divided by j.

Example:
If i = 5 and j = 2, then i % j = 1.
If i = 6 and j = 3, then i % j = 0.

---

### Post by CptPicard on 2008-12-30
Did you actually write and understand it if you need to ask the question or did you just copy it from somewhere? :)

---

### Post by CLomax on 2008-12-30
> It's the modulo operator, which calculates the remainder of i divided by j.

Thank you very much, I understand perfectly :).

> Did you actually write and understand it if you need to ask the question or did you just copy it from somewhere? :)

It was that one part which I did just copy (I will [COLOR="Blue"]never[/COLOR] do it again.) The rest I either wrote myself and got it right, or wrote myself but completely wrong and referred to other peoples programs which are somewhat similar.

It just happens that I took advantage of the fact that it's open source the wrong way. :)

---

### Post by samjh on 2008-12-30
Just so you know, use the code tags to post code.  It will preserve the indentation.

See: [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)

---


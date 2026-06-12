---
title: "Homework help... Again."
date: 2012-02-14
forum: Programming Talk
---

### Post by rafaelcbf on 2012-02-14
So i'm wirghting this program:

[PHP]#include <stdio.h>
#include <iostream>

int main()
{
char A,a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z;
printf ("Introduzca un caracter, por favor.");
scanf("%c", &A);
if (A==b,c,d,f,g,h,j,k,l,m,n,p,q,r,s,t,v,w,x,y,z)
printf("Caracter es una consonante.");
else (A==a,e,i,o,u)
printf ("Caracter es una vocal.");
else (A==%i)
printf ("Caracter es un numero.");
}[/PHP]

It's supposed to:

1.-Ask you to input a (1) charecter/intager.
2.- Then it should output wether if it's a consonant, vowel or integer.

That's it, but I'm still having loads of trouble with characters, I can I get some orientation? Please.

---

### Post by Cookieh on 2012-02-14
I have made a code in C which looks a bit like this 

```


#include<stdio.h> #include<conio.h> #include<string.h> void main() {  char s[100];  int b,c,d,e,i,l,p;  b=c=d=e=0;  clrscr();  printf("\n\t Enter the string :=>");  gets(s);  l=strlen(s);  for(i=0;s[i]!='\0';i++)   {    if((s[i]>=65&&s[i]<=90||s[i]>=97&&s[i]<=122))    b++;    if(s[i]>=48&&s[i]<=57)    c++;    if(s[i]=='a'||s[i]=='e'||s[i]=='i'||s[i]=='o'||s[i]=='u'||s[i]=='A'||s[i]=='E'||s[i]=='I'||s[i]=='O'||s[i]=='U')    d++;       if (s[i]==' ')    e++;    }    p=b-d;    printf("\n\t No of vowels=%d \n",d);    printf("\n\t No of consonants=%d \n ",p);    printf("\n\t No of digits=%d \n",c);    printf("\n\t no of words=%d \n ",e+1);    printf("\n\t No of specal character=%d \n",l-b-c-e);
getch();
}

```

The only thing is that this is not my complete version as my development version is on my mac which is currently not usable. I think that this would be pretty simple to recreate in php.. Good Luck

---

### Post by Cookieh on 2012-02-14
Sorry, I can not get it to be in the formating which has indentations, hopefully you can solve it... Sorry :)

---

### Post by rafaelcbf on 2012-02-14
[PHP]#include<stdio.h>
 #include<conio.h>
 #include<string.h>
 void main()
 {
  char s[100];
  int b,c,d,e,i,l,p;
  b=c=d=e=0;
  clrscr();
  printf("\n\t Enter the string :=>");
  gets(s);
  l=strlen(s);
  for(i=0;s[i]!='\0';i++)   {    if((s[i]>=65&&s[i]<=90||s[i]>=97&&s[i]<=122))    b++;
    if(s[i]>=48&&s[i]<=57)    c++;    if(s[i]=='a'||s[i]=='e'||s[i]=='i'||s[i]=='o'||s[i]=='u'||s[i]=='A'||s[i]=='E'||s[i]=='I'||s[i]=='O'||s[i]=='U')    d++;
       if (s[i]==' ')    e++;    }
    p=b-d;
    printf("\n\t No of vowels=%d \n",d);
    printf("\n\t No of consonants=%d \n ",p);
    printf("\n\t No of digits=%d \n",c);
    printf("\n\t no of words=%d \n ",e+1); 
   printf("\n\t No of specal character=%d \n",l-b-c-e);
getch();
}[/PHP]

I see what it does, but this is for a whole string, I just need it to be for one (1) char or int. I guess I could kind of re work it. Thank you. Giving me the answer is not the same as help though, can anyone tell me more or less what I'm doing wrong? Please.

---

### Post by Arndt on 2012-02-14
> **rafaelcbf said:**
> So i'm wirghting this program:

[PHP]#include <stdio.h>
#include <iostream>

int main()
{
char A,a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z;
printf ("Introduzca un caracter, por favor.");
scanf("%c", &A);
if (A==b,c,d,f,g,h,j,k,l,m,n,p,q,r,s,t,v,w,x,y,z)
printf("Caracter es una consonante.");
else (A==a,e,i,o,u)
printf ("Caracter es una vocal.");
else (A==%i)
printf ("Caracter es un numero.");
}[/PHP]

It's supposed to:

1.-Ask you to input a (1) charecter/intager.
2.- Then it should output wether if it's a consonant, vowel or integer.

That's it, but I'm still having loads of trouble with characters, I can I get some orientation? Please.

I recommend that you read, refresh your memory or ask your teacher about these things:

1) character constants

2) tests and logical operators

Your program seems to be intended to be C++, judging from the include files, but you should say so explicitly - many languages are discussed here.

---

### Post by rafaelcbf on 2012-02-14
Oh, sorry about that, yes this is c++.

---

### Post by lisati on 2012-02-14
> **arndt said:**
> i recommend that you read, refresh your memory or ask your teacher about these things:

1) character constants

2) tests and logical operators

Agreed
The way the first listing reads to me is as if it is comparing variables, which is not necessarily the same thing as testing the variables against predefined values.

If you do something like:
> 
if (A=b)....

A and b are labels that refer to memory locations that could contain any information.

---

### Post by Tony Flury on 2012-02-15
> **rafaelcbf said:**
> Oh, sorry about that, yes this is c++.

If it is C++ then you should not really use stdio (that is C), and you should use cin and cout (with the >> and <<) operators for input and output).

---

### Post by Arndt on 2012-02-15
> **Tony Flury said:**
> If it is C++ then you should not really use stdio (that is C), and you should use cin and cout (with the >> and <<) operators for input and output).

But all he needs to do is remove "#include <iostream>" and it becomes C.

---

### Post by Tony Flury on 2012-02-15
Arndt - very true - he needs to decide one way or another - or taught one way or another :-(

---

### Post by chickendude on 2012-02-15
Expounding a little on what the others said (hopefully not TOO much), look at this line:```
char A,a,b,c,d,e,f,g,h,i,j,k,l,m,n,o,p,q,r,s,t,u,v,w,x,y,z; 
```What are those variables defined as? ;)
And here:```
if (A==b,c,d,f,g,h,j,k,l,m,n,p,q,r,s,t,v,w,x,y,z)
```Here you are testing if A==b (but what was b defined as again?), but not c, d, f, g, etc.

char A creates a (null) variable called A designed to hold the value of a character. You then need to STORE a value to the variable (otherwise who knows what value it will hold). To get the value of a character, we place it in single quotes. A char really holds the ASCII value of a character, in other words, a number. So if you want to insert the character value of a, use 'a'.

---

### Post by trent.josephsen on 2012-02-15
@chickendude: Your post is misleading on two points.

```
if (A==b,c,d,f,g,h,j,k,l,m,n,p,q,r,s,t,v,w,x,y,z)
```
I don't know what you're trying to say here, but it should at least be obvious that the only thing that matters to the execution of the if is z.  In other words, barring side effects, it's equivalent to if(z).  A==b is discarded along with all the others because that's how the comma operator works.

> char A creates a (null) variable called A designed to hold the value of a character.

"null" has a few specific meanings, neither of which apply here.  NULL is a null pointer literal.  "null" or "the null character" can also mean a character of value zero, but unless A has static storage duration, it won't be initialized to anything, so A is not null until you assign the null character to it like this:

```
A = 0; /* or A = '\0'; */
```

A is *uninitialized*, not null.

@OP:  You have other things to worry about first; please decide whether you're using C or C++ before bothering with my nitpicking.

---

### Post by rafaelcbf on 2012-02-15
Crap, sorry I hadn't checked back. Um I re wrote it, I think I should have checked back sooner. So now it looks likes this:

[PHP]#include <stdio.h>
#include <iostream>
int main()
{
char x;
printf("Ingrece un caracter.");
scanf("%c", &x);
if (x=='a')
{
printf("Es una vocal.");
}
else if (x=='e')
{
	printf("Es una vocal.");
}
else if (x=='i')
{
	printf("Es una vocal.");
}
else if (x=='o')
{
	printf("Es una vocal.");
}
else if (x=='u')
{
	printf("Es una vocal");
}
else if (x=='b')
{
	printf("Es una consonante.");
}
else if (x=='c')
{
	printf("Es una consonante.");
}
else if (x=='d')
{
	printf("Es una consonante.");
}
else if (x=='f')
{
	printf("Es una consonante.");
}
else if (x=='g')
{
	printf("Es una consonante.");
}
else if (x=='h')
{
	printf("Es una consonante.");
}
else if (x=='j')
{
	printf("Es una consonante.");
}
else if (x=='k')
{
	printf("Es una consonante.");
}
else if (x=='l')
{
	printf("Es una consonante.");
}
else if (x=='m')
{
	printf("Es una consonante.");
}
else if (x=='n')
{
	printf("Es una consonante.");
}
else if (x=='p')
{
	printf("Es una consonante.");
}
else if (x=='q')
{
	printf("Es una consonante.");
}
else if (x=='r')
{
	printf("Es una consonante.");
}
else if (x=='s')
{
	printf("Es una consonante.");
}
else if (x=='t')
{
	printf("Es una consonante.");
}
else if (x=='v')
{
	printf("Es una consonante.");
}
else if (x=='w')
{
	printf("Es una consonante.");
}
else if (x=='x')
{
	printf("Es una consonante.");
}
else if (x=='y')
{
	printf("Es una consonante.");
}
else if (x=='z')
{
	printf("Es una consonante.");
}
else if (x=="%i")
{
	printf("Es un numero.");
}
}
[/PHP] 

Yes i know I did it the long way, but that's just cause I couldn't do the short way, it works, all the way up to when I have to know if it's an integer, but it tells me this:

[PHP]g++ -Wall -c "segundointento.cpp" (in directory: /home/rafaelcbf/Desktop/Programas/Source)
segundointento.cpp: In function &#8216;int main()&#8217;:
segundointento.cpp:112:13: warning: comparison with string literal results in unspecified behaviour [-Waddress]
segundointento.cpp:112:13: error: ISO C++ forbids comparison between pointer and integer [-fpermissive]
Compilation failed.[/PHP]

So yeah I get it, I cant "mix" chars and ints, can I get a little hint? Please. Oh and I've learned with <iostream> but all the stuff I've been reading use cout and cin, so I'll try to make the move to them as soon as possible, ignoring what my teacher is teaching us, which I'm starting to thinks is kind of out dated. I want to use c++.

---

### Post by Tony Flury on 2012-02-15
I wont do your home work for you but - two hints :

1) look at the standard library function "isdigit"

2) Character are either consonant, vowels or integers :
Only 10 numbers (0 to 9), 5 vowels (a,e,i,o,u), and the rest are consonants - so check for numbers (see above) and vowels (you know how to do that), and then your program can assume that everything else is a consonant (you don't need to check it).

---

### Post by Bachstelze on 2012-02-15
> **Tony Flury said:**
> 
2) Character are either consonant, vowels or integers :


Surely you meant "*alphanumeric* characters". ;)

---

### Post by CryptAck on 2012-02-15
> **Bachstelze said:**
> Surely you meant "*alphanumeric* characters". ;)

My guess is he meant the C data type, char, as character not the classification of the data itself. 

I could be wrong though :D

---

### Post by Bachstelze on 2012-02-15
> **CryptAck said:**
> My guess is he meant the C data type, char, as character not the classification of the data itself. 

I could be wrong though :D

Excuse me? Any ASCII character (and then some) can be stored in a char.

---

### Post by rafaelcbf on 2012-02-15
> **Tony Flury said:**
> I wont do your home work for you but - two hints :

1) look at the standard library function "isdigit"

2) Character are either consonant, vowels or integers :
Only 10 numbers (0 to 9), 5 vowels (a,e,i,o,u), and the rest are consonants - so check for numbers (see above) and vowels (you know how to do that), and then your program can assume that everything else is a consonant (you don't need to check it).


I'm not looking for my homework to get done for me. Thank you very much, I will look in to that.

---

### Post by CryptAck on 2012-02-15
> **Bachstelze said:**
> Excuse me? Any ASCII character (and then some) can be stored in a char.

Yes, I know. The C data type of char is alphanumeric and can contain any byte field.  

I was saying he didn't need to specify that it was "alphanumeric" if he was talking about the data type (char) instead of the data ('1' numeric, 'a' character).

---

### Post by Bachstelze on 2012-02-15
> **CryptAck said:**
> Yes, I know. The C data type of char is alphanumeric and can contain any byte field.  

I was saying he didn't need to specify that it was "alphanumeric" if he was talking about the data type (char) instead of the data ('1' numeric, 'a' character).

You don't make any sense. Fact is that a variable of type char can contain any character, alphanumeric or not, so it is definitely a mistake to assume that if it is not a digit, then it is a letter.

---

### Post by rafaelcbf on 2012-02-15
OK, I found this: [PHPint isdigit ( int c );][/PHP]... mmm But where do I put it. I bvously change 'c' to 'x', but where does it go?

---

### Post by CryptAck on 2012-02-15
> **Bachstelze said:**
> Fact is that a variable of type char can contain any character, alphanumeric or not, so it is definitely a mistake to assume that if it is not a digit, then it is a letter.

I understand that, but the point has little to do with the details of the char data type, it has to do with the requirement.

> 
1.-Ask you to input a (1) charecter/intager.
2.- Then it should output wether if it's a consonant, vowel or integer.


Based on requirements, there is only three provided outputs, so the data being inputted and stored within the char should only be alpha or numeric...there is no reason to state "alphanumeric" as the requirements already provided that detail. 

Now there is a question of whether or not an additional requirement for data validation is required (for other characters, such as ".", " ", etc.), but given the simplicity of this program, my guess is no.

---

### Post by rafaelcbf on 2012-02-15
Thank you guys, I got it. yay.:D

---

### Post by Bachstelze on 2012-02-16
> **CryptAck said:**
> 
Now there is a question of whether or not an additional requirement for data validation is required (for other characters, such as ".", " ", etc.), but given the simplicity of this program, my guess is no.

What? Data validation is *always* required. And don't tell me it's "too complicated"; if you can use isdigit(), you can use isalnum().

---

### Post by Arndt on 2012-02-16
> **Bachstelze said:**
> What? Data validation is *always* required. And don't tell me it's "too complicated"; if you can use isdigit(), you can use isalnum().

It's one of the joys of a teacher or assistant, when judging the correctness of a student's program: trying to get it to behave strangely.

---

### Post by CryptAck on 2012-02-16
> **Bachstelze said:**
> What? Data validation is *always* required. And don't tell me it's "too complicated"; if you can use isdigit(), you can use isalnum().

I agree that in this situation performing data validation is quite simple (plus, with direct user input you'll almost always encounter bad data at some point). But in my opinion, the theory that data validation is *always required* for programs is a bit costly.

Depending on the software or system's architecture there are times when a specific program should not have to worry about invalid data. Another program, or process, should have handled this validation ahead of the current program. Repeating the same validation routines just costs extra time. 

Good system/software design is about ensuring that all  requirements are fulfilled. If a requirement appears to be missing, it should be discussed and added before being coded.

---

### Post by CryptAck on 2012-02-16
> **Arndt said:**
> It's one of the joys of a teacher or assistant, when judging the correctness of a student's program: trying to get it to behave strangely.

Completely agree! :)

---


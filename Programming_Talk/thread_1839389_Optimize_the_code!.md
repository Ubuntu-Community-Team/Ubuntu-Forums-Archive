---
title: "Optimize the code!"
date: 2011-09-05
forum: Programming Talk
---

### Post by sjs7007 on 2011-09-05
Hey, I tried to solve this problem.([http://www.codechef.com/problems/K2)using](http://www.codechef.com/problems/K2)using) this code.


Though my code was right , it exceeded the time limit.


#include<stdio.h>
void convert(long long int number,long long int base,int *converted,int *index);
void palcheck( int converted[1000], int *index, int *test);
main()
{
long long int number,base;
int converted[1000],test=1,index,t,i;
scanf("%d",&t);
for(i=1;i<=t;i++)
{
test=1;
scanf("%lld",&number);
for(base=2;base<=number-1;base++)
{
convert(number,base,converted,&index);
palcheck(converted,&index,&test);
if(test==0) printf("%lld \n",base) && (base=number+1);
}
if(test!=0) printf("%lld \n",number+1);

}
}



void convert(long long int number,long long int base, int *converted,int *index)
{
int i;
for(i=1;number>0;i++)
{
converted[i]=number%base;
number=number/base;
}
*index=i-1;
}

void palcheck(int *converted , int *index, int *test)
{
int i,k=0;
for(i=1;i<=*index;i++)
{
if(converted[i]==converted[*index-i+1]) k++ ;
else (i=*index+1);
}
if(k==*index) *test=0;
else *test=1;
}

Basically the pseudo code is :

1: Take in number.
2. Convert it to base n in this method and store each digit in array.

for(i=1;number>0;i++)
{
converted[i]=number%base;
number=number/base;
}

3. Check if 1st and last digit are same,if yes then if 2nd and 2nd last and so on for palindromic condition.....


Any ideas how to optimize the code?

---

### Post by dwhitney67 on 2011-09-05
What does this code do?  Perhaps before attempting the scanf(), you could issue a prompt.

It would better for us if you would post the problem, rather than the solution... which is impossible to say if it "works", since I don't know what problem you are trying to solve.


P.S.  Why are you converting the input?  Read it in as a string, and leave it as such when doing the comparisons!

---

### Post by Marlonsm on 2011-09-05
I think the part where you check if it's a palindrome can be optimized.

It seems you're testing every number twice, for example, the number 123321:

1 = 1 (ok)
2 = 2 (ok)
3 = 3 (ok)
3 = 3 (ok)
2 = 2 (ok)
1 = 1 (ok)

If the first half of those tests is true, the second half will also be, so there is no need to test it. Just remember that there will be two slightly different cases, an even string length or an odd one. 

I'm not sure something similar can be done in your case, but in Python, to test a number "n", I'd just do something like:
```
if str(n) == str(n)[::-1] :
```
The [::-1] part inverts the whole string, so a single test is done.

---

### Post by gardnan on 2011-09-05
> if(test==0) printf("%lld \n",base) && (base=number+1);
Alright, I am confused. This line looks like Perl or Bash script.

---

### Post by sjs7007 on 2011-09-05
@dwhitney67: I already posted the link to the problem. [http://www.codechef.com/problems/K2](http://www.codechef.com/problems/K2). And yes I'll surely add what to input in print.



@marlonsm : Thanks dude. But for some strange reason its not giving output for large nos like(9876543219) after making the change. I have added a comment in the line I made the change
Have a look : [http://dl.dropbox.com/u/19182824/current_change.c](http://dl.dropbox.com/u/19182824/current_change.c)


@gardnan : Its in C.


#include<stdio.h>
void convert(long long int number,long long int base,int *converted,int *index);
void palcheck( int converted[1000], int *index, int *test);
main()
{
    long long int number,base;
    int converted[1000],test=1,index,t,i;
    printf("Enter the number of test cases : ");
    scanf("%d",&t);
    for(i=1;i<=t;i++)
    {
        test=1;
        printf("Enter the number : ");
        scanf("%lld",&number);
        for(base=2;base<=number-1;base++)
        {
            convert(number,base,converted,&index);
            palcheck(converted,&index,&test);
            if(test==0) printf("The smallest base in which given number is palindromic is %lld \n",base) && (base=number+1);
        }
    if(test!=0) printf("The smallest base in which given number is palindromic is %lld \n",number+1);

    }
}



void convert(long long int number,long long int base, int *converted,int *index)
{
    int i;
    for(i=1;number>0;i++)
    {
        converted[i]=number%base;
        number=number/base;
    }
    *index=i-1;
}

void palcheck(int *converted , int *index,  int *test)
{
    int i,k=0,p;
    for(i=1;i<=*index;i++)
    {
        if(converted[i]==converted[*index-i+1]) k++ ;
        else (i=*index+1);
    }
    if(k==*index) *test=0;
    else *test=1;
}

Or here is the file: [http://dl.dropbox.com/u/19182824/current_4.c](http://dl.dropbox.com/u/19182824/current_4.c)

Thanks to everyone for your prompt replies!

---

### Post by Arndt on 2011-09-05
> **sjs7007 said:**
> @dwhitney67: I already posted the link to the problem. [http://www.codechef.com/problems/K2](http://www.codechef.com/problems/K2). And yes I'll surely add what to input in print.



@marlonsm : Thanks dude. But for some strange reason its not giving output for large nos like(9876543219) after making the change. I have added a comment in the line I made the change
Have a look : [http://dl.dropbox.com/u/19182824/current_change.c](http://dl.dropbox.com/u/19182824/current_change.c)


@gardnan : Its in C.


#include<stdio.h>
void convert(long long int number,long long int base,int *converted,int *index);
void palcheck( int converted[1000], int *index, int *test);
main()
{
    long long int number,base;
    int converted[1000],test=1,index,t,i;
    printf("Enter the number of test cases : ");
    scanf("%d",&t);
    for(i=1;i<=t;i++)
    {
        test=1;
        printf("Enter the number : ");
        scanf("%lld",&number);
        for(base=2;base<=number-1;base++)
        {
            convert(number,base,converted,&index);
            palcheck(converted,&index,&test);
            if(test==0) printf("The smallest base in which given number is palindromic is %lld \n",base) && (base=number+1);
        }
    if(test!=0) printf("The smallest base in which given number is palindromic is %lld \n",number+1);

    }
}



void convert(long long int number,long long int base, int *converted,int *index)
{
    int i;
    for(i=1;number>0;i++)
    {
        converted[i]=number%base;
        number=number/base;
    }
    *index=i-1;
}

void palcheck(int *converted , int *index,  int *test)
{
    int i,k=0,p;
    for(i=1;i<=*index;i++)
    {
        if(converted[i]==converted[*index-i+1]) k++ ;
        else (i=*index+1);
    }
    if(k==*index) *test=0;
    else *test=1;
}

Or here is the file: [http://dl.dropbox.com/u/19182824/current_4.c](http://dl.dropbox.com/u/19182824/current_4.c)

Thanks to everyone for your prompt replies!

Please use CODE tags around your code, so the indendation is kept (you can use the # tool in the toolbar).

---

### Post by dwhitney67 on 2011-09-05
> **sjs7007 said:**
> @dwhitney67: I already posted the link to the problem. [http://www.codechef.com/problems/K2](http://www.codechef.com/problems/K2).

Here's my rebuttal:  [http://dictionary.reference.com/browse/proofread](http://dictionary.reference.com/browse/proofread)

Please re-read your original post (OP) and please let the world know what you see after you click on the URL you supplied.

---

### Post by sjs7007 on 2011-09-05
.

---

### Post by sjs7007 on 2011-09-05
@arndt: ```




#include<stdio.h>
void convert(long long int number,long long int base,int *converted,int *index);
void palcheck( int converted[1000], int *index, int *test);
main()
{
    long long int number,base;
    int converted[1000],test=1,index,t,i;
    printf("Enter the number of test cases : ");
    scanf("%d",&t);
    for(i=1;i<=t;i++)
    {
        test=1;
        printf("Enter the number : ");
        scanf("%lld",&number);
        for(base=2;base<=number-1;base++)
        {
            convert(number,base,converted,&index);
            palcheck(converted,&index,&test);
            if(test==0) printf("The smallest base in which given number is palindromic is %lld \n",base) && (base=number+1);
        }
    if(test!=0) printf("The smallest base in which given number is palindromic is %lld \n",number+1);

    }
}



void convert(long long int number,long long int base, int *converted,int *index)
{
    int i;
    for(i=1;number>0;i++)
    {
        converted[i]=number%base;
        number=number/base;
    }
    *index=i-1;
}

void palcheck(int *converted , int *index,  int *test)
{
    int i,k=0,p;
    for(i=1;i<=*index;i++)
    {
        if(converted[i]==converted[*index-i+1]) k++ ;
        else (i=*index+1);
    }
    if(k==*index) *test=0;
    else *test=1;
}




```


@dwhitney67: I had realized my mistake after your comment. But in my defense I had put the link was in parenthesis. But since I was wrong , I am sorry.

---


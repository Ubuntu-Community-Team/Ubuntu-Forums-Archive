---
title: "scanf not working and program not running"
date: 2012-09-29
forum: Programming Talk
---

### Post by dharmvir tiwari on 2012-09-29
```

#include<stdio.h>
void main()
{
    int i,j,b[100],w[100],t[100],s[100],count,max=0,tq,temp=0,temp1,n;
    float aw=0,at=0;
    printf("\nENTER THE NUMBER OF PROCESSES:");
    scanf(" %d",&n);// Warning: ignoring return value of ‘scanf’,  declared with attribute      //warn_unused_result [-Wunused-result] (a)
    printf("\nENTER THE PROCESSES BURST TIMES:");
    for(i=0;i<n;i++)
    {
        scanf(" %d",&b[i]);
        s[i]=b[i];
    }
    printf("\nENTER THE TIME QUANTUM:");
    scanf(" %d",&tq);
    for(i=0;i<n;i++)
    {
        if(max<b[i])
        {
            max=b[i];
        }
    }
    if((max%tq)==0)
    {
        count=max/tq;
    }
    else
    count=(max/tq)+1;
    for(i=0;i<count;i++)
    {
    for(j=0;j<n;j++)
    {
        if(s[j]>tq)
        {
            temp1=temp;
            temp=temp+tq;
            printf("\nPROCESS %d EXECUTED FROM %d TO %d",j,temp1,temp);
            s[j]=s[j]-tq;
        }
        else
        if(s[j]<tq && s[j]>=0)
        {
            temp1=temp;
            temp=s[j];
            printf("\nPROCESS %d EXECUTED FROM %d TO %d",j,temp1,temp);
            t[j]=temp;
            s[j]=-1;
        }
    }
    printf("\n\n");
    }
    for(i=0;i<n;i++)
    {
        w[i]=w[i-1]+b[i-1];
        t[i]=t[i-1]+b[i];
    }
    for(i=0;i<n;i++)
    {
        aw+=w[i];
        at+=t[i];
    }
    aw=aw/n;
    at=at/n;
    printf("\nPROCESS\tBURST TIME\tWAITING TIME\tTURN AROUND TIME\n");
    for(i=0;i<n;i++)
    {
        printf("\np%d\t\t%d\t\t%d\t\t%d\n",i,b[i],w[i],t[i]);
    }
    printf("\nAVERAGE WAITING TIME:%fmS\tAVERAGE TURN AROUND TIME:%fmS",aw,at);
    }

```


i have tried it many times but the same warning is being prompted
"ignoring return value of ‘scanf’, declared with attribute warn_unused_result [-Wunused-result] "
when i used c++ for the same code,the compiler isn't recognizing <iostream>
please help me with that,i have attached the screen shot of the warning being displayed.

---

### Post by spjackson on 2012-09-29
> **dharmvir tiwari said:**
> i have tried it many times but the same warning is being prompted
"ignoring return value of &#8216;scanf&#8217;, declared with attribute warn_unused_result [-Wunused-result] "
when i used c++ for the same code,the compiler isn't recognizing <iostream>
please help me with that,i have attached the screen shot of the warning being displayed.
The return type of main should be int, not void.

By specifying -Wunused-result, you have asked the compiler to warn you if you call a function that returns a value and you don't use the returned value. So that's what it is doing. If you do not want this warning, then turn off that compiler flag. If you want to know how to use the result of scanf then "man scanf" gives you a perfect example.

As for compiling the same code with C++, I don't understand what you are saying. You don't include <iostream> so how do you expect it to be recognised? What error message do you get? And if the code is not **exactly** the same, then post the differences.

---

### Post by dharmvir tiwari on 2012-09-29
But when i am turning of the warning then i am not able to provide any input to the program,the program is only printing and not taking any input.
And about the c++ counterpart,when we are using the input and output streams(cin>> , cout<<) in place of scanf and printf  then also i am not able to give any input to the program.

---

### Post by Doug S on 2012-09-29
It is not clear to me what the problem is for you. I compiled your program, as posted with no errors or warnings, and it ran fine for me. Note: I only run Ubuntu server editions, no gui.
Example of my run:```
doug@doug-64:~/c$ ./forum2064352
ENTER THE NUMBER OF PROCESSES:4
ENTER THE PROCESSES BURST TIMES:4
4
4
4
ENTER THE TIME QUANTUM:4
 
PROCESS BURST TIME      WAITING TIME    TURN AROUND TIME
p0              4               65222           32615
p1              4               65226           32619
p2              4               65230           32623
p3              4               65234           32627
AVERAGE WAITING TIME:65228.000000mS     AVERAGE TURN AROUND TIME:32621.000000mSdoug@doug-64:~/c$

```I compiled with this command:```
doug@doug-64:~/c$ cc forum2064352.c -o forum2064352
doug@doug-64:~/c$
```

---

### Post by dharmvir tiwari on 2012-09-30
> **spjackson said:**
> The return type of main should be int, not void.

By specifying -Wunused-result, you have asked the compiler to warn you if you call a function that returns a value and you don't use the returned value. So that's what it is doing. If you do not want this warning, then turn off that compiler flag. If you want to know how to use the result of scanf then "man scanf" gives you a perfect example.

As for compiling the same code with C++, I don't understand what you are saying. You don't include <iostream> so how do you expect it to be recognised? What error message do you get? And if the code is not **exactly** the same, then post the differences.

Can you explain me  more about -Wunused-result?

---

### Post by dharmvir tiwari on 2012-09-30
> **Doug S said:**
> It is not clear to me what the problem is for you. I compiled your program, as posted with no errors or warnings, and it ran fine for me. Note: I only run Ubuntu server editions, no gui.
Example of my run:```
doug@doug-64:~/c$ ./forum2064352
ENTER THE NUMBER OF PROCESSES:4
ENTER THE PROCESSES BURST TIMES:4
4
4
4
ENTER THE TIME QUANTUM:4
 
PROCESS BURST TIME      WAITING TIME    TURN AROUND TIME
p0              4               65222           32615
p1              4               65226           32619
p2              4               65230           32623
p3              4               65234           32627
AVERAGE WAITING TIME:65228.000000mS     AVERAGE TURN AROUND TIME:32621.000000mSdoug@doug-64:~/c$

```I compiled with this command:```
doug@doug-64:~/c$ cc forum2064352.c -o forum2064352
doug@doug-64:~/c$
```
I got that,it was a problem with my IDE.There i was not using console project,please check the same code with some IDE other than cosole project.I have attached a thumbnail of monodevelop.
Thanks for that.

---

### Post by The Cog on 2012-09-30
Moved to Programming Talk

---

### Post by Tony Flury on 2012-09-30
> **dharmvir tiwari said:**
> Can you explain me  more about -Wunused-result?

It does what you expect - it turns on the Unused Result Warning. Essentially if you do a 
```

man scanf

```
You will see immediately that scanf is defined to return a integer :

```

SCANF(3)                   Linux Programmer's Manual                  SCANF(3)

NAME
       scanf,  fscanf, sscanf, vscanf, vsscanf, vfscanf - input format conver&#8208;
       sion

SYNOPSIS
       #include <stdio.h>

       int scanf(const char *format, ...);

```

that integer is the number of values read when you execute scanf 

```

RETURN VALUE
       These  functions  return the number of input items successfully matched
       and assigned, which can be fewer than provided for, or even zero in the
       event of an early matching failure.

       The  value EOF is returned if the end of input is reached before either
       the first successful conversion or a matching failure occurs.   EOF  is
       also returned if a read error occurs, in which case the error indicator
       for the stream (see ferror(3)) is set, and errno is  set  indicate  the
       error.

```

Your code is not using the result - hence prompting the Unused Result warning - it does exactly what it says on the tin.

You should note though it is only a warning - not an error, and unless your IDE is doing something really stupid, it should have created the executable, which will execute fine.

---


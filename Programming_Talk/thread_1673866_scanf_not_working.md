---
title: "scanf not working"
date: 2011-01-23
forum: Programming Talk
---

### Post by c2tarun on 2011-01-23
```

do
 {
  printf("\n1.PUSH");
  printf("\n2.POP");
  printf("\n3.TRAVERSE");
  printf("\nEnter your choice");
  scanf("%d",&choice);
  switch(choice)
    {
    case 1: push();
        break;
    case 2: pop();
        break;
    case 3: traverse();
        break;
    default : printf("\nwrong choice");
    }
    printf("\n do you wish to continue(Y/N)");
    scanf("%c",&ch);  // This line is not working
  }
   while(ch =='Y'|| ch =='y');

```
this is the part of a code. I tried to run the programs. Whole program is working fine the only problem is the line with comment is not accepting any input. Is it possible that the break statement is breaking the whole loop?
Edit: Just now i tried by changing the declaration of ch to 'char ch[2]' and then commented line to 'scanf("%s",ch);' and condition of whole to 'ch[0]== 'Y')' now everything is working fine. What was wrong with '%c'?

---

### Post by Roberto_Lapuente on 2011-01-23
Which programming language are you using?

---

### Post by Roberto_Lapuente on 2011-01-23
Im new to c, c++; but in Java the break instruction will break the loop. You should use if else instead of the swith instruction.

---

### Post by slavik on 2011-01-23
put a space in front of %c.

Also, above comment is wrong on many different levels.

---

### Post by c2tarun on 2011-01-23
> **slavik said:**
> put a space in front of %c.

Also, above comment is wrong on many different levels.

It worked, Can you please explain why do we have to put a space there?

---

### Post by dharmvir tiwari on 2012-09-28
#include<stdio.h>
void main()
{
    int i,j,b[100],w[100],t[100],s[100],count,max=0,tq,temp=0,temp1,n;
    float aw=0,at=0;
    printf("\nENTER THE NUMBER OF PROCESSES:");
    scanf(" %d",&n);// Warning: ignoring return value of ‘scanf’, declared with attribute      //warn_unused_result [-Wunused-result] (a)
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
    /*I am using MonoDevelop IDE and i am getting the warnig as "ignoring return value of ‘scanf’, declared with attribute warn_unused_result [-Wunused-result] (a)" at all the places where i am using scanf function ,please help me with that*/

---

### Post by Tony Flury on 2012-09-28
dharmvir tiwari : 

Two things :
[LIST=1]
[*]Include your code in code tags - it makes your code a lot easier to read
[*]Don't hijack someone elses thread - i know your question is slightly connected - but it is different, so start a new thread.
[/LIST]

---

### Post by Tony Flury on 2012-09-28
> **c2tarun said:**
> It worked, Can you please explain why do we have to put a space there?

Your initial scanf to input your choice 

scanf("%d",&choice)

will only read the numbers from the input, and leave everything else on your input stream (including the newline character, or any spaces, letters etc). In theory this would be accepted as input "2abce" - and you would get 2 back and the "abce" will still be on the input stream.

Your next scanf : 

scanf("%c",&ch)

will read the next character in the input stream - which is probably the newline.

by putting the space before the "%c" the scanf will ignore the whitespace characters (including the newline).

Taking user input using scanf is not a great idea because of these problems - it is recommend by most people that you read input one character at a time, and check it as you go to make sure that the input is valid.  scanf works best when you can guarantee that the data is a known forma - which you never can if a human is typing it :-)

---


---
title: "code problem :("
date: 2012-08-15
forum: Programming Talk
---

### Post by adityamagadi on 2012-08-15
hey guys i was trying to implement the RSA algorithm in C with the following code :
 
```
#include<stdio.h>
#include<stdlib.h>
#include<math.h>
long int e=0,d=0,n=0;
long int val[50];
char decode(long int ch)
{
 int i;
 long int temp=ch;
 for(i=1;i<d;i++)
  ch=(temp*ch)%n;
 return ch;
}
int gcd(long int a,long int b)
{
 long int temp;
 while(b!=0)
 {
  temp=b;
  b=a%b;
  a=temp;
 }
 return a;
}
int prime(int a)
{
 int i;
 for(i=2;i<a;i++)
 {
  if((a%i)==0)
   return 0;
 }
 return 1;
}
int encode(char ch)
{
 int i;
 long int temp;
  temp=ch;
 for(i=1;i<e;i++)
  temp=(temp*ch)%n;
 return temp;
}
int main()
{
 int i;
 long int p;
 long int q,phi,c[50];
 char text[50],ctext[50];
 printf("Enter the text to be encoded:   ");
 scanf("%s",text);
 do
 {
  p=rand()%30;
 }while(!prime(p));
 do
 {
  q=rand()%30;
 }while(!prime(q));
 n=p*q;
 phi=(p-1)*(q-1);
 printf("\n p=%d\t q=%d\t n=%d\t phi=%d\n", p,q,n,phi);
 do
 {
  e=rand()%phi;
 }while(!gcd(e,phi));
 do
 {
  d=rand()%phi;
 }while(((d*e)%phi)!=1);
 printf("*******Encoding Message********\n\n");
 //sleep(5);
 for(i=0;text[i]!='\0';i++)
  val[i]=encode(text[i]);
 val[i]=-999;
 printf("\n Encoded Message:    ");
 for(i=0;val[i]!=-999;i++)
  printf("%ld",val[i]);
 printf("\n\n*****Decoding Encryted Message**********\n\n");
 //sleep(5);
 for(i=0;val[i]!=-999;i++)
  ctext[i]=decode(val[i]);
 ctext[i]='\0';
 printf("\n Decoded Message is: %s \n\n",ctext);
}
```
 
 
i dont understand why my code execution is getting stuck at printing the values of n,p,q and phi .
 
can someone provide a fix to this issue?
 
-thanks in advance :)

---

### Post by sffvba[e0rt on 2012-08-15
*Thread moved to **Programming Talk**.*


404

---

### Post by steeldriver on 2012-08-15
what do you mean exactly by 'getting stuck at'?[B]

%d[/B] is the printf format specifier for **int** - since you have declared your variables as **long int** you would need **%ld** I think - it will probably print the wrong values if you use %d but it shouldn't 'get stuck' afaik

---

### Post by Bachstelze on 2012-08-15
What is this?

```
 }while(!gcd(e,phi));
```

---

### Post by adityamagadi on 2012-08-15
by getting stuck i mean the execution just stops and i have to manually kill the process.

---

### Post by steeldriver on 2012-08-15
well like Bachstelze indicates you need to check that your do...while loop(s) have valid exit conditions - put some additional printfs in if necessary

---


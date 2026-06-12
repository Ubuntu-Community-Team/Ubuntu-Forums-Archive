---
title: "Tthree sets of Array to be displayed in three columns"
date: 2009-11-19
forum: Programming Talk
---

### Post by gracebueno12 on 2009-11-19
Please help me rum this program... please.
 
 
Write a program that will declare 3 sets of array.
The first array will accept 5 integers which then be arranged in ascending order and stored in such order in the second array. The third array should contain the same set of numbers, however, this time, the integers are arranged in descending order.
 
Display the output in Three columns representing the three arrays together with its subscripts.
 
Also, the program should display the number that has the highest and the lowest value.
 
I have already made a program but its output is not yet in three columns. And It doesnt display the output of the highest and lowest number yet.
 
#include<stdio.h> 
#include<conio.h> 
void main(){ 
int i,j,k,l,temp,mark[5]; 
for(i=0;i<5;i++){
printf("First array. Enter integer: %d:", i); 
scanf("%d",&mark[i]); 
}
for (i=0;i<5;i++) 
for(j=i+1;j<5;j++) 
{ 
if(mark[i]>mark[j]) 
{ 
temp=mark[j]; 
mark[j]=mark[i]; 
mark[i]=temp; 
}}
printf("\n \nSecond Array in Ascending Order:"); 
for(i=0;i<5;i++) 
{ 
printf("\n%d",mark[i]);
}
printf("\n \n");
for (i=0;i<5;i++) 
for(j=i+1;j<5;j++) 
{ 
if(mark[i]<mark[j]) 
{ 
temp=mark[j]; 
mark[j]=mark[i]; 
mark[i]=temp; 
}}
printf("\nThird Array in Descending Order:");
for(i=0;i<5;i++) 
{ 
printf("\n%d",mark[i]);
}
printf("\n \n \n");
getch(); 
} 

 
Thank YOU.

---

### Post by meson2439 on 2009-11-20
Although I know this is your homework, but since I'm a newbie myself, I'm using this to give myself a practice.

```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[])
{
	int mark[5], kram[5],markp[5];
	int i,tp,k;
	char marks[5];
	char *endptr;
	
	/*assigning arrays*/
	
	for(i=0;i<5;i++)
	{
		printf("First array. Enter integer: %d \n",i);
		fgets(marks,5,stdin);
		mark[i]=strtol(marks,&endptr,10);
		markp[i]=mark[i];
	}
	
	/*ascending order*/
	
	k=1;//give it a positive value first to start the loop
	while (k>0)
	{
		k=0;
		for (i=1;i<5;i++)
		{
			if (markp[i]<markp[i-1])
			{
				k++;
				tp=markp[i];
				markp[i]=markp[i-1];
				markp[i-1]=tp;
			}
		}
	}
	
	/*descending order*/
	for (i=0;i<5;i++) kram[4-i]=markp[i];
	
	/*printing assigned arrays*/
	printf("\nThe arrays all printed out\n");
	for (i=0;i<5;i++)
	{
		printf("%d \t %d \t %d\n",mark[i],markp[i],kram[i]);
	}
	
	/*printing maximum values
	 * every other array has the same value so*/
	printf("maximum values=%d, minimum values=%d\n",markp[0],markp[4]);
		
	return 0;
}

```

p.s: please indent your code, it is very hard to read (not that mine was any better in terms of style). Also use the spell checker.

---


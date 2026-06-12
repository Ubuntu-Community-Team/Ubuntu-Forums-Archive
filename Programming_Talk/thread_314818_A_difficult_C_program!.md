---
title: "A difficult C program!"
date: 2006-12-08
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2006-12-08
I have wrote a c program,it is used for print date(from 20030101 to 20041231).
There is some bugs in my program,but I can not find it.
May be I need some help.Thanks for the people helping me!
The bug is different months show the mess day-count(june have 29 days,other months is the same)
The program as follows:


#include<stdio.h>
main()
{
	int d[2]={0,1},m[2]={0,1},y[4]={2,0,0,3};
	int year,month,day;
	
	while(y[3]<5){
		year=y[0]*1000+y[1]*100+y[2]*10+y[3];
		month=1;
		m[0]=0;m[1]=1;
		
		 
	while(month<12)	{
		month=m[0]*10+m[1];
		d[0]=0;d[1]=1;
		
			while(1)	{
	 	day=d[0]*10+d[1];
	 	printf("%d%d%d%d%d%d%d%d\n",y[0],y[1],y[2],y[3],m[0],m[1],d[0],d[1]);
	 	if(d[1]==9)
	 		{d[1]=0;
	 		  d[0]++;}
	 	else d[1]++;
	 	
	 	if(month==1||3||5||7||8||10||12){
			if(day==31)  	break;
			}
	 	
			if(month==4||6||9||11){
				if(day==30)	break;
				}
			
			    if((year%4==0&&year%100!=0)||(year%400==0))
					{if(day==29)break;}
				else
					if(day==28 )break;	
	}			
		
		if(m[1]==9)
			{m[1]=0;
			  m[0]++;}
		else m[1]++;
	
	}
	

		if(y[3]==9)
			{y[3]=0;
			  y[2]++;}
		else y[3]++;
	
	}

}

---

### Post by engineer on 2006-12-08
sounds like school homework!

i'd recommend to use more braces. then you'll find the errors more easily.

---

### Post by Klipt on 2006-12-08
Put your code in code tags so the formatting doesn't disappear; it's easier to read.

The main problem is that you can't say
```
if (x == 0 || 1 || 2)
```
Since in C integer values are considered 'false' if 0 and 'true' otherwise, so you're saying "If x == 0, or 1, or 2" which will always be true since 1 is non-zero. You have to write it like
```
if (x == 0 || x == 1 || x == 2)
```

---

### Post by Lster on 2006-12-08
Yes, it would be easier to read if you indented the code and used braces.

---

### Post by daniminas on 2006-12-08
Like Klipt says, the solution, i think is to change:

```
if (x == 0 || 1 || 2)
```

and put:

```
if (x == 0 || x == 1 || x == 2)
```


;)

---

### Post by LaoLiulaoliu on 2006-12-09
thank you for all of you!

---

### Post by Wim Sturkenboom on 2006-12-09
You certainly have a complicated way of doing it; but OK, nobody knows all C functions

```
step 1
use mktime to calculate the number of seconds since 01-01-1970 for the first date (t1) and for the last date (t2)
step 2
increment t1 by the number of seconds in a day
step 3
use localtime to get year, month and day from t1
print it
step 4
goto to step 2 if t2>t1
```

---


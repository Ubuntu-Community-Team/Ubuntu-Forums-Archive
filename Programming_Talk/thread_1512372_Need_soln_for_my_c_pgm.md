---
title: "Need soln for my c pgm"
date: 2010-06-18
forum: Programming Talk
---

### Post by navaneethan on 2010-06-18
Good morning to all,

THis is the c program which i have done in my own logic 
I **expect the output**

> A B C D E F F E D C B A
A B C D E E D C B A
A B C D D C B A
A B C C B A
A B B A
A A

**my pgm.c**

> #include<stdio.h>
void main()
{
	int i,j,k,n=6;
	char a[7];
	printf("ENTER A TO F:=");
	for(i=0;i<6;i++)
	{
		scanf("%c",&a[i]);
	}
	while(n>=0)
	{
		for(j=0;j<=n;j++)
		printf("%s",a[j]);
		for(k=n;k>=0;k--)
		{
			printf("%s",a[k]);
		}
		printf("\n");
	n-=1;
	}	
}



but when i execute this program i have no errors but couldn't able to get output...please suggest me

---

### Post by schauerlich on 2010-06-18
At the very least, put it in [noparse]```
[/noparse] tags.

Also, use -Wall whenever you compile things. If you did, you would have seen this:

[code]warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;
```

you also have some issues with the bounds on your for loops (> vs >=, etc)

```
[color=#BC7A00]#include <stdio.h>
[/color]
[color=#B00040]int[/color] [color=#0000FF]main[/color]([color=#B00040]void[/color]) {
  [color=#B00040]int[/color] i, j, k, n [color=#666666]=[/color] [color=#666666]6[/color];
  [color=#B00040]char[/color] a[[color=#666666]7[/color]];

  printf([color=#BA2121]"ENTER A TO F:= "[/color]);

  [color=#008000]**for**[/color] (i [color=#666666]=[/color] [color=#666666]0[/color]; i [color=#666666]<[/color] [color=#666666]6[/color]; i[color=#666666]++[/color]) {
    scanf([color=#BA2121]"%c"[/color], [color=#666666]&[/color]a[i]);
  }

  [color=#008000]**while**[/color] (n [color=#666666]>=[/color] [color=#666666]0[/color]) {
    [color=#008000]**for**[/color] (j [color=#666666]=[/color] [color=#666666]0[/color]; j [color=#666666]<[/color] n ;j[color=#666666]++[/color]) {
      printf([color=#BA2121]"%c "[/color], a[j]);
    }

    [color=#008000]**for**[/color] (k [color=#666666]=[/color] n [color=#666666]-[/color] [color=#666666]1[/color]; k [color=#666666]>=[/color] [color=#666666]0[/color]; k[color=#666666]--[/color]) {
      printf([color=#BA2121]"%c "[/color],a[k]);
    }

    printf([color=#BA2121]"[/color][color=#BB6622]**\n**[/color][color=#BA2121]"[/color]);
    n [color=#666666]-=[/color] [color=#666666]1[/color];
  }
  
  [color=#008000]**return**[/color] [color=#666666]0[/color];
}

```
[good luck on the rest of your homework](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by navaneethan on 2010-07-08
This is not my home work I was practicing on it

---


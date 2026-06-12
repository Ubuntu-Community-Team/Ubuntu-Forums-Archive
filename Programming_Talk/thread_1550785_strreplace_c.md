---
title: "strreplace c"
date: 2010-08-11
forum: Programming Talk
---

### Post by navaneethan on 2010-08-11
In this program i wanna replace a character in the given string
for example if i give a string **"kongu"**
and i give the character "**n**"
again i give the character "**z**" to replace the "n"
final string should be "kozgu"
 
i wrote the program
 
 
 
```
#include<stdio.h>
#include<conio.h>
void main()
{
	char s[10],ch,c;
	int i,n=0;
	clrscr();
	printf("Enter the String:");
	scanf("%s",&s);
        printf("\nEnter the char from the string to replace:");
	scanf("%c",&ch);
	printf("\nEnter the fresh char to be replaced:");
	scanf("%c",&c);
	n=strlen(s);
	for(i=0;i<n;i++)
	{
		if(s[i]==ch){
			s[i]=c;
			printf("Replaced");
			}
		else
			continue;
	}
	printf("The replaced string is:%s",s);
	getch();
}
```
 
Is any problem to get output,I didn't get plz check it ,actually my concept is correct i think then where is the issue to get?
please suggest

---

### Post by Bachstelze on 2010-08-11
Don't use scanf.  Try this program, maybe you'll see what's wrong.

```
#include <stdio.h>

int main(void)
{
    char a, b;
    printf("a? ");
    scanf("%c", &a);
    printf("b? ");
    scanf("%c", &b);
    printf("a: %c; b: %c\n", a, b);
    return 0;
}

```

---

### Post by navaneethan on 2010-08-11
ya when we use scanf for getting a character as a input the "ENTER" will be taken as a character ,ya i accept,rather than scanf what will be chosen to do?

---

### Post by Bachstelze on 2010-08-11
You need to flush the input. This will work:

```
#include <stdio.h>

int main(void)
{
    int a, b, c;
    printf("a? ");
    a = getchar();
    while((c = getchar()) != EOF && c != '\n');
    printf("b? ");
    b = getchar();
    while((c = getchar()) != EOF && c != '\n');
    printf("a: %c; b: %c\n", a, b);
    return 0;
}

```

And for heaven's sake, **[font=monospace]int main(void)[/font]**!

---

### Post by navaneethan on 2010-08-11
> **Bachstelze said:**
> Don't use scanf.  Try this program, maybe you'll see what's wrong.

```
#include <stdio.h>

int main(void)
{
    char a, b;
    printf("a? ");
    scanf("%c", &a);
    printf("b? ");
    scanf("%c", &b);
    printf("a: %c; b: %c\n", a, b);
    return 0;
}

```

Here almost Got the answer

```
#include<stdio.h>
#include<conio.h>
void main()
{
	char s[10],ch,c;
	int i,n=0;
	clrscr();
	printf("Enter the String:");
	gets(s);
       printf("\nEnter the char from the string to replace:");
	//scanf("%c",&ch);
	ch=getchar();
	//printf("Enter the fresh char to be replaced:");
	//scanf("%c",&c);
	c=getchar();
	n=strlen(s);
	for(i=0;i<n;i++)
	{
		if(s[i]==ch){
			s[i]=c;
			printf("\nReplaced");
			}
		else
			continue;
	}
	printf("The replaced string is:%s",s);
	getch();
}
```

for a single character to get as a input we should not use scanf that i learned here :-)

---

### Post by navaneethan on 2010-08-11
> **Bachstelze said:**
> You need to flush the input. This will work:

```
#include <stdio.h>

int main(void)
{
    int a, b, c;
    printf("a? ");
    a = getchar();
    while((c = getchar()) != EOF && c != '\n');
    printf("b? ");
    b = getchar();
    while((c = getchar()) != EOF && c != '\n');
    printf("a: %c; b: %c\n", a, b);
    return 0;
}

```

And for heaven's sake, **[font=monospace]int main(void)[/font]**!


yeah! very nice information Thanks a lot!!!I can able to understand the purpose of while which avoids the newline character !!! Is any special case hided behind the while? please if yes means let me know nreiefly

---

### Post by Bachstelze on 2010-08-11
The while says: if there is a character waiting on stdin, get it. If it is not newline, do it again. So in this case, assuming you just entered one character + newline, the first getchar() will get the character, and then the while condition will get the newline. You can enter as many characters as you want, it will always get the first one, and discard the rest.

---

### Post by navaneethan on 2010-08-11
thank god introducing such a solver!!!
please just a little one!!

why can't we express the thing like that? because you say c gets a newline (\n) char and it leaves ..ya absolutely the condition goes wrong ultimately..

while((c = getchar()) != EOF && c != '\n')
{ empty;
}
 next stmt;

then what is the difference both of them?

while((c = getchar()) != EOF && c != '\n');
 next stmt;

Is both while cases are true?

thanks wiser!!! love your knowledge!!!

---

### Post by navaneethan on 2010-08-11
I would like to say once again thanks dear friend :-) I am happy now

---

### Post by Bachstelze on 2010-08-11
> **navaneethan said:**
> 
while((c = getchar()) != EOF && c != '\n')
{ empty;
}
 next stmt;

then what is the difference both of them?

while((c = getchar()) != EOF && c != '\n');
 next stmt;

Is both while cases are true?

They do exactly the same thing.

```
while((c = getchar()) != EOF && c != '\n');
```

```
while((c = getchar()) != EOF && c != '\n')
        ;
```

```
while((c = getchar()) != EOF && c != '\n') {
        ;
}
```

```
while((c = getchar()) != EOF && c != '\n')                   ;
```

```
while((c = getchar()) != EOF && c != '\n')





;
```

```
while((c = getchar()) != EOF && c != '\n')







{






;





}
```

Same thing. C does not care how much whitespace you put between constructs.

---

### Post by navaneethan on 2010-08-11
I follow you :-) keep on going :-)

---

### Post by dwhitney67 on 2010-08-11
Now that you understand the limitations of scanf(), and have learned to manually *flush* the standard-in stream, it is time to learn about fgets().


```

#include <stdio.h>
#include <string.h>

int main(void)
{
   char  str[10];
   char* nl = 0;

   printf("Enter the string: ");
   fgets(str, sizeof(str), stdin);  // use fgets() to prevent buffer overrun

   nl = strchr(str, '\n');   // check if newline char is in string

   if (nl)
   {
      *nl = '\0';   // replace newline char with null char.
   }

   ...
}

```

---

### Post by WitchCraft on 2010-08-11
I might be wrong, but shouldn't that be strrchr ?

Edit: oh well, no, doesn't matter, it's enter-delimited input ;-)

---

### Post by navaneethan on 2010-08-12
May i know about strchr() here?
Actually what is the difference between flushing stdin and buffer overrun please?

---

### Post by dwhitney67 on 2010-08-12
> **navaneethan said:**
> May i know about strchr() here?

](*,)
Click here:  [http://www.google.com/search?q=%22C%22+strchr](http://www.google.com/search?q=%22C%22+strchr)


> **navaneethan said:**
> 
Actually what is the difference between flushing stdin and buffer overrun please?
Flushing stdin serves the purpose of removing all unwanted characters in the stream, up till the point where you reach a point where there are no more characters in the stream OR you have found a character that is of interest.

Buffer overrunning occurs when data of size N-bytes is written to a buffer whose reserved data space is *less than* N-bytes.

For example, the following will cause a buffer overrun:
```

char msg[4];

strcpy(msg, "Hello");

```

---

### Post by WitchCraft on 2010-08-12
> **dwhitney67 said:**
> ](*,)
Click here:  [http://www.google.com/search?q=%22C%22+strchr](http://www.google.com/search?q=%22C%22+strchr)


Why venture that far ?

```

man 2 strchr

```
is far more precise

---

### Post by dwhitney67 on 2010-08-12
> **WitchCraft said:**
> Why venture that far ?

It requires the person to open a terminal, AND your assuming the person is sitting at their Linux box AND that they have the man-pages package installed.  I know for sure that they have a web-browser open if they read my post, hence the simplicity of performing a Google search.

> **WitchCraft said:**
> 
is far more precise

Not necessarily; man-pages are available on the web.

---

### Post by trent.josephsen on 2010-08-12
Plus, I do believe it is `man 3 strchr` (or just `man strchr`)

---

### Post by WitchCraft on 2010-08-13
> **trent.josephsen said:**
> Plus, I do believe it is `man 3 strchr` (or just `man strchr`)

You're right, it should be 3. Depends on which Linux you use.
Buuuuuuuuuuuuuuuuuug....

---


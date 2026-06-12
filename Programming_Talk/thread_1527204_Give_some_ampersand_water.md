---
title: "Give some ampersand water"
date: 2010-07-09
forum: Programming Talk
---

### Post by navaneethan on 2010-07-09
> #include<stdio.h>
#include<conio.h>
void main()
{
	char s[]="nava";
	char s1[]="neethan";
	printf("%s is %c",&s[3],s1[3]);
		getch();
}

OUTPUT:
 a is t


In this above program I have couple of doubts

1.In the Printf statement whether &(ampersand) is necessary to print the s[3]

without ampersand i am not getting the output in visual studio c++ environment

2.If i put in the same printf statement **&s1[3]** instead of **s1[3]** means i am getting different output,i have given below



_modified program:_

> #include<stdio.h>
#include<conio.h>
void main()
{
	char s[]="nava";
	char s1[]="neethan";
	printf("%s is %c",&s[3],&s1[3]);
		getch();
}

_OUTPUT for modified one:_

a is s


here i am not clear plz explain

---

### Post by schauerlich on 2010-07-09
%s expects a pointer to a char, so yes, you need to include the ampersand for the first one. %c expects a character, so you shouldn't use it. The reason you get weird output in the modified program is that you're giving it a pointer, which is probably 4 or 8 bytes depending on your machine. It expects a char, so it takes the first byte of the pointer address and interprets it as a character, in this case the letter 's'. As with your other thread, use the -Wall option when compiling.

---

### Post by MadCow108 on 2010-07-09
first of all get rid of conio.h that header is obsolete even in windows.

%s expects a pointer to a null terminated array of bytes (characters) this is a c-style string

%c prints single characters, no need for null termination (as the compiler knows a (ascii) character is always 1 bytes wide)

s[3] dereferences the pointer with offset 3, result a character which is printed with %c

&s[3] is a pointer to this character so with %s you will not just get that one character but all until the null.

&s1[3] printed with %c is just wrong, in that case printf prints the value of the first byte (or last depending on endianness) of the 4 byte pointer (which is, interpreted as char, just garbage)

&s1[3] printed as %s not %c would output "than"

---


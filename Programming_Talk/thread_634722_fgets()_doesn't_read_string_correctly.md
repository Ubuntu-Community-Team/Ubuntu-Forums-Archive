---
title: "fgets() doesn't read string correctly"
date: 2007-12-08
forum: Programming Talk
---

### Post by dolgion1 on 2007-12-08
Hi people, i have a problem with the fgets() function, or rather actually scanf.


	scanf("%d",&n);
	fflush ( stdin );
	fgets(line,sizeof(line),stdin);

---

### Post by ray bot on 2007-12-08
If line is a char array, then shouldn't that last statement be fgets(line, strlen(line), stdin);

---

### Post by dolgion1 on 2007-12-08
no that doesnt solve it 
(btw sorry for the double post)

---

### Post by yabbadabbadont on 2007-12-08
Please provide all the relevant code, not just a snippet.

---

### Post by Compyx on 2007-12-08
LIke Yabbadabbadont said, post your code. My guess is you've declared line as a pointer to char, rather than a array of char.

With line as a pointer to char, sizeof(line) yields the size of the pointer, not the size of the memory pointed to by line. So on my 32-bit system fgets() would read at most 3 chars from stdin.

But without seeing the actual code in question, this is all just guess-work. Also loose the parentheses, the sizeof operator only needs those when applied to a type, when applied to an object you don't need them, they only obscure your code.

---

### Post by dolgion1 on 2007-12-08
okay here is some complete code that ive written to 
test out the problem with using scanf right before using fgets:

#include <stdio.h>

int main()
{
	char array[10];
	int number;
	scanf("%d",&number);
	fgets(array,sizeof(array),stdin);
	printf("%s\n",array);
	return 0;
}

ive tried using fflush(stdin); between scanf and fgets, but that somehow doesn't change anything. i use the gcc compiler in the ubuntu terminal. a friend of mine got that code working without problems on visual c++ in windows, but i dont believe that this could be solely a linux related problem

ill be thankful for any help

---

### Post by LaRoza on 2007-12-08
It does work, just don't put a newline before the string.

> 
laroza@laroza-desktop:~$ ./p.c
1 me
 me

laroza@laroza-desktop:~$ 


(I am using a C interpreter, but it will work the same when compiled)

---

### Post by Jessehk on 2007-12-08
You shouldn't be **fflush()**'ing an input stream -- the standard doesn't dictate what it will actually do.

You should also avoid using scanf to read the integer. Read in a string with **fgets** and then convert it to an integer using **sscanf** (the two s's are intentional). I can provide an example if it would help. 

All of those functions can fail. You need to be checking return values in order to check for errors.

C is difficult and there are lots of little quirks -- you need to be aware of them.

---

### Post by opipa on 2011-07-23
What I did is to put fgets() before scanf(), so that the last input of scanf (normally a NEWLINE) doesn't go to fgets. Just my speculation. I am working under gcc as well.

---

### Post by dwhitney67 on 2011-07-23
> **opipa said:**
> What I did is to put fgets() before scanf(), so that the last input of scanf (normally a NEWLINE) doesn't go to fgets. Just my speculation. I am working under gcc as well.

Read this:  [http://www.flamewarriors.com/warriorshtm/necromancer.htm](http://www.flamewarriors.com/warriorshtm/necromancer.htm)

---

### Post by slavik on 2011-07-23
we don't resurrect things here.

---


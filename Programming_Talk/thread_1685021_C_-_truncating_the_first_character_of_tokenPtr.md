---
title: "C - truncating the first character of tokenPtr"
date: 2011-02-10
forum: Programming Talk
---

### Post by laus_deo on 2011-02-10
So the title says most of what I need. I'm trying to split a sentence into parts, and then take off the first character of each token. I have the tokenPtr working right, I just can't figure out the rest.

---

### Post by Arndt on 2011-02-10
> **laus_deo said:**
> So the title says most of what I need. I'm trying to split a sentence into parts, and then take off the first character of each token. I have the tokenPtr working right, I just can't figure out the rest.

(Why does everybody start their sentences with "so" recently?)

Show us what you have so far, preferably a complete program.

---

### Post by laus_deo on 2011-02-10
Okay, I seem to be completely failing at this. But my over all goal is to have each token, and take off the first letter while appending it to the end of the string. Here's what I have been trying. 

```
#include <stdio.h>
#include <string.h>

int main()
{
	char input[100], first[2], string[100];
	char *tokenPtr, *temp;
 		
	printf("Please input a line of text\n"); 
	fgets(input, 100, stdin);

	tokenPtr = strtok(input, " "); 

	while(tokenPtr != NULL)
	{
		strncat(tokenPtr, tokenPtr , 1);

		printf("%s\n", tokenPtr);

		tokenPtr = strtok(NULL," ");
	
	}


	return 0; 
}


```

Here I'm still working on just getting that character appended to the end, but that doesn't seem to be working right either? Is there an easy way to change  my tokenPtr pointer to a string to make it easier to work with? I've tried statements such as

```

char string[100];
.
.
.
string = *tokenPtr;

```

but that just spits out errors.

---


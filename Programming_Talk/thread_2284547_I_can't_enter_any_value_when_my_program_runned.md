---
title: "I can't enter any value when my program runned"
date: 2015-06-30
forum: Programming Talk
---

### Post by NoWeDoR on 2015-06-30
I wrote a program in C/Linux but as in the picture I have an issue. How can I solve this? 
Thanks for helps.

The picture is:
[http://www.megafileupload.com/8U5g/Screenshot_from_2015-06-30_11_29_09%281%29.png](http://www.megafileupload.com/8U5g/Screenshot_from_2015-06-30_11_29_09%281%29.png)

My codes are:

```
#include <stdio.h>

int main()
{
	FILE *ptrFILE;
	int lineNumber = 1, choice, i, totalLineNumber;
	char c;

	if ((ptrFILE = fopen("Test.txt", "r")) == NULL)
	{
		printf("File couldn't open..\n\n");
	}
	
	printf("*-* Content of file *-*\n\n");
	c = fgetc(ptrFILE);
	while (!feof(ptrFILE))
	{
		printf("%c", c);
		if (c == '\n')
		{
			lineNumber++;
		}
		c = fgetc(ptrFILE);
	}
	printf("\n\nTotal line number : %d\n\n\n\n", lineNumber);
	totalLineNumber = lineNumber;

	printf("Express the line number which you want to display (Enter positive value for at\nthe beginning or vice versa) : ");
	scanf("%d", &choice);
	printf("\n");
	if (choice > 0)
	{
		lineNumber = 0;
		fseek(ptrFILE, 0L, SEEK_SET);
		c = fgetc(ptrFILE);
		while (!feof(ptrFILE))
		{
			printf("%c", c);
			if (c == '\n')
			{
				lineNumber++;
				if (lineNumber == choice)
				{
					break;
				}
			}
			c = fgetc(ptrFILE);
		}
		printf("\n\n\n");
	}
	else if (choice < 0)
	{
		lineNumber = 0;
		fseek(ptrFILE, 0L, SEEK_SET);
		c = fgetc(ptrFILE);
		while (!feof(ptrFILE))
		{
			if (c == '\n')
			{
				lineNumber++;
			}
			if (lineNumber>totalLineNumber + choice)
			{
				printf("%c", c);
			}
			c = getc(ptrFILE);
		}
		printf("\n\n\n");
	}

	fclose(ptrFILE);
	return 0;
}
```

---

### Post by trent.josephsen on 2015-06-30
Your link doesn't work for me. Please copy and paste the actual behavior or error message, both to help people who would help you and for the sake of other people who may find this thread by searching in the future.

---


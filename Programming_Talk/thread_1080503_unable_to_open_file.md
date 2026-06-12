---
title: "unable to open file"
date: 2009-02-25
forum: Programming Talk
---

### Post by swappo1 on 2009-02-25
I keep getting my error message when trying to open the file.
```
/*fileex.c*/
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	char ch;
	int i;
	FILE * fp;
		
	if((fp = fopen("test3.txt", "r")) == NULL);
		{
		printf("ERROR - cannot open file\n");
		exit (1);
		}
	
	fp = fopen("test3.txt", "r");
	while((ch = getc(fp)) != EOF);
		putchar(ch);
	
	return 0;
}
```
I gained permission by the following:
> $chmod 755 test3.txt

Any ideas what the problem is?

---

### Post by dwhitney67 on 2009-02-25
I cannot see it off-hand.  Are you sure the file exists?

Btw, you do not need to open the file twice.  Once it is open, you can continue to use the same file handle 'fp'.

-------

Edit:  I see the problem... it's the trailing semi-colon at the end of the if-statement.

---

### Post by swappo1 on 2009-02-25
Yeah, the semicolon at the end of the if and while statement.  I must be going blind.  Thanks.

---


---
title: "C Program that prints formated table"
date: 2009-10-24
forum: Programming Talk
---

### Post by matmatmat on 2009-10-24
I have this code:
```

#include <stdio.h>
#include "useful_functions.h"

int main(int argc, char *argv[]){
	//[row][column][chars]
	char table[300][20][200];
	//longest entry in column
	int max[20];
	int row,column,chars;
	row = column = chars = 0;
	int ocolumn;

	FILE *fp = fopen(*++argv, "r");
	char c;

	if (fp != NULL){
		while ((c=getc(fp)) != EOF){
			if (c == '\n'){
				row++;
				chars = 0;
				ocolumn = column;
				column = 0;
			}else if (c == ' '){
				int length = strlen(table[row][column]);
				if (length > max[column]){
					max[column] = length;
				}
				column++;
				chars = 0;
			}else{
				table[row][column][chars++] = c;
			}
		}
		int i,j;
		for (i=0;i < row; i++){
			for (j=0;j <= ocolumn;j++){
				printf("| %s ", table[i][j]);
				pad(max[j] - strlen(table[i][j]));
			}
			printf("|\n");
		}
	}else{
		printf("Could not open file\n");
	}
}

```
"useful_functions":
```

void pad(int numofspaces){
	int i;
	for (i=0;i<numofspaces;i++){
		printf(" ");
	}
}

```
when passed this file:
```

Name Score
1 1
2 3

```
it works, apart from it doesn't pad the second field.
When passed this file:
```

Name Age Score
Matthew 100 12

```
it prints out loads of spaces/newlines...

---

### Post by MadCow108 on 2009-10-24
learn to use a debugger to solve problems yourself!
you can't come to this forum for every single program which doesn't work on first try.

also you don't have to pad by hand, printf can already do that
[http://www.cplusplus.com/reference/clibrary/cstdio/printf/](http://www.cplusplus.com/reference/clibrary/cstdio/printf/)

---

### Post by Arndt on 2009-10-24
> **matmatmat said:**
> I have this code:
```

#include <stdio.h>
#include "useful_functions.h"

int main(int argc, char *argv[]){
	//[row][column][chars]
	char table[300][20][200];
	//longest entry in column
	int max[20];
	int row,column,chars;
	row = column = chars = 0;
	int ocolumn;

	FILE *fp = fopen(*++argv, "r");
	char c;

	if (fp != NULL){
		while ((c=getc(fp)) != EOF){


```
it prints out loads of spaces/newlines...

I'll point out one thing which won't help you at all right now: as far as I know, C allows 'char' to be either signed or unsigned - it's up to the implementation. If unsigned, your code won't work, because then c can't be equal to -1. If you look at the documentation for getc, you will see that it returns an int, so that's what the type of c should be.

---


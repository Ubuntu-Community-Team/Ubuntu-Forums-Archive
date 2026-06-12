---
title: "entab.c - my c program acting up"
date: 2009-06-07
forum: Programming Talk
---

### Post by JordyD on 2009-06-07
So I bought this book called "The C Programming Language". I devoted myself to doing every single exercise in the book. I know it will take ages, but I'm going to do it. So I'm stuck on this exercise called entab.c. This is the description:> Write a program entab that replaces strings of blanks by the minimum number of tabs and blanks to achieve the same spacing. Use the same tab stops as for detab*. When either a tab or a single blank would suffice to reach a tab stop, which should be given preference?* I used 8

I wrote the program, it *almost* works. It replaces the spaces with tabs when possible and spaces when not. My only problem is that it randomly steals the first letter off the beginning of a word and replaces it with a space.

This is my code:[PHP]#include		<stdio.h>
#define	TAB    	8
#define	MAXLINE	1000
#define	MAXOUT	1000000
#define	YES     1
#define	NO      0

int getline(char s[], int lim);
void append(char to[], char with);

/* main: replace strings of blanks in input with proper amount of tabs and spaces */
main() {
	char line[MAXLINE];		/* current input line */
	char output[MAXOUT];	/* modified output */
	int len;				/* length of current line */
	int pos;				/* position in current line */
	int spaces = 0;			/* number of consecutive spaces */
    int tab;				/* whether or not we are at a tabstop */
	int i;					/* meaningless counter variable */

	output[0] = '\0';

	while ((len = getline(line, MAXLINE)) > 0) {
		for (pos = 0; pos < len; ++pos) {
			if (pos % TAB == 0)
				tab = YES;
			else
				tab = NO;
			if (line[pos] == ' ' && tab == NO)
				++spaces;
			else if (tab == YES && spaces > 0) {
				append(output, '\t');
				spaces = 1;
			}
			else {
				for (i = 0; i < spaces; ++i)
					append(output, ' ');
				append(output, line[pos]);
				spaces = 0;
			}
		}
	}
	printf("%s", output);
	return 0;
}

/* getline: read a line into s, return length */
int getline(char s[], int lim) {
	int c;	/* current character */
	int i;	/* current position in string */
	
	for (i=0; i<lim-1 && (c=getchar())!=EOF && c!='\n'; ++i)
		s[i] = c;
	if (c == '\n') {
		s[i] = c;
		++i;
	}
	s[i] = '\0';

	return i;
}

/* append: append 'from' to 'to' */
void append(char to[], char with) {
	int end = 0;

	while (to[end] != '\0')
		++end;
	to[end] = with;
	to[end+1] = '\0';
}
[/PHP]

Notice I created my own functions for append and getline. I'm sure there is a library somewhere that provides these, but the book hasn't informed me, so I don't use them.

Please help me, I've been stuck on this forever.

Thanks,
Jordy

---

### Post by tuggy on 2009-06-08
Hi
very simple, in your else if condition you should still test if the character read is a whitespace or not, and only append the '\t' character if it is

```
else if (line[pos] == ' ' && tab == YES && spaces > 0) {

```

---

### Post by JordyD on 2009-06-08
> **tuggy said:**
> Hi
very simple, in your else if condition you should still test if the character read is a whitespace or not, and only append the '\t' character if it is

```
else if (line[pos] == ' ' && tab == YES && spaces > 0) {

```

Oh! I see now! That makes so much sense. Thanks. :D

---


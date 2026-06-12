---
title: "&quot;status_access_violation&quot; help me figure out why? (C Programming+cygwin+gcc+eclipse)"
date: 2008-04-03
forum: Programming Talk
---

### Post by Kougaiji on 2008-04-03
Hey all, I'm somewhat new to C (taking my first, and probably only, c programming class in my electrical engineering major requirement) and I just completed a programming assignment. The assignment was to create a crypto-analyzer, or something to encrypt/decrypt a file into an output file using another file as the key.

I've had issues in the past, where something I compile in GCC/Eclipse doesn't compile on my TA's VisualStudio program, and I'm wondering if this may be such a problem or if there's something wrong with my program (probably has to do with array addressing). I've looked through it and cannot figure what is wrong.

Hope someone here can help...
it's rather short, it shouldn't take too long to find the issue.

the main program main.c
```
#include <time.h>
#include <stdio.h>
#include "decipher.h"
int main() {
	clock_t start, end;
	double runTime;
	start = clock();
	
	FILE *ct;
	FILE *en;
	FILE *ky;
	FILE *opf;
	ct = fopen("cleartext.txt", "r");
	en = fopen("encrypted.txt", "r");
	ky = fopen("key.txt", "r");
	
	char question = '0';
	while (question == '0') {
		char choice = '3';
		char output[25];
		
		printf("\nRunning Cryptoanalyzer ver. 0.1.0");
		printf("\nPlease enter the operation option # you wish to perform");
		printf("\n1. Encipher\n2. Decipher\n3. Exit");
		scanf("%c", &choice);
		getchar();
		
		printf("\nPlease enter the output file name:");
		scanf("%s", output);
		getchar();

		opf = fopen(output, "a+");
		
		switch (choice) {
		case '1': encrypt(ct, ky, opf); break;
		case '2': decrypt(en, ky, opf); break;
		default: question = -1;
		}
	}
	
	end = clock();
	runTime = ((end - start) / (double) CLOCKS_PER_SEC );
	printf("The runtime of my program is %g seconds", runTime);
	getchar();
	fclose(ct);
	fclose(en);
	fclose(ky);
	fclose(opf);
	return 0;
}

```

the includes, if necessary, but I really...err somewhat doubt the issue is here.

decipher.c
```
#include <stdio.h>

void encrypt (FILE *cleartext, FILE *key, FILE *out) {
	char x;
	char y;
	char k[26];
	fgets(k, sizeof(k), key);
	int letNum;
	
	while ((x = getc(cleartext)) != EOF) {
		if ((x >= 'A') && (x <= 'Z')) {
			letNum = x - 65;
			y = k[letNum];
			putc(y, out);
		}
		else if ((x >= 'a') && (x <= 'z')) {
			letNum = x - 97;
			y = k[letNum];
			putc(y, out);
		}
		else
			putc(x, out);
	}
	rewind(cleartext);
	rewind(out);
	rewind(key);
}


void decrypt (FILE *encrypted, FILE *key, FILE *out) {
	char x;
	char y;
	char k[26];
	fgets(k, sizeof(k), key);
	int n;
	
	while ((x = getc(encrypted)) != EOF) {
		if ((x >= 'A') && (x <= 'Z')) {
			for (n = 0; n <= 25; n++) {
				if (x == k[n]) {
					y = n + 65;
				}
			}
			putc(y, out);
		}
		else if ((x >= 'a') && (x <= 'z')) {
			for (n = 0; n <= 25; n++) {
				if (x == k[n]) {
					y = n + 97;
				}
			}
			putc(y, out);
		}
		else
			putc(x, out);
	}
	rewind(encrypted);
	rewind(out);
	rewind(key);
}

```

the error looks something like this:
[IMG]http://img257.imageshack.us/img257/4499/20560363jb6.jpg[/IMG]

This isn't the first time I've run across something like this, so any kind of explanation would be helpful.

Thanks a lot!

By the way: I'm running this on a 64 bit XP machine (if that has any relevance)

EDIT: Yes, these files exist and reside within the same folder, this program has no issues compiling...

---


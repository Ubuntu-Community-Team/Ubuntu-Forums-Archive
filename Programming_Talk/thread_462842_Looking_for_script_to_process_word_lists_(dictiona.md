---
title: "Looking for script to process word lists (dictionaries if you like)"
date: 2007-06-03
forum: Programming Talk
---

### Post by robenroute on 2007-06-03
Hi there,

I would like to accomplish the following: a have a list of words (approx. 20,000 words), but the words are of different length. Each line in the file contains one word and one word only and is terminated by a CR/LF. The are words of two letters (e.g. "in", "he", etc.), three, four, etc. How would I create a new file of only all the 3- and 4-letter words? Or a list of only 6-letter words?

Thanks very much in advance!

---

### Post by jyba on 2007-06-03
```
grep '^...$' /usr/share/dict/words >three_letter_words.txt
grep '^....$' /usr/share/dict/words >four_letter_words.txt
grep '^.....$' /usr/share/dict/words >five_letter_words.txt
grep '^......$' /usr/share/dict/words >six_letter_words.txt
```

---

### Post by bashologist on 2007-06-03
Instead of opening the file repeatedly you could do it all at once with python.
```
#!/usr/bin/env python
reading_file = open("dictionary.txt", "r")
file_lines = reading_file.readlines()
reading_file.close()
dictionary = {}
for line in file_lines:
	line_length = len(line) - 1
	if line_length in dictionary:
		dictionary[line_length].append(line)
	else:
		dictionary[line_length] = [line]
for key in dictionary.keys():
	filename = "%schars.txt" % key
	writing_file = open(filename, "w")
	writing_file.writelines(dictionary[key])
	writing_file.close()
```

---

### Post by robenroute on 2007-06-03
Thanks for the feedback and suggestions. The Python script looks very flexible. It's been a few years since my last line of code (must have been Forth or Smalltalk, can't remember, really). It might be worth checking this Python stuff out; I've been hearing good things about Python....

Thanks again!

---

### Post by ghostdog74 on 2007-06-03
learn more of your shell and what it can offer you. here's one in awk
```

awk  'length==3{print > "three-letter.txt"}
      length==4{print > "four-letter.txt"}' "file"

```

---

### Post by ruy_lopez on 2007-06-03
If you are masochistic, or if you are parsing large dictionaries, a simple c prog might do it quicker. 

The code below takes arguments for input file, outputfile, and an optional line length. So if you were interested in lines with 5 and 7 chars, you would use it like this:

```
./a.out dictionary.txt output 5 7
```

If you don't supply line lengths, it'll create files for every line length it finds.

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <errno.h>

int fileops(char *, ssize_t, char *);

int main(int argc, char *argv[])
{
	FILE *fp;
	char *line = NULL;
	size_t len = 0;
	ssize_t n;
	int i, found = 1;

	if (argc < 3) {
		fprintf(stderr, 
			"usage: %s <in file> <out fname> [line len] ...\n", 
								argv[0]);
		exit(1);
	}
	if ((fp = fopen(argv[1], "r")) == NULL) {
		fprintf(stderr, "fopen error: %s\n", strerror(errno));
		exit(1);
	}

	while ((n = getline(&line, &len, fp)) != -1) {

		if (argc > 3) {
			found = 0;
			for (i = 3; i < argc; i++) {
				if (atoi(argv[i]) == n - 1) {
					found = 1;
					break;
				}
				else
					continue;
			}
		}

		if (found == 0) {
			continue;
			found = 0;
		}

		if (fileops(line, n, argv[2]) != 0) {
			if (line)
				free(line);
			fclose(fp);
			exit(1);
		}	
		printf("%s%d << %s", argv[2], n-1, line);
	}

	if (line)
		free(line);
	fclose(fp);
	return 0;
}

int fileops(char *lineptr, ssize_t size, char *fname)
{
	char filename[40];
	FILE *ofp;

	if (strlen(fname) > 20) {
		fprintf(stderr, "out fname must be < 20\n");
		return(1);
	}

	if (snprintf(filename, sizeof(filename), "%s%d", fname, size - 1) < 0) {
		fprintf(stderr, "snprintf error: %s\n", strerror(errno));
		return(1);
	}
	
	if ((ofp = fopen(filename, "a+")) == NULL) {
		fprintf(stderr, "fopen error: %s\n", strerror(errno));
		return(1);
	}

	if (fwrite(lineptr, sizeof(char), size, ofp) < 0) {
		fprintf(stderr, "fwrite error: %s\n", strerror(errno));
		fclose(ofp);
		return(1);
	}

	fclose(ofp);
	return(0);
}

```

---

### Post by robenroute on 2007-06-08
Gee, I'm overwhelmed! Thanks again for all the feedback. It's interesting there are so many different solutions (implementation-wise, as in: C, Python, awk, etc.)

Thanks again!

(I really pity those poor bstrds stuck with Wwww.., Wwww...; dammit, I can't even get that word over my lips ;-))

---

### Post by pmasiar on 2007-06-08
nvm

---


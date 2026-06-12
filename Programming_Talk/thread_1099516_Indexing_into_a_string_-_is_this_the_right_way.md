---
title: "Indexing into a string - is this the right way?"
date: 2009-03-18
forum: Programming Talk
---

### Post by Krupski on 2009-03-18
Hi all,

I need to read a text file line by line, find a particular line (by using strstr() to locate a keyword), then index into the line to print out a part of it.

What I need to know is (see below), is this method of "indexing" into the string the proper way to do it? If not, could you tell me a better way?

Here's a demo of what I mean:

```

#include <stdio.h>
#include <string.h>

int main(void)
{
    char buf[100];
    char *p1;

    strcpy(buf, "this is a test string\n");
    p1 = buf;

    p1 = buf + 0;
    fprintf(stdout, "%s", p1);

    p1 = buf + 5;
    fprintf(stdout, "%s", p1);

    p1 = buf + 10;
    fprintf(stdout, "%s", p1);

    p1 = buf + 15;
    fprintf(stdout, "%s", p1);

    return 0;
}

```

When run, it returns:

```

root@michael:~/c-progs# ./test
this is a test string
is a test string
test string
string

```

...which is what I want / expect.

Am I doing this the right way?

Thanks!

-- Roger

---

### Post by sujoy on 2009-03-18
yes it works sure, but that p1 pointer isn't really needed.

```
#include <stdio.h>
#include <string.h>

int main(void)
{
    char buf[100];

    strcpy(buf, "this is a test string\n");

    fprintf(stdout, "%s", buf);
    fprintf(stdout, "%s", &buf[5]);
    fprintf(stdout, "%s", &buf[10]);
    fprintf(stdout, "%s", &buf[15]);

    return 0;
}
```

however do some bound checking to make sure you are not accessing beyond the array length.

---

### Post by Krupski on 2009-03-18
> **sujoy said:**
> yes it works sure, but that p1 pointer isn't really needed.

```
#include <stdio.h>
#include <string.h>

int main(void)
{
    char buf[100];

    strcpy(buf, "this is a test string\n");

    fprintf(stdout, "%s", buf);
    fprintf(stdout, "%s", &buf[5]);
    fprintf(stdout, "%s", &buf[10]);
    fprintf(stdout, "%s", &buf[15]);

    return 0;
}
```

however do some bound checking to make sure you are not accessing beyond the array length.

Figured there would be a simpler way. Thank you!

-- Roger

---

### Post by dwhitney67 on 2009-03-18
> **sujoy said:**
> yes it works sure, but that p1 pointer isn't really needed.

```
#include <stdio.h>
#include <string.h>

int main(void)
{
    char buf[100];

    strcpy(buf, "this is a test string\n");

    fprintf(stdout, "%s", buf);
    fprintf(stdout, "%s", &buf[5]);
    fprintf(stdout, "%s", &buf[10]);
    fprintf(stdout, "%s", &buf[15]);

    return 0;
}
```

however do some bound checking to make sure you are not accessing beyond the array length.

Or something like:
```

...
    fprintf(stdout, "%s", buf);
    fprintf(stdout, "%s", buf + 5);
    fprintf(stdout, "%s", buf + 10);
    fprintf(stdout, "%s", buf + 15);
...

```

---

### Post by jfbilodeau on 2009-03-18
I'm not sure I fully understand your question, but what about using strtok?

---

### Post by Krupski on 2009-03-18
> **jfbilodeau said:**
> I'm not sure I fully understand your question, but what about using strtok?

Well, I already got the answer (thanks!), but the reason I'm doing this is to extract CPU speed out of "/proc/cpuinfo".

I open the file, read a line until I find "processor", then index into that line to get the number using atoi(). Then I read lines until I find "cpu MHz". I index into that line and get the CPU frequency using atof() (I use atof because I convert the frequency to GHz and don't want to lose resolution with integer divides).

Here's the whole program in it's glorious uselessness! :)

```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int readln(FILE*, char*);

int main(void)
{
	FILE *fp1;
	char buffer[BUFSIZ];
	const char *fname[1] = { "/proc/cpuinfo" };
	const char *hertz[9] = { "", "k", "M", "G", "T", "P", "E", "Z", "Y" };
	int cpu, mult;
	double freq;

	fp1 = fopen(*fname, "r");

	if(fp1 == NULL) {
		fprintf(stderr, "error: can't open %s\n", *fname);
		return 1;
	}

	while( ! feof(fp1)) {

		readln(fp1, buffer);

		if(strstr(buffer, "processor") != NULL) {
			cpu = atoi(buffer + 11);
		}

		if(strstr(buffer, "cpu MHz") != NULL) {
			freq = atof(buffer + 10) * 1000000;

			mult = 0;

			while(freq >= 1000) {
				freq /= 1000; mult++;
			}

			fprintf(stdout, "Core %d, %.2f %sHz.\n", cpu, freq, hertz[mult]);
		}
	}

	fclose(fp1);
	return 0;
}


int readln(FILE *fp, char *str)
{
	char buf[BUFSIZ];
	int len;

	buf[0] = 0; fgets(buf, BUFSIZ, fp);

	len = strlen(buf);

	while(len >= 0) {
		if(	buf[len] == 32 ||
			buf[len] == 13 ||
			buf[len] == 10 ||
			buf[len] == 0) {
				buf[len] = 0;
				len--;
		} else { break; }
	}

	len++;
	buf[len] = 0;
	strcpy(str, buf);

	return 0;
}

```


Now..... this program contains a lot of silly, worthless pieces... but they are part of my continuing quest to figure out how C works... these programs are "vehicles" for testing my ideas... trying to see if what I assume to be true is, in fact true.

For example, the part that prints "M" for megahertz or "G" for gigahertz is just a test to see how to select pieces of a static string and use that piece. Obviously, being able to print CPU speed in "hertz" or "exahertz" is rather useless... 

Confused? Me too!  :)

-- Roger

---


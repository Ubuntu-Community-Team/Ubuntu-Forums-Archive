---
title: "C string parse, unexpected termination of loop."
date: 2012-05-30
forum: Programming Talk
---

### Post by Grenage on 2012-05-30
I'm new to C, and programming in general, so please bear that in mind.

I have a function which takes a terminated string, and loops though the characters, removing quotations and substituting non-delimiting commas.  It writes each desired character to a second string, and *should* ignore the quotation marks; that isn't happening.  If I write the quotation to the new string, all works as expected, but if I skip the write with a continue statement, it aborts the rest of the loop iterations:

```
void substring(char text[256])
{
	int i=0;
	int qc = 0;
	char parsed[256];

	bzero(parsed,256);

	for (i = 0; text[i] != '\0';++i) {
		if (text[i] == '\"') {
			parsed[i] = text[i];  <-- What I want to remove
			++qc;
			continue;
		}
		if (text[i] == ',') {
			if ((qc % 2) != 0) {
				parsed[i] = '';
				continue;
			}
		}
		parsed[i] = text[i];
	}
	printf("%s",parsed);
}
```

I'm not really after a solution, just an explanation as to *why* it's happening.  Forgive the coding...

---

### Post by trent.josephsen on 2012-05-30
I'm a little confused by what you want to do, but you do realize that after the first time you encounter a quotation mark, the index you want to copy to will be different from the index you're copying from, right?

i.e. when you encounter the first " in 'Hello, "world"', without the assignment you want to remove, you'll skip right over index 7 in the destination array, which (since you zeroed the entire array beforehand) remains 0. When you go to print it out, printf sees the zero and assumes it's the end of the string.

You need two indexes (or two pointers) for the two strings, because they don't have the same length.

---

### Post by Grenage on 2012-05-30
Urgh of course, why did I not spot that! Thank you for pointing it out; it's been such an eye-opener going from VBA dabbling to C.

---


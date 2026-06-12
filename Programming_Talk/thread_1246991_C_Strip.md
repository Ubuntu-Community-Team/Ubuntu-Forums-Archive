---
title: "C Strip"
date: 2009-08-22
forum: Programming Talk
---

### Post by matmatmat on 2009-08-22
I have this code that strips '-' from a string:
```

void strip(char *porig, char *pnew)
{
  char *p, *p1;
  char buf[2];
  register int i, j;

  memset(buf, 0, sizeof(buf));

  p = porig, p1 = pnew;
  for(i = 0, j = 0; p[i] != '\0'; ) {
	if (p[i] == '\n') break;

	if (p[i] == '-') {
	   i++;
	   continue;
	}

        p1[j] = p[i];
	i++, j++;
  }

}

```
& this code that calls it:
```

	int top = 0;
	int bot = 0;
	char test[2];
	strip("1-3", test);
	printf("%s\n", test);
	bot = atoi(&test[0]);
	top = atoi(&test[1]);
	printf("%i\n%i\n", bot, top);

```
which prints:
```

13
13
3

```
when I expected it to print:
```

13
1
3

```
(I'm guessing the &test[0] is passing the whole array?)
What should I do?

---

### Post by napsy on 2009-08-22
instead of 
```

bot = atoi(&test[0]);
top = atoi(&test[1]);

```

try

```

bot = test[0] - '0';
top = test[1] - '0';

```

---

### Post by MadCow108 on 2009-08-22
your test is to small and it's missing the null termination.
add a:
p1[j]='\0';
and make it to size 3 (for this problem)
and yes atoi scans the whole stirng until it finds a null termination.
so you can either copy the value to a new string or use this:
bot = test[0]-'0';

or you could use strtok to tokenize your string instead of implementing something similar yourself
```

char str[] ="1-3";
char * pch;
pch = strtok (str," -");
while (pch != NULL)
{
	printf ("%s\n",pch);
	pch = strtok (NULL, " -");
}

```

---

### Post by matmatmat on 2009-08-22
Thanks

---


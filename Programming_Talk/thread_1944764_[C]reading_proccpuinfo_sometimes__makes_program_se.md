---
title: "[C]reading /proc/cpuinfo sometimes  makes program segfault"
date: 2012-03-21
forum: Programming Talk
---

### Post by Jordanwb on 2012-03-21
This is my program:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main (void)
{
	FILE *f = fopen ("/proc/cpuinfo", "r");
	
	char *a = malloc (256);
	char *b = malloc (128);
	char *c = malloc (128);
	
	while (!feof (f))
	{
		fgets (a, 512, f);
		
		if (strlen (a) == 1) continue;
		
		sscanf (a, "%[^\t:] : %[^\t\n]", b, c);
		
		printf ("%s = %s\n", b, c);
	}
	
	fclose (f);
}

```

This is my desktop machine's cpuinfo: [http://pastebin.com/0nk6WfHN](http://pastebin.com/0nk6WfHN)

This is my NAS's cpuinfo: [http://pastebin.com/ct82bBtU](http://pastebin.com/ct82bBtU)

If I run my program on the NAS, it runs fine although the Serial line is printed twice for some reason. If I run this on my desktop it handles everything okay but prints "power management = 36 bits physical, 48 bits virtual" twice then segfaults and I don't know why.

Thanks in advance.

---

### Post by xbxb on 2012-03-21
Open /proc/cpuinfo and see if there is any information after

power management: 

If there is none, that would account for the segfault.
You need to code for that possibility.

---

### Post by Jordanwb on 2012-03-21
> **xbxb said:**
> Open /proc/cpuinfo and see if there is any information after

power management: 

If there is none, that would account for the segfault.
You need to code for that possibility.

the pastebins show the contents of /proc/cpuinfo on my desktop machine and my NAS. On my desktop there's nothing after "power management" which I know is causing the segfault but I don't know what to do about it.

---

### Post by xbxb on 2012-03-21
Don't print strings that never existed.

---

### Post by Bachstelze on 2012-03-22
```
char *a = malloc (256);
[...]
fgets (a, 512, f);
```

---

### Post by Jordanwb on 2012-03-22
> **Bachstelze said:**
> ```
char *a = malloc (256);
[...]
fgets (a, 512, f);
```

Oh derp. I didn't notice that thanks.

---


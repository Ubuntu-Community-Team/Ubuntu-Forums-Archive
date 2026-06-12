---
title: "Segmation Fault: Reversing a string"
date: 2009-10-15
forum: Programming Talk
---

### Post by matmatmat on 2009-10-15
I have this code:
```

#include "functions.h" 
void copy(char to[], char from[]){
	int i = 0;
	while ((to[i] = from[i]) != '\0'){
		++i;
	}
}

void reverse(char string[], int len){
	char new[len];
	int i = 0;
	len--;
	while ((new[i] = string[len]) != '\0'){
		i++;
		len--;
	}
	new[i] = '\0';
	copy(string, new);
}

```
when reverse is called with:
```

char string[] = "hello";
reverse(string, 5);

```
it runs and gives this output:
```

olleh&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;?&#65533;
                  &#65533;&#65533;&#65533;H&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1079;&#65533;?&#65533;|&#65533;
Segmentation fault

```

---

### Post by dwhitney67 on 2009-10-15
Should it not be:
```

char new[len + 1];   // you need the extra space for the null character
...

```

---

### Post by matmatmat on 2009-10-15
This:
```

void reverse(char string[], int len){
	char new[len + 1];
	int i = 0;
	len--;
	while ((new[i] = string[len]) != '\0'){
		i++;
		len--;
	}
	new[i] = '\0';
	copy(string, new);
}

```
still doesn't work, if you remove the:
```

len--;

```
it prints nothing

---

### Post by MadCow108 on 2009-10-15
the len is correct if you pass the correct string length (which he doesn't in the example, "hello" has length 6 not 5)

your logic is wrong:
```

while ((new[i] = string[len]) != '\0'){

```
string only has a null terminator at the end not at the start, so under correct length the while will never execute
use counting variables

---

### Post by matmatmat on 2009-10-15
Thanks, but it still doesn't work:
```

void reverse(char string[], int len){
	char new[len];
	int i = 0;
	int j;
	for (j = 0; j < len; j++){
		new[i] = string[len]; 
		i++;
		len--;
	}
	new[i] = '\0';
	copy(string, new);
}

```
which prints out 'P'

---

### Post by MadCow108 on 2009-10-15
your reducing your boundary variable in the for so the loop does not run the correct amount of iterations
you also have to avoid copying the null into the first byte of the new string or it won't print

---

### Post by Can+~ on 2009-10-15
The algorithm is far more simple:

```
for each i in 1 to n:
    reversed[i] = str[n-i]
```

---

### Post by MadCow108 on 2009-10-15
how's that simpler? (because its the same % an extra variable)
C just has no for each

---

### Post by matmatmat on 2009-10-15
Thanks

---

### Post by Can+~ on 2009-10-15
> **MadCow108 said:**
> how's that simpler? (because its the same % an extra variable)
C just has no for each

pseudo code

> **"matmatmat"]
[PHP]void reverse(char string[], int len){
	char new[len] said:**
>  = string[len]; 
		i++;
		len--;
	}
	new[i] = '\0';
	copy(string, new);
}[/PHP]


And what I meant by simpler, is that he doesn't need 3 variables, when you only need length and an iterator.

---

### Post by nvteighen on 2009-10-15
There are several issues there regarding logic and allocation. First of all, your loops are misbehaiving in both cases... In the first, your condition is wrong; in the second, it's never met because of how you wrote the first.

Then, there's an allocation issue and a confusion about how long the string vs. how long the array is... plus the issue that you need dynamic allocation if you want that approach. What I haven't been able to isolate yet is the possible memory corruption that affects len to become negative values... (which is also part of this massive segfault).

FYI, there are standard strcpy() and strncpy() which already implement copy()...

---

### Post by dwhitney67 on 2009-10-15
From my sandbox of useless code...
```

void reverse(char string[])
{
  const size_t len  = strlen(string);
  const size_t half = len / 2;

  for (size_t i = 0; i < half; ++i)
  {
    char tmp = string[i];
    string[i] = string[len-(i+1)];
    string[len-(i+1)] = tmp;
  }
}

```

---

### Post by Arndt on 2009-10-16
> **Can+~ said:**
> pseudo code



And what I meant by simpler, is that he doesn't need 3 variables, when you only need length and an iterator.

It's simpler, but it's a little too simple. You're overwriting the beginning of the string with new stuff before you have stored the old content where it should be at the end of the string.

And there's a fencepost error: you start from 1, so the string indices go from 1 to n, but you fetch them from n-i, that is from n-1 to 0.

---

### Post by SouthOfHell on 2009-10-16
> **dwhitney67 said:**
> From my sandbox of useless code...
```

void reverse(char string[])
{
  const size_t len  = strlen(string);
  const size_t half = len / 2;

  for (size_t i = 0; i < half; ++i)
  {
    char tmp = string[i];
    string[i] = string[len-(i+1)];
    string[len-(i+1)] = tmp;
  }
}

```

I'm a beginner C programmer myself, I've looked over this code and I'm dying to know: why did you use size_t type to hold the length of the string parameter? (not that I'm questioning your logic or anything btw, I'm just curious)

---

### Post by MadCow108 on 2009-10-16
because strlen returns size_t
[http://www.cplusplus.com/reference/clibrary/cstring/strlen/](http://www.cplusplus.com/reference/clibrary/cstring/strlen/)

size_t is just a typedef to a unsigned integer type, so you could also use unsigned int.

---

### Post by matmatmat on 2009-10-16
> **nvteighen said:**
> T
FYI, there are standard strcpy() and strncpy() which already implement copy()...

I know :)

---


---
title: "array of strings in c"
date: 2007-03-01
forum: Programming Talk
---

### Post by jordanmthomas on 2007-03-01
I have a question that should be easy to answer, but I have been trying to fix it for a while now with no success.  I have an assignment to read lines from a file and then sort them.  Sounds simple enough, but I am having trouble.

I am making an array of pointers to characters which are all pointing to nothing:
[PHP]char** array;
array = (char **)calloc(numLines, sizeof (char *));

for(i = 0; i < numLines; i++)
{
	array[i] = (char*)malloc(sizeof(char*));
}[/PHP]

It is my understanding that I can point these empty character pointers to a string and I'd be set.
Say I have a char pointer named addMe pointing to "jordan"
I have printed this out successfully so I am certain that it what it points to.

Why is it that this does not work? :
[PHP]array[0] = *addMe;[/PHP]
Doesn't this make the char* in array[0] point to the contents of addMe?
It seems to halfway work, but it only gets the first character from addMe; i.e.
[PHP]printf("%s\n",*array[0]);[/PHP]
would give "j" and not "jordan"

I am sure it's something simple I am missing but I can't figure it out.

---

### Post by jordanmthomas on 2007-03-01
Funny how writing your question basically gives you your own answer.  :) 

Now I am adding it like this:
[PHP]array[i] = addMe;[/PHP]
and printing like this:
[PHP]printf("%s",array[i]);[/PHP]

Thanks for any interest you might have had.

---

### Post by slavik on 2007-03-01
(char *) is 4 bytes since it is a pointer to a character ...

you want something along the lines of:
```

char *lines[NUMLINES];
char buffer[81];
while (fgets(buffer,80,stdin) != NULL) {
[indent]buffer[strlen(buffer)] = '\0'; /* change newline char to NULL char */
lines[iterator] = (char *)malloc(strlen(buffer));
strcpy(lines[iterator],buffer);
iterator++;[/indent]
}
/* sort the array */
/* print the array */
puts(lines[iterator]); /* should work fine */

```

note, code is untested :P

for comparison, perl code :)

```

#!/usr/bin/perl

while (<>) { push @_, $_; }
print sort @_;

```

---

### Post by hod139 on 2007-03-01
> **slavik said:**
> (char *) is 4 bytes since it is a pointer to a character ...

you want something along the lines of:
```

char *lines[NUMLINES];
char buffer[81];
while (fgets(buffer,80,stdin) != NULL) {[INDENT]buffer[strlen(buffer)] = '\0'; /* change newline char to NULL char */
lines[iterator] = (char *)malloc(strlen(buffer));
** strcpy(lines[iterator],buffer);**
iterator++;[/INDENT]}[code]
Please don't ever use strcpy (even if you are using it correctly)!!  It never checks the length of the input string and is a very commonly used vector for buffer overflows.  You should get into the practice of always using strncpy, followed by setting the newline = '\0'.
[code]
strncpy(lines[iterator], buffer, strlen(buffer)); // only copy strlen(buffer) bytes
lines[iterator][strlen(buffer)-1] = '\0'; // Just to be extra safe

```

---


---
title: "A little help with C"
date: 2007-10-20
forum: Programming Talk
---

### Post by DFord425 on 2007-10-20
Can someone shed some light on this:
```
Segmentation fault (core dumped)

```
I get this error when i try to run a program but i have no idea what it means.

---

### Post by slavik on 2007-10-20
a segfault is usually when you try to access a memory location you do not have access to access.

If this is your code, you can post it and we can try to help you out. If it's someone else's code, you should submit a bug report.

---

### Post by DFord425 on 2007-10-20
Here is my code:
```
main(int ac, char *av[])
{
	char *sw;
	char *file;
	printf("%d\n", ac);
	if(ac == 3)
	{
		strcpy(sw, av[1]);
		strcpy(file, av[2]);
	}
	else
	{
		strcpy(file, av[1]);
		strcpy(sw, "00");
	}
	printf("%s\n", file);		
	do_touch(file, sw);
}
```
It reads in arguments for a command and checks to see if there are any switchs such as:
[CODE./touch1 test.c
Segmentation fault (core dumped)
[/CODE]
It doesnt get to the printf statement after the else{}.  The first printf is just to test something, its not important.

---

### Post by AlexenderReez on 2007-10-20
you didn't define reference to do_touch ....check again...

---

### Post by aks44 on 2007-10-20
Neither your **sw** nor **file** pointers are initialized. They may point to anywhere.


Use malloc(strlen(...)+1) before strcpy (and free later on when you don't need the strings anymore):

```
int main(int argc, char* argv[])
{
  int len = strlen(argv[1]);
  char* sw = malloc(len+1); // +1 to fit the null terminator
  strcpy(sw, argv[1]);
  // ...
  free(sw);
  return EXIT_SUCCESS;
}
```

BTW, IIRC functions *implicitely* returning an int are deprecated.


You may also want to find a decent C tutorial to get you started on the basics.

---


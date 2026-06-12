---
title: "Why get these output"
date: 2012-11-19
forum: Programming Talk
---

### Post by pellyhawk on 2012-11-19
Here is my code block

```
	char * passwd = "123456";
        printf("passwd = %d\n",passwd);
	printf("passwd = %s\n",passwd);
	for (int k = 0; k < 19; k++)
	{
	    printf("%c", passwd);
	}
```

and got these results, very weird.

```
passwd = 3068087
passwd = 123456
&#36137;&#36137;&#36137;&#36137;&#36137;&#36137;&#36137;&#36137;&#36137;
```

Any help is welcome. Thanks.

---

### Post by trent.josephsen on 2012-11-19
You are telling printf to display values of different types, but you are not in fact converting between those types.

```
	char * passwd = "123456";
        printf("passwd = %d\n",passwd);
```
printf interprets the second argument, which is a pointer-to-char, as an int and displays it as such. The result is gibberish -- might not even correspond to an actual memory location, what with alignment and other concerns. If you ever do want to display the value of a pointer, use %p and cast it to (void *), like `printf("%p", (void *)passwd);`
```
	printf("passwd = %s\n",passwd);
```
This acts as you would expect.

```
	for (int k = 0; k < 19; k++)
	{
	    printf("%c", passwd);
	}
```
Here you're again re-interpreting a pointer-to-char, but this time as a char. You probably wanted

```
for (int k = 0; k < 6; k++) {
    printf("%c", passwd[k]);
}
```
Notice I also changed 19 to 6 so that you won't read off the end of the 6-character string. In the general case, you could just keep printing characters until the null terminator:
```
 for (int k = 0; passwd[k]; k++) {
    printf("%c", passwd[k]);
}
```

This will work for any C string no matter what size.

---


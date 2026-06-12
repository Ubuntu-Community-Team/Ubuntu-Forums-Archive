---
title: "Example of how to use the C read function"
date: 2012-02-13
forum: Programming Talk
---

### Post by ItecKid on 2012-02-13
Wracking my brain on this one.  I have a C code like this:

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int ch_read (char *foo) 
{
	if (read(0, foo, 1) != 1) {
		return -1;
	}
	else {
		return 1;
	}
}

int ch_write (char foo) 
{
	if (write(1, &foo, 1) != 1) {
		return -1;
	}
	else {
		return 1;
	}
}

int write_help (char *msg, int len) {
	int i = 0;
	int flag = 0;
	for (; i < len; i++) {
		flag = ch_write (msg[i]);
		if (flag == -1) {
			fprintf (stderr, "Error writing byte!");
			return -1;
		}
	}
	return len;
}

int read_help (char *msg, int len) {
	int i = 0;
	int flag = 0;
	for (; i < len; i++) {	
		flag = ch_read (&msg[i]);
		if (flag == -1) {
			fprintf (stderr, "Error reading byte!");
			return -1;
		}
	}
	return len;
}

int main (int argc, char *argv[]) 
{
	char *msg = (char *)malloc(100);
	if (argc != 2) {
		read_help (msg, 24);
		printf ("%s\n", msg);
	}
	else {
		strcpy (msg, argv[1]);
		write_help (msg, strlen(msg));
	}
	return EXIT_SUCCESS;
}

```

The code is run by using shell pipe to take use the output when an argument is passed as input to itself.  So, it would be run like:

```
./a.out aString | ./a.out
```

My question is, what is the proper way to call ch_read from the read_help my function?  My current implementation produces a seg fault.  I have a similar example working with integers, so I know the logic is correct, just not sure what is the correct value to pass to ch_read.

Any help is greatly appreciated.  This code is part of a larger design, and I am not allowed to modify any part of main, ch_read, or ch_write.

---

### Post by Bachstelze on 2012-02-13
You really, really have some reading to do about how strings work in C. In main() you declare a pointer, but you don't allocate any memory to it.

---

### Post by ItecKid on 2012-02-13
> **Bachstelze said:**
> You really, really have some reading to do about how strings work in C. In main() you declare a pointer, but you don't allocate any memory to it.

Yes, you are correct of course.

I saw that error some time after posting this, and meant to come back and update the thread.  However, while it does fix the segfault, I still have a small issue.  I get the entire msg printed to stdout, but I also get an "Error reading byte" on stderr.

---

### Post by Bachstelze on 2012-02-13
Think about what causes "Error reading byte".

(Also, you shouldn't cast the result of malloc().)

---

### Post by ItecKid on 2012-02-13
> **Bachstelze said:**
> Think about what causes "Error reading byte".

(Also, you shouldn't cast the result of malloc().)

Given that I am still getting the entirety of the message (along with the error), my guess is that the ch_read function is being called on the null terminator at the end of msg.

So, I add an if statement in the read_help to my code like this:

```

/* code from above */

if (msg[i] != '\0') {
flag = ch_read (&msg[i]);
}

/* code continues... */

```

This gives me NO output on either stdout or stderr.

---

### Post by Bachstelze on 2012-02-13
No, there is no null terminator at the end of the data passed on stdin. But you have the right idea. Think about what happens when you call read() again after all the characters of the message have been read. There is nothing more to read, so what will read() do?

---

### Post by ItecKid on 2012-02-13
> **Bachstelze said:**
> No, there is no null terminator at the end of the data passed on stdin. But you have the right idea. Think about what happens when you call read() again after all the characters of the message have been read. There is nothing more to read, so what will read() do?

The read() call will fail if there is no data to be read-i.e, all the characters from the message have been read in.  So I somehow need to prevent the call to read() after the last character.  If the string is not null terminated, how do I identify when the last character has been read?

---

### Post by Bachstelze on 2012-02-13
No, the read() call will not "fail". It will return 0. Your problem is that you treat anything that is not 1 as an error.

---

### Post by ItecKid on 2012-02-13
Ah!  I see where you're going with this now.

The constraints of the exercise do not allow me to modify the ch_read function.  However, I can append a special character to the original message to denote the end of input, and break out of the loop when that character is found.

Cheers mate.

---

### Post by Bachstelze on 2012-02-13
Then you shoud tell your instructor that the ch_dir function is wrong, because it does not allow you to distinguish between end-of-file and error. I guess when you are reading from stdin, there is little potential for error, but you never know...

So I guess what you can do is assume there can be no error and that if read_ch returns -1, it's because it has reached the end of the message. It's a little bit dirty, but I will hazard a guess that it's what is espected.

---


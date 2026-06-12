---
title: "c++ modifiable output"
date: 2009-04-14
forum: Programming Talk
---

### Post by cplusrun on 2009-04-14
I'm trying to make a program that let's a user modify an output. Here's what it would look like

Employee's name: | Employee |

Then if they want they can erase a field

Employee's name: |          |

Then retype it:

Employee's name: | New name |

If anyone could point me in the direction of the function I would use for this I would appreciate it. Thanks.

---

### Post by cabalas on 2009-04-14
I assume from the way your description that this is meant to be a command line app, to do something like this you will probably be wanting something like ncurses to handle the ui, a quick google should turn up some useful links.

---

### Post by Krupski on 2009-04-14
> **cplusrun said:**
> I'm trying to make a program that let's a user modify an output. Here's what it would look like

Employee's name: | Employee |

Then if they want they can erase a field

Employee's name: |          |

Then retype it:

Employee's name: | New name |

If anyone could point me in the direction of the function I would use for this I would appreciate it. Thanks.

Something like this:

```

#include <stdio.h>
#include <string.h>

int readln(FILE*, char*);

int main(void)
{
	char buf[BUFSIZ];
	char name[BUFSIZ];

	strcpy(name, "John Smith");

	while(1) {
		fprintf(stdout, "Employee's name: %s\rEmployee's name: ", name);
		readln(stdin, buf);
		if(buf[0] == 0) { break; }
		strcpy(name, buf);
	}

	fprintf(stdout, "\nName is now: %s\n", name);
	return 0;
}


int readln(FILE *fp, char *str)
{
	char buffer[BUFSIZ];
	int len;

	buffer[0] = 0; fgets(buffer, BUFSIZ, fp);

	len = strlen(buffer);

	while(len >= 0) {
		if(	buffer[len] == 32 ||
			buffer[len] == 13 ||
			buffer[len] == 10 ||
                       buffer[len] ==  9 ||
			buffer[len] ==  0) { buffer[len] = 0; len--; }
		    else { break; }
	}

	len++;

	buffer[len] = 0;

	strcpy(str, buffer);

	return len;
}

```


???

---

### Post by cplusrun on 2009-04-14
This is very close to what I'm looking for Krupski, only problem is that the cursor starts before the word, and Delete key doesnt work. I'm taking a look at the code to see how to change this. Thank you.

And thanks for your post too cabalas, I'll definitely check out curses

---

### Post by Krupski on 2009-04-14
> **cplusrun said:**
> This is very close to what I'm looking for Krupski, only problem is that the cursor starts before the word, and Delete key doesnt work. I'm taking a look at the code to see how to change this.

Well, obviously that code is a very rough and unfinished piece of programming. It's only to get you started in (hopefully) the right direction.

Good luck!

-- Roger

---

### Post by cplusrun on 2009-04-14
Well I shall attempt to finish it then ;) I'll repost my solution later for anyone who's searching for how to do this. Thanks for your help!

---

### Post by cplusrun on 2009-04-14
Hmm... looking deeper into that code I found that the only reason it looks like it's able to manipulate the output is because of that \r in the original fprintf. Other than that there doesnt seem to be a way to actually edit the original string. Thanks anyway Krupski! I'll go check out the curses library, see if theres anything that'll help me there

---

### Post by Arndt on 2009-04-15
> **cplusrun said:**
> I'm trying to make a program that let's a user modify an output. Here's what it would look like

Employee's name: | Employee |

Then if they want they can erase a field

Employee's name: |          |

Then retype it:

Employee's name: | New name |

If anyone could point me in the direction of the function I would use for this I would appreciate it. Thanks.

The man page tty_ioctl mentions the ioctl TIOCSTI (simulate terminal input). So the program would output the prompt and the value of the field, but also insert the characters in the input buffer, from which they can be erased by the user, or accepted. I don't think they are echoed when inserted, but maybe they are.

I don't recommend this. If nothing else, the program will probably behave strangely if given input from a pipe.

---

### Post by cplusrun on 2009-04-15
Thank you Arndt, tried looking up a man page for ioctl, and it seems rather complicated. I'll try to work with it and post. Unfortunately, the use of this destroys portability, but at least I'll have the satisfaction of messing with output on screen on a linux system ;D 

Btw, if you could provide any c++ code of how to use this, please post it. Thanks!

---

### Post by Arndt on 2009-04-16
> **cplusrun said:**
> Thank you Arndt, tried looking up a man page for ioctl, and it seems rather complicated. I'll try to work with it and post. Unfortunately, the use of this destroys portability, but at least I'll have the satisfaction of messing with output on screen on a linux system ;D 

Btw, if you could provide any c++ code of how to use this, please post it. Thanks!

Sorry, I would have to build it from scratch, and it was many years since I actually used these parts of the Unix I/O system. I only remembered that there was such a command.

---


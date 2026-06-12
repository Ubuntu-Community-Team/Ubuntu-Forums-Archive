---
title: "Cannot execute binary file"
date: 2011-04-15
forum: Programming Talk
---

### Post by xtjacob on 2011-04-15
Hello all,
I'm currently learning C, and I'm on multiple functions, but after I compile the code, and make it executable I get the error "cannot execute binary file". I used "gcc -c multf.c -o multf" to compile it, and I'm running an amb_64 kernel. Here's my code: 
```
#include <stdio.h>
void butler();

int main()
{
	printf("I will summon the butler funtion.\n");
	butler();
	printf("Yes. Bring me some tea and a 1TB Hard Drive.\n");
	return 0;
}

void butler()
{
	printf("You rang, sir?\n");
}
```
What's the problem here?

---

### Post by xtjacob on 2011-04-15
Alright, it seems that I did not know how to compile C code properly. This thread can probably be deleted.

---

### Post by safarin on 2011-04-15
How you compile?

```
$ ./multf
```

---

### Post by xtjacob on 2011-04-15
Before I used ```
gcc -c multf.c -o multf
```
Now I use ```
cc -o multf multf.c
```

---

### Post by safarin on 2011-04-15
> **xtjacob said:**
> Before I used ```
gcc -c multf.c -o multf
```
Now I use ```
cc -o multf multf.c
```

your problem already solved or not? Actually to compile you can use

```
gcc multf.c -o multf
```

---

### Post by xtjacob on 2011-04-15
Yah, I realized that "-c" produces object, while "-o" produces an executable.

---


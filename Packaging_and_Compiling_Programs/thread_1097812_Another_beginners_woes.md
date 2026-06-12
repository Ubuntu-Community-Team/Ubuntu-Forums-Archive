---
title: "Another beginners woes"
date: 2009-03-16
forum: Packaging and Compiling Programs
---

### Post by dimothy10 on 2009-03-16
Dear All,

Am fairly new to Ubuntu and even newer to programming C++ but am eager to try and forge on regardless.  Until today I have kept my limited exploits to Hello World style programs under Windows using the Dev-C++ IDE and so far have found it very agreeable.  I recently decided to try and program under Ubuntu as well but seem to have hit an early pothole.  

I have written a very simple Hello World program in gedit and save it as hello.cpp .  I have then used the following command to compile it: 

```
g++ hello.cpp -o hello
```

I get no error messages when compiling it seems and I can now see the program hello (with no extension listed) via the use of the ls command.  However when i type hello in to a terminal i get the following error message:

```
The program 'hello' can be found in the following packages:
 * hello-debhelper
 * hello
Try: sudo apt-get install <selected package>
bash: hello: command not found
```

I assume that I am missing a vital step in the compiling process as, as far as i am aware, the code is sound and should work.  I have included it below just in case:

```

#include <iostream>

int main ()
{
	std::cout << "Hello World!\n";
	return (0);
}
```

Thanks in advance

Tim

---

### Post by albandy on 2009-03-16
type this ./hello
You've to specify the path, so ./hello tells the system to run hello from current path

---

### Post by dimothy10 on 2009-03-16
AH HA!!!

Thanks for that.  You can probably tell i am very new to linux as well as programming lol.  Thanks again for the speedy reply

---


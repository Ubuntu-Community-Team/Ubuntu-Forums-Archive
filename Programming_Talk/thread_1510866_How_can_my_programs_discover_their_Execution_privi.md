---
title: "How can my programs discover their Execution privileges?"
date: 2010-06-16
forum: Programming Talk
---

### Post by Kerubu on 2010-06-16
I'm writing some programs that use the libusb libraries to access usb devices using code written in user space. However with just normal user privileges the functions my program can do are limited e.g. I cannot even open a device.

To open a device I have to execute my program with 'sudo' to give it superuser rights. Now yes I know this is bad programming but it's only a temporary measure.

But what I'd like to know is how can I or what code do I need to include for the program to check what privileges it has when it is executed?

Many thanks

Kerubu

---

### Post by schauerlich on 2010-06-16
getuid() returns the real user ID of the calling process

[http://linuxmanpages.com/man2/getuid.2.php](http://linuxmanpages.com/man2/getuid.2.php)

```

#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>

int main(void) {
  uid_t processUID = getuid();

  if (processUID == 0) {
    puts("We're root; time to delete everything!");
  } 
  else {
    puts("Requires root privileges");
    return EXIT_FAILURE;
  }
        
  return EXIT_SUCCESS;
}


```

```
schauerlich@inara:~$ gcc -Wall -o uid uid.c 
schauerlich@inara:~$ ./uid 
Requires root privileges
schauerlich@inara:~$ sudo ./uid 
Password:
We're root; time to delete everything!
schauerlich@inara:~$

```

---

### Post by Kerubu on 2010-06-16
> **schauerlich said:**
> getuid() returns the real user ID of the calling process

[http://linuxmanpages.com/man2/getuid.2.php](http://linuxmanpages.com/man2/getuid.2.php)

cheers schauerlich !

---


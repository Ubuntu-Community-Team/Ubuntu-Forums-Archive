---
title: "Error Compiling a C program"
date: 2013-01-28
forum: Programming Talk
---

### Post by dansofe0r on 2013-01-28
Hey everyone, 

I'm trying to compile a program in C. I use gcc -o aprogram aprogram.c -lpcap in the terminal. Then this comes up: 

aprogram.c: In function ‘aprogram’:
aprogram.c:83:2: warning: format ‘%s’ expects argument of type ‘char *’, but argument 2 has type ‘int’ [-Wformat]
aprogram.c:84:2: warning: format ‘%s’ expects argument of type ‘char *’, but argument 2 has type ‘int’ [-Wformat]

So, here are the lines in question. I have already tried to change their type to char *vara and char *varb, but that didn't work because it still gave me the same error messages.
```

    unsigned int vara;   
    unsigned int varb;

```and these are the lines that use the %s format parameter: 
```

    printf("\t %s\t", inet_ntoa(structa->vara));
    printf(" %s )\n", inet_ntoa(structa->varb));

```Thanks!

---

### Post by lisati on 2013-01-28
*Thread moved to **Programming Talk**.*

---

### Post by satsujinka on 2013-01-28
> **dansofe0r said:**
> Hey everyone, 

I'm trying to compile a program in C. I use gcc -o aprogram aprogram.c -lpcap in the terminal. Then this comes up: 

aprogram.c: In function ‘aprogram’:
aprogram.c:83:2: warning: format ‘%s’ expects argument of type ‘char *’, but argument 2 has type ‘int’ [-Wformat]
aprogram.c:84:2: warning: format ‘%s’ expects argument of type ‘char *’, but argument 2 has type ‘int’ [-Wformat]

So, here are the lines in question. I have already tried to change their type to char *vara and char *varb, but that didn't work because it still gave me the same error messages.
```

    unsigned int vara;   
    unsigned int varb;

```and these are the lines that use the %s format parameter: 
```

    printf("\t %s\t", inet_ntoa(structa->vara));
    printf(" %s )\n", inet_ntoa(structa->varb));

```Thanks!

If you could give us the updated code, that'd be easier to work with. It would also help if it was complete, so that we could attempt to compile it ourselves.

---

### Post by lisati on 2013-01-28
OK, I've had another look at what we've been given. Here's my take on what's happening, assuming that you're manipulating IP addresses: the warning is telling us that printf() is expecting a "char", but the output from inet_ntoa gives an int.

BTW, from what I've read, inet_ntoa only handles IPv4 format addresses, not so good for IPv6.

---

### Post by dwhitney67 on 2013-01-29
> **dansofe0r said:**
> 
So, here are the lines in question. I have already tried to change their type to char *vara and char *varb, but that didn't work because it still gave me the same error messages.

I didn't see a question mark, but I assume you are questioning why the compiler is spitting out an error.

The compiler does not know about inet_ntoa(), and thus assumes that it returns an int value.  Obviously this would conflict with the format type given in your printf() statement.

You will need to include the appropriate system header file to inform the compiler of the true function signature of inet_ntoa().  Looking at the 'man page' for inet_ntoa(), three header files are listed.  My educated guess is that it is **arpa/inet.h** that needs to be included in your code.

---

### Post by dansofe0r on 2013-01-29
Thank you all for taking the time out to read my thread and trying to help. Here is the function that isn't allowing me to happily run my code.  Compiling this function will give you the same compilation errors that I have been getting. 

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <arpa/inet.h>
#include <pcap.h>
#include "output.h"
#include "output-network.h"

void output_ip(const u_char *header_start) {
    const struct ip_hdr *ip_header;
    
    ip_header = (const struct ip_hdr *)header_start;
    printf("\t((  Layer 3  ::: IP Header  ))\n");
    printf("\t(  Source: %s\t", inet_ntoa(ip_header->ip_src_addr));
    printf("Dest: %s )\n", inet_ntoa(ip_header->ip_dest_addr));
    printf("\t(  Type: %u\t", (u_int) ip_header->ip_type);
    printf("ID: %hu\tLength: %hu)\n", ntohs(ip_header->ip_id), ntohs(ip_header->ip_len));
}

```and here is the struct in output-network.h for ip_hdr
```

struct ip_hdr {
    unsigned int ip_src_addr;    // Source IP address
    unsigned int ip_dest_addr;    // Destination IP address
};

```Please let me know if I can post any other useful information to figure this out.

---

### Post by steeldriver on 2013-01-29
If you are trying to print the value that is returned by a call to the inet_ntoa function, then the format specifier in your print statement needs to match the **return type** of the function

So what is the **return type** of inet_ntoa()?

---

### Post by spjackson on 2013-01-30
> **dansofe0r said:**
> Compiling this function will give you the same compilation errors that I have been getting. 

Well, yes and no. The original error message you were getting was to do with the return type of inet_ntoa and dwhitney67 told you to include arpa/inet.h which you have correctly done.

You should now be getting a different error message like this:
```

output.c: In function ‘output_ip’:
output.c:14:5: error: incompatible type for argument 1 of ‘inet_ntoa’
/usr/include/arpa/inet.h:54:14: note: expected ‘struct in_addr’ but argument is of type ‘unsigned int’
output.c:15:5: error: incompatible type for argument 1 of ‘inet_ntoa’
/usr/include/arpa/inet.h:54:14: note: expected ‘struct in_addr’ but argument is of type ‘unsigned int’

```

You have corrected the original problem concerning the return type of inet_ntoa but now you have a second problem which is the type of parameter you are passing to it. The above error message and the man page for inet_ntoa tell you what it needs.

---

### Post by dansofe0r on 2013-01-30
Good news everyone #futurama. 

After reading your posts and trying a few other things I found the solution that would allow the code to compile correctly. After including arpa/inet.h I changed the two lines that were having compatibility issues. 

They have been changed to:
```

printf("\t(  Source: %s\t", inet_ntoa(*(struct in_addr *)&ip_header->ip_src_addr));   
printf("Dest: %s )\n", inet_ntoa(*(struct in_addr *)&ip_header->ip_dest_addr));

```

Thanks again for your help! :P

---

### Post by dwhitney67 on 2013-01-30
> **dansofe0r said:**
> Good news everyone #futurama. 

After reading your posts and trying a few other things I found the solution that would allow the code to compile correctly. After including arpa/inet.h I changed the two lines that were having compatibility issues. 

They have been changed to:
```

printf("\t(  Source: %s\t", inet_ntoa(*(struct in_addr *)&ip_header->ip_src_addr));   
printf("Dest: %s )\n", inet_ntoa(*(struct in_addr *)&ip_header->ip_dest_addr));

```

Thanks again for your help! :P

It's good that you passed this hurdle, but what you have done it known as a "hack".

Why don't you go back to your ip_hdr structure to modify it to be:
```

struct ip_hdr {
    struct in_addr ip_src_addr;     // Source IP address
    struct in_addr ip_dest_addr;    // Destination IP address
};

```
Then you would use ip_src_addr (or ip_dst_addr) as:
```

printf("\t(  Source: %s\t", inet_ntoa(ip_header->ip_src_addr));
printf("Dest: %s )\n", inet_ntoa(ip_header->ip_dest_addr));

```
You did not reveal in your previous posts how to obtained values for the ip_hdr, but you should be able to set the s_addr portion of the in_addr structure to the value you already have.  For example:
```

ip_hdr->ip_src_addr = sin.sin_addr;

```
where 'sin' is the sockaddr_in structure that you presumably setup manually (or possibly obtained from accept()).

---

### Post by dansofe0r on 2013-01-30
> **dwhitney67 said:**
> It's good that you passed this hurdle, but what you have done it known as a "hack".

Why don't you go back to your ip_hdr structure to modify it to be:
```

struct ip_hdr {
    struct in_addr ip_src_addr;     // Source IP address
    struct in_addr ip_dest_addr;    // Destination IP address
};

```Then you would use ip_src_addr (or ip_dst_addr) as:
```

printf("\t(  Source: %s\t", inet_ntoa(ip_header->ip_src_addr));
printf("Dest: %s )\n", inet_ntoa(ip_header->ip_dest_addr));

```
I just tried what you suggested here and I am much more satisfied with your way. You made the quick and dirty fix I used into a nice and neat solution. Now I can use the ip_hdr struct without encountering that problem in other programs! Thanks. =D>

---


---
title: "C++ - MD5 and SHA1 (256/512) char*?"
date: 2011-03-21
forum: Programming Talk
---

### Post by cipherboy_loc on 2011-03-21
I would like to try and create a secure transmission client/server in C++ (or fail there in). This is just an example, but right now I am stuck on creating a MD5 hash of the message (to verify that the it was received intact). 


I know that I need to **#include <openssl/md5.h>**, but I have not made any progress farther than that. The documentation (is it really just the man page off of openssl.org?) seems to state that the **MD5()** function would used to hash an unsigned char message.

The code that doesn't work (example only):
```

        unsigned char* blah;
        MD5(unsigned('\0'), 0, blah);
        cout << blah << endl;
        delete blah;

```Shouldn't this put the hash of the null character (**d41d8cd98f00b204e9800998ecf8427e**)? Instead (upon compiling) it gives me:

> 
/tmp/ccXshDhk.o: In function `test()':
main.cxx:(.text+0x70): undefined reference to `MD5'
collect2: ld returned 1 exit status
Any ideas? Do I need to define a MD5 class variable (if so, how)?


Thanks, 
Cipherboy

---

### Post by dwhitney67 on 2011-03-21
Did you link with the OpenSSL library?  I do not know if the following is 100% correct, but something like:
```

g++ MyProg.cpp -lgnutls-openssl

```

---

### Post by slavik on 2011-03-21
[http://www.google.com/#sclient=psy&hl=en&q=c%2B%2B+md5+howto&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=a0e1d04ac32ef934](http://www.google.com/#sclient=psy&hl=en&q=c%2B%2B+md5+howto&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=a0e1d04ac32ef934)

---

### Post by johnl on 2011-03-21
```

#include <iostream>
#include <iomanip>
#include <openssl/md5.h>

int main() 
{
    unsigned char buffer[16];
    unsigned char input = '\0';

    /* first argument needs to be an unsigned char pointer
     * second argument is number of bytes in the first argument
     * last argument is our buffer, which needs to be able to hold
     * the 16 byte result of the MD5 operation */
    MD5(&input, 1, buffer);

    /* the result in buffer is not a string as you seem to expect,
     * it's a sequence of bytes.  you can print it like so:
     */

    for(int i = 0; i < sizeof(buffer); ++i) {
        std::cout << std::hex          /* print numbers as hexadecimal */
                  << std::setw(2)      /* print two digits */
                  << std::setfill('0') /* pad with '0' */
                  << static_cast<int>(buffer[i]);
    }
    std::cout << std::endl;

    /* compare the output to: echo -e -n '\0' | md5sum */
    return 0;
}

```

You need to link with **-lssl**

---

### Post by cipherboy_loc on 2011-03-21
Thanks dwhitney67. Marking as solved.

```

g++ main.cxx -lgnutls-openssl

```

Cipherboy

---

### Post by fsleeman on 2011-03-21
I tried that code but got different results from the md5sum program.

echo -e -n '\0' | md5sum
29fa3b71cc8c846ecd9372245a1b6447  -

./test 
93b885adfe0da089cdf634904fd59f71

Is there a reason this is different? I running Ubuntu 10.10 and all of the packages should be current.

---

### Post by dwhitney67 on 2011-03-21
> **fsleeman said:**
> I tried that code but got different results from the md5sum program.

echo -e -n '\0' | md5sum
29fa3b71cc8c846ecd9372245a1b6447  -

./test 
93b885adfe0da089cdf634904fd59f71

Is there a reason this is different? I running Ubuntu 10.10 and all of the packages should be current.

Show your test code, showing what you ran.  Note that in the OP's original post, he specified a data size of zero bytes; thus it is not relevant that one pass a null-character to the MD5() function.  This would have worked equally as well:
```

#include <openssl/md5.h>
#include <cstdio>

int main()
{
   unsigned char result[MD5_DIGEST_LENGTH];

   MD5(NULL, 0, result);

   for (size_t i = 0; i < MD5_DIGEST_LENGTH; ++i)
   {
      printf("%02x", result[i]);
   }
   printf("\n");
}

```

---

### Post by fsleeman on 2011-03-21
Ok, I think I figured out part of the problem. First, I actually compiled and ran the program on a Centos server, not my Ubuntu desktop. When I ran the code (copy and paste from johnl's post) I get the identical result between that code and the linux md5sum command.

However, on the Centos computer I get the differing results I previously posted. I am not 100% sure about the Centos version but its probably a couple years old, and the packages might be old too. If this library is an implementation of RFC 1321, shouldn't the results be the same? If not, doesn't that make this un-portable or am I missing something?

Just to be clear, the code gives the same result for Ubuntu, Centos, and Solaris. The md5sum on Centos gives a number different from the program I compiled. Even the comparable command on Solaris gives the same result as the compiled program.

---


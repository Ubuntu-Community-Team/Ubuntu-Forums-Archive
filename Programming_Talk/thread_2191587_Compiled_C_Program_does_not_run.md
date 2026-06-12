---
title: "Compiled C Program does not run"
date: 2013-12-03
forum: Programming Talk
---

### Post by dauletle on 2013-12-03
Hi all! This is a quick (and hopefully simple question) regarding running a compiled c program.  I wrote a program using the openssl/sha.h library that looked something like this:
```

int main()
{
	const int DataLen = 64;
	SHA_CTX shactx;
	unsigned char digest[SHA_DIGEST_LENGTH];


	printf("\r\nSHA-1 Message secret Hasher\r\n");
	printf("\r\nComputing Secret...\r\n");


	SHA1_Init(&shactx);
	SHA1_Update(&shactx, Message, DataLen);
    	SHA1_Final(digest, &shactx);


	printf("Message Hashed.\r\n");


	printf("%02x ", Message[0]);
	printf("%02x ", Message[1]);
	printf("%02x ", Message[2]);
	printf("%02x ", Message[3]);
	printf("%02x ", Message[48]);
	printf("%02x ", Message[49]);
	printf("%02x ", Message[50]);
	printf("%02x\r\n", Message[51]);
}

```

Once I write the code, I compile it by entering the following in the terminal:
```
gcc -g -Wall -Werror -std=c99 -ansi -pedantic -c main.c -o SHAHash
```

The code compiles with no errors.  So when I try to run it with the "sudo ./SHAHash" command, I get the following error:

```
./SHASearch: 1: ./SHASearch: Syntax error: word unexpected (expecting ")")
```

I felt like this was a straightforward process, but I feel that using the special library incorrectly would cause this issue.  Once again, any advice would be appreciated.  Thank you

---

### Post by papibe on 2013-12-03
Thread moved to **Programming Talk**.

---

### Post by steeldriver on 2013-12-03
Where is 'Message' declared / allocated? does it really have DataLen characters (or is that just the buffer size)? are you sure you understand the calling convention for the SHA_Update function? You may find this stackoverflow answer useful --> [http://stackoverflow.com/a/9284520](http://stackoverflow.com/a/9284520)

---

### Post by dauletle on 2013-12-03
Oops, I forgot to add the declarations and inclusions.  Here you go
```

#include <stdio.h>
#include <stdlib.h>
#include <stdbool.h>
#include <unistd.h>
#include <string.h>
#include <openssl/sha.h>




unsigned char Message[] = {
0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0A, 0x0B, 0x0C, 0x0D, 0x0E, 0x0F,
0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16, 0x17, 0x18, 0x19, 0x1A, 0x1B, 0x1C, 0x1D, 0x1E, 0x1F,
0x20, 0x21, 0x22, 0x23, 0x24, 0x25, 0x26, 0x27, 0x28, 0x29, 0x2A, 0x2B, 0x2C, 0x2D, 0x2E, 0x2F,
0x30, 0x31, 0x32, 0x33, 0x34, 0x35, 0x36, 0x37, 0x38, 0x39, 0x3A, 0x3B, 0x3C, 0x3D, 0x3E, 0x3F,
};


int main()
{
    const int DataLen = 64;
    SHA_CTX shactx;
    unsigned char digest[SHA_DIGEST_LENGTH];


    printf("\r\nSHA-1 Message secret Hasher\r\n");
    printf("\r\nComputing Secret...\r\n");


    SHA1_Init(&shactx);
    SHA1_Update(&shactx, Message, DataLen);
    SHA1_Final(digest, &shactx);

    //While this is a higher end function, I chose to work with the one above
    //This one also had the same errors
    //SHA1(Message, DataLen, digest); //Another way to hash using the SHA function

    printf("Message Hashed.\r\n");


    printf("%02x ", Message[0]);
    printf("%02x ", Message[1]);
    printf("%02x ", Message[2]);
    printf("%02x ", Message[3]);
    printf("%02x ", Message[48]);
    printf("%02x ", Message[49]);
    printf("%02x ", Message[50]);
    printf("%02x\r\n", Message[51]);
}

```

Then, these are the commands I put into the terminal
```

$:  gcc -g -Wall -Werror -std=c99 -ansi -pedantic -c main.c -o SHAHash
$:  sudo ./SHAHash
sudo: ./SHAHash: command not found
$:  chmod +x SHAHash
$:  sudo ./SHAHash
./SHAHash: 1: ./SHAHash: Syntax error: word unexpected (expecting ")")
$:

```

I found online that by changing the program to an executable, it would be able to run.  However, this could be the reason why it isn't running any better.  All suggestions will be appreciated

Also, thank you for moving the post to "Programming Talk".  I wasn't sure if I was in the right forum when I first posted it.

---

### Post by steeldriver on 2013-12-03
Ah I just noticed you are adding **-c** to the gcc command line - this tells the compiler to stop after the compilation phase, not performing the final link to an executable. So you are trying to execute a chunk of bare object code. This probably also explains why you need to explicitly chmod the file to make it 'executable'. Don't do that. You probably want

```
gcc -g -Wall -Werror -std=c99 -pedantic -o SHAHash main.c **-lcrypto**
```

(you can't use -ansi with c99 and // style comments, I don't think)

```

$ ./SHAHash

SHA-1 Message secret Hasher

Computing Secret...
Message Hashed.
00 01 02 03 30 31 32 33

```

---

### Post by dauletle on 2013-12-03
Great! It works now.  Thanks :)

---


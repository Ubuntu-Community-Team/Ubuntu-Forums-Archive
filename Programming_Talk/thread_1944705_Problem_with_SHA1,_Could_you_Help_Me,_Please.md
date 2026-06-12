---
title: "Problem with SHA1, Could you Help Me, Please?"
date: 2012-03-21
forum: Programming Talk
---

### Post by hazem_baz on 2012-03-21
Hi,

I am using the following simple code to find the hash value of a string with the help of SHA1.

#include <stdio.h>
#include <string.h>
#include <openssl/sha.h>

int main(int argn, char *argv[]) {

	int i = 0;
	unsigned char temp[SHA_DIGEST_LENGTH];
	char buf[SHA_DIGEST_LENGTH*2];

	if ( argn != 2 ) {
		printf("Usage: %s string\n", argv[0]);
		return -1;
	}

	memset(buf, 0x0, SHA_DIGEST_LENGTH*2);
	memset(temp, 0x0, SHA_DIGEST_LENGTH);

	SHA1((unsigned char *)argv[1], strlen(argv[1]), temp);

	for (i=0; i < SHA_DIGEST_LENGTH; i++) {
		sprintf((char*)&(buf[i*2]), "%02x", temp[i]);
	}

	printf("SHA1 of %s is %s\n", argv[1], buf);

	return 0;

}


i am working on Ubuntu11.04, and downloaded openssl, after i compile this code by following Command:

$ gcc sha.c -lssl -o sha

it give this Error Msg, 

/tmp/cc3xG64p.o: In function `main':
sha.c: ( .text+0xc9): undefined reference to `SHA1'
collect2: ld returned 1 exit status

and i dont know what is mean? and how to slove it?

i am waiting your reply ..

---

### Post by hazem_baz on 2012-03-21
the solution of this Error Msg is writing the following command line : 

$  gcc sha.c -Wall  -lcrypto -o sha

and i hope this Post will help any one who using SHA1, and face the same problem.

---


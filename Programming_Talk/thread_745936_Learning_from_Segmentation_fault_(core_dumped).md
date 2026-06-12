---
title: "Learning from Segmentation fault (core dumped)?"
date: 2008-04-05
forum: Programming Talk
---

### Post by dreadh3ad on 2008-04-05
I am writing a program in C and compiling with gcc via command line.  I have a general idea what function caused the problem (through commenting out newly added lines).  How can i get more specific information on this problem through a core dump?

Also C pointers confuse me.  help?

---

### Post by LaRoza on 2008-04-05
You will have to understand pointers (and arrays) to fix such problems, otherwise, it is just guesswork.

If the code is short, could you post it?

---

### Post by dreadh3ad on 2008-04-05
Here are the relevant snippets

I am trying to convert argv[1] into cbc_key[8] for DES encryption.

Any suggestions on good pointer references on the net?

```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <openssl/des.h>

#define ENC 1
#define DEC 0


DES_LONG ctol(unsigned char *c) {
        DES_LONG l;
        l =((DES_LONG)(*((c)++)));
        l = l | (((DES_LONG)(*((c)++)))<<8L);
        l = l | (((DES_LONG)(*((c)++)))<<16L);
        l = l | (((DES_LONG)(*((c)++)))<<24L);
        return l;
};



ltoc(DES_LONG l, unsigned char *c) {
        *((c)++)=(unsigned char)(l&0xff);
        *((c)++)=(unsigned char)(((l)>> 8L)&0xff);
        *((c)++)=(unsigned char)(((l)>>16L)&0xff);
        *((c)++)=(unsigned char)(((l)>>24L)&0xff);
}

int ctox(char c)
{
	if(c>='0'&&c<='9')
		return(c-'0');
	else
		return(10+(c-'a'));
}
	
/*If the char c is '0' - '9', use c - '0' to convert c to a digit.  If c is
'a'-'f', use c + 10 - 'a' to convert c to a digit. */

int main(int argc, char **argv)
{
	int k;
	long in[2];
	static unsigned char cbc_key[8] = {0x01,0x23,0x45,0x67,0x89,0xab,0xcd,0xef};
	des_key_schedule key;
	char* temp=malloc(2);
	char* a=argv[1];
	int i=0, b=0, c=1;
	int m, n;
	char d, e;


	for(i=0; i<(strlen(a))/2; i++)
	{
		m=ctox(a[b]);
		n=ctox(a[c]);
		//printf("%d\n", m);
		//printf("%d\n", n);
		b=b+2;
		c=c+2;
	}

	if ((k = des_set_key_checked(&cbc_key,key)) != 0)
		printf("\nkey error\n");

	in[0] = 875770417;
	in[1] = 1650536505;

	//convert
	printf("DES Clear Text: %ld%ld\n",in[0],in[1]);
	des_encrypt1(in,key,ENC);

	printf("DES Encryption: %ld%ld\n",in[0],in[1]);

	des_encrypt1(in,key,DEC);

	printf("DES Decryption: %ld%ld\n",in[0],in[1]);
}


```

---

### Post by lnostdal on 2008-04-05
```

gcc -Wall -g -o your-program your-program.c
gdb your-program
run <enter>
..
..
bt <enter>

```

make sure you compile with the -g option, as shown

bt is short for "backtrace"


edit:
you can also use a graphical debugger .. [http://www.kdbg.org/](http://www.kdbg.org/) (sudo aptitude install kdbg)

---


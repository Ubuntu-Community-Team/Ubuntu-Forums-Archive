---
title: "SHA1 C/C++ Procedure?"
date: 2007-01-13
forum: Programming Talk
---

### Post by breuerp on 2007-01-13
I'm writing a program that needs to produce that SHA-1 has of received input.  I suppose I could pipe the output of my program to sha1sum but that's just not elegant.  Does anyone know which library contains a SHA1 procedure that I can link in?

Cheers!

---

### Post by gpolo on 2007-01-13
should be on libgcrypt

---

### Post by breuerp on 2007-01-13
I don't see a prototype for a sha1 function in there.  I would have guessed it would have been there or in crypt.h

---

### Post by Houman on 2007-01-13
install it with apt, "sudo aptitude install libgcrypt11-dev"

---

### Post by breuerp on 2007-01-13
It's installed but there's no .h file that I can find in the /usr/lib or /usr/include

There appears to be a sha1 function in the OpenSSL development libraries.  I guess I'll try to see if I can figure that one out.  If anyone already knows, please pass it along, otherwise I'll post my results when I figure it out.

---

### Post by gpolo on 2007-01-13
I don't know if you are joking or not, but what you will use is the lib in /usr/lib

/usr/lib/libgcrypt.so or .a, depending on how you will distribute your program

If you wanna learn how to use this library, you can run: info gcrypt.

edit: of course you need to include gcrypt.h in your source

---

### Post by breuerp on 2007-01-14
Actually, I'm not joking (unfortunately).  I've been out of the programming biz for quite a while and I never programmed in Linux before (it's now my defacto OS) so I'm having to learn all the little things over again.  I'm not exactly clear on the differences between a .so and a .a file, but I guess that's why we put ourselves through these exercises.  Last time I programmed in *nix it was on an old SGI Iris and an old Ultra Sparc 15.  Thanks for the assist!

---

### Post by ZuLuuuuuu on 2007-01-14
AFAIK, the libraries having .so extension are dynamic (called shared object) libraries. If you include those kind of libraries into your program, then the functions you use in your program won't be compiled, but will be called from Unix whenever you run your program.

The libraries having .a extension are static (called archive) libraries. They are compiled as well as your program, so I think if you use static libraries then the client does not have to have that library in his/her computer. This has of course its negative side, which is: Your program's size will be greater compared to the same program using dynamic libraries.

I'm a C newbie so I might be wrong... For example, gpolo mentioned about including the .h file but I don't know how the gcrypt.h file is generated (is it generated or is there any pregenerated .h file or is including unnecessary if we use static library?).

---

### Post by tomchuk on 2007-01-14
gcrypt.h is part of the libgcrypt11-dev package.

Here's some code to get you started:
```

#include <gcrypt.h>
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv){

  /* Test for arg string */
  if ( argc < 2 ){
    fprintf( stderr, "Usage: %s <string>\n", argv[0] );
    exit( 1 );
  }

  /* Length of message to encrypt */
  int msg_len = strlen( argv[1] );

  /* Length of resulting sha1 hash - gcry_md_get_algo_dlen
   * returns digest lenght for an algo */
  int hash_len = gcry_md_get_algo_dlen( GCRY_MD_SHA1 );

  /* output sha1 hash - this will be binary data */
  unsigned char hash[ hash_len ];

  /* output sha1 hash - converted to hex representation
   * 2 hex digits for every byte + 1 for trailing \0 */
  char *out = (char *) malloc( sizeof(char) * ((hash_len*2)+1) );
  char *p = out;

  /* calculate the SHA1 digest. This is a bit of a shortcut function
   * most gcrypt operations require the creation of a handle, etc. */
  gcry_md_hash_buffer( GCRY_MD_SHA1, hash, argv[1], msg_len );

  /* Convert each byte to its 2 digit ascii
   * hex representation and place in out */
  int i;
  for ( i = 0; i < hash_len; i++, p += 2 ) {
    snprintf ( p, 3, "%02x", hash[i] );
  }

  printf( "%s\n", out );
  free( out );

}

```

compile with:
```

gcc sha1.c -lstdc++ -lgcrypt -lgpg-error -o sha1

```

Example run:
```

thomas@t40$ ./sha1 foo
0beec7b5ea3f0fdbc95d0dd47f3c5bc275da8a33
thomas@t40$ echo -n foo | sha1sum
0beec7b5ea3f0fdbc95d0dd47f3c5bc275da8a33  -

```

---

### Post by breuerp on 2007-01-15
Very cool, thanks.  I've got to go through and figure out exactly what's going on with your code though.  I need to dig into the gcrypt library to figure out exactly what you did.  Thanks for all of the help!

---

### Post by breuerp on 2007-01-15
> **ZuLuuuuuu said:**
> AFAIK, the libraries having .so extension are dynamic (called shared object) libraries. If you include those kind of libraries into your program, then the functions you use in your program won't be compiled, but will be called from Unix whenever you run your program.

The libraries having .a extension are static (called archive) libraries. They are compiled as well as your program, so I think if you use static libraries then the client does not have to have that library in his/her computer. This has of course its negative side, which is: Your program's size will be greater compared to the same program using dynamic libraries.

I'm a C newbie so I might be wrong... For example, gpolo mentioned about including the .h file but I don't know how the gcrypt.h file is generated (is it generated or is there any pregenerated .h file or is including unnecessary if we use static library?).
Zuluu,
    The .h file (stands for header), gives the function prototypes.  Essentially it's a nice table of contents so a programmer knows what functions are included, what they return and what data they expect to be passed in.  Whoever writes the library typically writes the .h file as well.  When compiling code with an outside library you can #include the library and the linker and compiler know to look for a .c (or .cpp) file by the same name which will have all of the implementation code.

     I've been stuck in Java hell for far too long. :)

---

### Post by ZuLuuuuuu on 2007-01-15
Thank you all.

---

### Post by tomchuk on 2007-01-15
Cleaned up my originally posted code and added some comments.

---


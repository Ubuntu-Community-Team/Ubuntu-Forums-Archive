---
title: "My c method crashes my program"
date: 2008-11-03
forum: Programming Talk
---

### Post by AussieGuy69 on 2008-11-03
This function crashes my program with 
*** glibc detected *** gnutella: corrupted double-linked list: 0x08835df8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7744d81]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb7745cad]
/usr/lib/libglib-2.0.so.0(g_malloc+0x2d)[0xb79afdcd]


My code is below:
void add_alternate_source(char filename[]) {
        int *file_size;
        int sha1;
        struct stat *file_stat;   
     
        //initalise file stats
        printf("\nGetting file statistics for %s \n", filename); //works, prints out fine
        int result = stat(filename, file_stat);

        //get file size
        printf("\n Size of file: %u\n", file_stat->st_size); //works, prints file size fine.
    
        //get file sha1

        
        //add X-Alternate-Location
   
}


int main() {

gchar *filename = "/home/myusername/shared/testfile";
add_alternate_source(filename);

}

any idea what I might be doing wrong?

---

### Post by WW on 2008-11-03
The second argument to the stat() function should be a pointer to an existing block of memory containing a stat structure.  You haven't allocated this memory.

---

### Post by AussieGuy69 on 2008-11-04
so. allocate the memory with alloc() for the pointer file_stat then free the object after im finished?.

---

### Post by WW on 2008-11-04
Or just declare
```

struct stat file_stat;

```
and change the subsequent use of file_stat as appropriate.

---

### Post by AussieGuy69 on 2008-11-04
Ive done that, now the program works fine.

coming from a java background I read up on memory allocation, wrote a little test program then allocated the memory properly for the size of the struct stat.

I also freed file_stat afterwards because the function will be called no less than a thousand times.

---

### Post by dribeas on 2008-11-04
> **AussieGuy69 said:**
> I also freed file_stat afterwards because the function will be called no less than a thousand times.

You can use stack allocated memory and get a pointer to your struct as @WW pointed out(which is the common usage):

```

struct stat file_stat;
int result = stat(filename, &file_stat);

```

While memory allocation is really fast in Java due to the implementation of moving garbage collectors, in non-managed languages allocation is more expensive as the system must find a suitable piece of memory. This is also not needed, as you can use local variables as above (which Java does not have).

Learning a language is not getting to know the syntax, but also the idioms that the language or experience enforces.

---


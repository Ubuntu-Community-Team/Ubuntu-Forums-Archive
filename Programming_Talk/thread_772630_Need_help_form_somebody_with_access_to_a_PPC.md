---
title: "Need help form somebody with access to a PPC"
date: 2008-04-28
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-28
Need help from somebody with a PowerPC...

The program below is to detour functions:
I have a x86 processor, I cannot test it.

Could somebody compile it and tell me whether it works fine or whether it results in a segmentation fault?

This program intercepts a function call, meaning calling the modified_function when you actually called example_function.

compile with: gcc detour.c -o detour

- detour.c
```

/*
#include <iostream>
#include <cstdlib>
#include <cstring>
*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#include <unistd.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/mman.h>

#define BRANCH_MOPCODE  0x12   // Branch instruction's major opcode
#define DEFAULT_STUBSZ   128  // large enough size for a function stub
#define DETOUR_LENGTH      4 // first n bytes of the "original" function
#define PAGESIZE 4096


/*
 * We will be using one of the PowerPC bx (Branch) family of instructions,
 * specifically "b" - unconditional branch.
 *
 * b    target_addr (AA = 0 LK = 0)
 * ba   target_addr (AA = 1 LK = 0)
 * bl   target_addr (AA = 0 LK = 1)
 * bla  target_addr (AA = 1 LK = 1)
 *
 * 0     5 6                                                          29 30 31
 * +------+-------------------------------------------------------------+-+-+
 * |______|_____________________________________________________________|_|_|
 *   OP                                 LI                              AA LK
 *
 *     target_addr specifies the branch target address
 *
 * If AA = 0, then the branch target address is the sum of LI || 0b00
 * sign-extended and the address of this instruction.
 *
 * If AA = 1, then the branch target address is the value LI || 0b00
 * sign-extended.
 *
 * If LK = 1, then the effective address of the instruction following
 * the branch instruction is placed into the link register.
 */
typedef struct
{
    unsigned int OP:  6 ;     // bits 0 - 5, primary opcode
    unsigned int LI: 24 ;    // bits 6 - 29, LI
    unsigned int AA:  1 ;   // bit 30, absolute address
    unsigned int LK:  1 ;  // bit 31, link or not
} branch_t;


  // Each instance of re-routing has the following data structure associated
 // with it. A pointer to a frr_data_t is returned by the "install"
// function. The "remove" function takes the same pointer as argument.

typedef struct
{
    void* f_orig;   // "original" function
    void* f_new;   // user-provided "new" function
    void* f_stub; // stub to call "original" inside "new"
    char f_bytes[DETOUR_LENGTH]; // bytes from f_orig
} frr_data_t;


// Given an "original" function and a "new" function, frr_install()
// re-routes so that anybody calling "original" will actually be
// calling "new". Inside "new", it is possible to call "original"
// through a stub.

void* InterceptFunction(void* example_function, unsigned long uslng_CopyLength, void* modified_function)
{
    int MPROTECT_ERROR = -1 ;
    branch_t branch ;

    //FRR->f_orig = example_function  ;
    //FRR->f_new  = modified_function ;

    // allocate space for the stub to call the original function
    void* voidptr_BackupForOriginalFunction = malloc(DEFAULT_STUBSZ) ;
    if (!voidptr_BackupForOriginalFunction) // On malloc failure
    {
        free(voidptr_BackupForOriginalFunction);
        return 0;
    }

    // Prepare to write to the first 4 bytes of "original"
    MPROTECT_ERROR = mprotect(example_function, 4, PROT_READ|PROT_WRITE|PROT_EXEC); // unprotect first 4 bytes
    if (MPROTECT_ERROR) // on mprotect error
        goto ERROR;

    // Prepare to populate the stub and make it executable
    MPROTECT_ERROR = mprotect(voidptr_BackupForOriginalFunction, DEFAULT_STUBSZ, PROT_READ|PROT_WRITE|PROT_EXEC);
    if (MPROTECT_ERROR) // on mprotect error
        goto ERROR;

    memcpy( (void*) voidptr_BackupForOriginalFunction, (void*) example_function, DETOUR_LENGTH);

    // Create unconditional branch from "original" to "new"
    branch.OP = BRANCH_MOPCODE;
    branch.LI = (unsigned int) modified_function >> 2;
    branch.AA = 1 ;
    branch.LK = 0 ;

    memcpy( (void*) example_function, (void*) &branch, DETOUR_LENGTH);

    // Create unconditional branch from "stub" to "original"
    branch.LI = (unsigned int) (example_function + DETOUR_LENGTH) >> 2;

    memcpy( voidptr_BackupForOriginalFunction + DETOUR_LENGTH, (void*) &branch, DETOUR_LENGTH);

    // Must flush cache(s). For demonstration purposes, this suffices.
    msync(voidptr_BackupForOriginalFunction, PAGESIZE, MS_INVALIDATE);
     // int msync(void *start, size_t length, int flags);
    //
      //  MS_INVALIDATE asks to invalidate other mappings of the same file
     // (so that they can be updated with the fresh values just written).
    //
          // msync()  flushes  changes  made  to the in-core copy of a file that was
         //  mapped into memory using mmap(2) back to disk. To be more precise,
        //   the part of the file that corresponds to the memory area starting
       //    at start and having length length is updated.
      //
     //      Without  use  of  this call  there  is  no guarantee that changes
    //       are written back before munmap(2) is called.

     // On success,  zero is returned.
    //  On error, -1 is returned, and errno is set appropriately.
    return voidptr_BackupForOriginalFunction ;

ERROR: // on malloc error
    if (voidptr_BackupForOriginalFunction)
        free(voidptr_BackupForOriginalFunction) ;
    return 0;
}


int detour_remove(void* example_function, void* original_function, void* modified_function)
{
    int MPROTECT_ERROR;

    MPROTECT_ERROR = mprotect(example_function, DETOUR_LENGTH, PROT_READ | PROT_WRITE | PROT_EXEC);
    if (MPROTECT_ERROR)
        return -1;

    memcpy( (void*) example_function, original_function, DETOUR_LENGTH);

    if (original_function)
        free(original_function) ;

     // Perhaps use dcbf/icbf to flush cache(s). For demonstration purposes,
    // calling a random function suffices. I don't think this is foolproof.
    sync();

    return 0;
}


// EXAMPLE USAGE
int example_function(int i, char* s)
{
    int ret;
    char* m = s;
    if (!s)
        m = "(null)";

    printf("function()    : called as function(%d, %s).\n", i, m) ;
    ret = i + 1 ;
    printf("function()    : returning %d.\n", ret) ;

    return ret ;
}

int (*original_function)(int, char*) ;


int modified_function(int i, char *s)
{
    int intReturnValue = -1;
    char* m = s;
    if (!s)
        m = "(null)";

    printf("modified_function(): called as modified_function(%d, %s).\n", i, m);

    if (original_function)
    {
        printf("modified_function(): calling original_function(%d, %s).\n", i, m);
        intReturnValue = original_function(i, s);
        printf("modified_function(): original_function(%d, %s) returned %d.\n", i, m, intReturnValue);
    }
    else
    {
        printf("modified_function(): original_function missing.\n");
    }

    printf("modified_function(): returning %d.\n", intReturnValue);

    return intReturnValue;
}


int main(int argc, char* argv[])
{
    int   intReturnValue;
    int   arg_i = 2;
    char* arg_s = "Hello, World!";
    frr_data_t* FRR;

    printf("[Clean]\n");
    printf("main()        : calling example_function(%d, %s).\n", arg_i, arg_s);
    intReturnValue = example_function(arg_i, arg_s);
    printf("main()        : example_function(%d, %s) returned %d.\n", arg_i, arg_s, intReturnValue);

    original_function = InterceptFunction(example_function, 0, modified_function);
    if (!original_function)
    {
        fprintf(stderr, "main(): frr_install failed.\n");
        return 1;
    }

    printf("\n[Rerouting installed]\n");
    printf("main()        : calling example_function(%d, %s).\n", arg_i, arg_s);
    intReturnValue = example_function(arg_i, arg_s);
    printf("main()        : example_function(%d, %s) returned %d.\n",arg_i, arg_s, intReturnValue);

    intReturnValue = detour_remove(example_function, original_function, modified_function) ;
    if (intReturnValue != 0)
    {
        fprintf(stderr, "main(): frr_remove failed.\n");
        return 1;
    }

    printf("\n[Rerouting removed]\n");
    printf("main()        : calling example_function(%d, %s).\n", arg_i, arg_s);
    intReturnValue = example_function(arg_i, arg_s);
    printf("main()        : example_function(%d, %s) returned %d.\n", arg_i, arg_s, intReturnValue);

    return 0;
}

```

---

### Post by kavon89 on 2008-04-28
I have an iBook running a G3 processor and OS X. Link me to a compiler etc and I'll do it for ya.

---

### Post by WitchCraft on 2008-04-28
> **kavon89 said:**
> I have an iBook running a G3 processor and OS X. Link me to a compiler etc and I'll do it for ya.

You need gcc, the GNU C compiler. I think it ships with Xcode development tools.
You compile with: gcc detour.c -o detour
Then you start the program from command line with: ./detour

Needs OS X, however.

---

### Post by WitchCraft on 2008-04-30
bump.

---


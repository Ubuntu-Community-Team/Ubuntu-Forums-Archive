---
title: "[SOLVED] Value of a pointer to a multidimensional array?"
date: 2008-04-19
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-19
Question to the program below:

Basically I have a list of offsets for different games, stored in a multidimensional array.

Now I have such a list for the offsets in Linux, Windows and Mac, 

Then I want to determine the OS, and assign the right list to a pointer.
Now I made the list for Linux, and made the pointer, and assigned the pointer the array address.

Then I quickly wanted to test whether the result is right.
But it returns a different/incorrect value from the pointer... why? 
What am I doing wrong?



```

#include <iostream>

#define QUAKE3_ARENA    0
#define OPENARENA       1
#define URBAN_TERROR    2
#define TREMULOUS       3

#define VM_Create_ADDR             0
#define VM_Call_ADDR               1
#define VM_ArgPtr_ADDR             2
#define cl_ADDR                    3
#define R_GetModelByHandle_ADDR    4
#define Cvar_Set2_ADDR             5
#define Com_MD5File_ADDR           6


int main()
{
    unsigned long offsets_linux[][7] =
    {
        // VM_Create_ADDR, VM_Call_ADDR, VM_ArgPtr_ADDR,  CLIENT_ADDR, R_GetModelByHandle_ADDR, Cvar_Set2_ADDR, Com_MD5File_ADDR
        {             0x0,          0x0,            0x0,          0x0,                     0x0,            0x0,              0X0 },    // QUAKE3_ARENA
        {      0x080C95B4,   0x080C8C88,     0x080C8866,   0x08830360,              0x081677A0,     0x08085C1A,       0x080905E0 },   // OPENARENA
        {      0x080C8ABC,   0x080C8190,     0x080C7D6E,   0x087C9C60,              0x081675AC,     0x08084AE2,       0x0808F4E8 },  // URBAN_TERROR
        {      0x080C6468,   0x080C5B3C,     0x080C571A,   0x088292C0,              0x08163638,     0x0808575A,              0x0 }  // TREMULOUS
    };
    printf("Offset: 0x%08X\n", offsets_linux[URBAN_TERROR][Com_MD5File_ADDR]);

    unsigned long (*poffset)[4][7] ;

    poffset = &offsets_linux ;
    printf("Offset: 0x%08X\n", *poffset[URBAN_TERROR][Com_MD5File_ADDR]);

    return EXIT_SUCCESS ;
}

```

Edit:
Oh, never mind, I got it: 
It's operator precedence, this must be: (*poffset)[URBAN_TERROR][Com_MD5File_ADDR]);

---


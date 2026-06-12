---
title: "[SOLVED] Non-invertible pointer operation?"
date: 2008-04-10
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-10
Hi!

A brief math/pointer question concering the Quake3 virtual machine:

(Programming language is C/C++)
The following preprocessor define:
#define VMDATA(QVMoffset) (cgvm->dataBase + (QVMoffset & cgvm->dataMask))


This does the following:

Given the address of the dataBase, the dataMask, and the QVM offsets, it computes the native (=not virtual machine) memory address of a variable that is in the Quake virtual machine memory.

so basically if there is a struct in the virtual machine, 
e.g. the struct cg, of type cg_t

Then you can get the address of this variable from the virtual machine file, and declare it somewhere as QVM memory address.

e.g. #define QVM_CG_OFFSET 0x31DF64

Then you can get the cg struct from a running virtual machine via pointer:

cg_t* mycg = (cg_t*)  VMDATA(QVM_CG_OFFSET)

This works very well.

Now, when the virtual machine executes an outside function (e.g. foo), then it does this like this:
   foo(VMDATA(argument1), VMDATA(argument2), VMDATA(argument3), etc....)

where the arguments come from within the virtual machine address space, so the VM memory addresses need  to be converted to native memory addresses via the define VMDATA.


So if I instruct the virtual machine from outside to execute an exported function, like foo, i need to give to it the addresses of argument1, argument2, argument3 etc.)

The problem however is, because i call the virtual machine function with variable addresses from native address space, the arguments addresses are already native memory addresses, and when the VM runs VMDATA on the arguments, the function foo gets the wrong memory addresses...

So I want to invert the VMDATA macro, to compute my variable's native address to a virtual machine address, so that if the virtual machine executes the VMDATA macros, that it gets the right addresses...

Mathematically stated, we can describe the VMDATA macro as a function:

memory address =  cgvm->dataBase + (QVMoffset & cgvm->dataMask)

or in short notation:
QVM offset := x
native memory address := y
VMDATA:    y = cgvm->dataBase + ( x & cgvm->dataMask)

now i need to compute x from y...
so i treat it like a normal equation:
 y = cgvm->dataBase + ( x & cgvm->dataMask)

 y - cgvm->dataBase=   ( x & cgvm->dataMask)

 y - cgvm->dataBase =   x & cgvm->dataMask


Now i need the inverse operation for a bitwise AND...


I made myself a little example for this:
now my finding is, that if i have x and dataMask and dataBase:
1101010110111 = x
1111110000000 = cgvm->dataMask
then it follows that:
1101010000000 = y - cgvm->dataBase 
--------------

But if I have y and dataMask and dataBase:
1101010000000 = y - cgvm->dataBase 
1111110000000 = cgvm->dataMask
it follows that x could be 
1101010110111
but it could also be
1101010100000
or
1111110000100
or almost infinite possiblilies...

Is my conclusion right that this operation (unary &) is ambigious, meaning there is no way to conclusively invert the function VMDATA???

Or am I wrong and x can be a function of y? If yes, how?

---

### Post by WW on 2008-04-10
Yes, you are correct.  There are different values of QVMoffset that give the same value for VMDATA, so VMDATA is not invertible.

But I wonder why VMDATA works this way.  Perhaps there is only a limited range of values of QVMoffset that are actually used by the program; in this case there may be an inverse.  This sounds like a question for the Quake3 developers.

---

### Post by WitchCraft on 2008-04-10
I've done some further findings:

```

#include <iostream>

using namespace std;
/*
"parms"
"0x2ff54f40"
"cgvm->dataBase "
"771051744" // incorrect, conversion to unsigned long is incorrect
"cgvm->dataMask "
"33554431"
"myrefEnt "
"0x2e35a564"



0x2e35a564 = unknown + (0x2ff54f40 & 33554431)
native memory address = cgvm->dataBase + (QVMoffset & cgvm->dataMask)
VMDATA: y = cgvm->dataBase + ( x & cgvm->dataMask)
*/

int main()
{
	unsigned long QVMoffset = 0x2ff54f40    ;
	unsigned long dataBase  = 0x2c405624    ; // 0x2c405624 = 742413860 (and not 771051744)
	unsigned long dataMask  = 0x01ffffff    ; // 0x01ffffff = 33554431


	// 0x2ff54f40 = 00101111111101010100111101000000 = QVMoffset
	// 0x01ffffff = 00000001111111111111111111111111 = dataMask
	// 0x01F54F40 = 00000001111101010100111101000000 = result_unary_and



	unsigned long result_unary_and = QVMoffset & dataMask ;

	unsigned long native_memory_address = 0 ;


	printf("Result unary and = %d\n", result_unary_and);
	printf("Result unary and = 0x%08x\n", result_unary_and);

	std::cout << std::endl ;

	native_memory_address = dataBase + (QVMoffset & dataMask) ;

    printf("Native memory address = %d\n", native_memory_address);
    printf("Native memory address = 0x%08x\n", native_memory_address);

	std::cout << std::endl ;



    return EXIT_SUCCESS;
}


```

and 

```

typedef enum 
{
	h_high,
	h_low,
	h_dontcare
} ha_pref;


	dataLength = header->dataLength + header->litLength + header->bssLength;
	for ( i = 0 ; dataLength > ( 1 << i ) ; i++ ) 
        {}
	dataLength = 1 << i;

vm->dataBase = Hunk_Alloc( dataLength, h_high );
vm->dataMask = dataLength - 1;

```


So because dataMask is 00000001111111111111111111111111 
it looks like the first 7 bits get blanked, while the rest stays 'AS IS'


This looks like once i subtract cgvm->dataBase  from the native address, i can have anything in the first 7 bits of the qvm address, but the 25 remaining bits must be correct.

Is it correct when I deduce from this, that in order for this to work,  all the VM data is located at a higher memory address than any native data... ?

If that's correct, then it follows that i only have to subtract cgvm->dataBase from the native address, in order to get a QVM address that retranslates to the correct native address...

yep using:

unsigned long VMDATA(unsigned long QVMoffset)
{
	return dataBase + (QVMoffset & dataMask) ;
}

unsigned long ANTI_VMDATA(unsigned long NativeAddress)
{
	return (NativeAddress - dataBase) ;
}


then 
printf("Native address = 0x%08x\n", VMDATA(ANTI_VMDATA(0x2e35a564)));


returns 0x2e35a564 ;-)


*QVM got 0wn3d*

---


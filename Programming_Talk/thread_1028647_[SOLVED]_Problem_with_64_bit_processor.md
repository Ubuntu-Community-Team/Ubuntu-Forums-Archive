---
title: "[SOLVED] Problem with 64 bit processor"
date: 2009-01-02
forum: Programming Talk
---

### Post by WitchCraft on 2009-01-02
Hi, question:

The bellow program overwrites (in RAM) the function SayHello with modified_SayHello, and stores the original SayHello function (respectively a stub to it) in original_SayHello.

It works excellently on a IA-32 processor.

But if I compile & run it on a AMD-64 processor with the -m32 option, it segfaults when calling original_SayHello();....
And when I compile & run it without -m32, it doesn't work at all... 

Why? It basically should, i don't understand what is wrong...
Anybody has a better idea for debugging this than having to make a memory dump by memcopying the entire address space in a hexdump?
```


#include <iostream>
#include <cstdlib>
#include <cstring>
#include <unistd.h>
#include <sys/mman.h>

	unsigned long uslngPageSize = 0    ;
	unsigned long uslngPageMask = 0    ;
	
	#define unprotect(addr,len)  (mprotect(addr,len,PROT_READ|PROT_WRITE|PROT_EXEC))
	#define GETPAGESIZE()         sysconf (_SC_PAGE_SIZE)


	#define JMP_OPCODE 0xE9
	#define OPCODE_LENGTH 1
	#define DATATYPE_ADDRESS unsigned long
	#define ADDRESS_LENGTH (sizeof(DATATYPE_ADDRESS))
	#define MIN_REQUIRED_FOR_DETOUR (OPCODE_LENGTH + ADDRESS_LENGTH)
	#define INT_DETOUR_FACTOR 1
	#define OPCODE_NOT_DEFINED 0



// offset[ENGINE][FUNCTION_NAME] ;
// detourlength[ENGINE][FUNCTION_NAME]

#define INTERCEPT(FUNCTION_NAME) \
	original_##FUNCTION_NAME = TemplateFuncInterceptFunction( \
	                                                         original_##FUNCTION_NAME, \
	                                                         reinterpret_cast<unsigned long> (&FUNCTION_NAME), \
															 reinterpret_cast<unsigned long> (&modified_##FUNCTION_NAME), \
	                                                         static_cast<unsigned long> (FUNCTION_NAME##_COPY) \
	                                                        )


#define NATURALIZE(FUNCTION_NAME) \
    Naturalized_##FUNCTION_NAME = FuncConvertAddress(Naturalized_##FUNCTION_NAME, &FUNCTION_NAME)

template <class DataType>
DataType FuncConvertAddress(const DataType dt_FunctionPointer, unsigned long uslng_FunctionAddress)
{
	return reinterpret_cast<DataType> (uslng_FunctionAddress) ;
}




void* FuncGetPage(const unsigned long &uslngVirtualMemoryAddress)
{
	return reinterpret_cast<void*> (uslngVirtualMemoryAddress & uslngPageMask) ;
}


void* InterceptFunction (void* voidptr_AddressOfDetouredFunction, unsigned long uslng_CopyLength, void* voidptr_AddressOfDetourFunction)
{
	printf("Entering interception subroutine\n");
	DATATYPE_ADDRESS Relocation ;
	//printf("copy length: %ld\n", uslng_CopyLength);
	//printf("MIN_REQUIRED_FOR_DETOUR : %d\n", MIN_REQUIRED_FOR_DETOUR );
	void* voidptr_BackupForOriginalFunction = malloc( uslng_CopyLength + MIN_REQUIRED_FOR_DETOUR ) ;
	//printf("Sizeof Backuppointer %ld\n", sizeof(voidptr_BackupForOriginalFunction));
	//printf("Sizeof AddrDetouredFunction %d\n", sizeof(voidptr_AddressOfDetouredFunction));

	memcpy( voidptr_BackupForOriginalFunction, voidptr_AddressOfDetouredFunction, uslng_CopyLength) ;

	if (OPCODE_NOT_DEFINED)
	{
		printf("Error: OP-Code not defined\n.") ;
		exit(EXIT_FAILURE) ;
	}

	memset( reinterpret_cast<void*> (reinterpret_cast<unsigned long> (voidptr_BackupForOriginalFunction) + uslng_CopyLength),
	        JMP_OPCODE, OPCODE_LENGTH ) ;
			

	
	Relocation = static_cast<DATATYPE_ADDRESS> (reinterpret_cast<unsigned long> (voidptr_AddressOfDetouredFunction)
		          - (reinterpret_cast<unsigned long> (voidptr_BackupForOriginalFunction)
				  + MIN_REQUIRED_FOR_DETOUR)) ;
  

	memcpy( reinterpret_cast<void*> ( reinterpret_cast<unsigned long> (voidptr_BackupForOriginalFunction)
		     + uslng_CopyLength + OPCODE_LENGTH), &Relocation, ADDRESS_LENGTH) ;



	unprotect(FuncGetPage(reinterpret_cast <unsigned long> (voidptr_AddressOfDetouredFunction)),uslngPageSize) ;

	memset(voidptr_AddressOfDetouredFunction, JMP_OPCODE, OPCODE_LENGTH) ;

	Relocation = static_cast<DATATYPE_ADDRESS> ( reinterpret_cast<unsigned long> (voidptr_AddressOfDetourFunction)
		          - (reinterpret_cast<unsigned long> (voidptr_AddressOfDetouredFunction)
				  + MIN_REQUIRED_FOR_DETOUR)) ;

	memcpy( reinterpret_cast<void*> (reinterpret_cast<unsigned long> (voidptr_AddressOfDetouredFunction)
		     + OPCODE_LENGTH), &Relocation, ADDRESS_LENGTH) ;
	printf("Exiting interception subroutine\n");
	return voidptr_BackupForOriginalFunction ;
}


// C++ is typesafe, they said...
// I say: Yes, but at which price ?
template <class DataType>
DataType TemplateFuncInterceptFunction( DataType dt_Original_Function, unsigned long uslng_FunctionAddress,
                                        unsigned long uslng_modified_FunctionName, unsigned long uslng_DetourLength)
{
	return reinterpret_cast<DataType>
			( reinterpret_cast<unsigned long>
				( InterceptFunction( reinterpret_cast<void*> (uslng_FunctionAddress),
									 uslng_DetourLength,
									 reinterpret_cast<void*> (uslng_modified_FunctionName)
				                   )
				)
			);
}

void SayHello()
{
	printf("Hello World\n");
}

void modified_SayHello()
{
	printf("**** World\n");
}

void (*original_SayHello)();
//#define SayHello_COPY 9
#define SayHello_COPY 6
int main()
{
	system("reset");	
	uslngPageSize = sysconf(_SC_PAGESIZE)    ;
	uslngPageMask = ( ~(uslngPageSize - 1) ) ;
	printf("PageSize: %ld\n", uslngPageSize);
	printf("PageMask: 0x%08lX\n", uslngPageMask);
	SayHello();
	printf("Now detouring!!!\n");
	//original_SayHello= &SayHello;
	INTERCEPT(SayHello);
	printf("Detoured:\n");
	SayHello();
	SayHello();
	SayHello();
	printf("Backup:\n");
	printf("jumping\n");	
	original_SayHello();
	return 0;	
}

```

---

### Post by dwhitney67 on 2009-01-02
The application also segfaults on a 32-bit system:
```

PageSize: 4096
PageMask: 0xFFFFF000
Hello World
Now detouring!!!
Entering interception subroutine
Exiting interception subroutine
Detoured:
**** World
**** World
**** World
Backup:
jumping
Segmentation fault

```
Maybe you should consider restoring (i.e. doing the opposite) the steps taken in INTERCEPT().

---

### Post by WitchCraft on 2009-01-02
> **dwhitney67 said:**
> The application also segfaults on a 32-bit system:
```

PageSize: 4096
PageMask: 0xFFFFF000
Hello World
Now detouring!!!
Entering interception subroutine
Exiting interception subroutine
Detoured:
**** World
**** World
**** World
Backup:
jumping
Segmentation fault

```
Maybe you should consider restoring (i.e. doing the opposite) the steps taken in INTERCEPT().

it doesn't segfault on my 32 bit system.
Maybe your compiler is different, so you need to adjust 

#define SayHello_COPY 6

to another number

disassemble the function SayHello,
and the first place where you see 
"<_Z8SayHellov+[COLOR="Red"]X[/COLOR]>:" with [COLOR="Red"]X[/COLOR] >= 5 is SayHello_COPY

in my case
0x080487ab <_Z8SayHellov+[COLOR="Red"]6[/COLOR]>:
so SayHello_COPY is [COLOR="Red"]6[/COLOR] on my compiler. 
This is essential.
Then the code should work for you, too.

```

root@toshiba:/media/disk-1# gdb detour
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(gdb) disas SayHello
Dump of assembler code for function _Z8SayHellov:
0x080487a5 <_Z8SayHellov+0>:	push   %ebp
0x080487a6 <_Z8SayHellov+1>:	mov    %esp,%ebp
0x080487a8 <_Z8SayHellov+3>:	sub    $0x8,%esp
0x080487ab <_Z8SayHellov+6>:	movl   $0x8048aab,(%esp)
0x080487b2 <_Z8SayHellov+13>:	call   0x8048644 <puts@plt>
0x080487b7 <_Z8SayHellov+18>:	leave  
0x080487b8 <_Z8SayHellov+19>:	ret    
End of assembler dump.
(gdb) 

```

---

### Post by dwhitney67 on 2009-01-02
Still no joy.  I am using the original code you posted; here's the gdb output after compiling the code.
```

gdb a.out
GNU gdb Fedora (6.8-23.fc9)
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i386-redhat-linux-gnu"...
(gdb) disas SayHello
Dump of assembler code for function _Z8SayHellov:
0x08048745 <_Z8SayHellov+0>:	push   %ebp
0x08048746 <_Z8SayHellov+1>:	mov    %esp,%ebp
0x08048748 <_Z8SayHellov+3>:	sub    $0x8,%esp
0x0804874b <_Z8SayHellov+6>:	movl   $0x8048a4f,(%esp)
0x08048752 <_Z8SayHellov+13>:	call   0x80485f0 <puts@plt>
0x08048757 <_Z8SayHellov+18>:	leave  
0x08048758 <_Z8SayHellov+19>:	ret    
End of assembler dump.

```
I am using gcc (GCC) 4.3.0 20080428 (Red Hat 4.3.0-8), courtesy of Fedora 9.

---

### Post by WitchCraft on 2009-01-02
> **dwhitney67 said:**
> Still no joy.  I am using the original code you posted; here's the gdb output after compiling the code.
```

gdb a.out
GNU gdb Fedora (6.8-23.fc9)
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i386-redhat-linux-gnu"...
(gdb) disas SayHello
Dump of assembler code for function _Z8SayHellov:
0x08048745 <_Z8SayHellov+0>:	push   %ebp
0x08048746 <_Z8SayHellov+1>:	mov    %esp,%ebp
0x08048748 <_Z8SayHellov+3>:	sub    $0x8,%esp
0x0804874b <_Z8SayHellov+6>:	movl   $0x8048a4f,(%esp)
0x08048752 <_Z8SayHellov+13>:	call   0x80485f0 <puts@plt>
0x08048757 <_Z8SayHellov+18>:	leave  
0x08048758 <_Z8SayHellov+19>:	ret    
End of assembler dump.

```
I am using gcc (GCC) 4.3.0 20080428 (Red Hat 4.3.0-8), courtesy of Fedora 9.

interesting. are you sure you have a pure 32 bit system, and not a 32 bit system on a 64 bit processor?

i'm using
g++ (Debian 4.3.2-1) 4.3.2

i think it might be a problem with permissions for reprotecting the memory

---

### Post by dwhitney67 on 2009-01-02
> **WitchCraft said:**
> interesting. are you sure you have a pure 32 bit system, and not a 32 bit system on a 64 bit processor?

i'm using
g++ (Debian 4.3.2-1) 4.3.2

Ha!  I'm quite sure.  I have a Compaq Presario X1030US, sporting a 1.4GHz Intel Pentium M processor.  I had this laptop since Feb 2004.

---

### Post by WitchCraft on 2009-01-02
> **dwhitney67 said:**
> Ha!  I'm quite sure.  I have a Compaq Presario X1030US, sporting a 1.4GHz Intel Pentium M processor.  I had this laptop since Feb 2004.

Well, then I believe you !

I think i found the error.

Add a
```

unprotect(FuncGetPage(reinterpret_cast <unsigned long> (voidptr_BackupForOriginalFunction)),uslngPageSize) ;	

```

in front of
```

	printf("Exiting interception subroutine\n");

```

now it works on my x64 with -m32. Yay!

Edit: Wow, now it works even without -m32

DATATYPE_ADDRESS must be changed to int!

---

### Post by WitchCraft on 2009-01-02
And this is how to dump the process memory, FMI:

```

#include <iostream>
#include <cstdlib>

#include <unistd.h>
#include <fcntl.h>
#include <sys/mman.h>

int main(int argc, char *argv[])
{
    int i;
    volatile unsigned char *cp;
    int fd;
    volatile void *v;
    off_t nvram = 0xfff00000;
    // avoid linux mmap bug
    size_t length = 0x100000 ; // - 0x1000

    if (argc > 1)
        nvram = (strtol(argv[1], 0, 0)) << 16;

    if (argc > 2)
        length = (strtol(argv[2], 0, 0)) ;

    if ((fd = open("/dev/mem",O_RDWR)) != -1)
    {
        v = mmap(0, length, PROT_READ | PROT_WRITE, MAP_SHARED,fd,nvram);
        fprintf(stderr, "mmap returns %p\n", v);

        if ( (long) v == -1)
        {
            perror("mmap");
            exit(EXIT_FAILURE);
        }
    }
    else
    {
        perror("open /dev/mem");
        exit(EXIT_FAILURE);
    }

    write(1, (const void*) v, length);
    return EXIT_SUCCESS ;
}

```

and for Windows:
[http://www.codeproject.com/KB/threads/MDumpAll.aspx](http://www.codeproject.com/KB/threads/MDumpAll.aspx)

---

### Post by WitchCraft on 2009-02-11
Revised edition, now working and including unpatch and windoze functions

```


#if ( defined (_WIN32) || defined (_WIN64) )
    #define WIN32_LEAN_AND_MEAN
    #define WIN64_LEAN_AND_MEAN
    #include <windows.h>
    
    #define unprotect(addr,len) (VirtualProtect(addr,len,PAGE_EXECUTE_READWRITE,&oldprot))
    #define GETPAGESIZE()        getpagesize()

    DWORD oldprot ;

    unsigned long getpagesize (void)
    {
        static long g_pagesize = 0 ;
        if (! g_pagesize)
        {
            SYSTEM_INFO system_info ;
            GetSystemInfo(&system_info) ;
            g_pagesize = system_info.dwPageSize ;
        }
        return (unsigned long) g_pagesize ;
    }
    
    #define CLEAR_SCREEN "cls"

#else // LINUX / UNIX / OS X
    #include <unistd.h>
    #include <sys/mman.h>

    #define unprotect(addr,len)  (mprotect(addr,len,PROT_READ|PROT_WRITE|PROT_EXEC))
    #define GETPAGESIZE()         sysconf (_SC_PAGE_SIZE)
    #define CLEAR_SCREEN "reset"
#endif


#include <iostream>
#include <cstdlib>
#include <cstring>


    unsigned long uslngPageSize = 0    ;
    unsigned long uslngPageMask = 0    ;








    #define JMP_OPCODE 0xE9
    #define OPCODE_LENGTH 1
    #define DATATYPE_ADDRESS int
    #define ADDRESS_LENGTH (sizeof(DATATYPE_ADDRESS))
    #define MIN_REQUIRED_FOR_DETOUR (OPCODE_LENGTH + ADDRESS_LENGTH)
    #define INT_DETOUR_FACTOR 1
    #define OPCODE_NOT_DEFINED 0



// offset[ENGINE][FUNCTION_NAME] ;
// detourlength[ENGINE][FUNCTION_NAME]

#define HOTPATCH(FUNCTION_NAME) \
    original_##FUNCTION_NAME = TemplateFuncInterceptFunction( \
                                                             original_##FUNCTION_NAME, \
                                                             reinterpret_cast<unsigned long> (&FUNCTION_NAME), \
                                                             reinterpret_cast<unsigned long> (&modified_##FUNCTION_NAME), \
                                                             static_cast<unsigned long> (FUNCTION_NAME##_COPY) \
                                                            )

#define UNPATCH(FUNCTION_NAME) \
    unpatchfunc( reinterpret_cast<void*>(reinterpret_cast<unsigned long>(&FUNCTION_NAME)), reinterpret_cast<unsigned char*> (reinterpret_cast<unsigned long>( original_##FUNCTION_NAME)), static_cast<unsigned long> (FUNCTION_NAME##_COPY))



#define NATURALIZE(FUNCTION_NAME) \
    Naturalized_##FUNCTION_NAME = FuncConvertAddress(Naturalized_##FUNCTION_NAME, &FUNCTION_NAME)


template <class DataType>
DataType FuncConvertAddress(const DataType dt_FunctionPointer, unsigned long uslng_FunctionAddress)
{
    return reinterpret_cast<DataType> (uslng_FunctionAddress) ;
}




void* FuncGetPage(const unsigned long &uslngVirtualMemoryAddress)
{
    return reinterpret_cast<void*> (uslngVirtualMemoryAddress & uslngPageMask) ;
}


void* InterceptFunction (void* voidptr_AddressOfDetouredFunction, unsigned long uslng_CopyLength, void* voidptr_AddressOfDetourFunction)
{
    DATATYPE_ADDRESS Relocation ;
    //printf("copy length: %ld\n", uslng_CopyLength);
    //printf("MIN_REQUIRED_FOR_DETOUR : %d\n", MIN_REQUIRED_FOR_DETOUR );
    void* voidptr_BackupForOriginalFunction = malloc( uslng_CopyLength + MIN_REQUIRED_FOR_DETOUR ) ;
    //printf("Sizeof Backuppointer %ld\n", sizeof(voidptr_BackupForOriginalFunction));
    //printf("Sizeof AddrDetouredFunction %d\n", sizeof(voidptr_AddressOfDetouredFunction));

    memcpy( voidptr_BackupForOriginalFunction, voidptr_AddressOfDetouredFunction, uslng_CopyLength) ;

    if (OPCODE_NOT_DEFINED)
    {
        printf("Error: OP-Code not defined\n.") ;
        exit(EXIT_FAILURE) ;
    }

    memset( reinterpret_cast<void*> (reinterpret_cast<unsigned long> (voidptr_BackupForOriginalFunction) + uslng_CopyLength),
            JMP_OPCODE, OPCODE_LENGTH ) ;



    Relocation = static_cast<DATATYPE_ADDRESS> (reinterpret_cast<unsigned long> (voidptr_AddressOfDetouredFunction)
                  - (reinterpret_cast<unsigned long> (voidptr_BackupForOriginalFunction)
                  + MIN_REQUIRED_FOR_DETOUR)) ;


    memcpy( reinterpret_cast<void*> ( reinterpret_cast<unsigned long> (voidptr_BackupForOriginalFunction)
             + uslng_CopyLength + OPCODE_LENGTH), &Relocation, ADDRESS_LENGTH) ;



    unprotect(FuncGetPage(reinterpret_cast <unsigned long> (voidptr_AddressOfDetouredFunction)),uslngPageSize) ;

    memset(voidptr_AddressOfDetouredFunction, JMP_OPCODE, OPCODE_LENGTH) ;

    Relocation = static_cast<DATATYPE_ADDRESS> ( reinterpret_cast<unsigned long> (voidptr_AddressOfDetourFunction)
                  - (reinterpret_cast<unsigned long> (voidptr_AddressOfDetouredFunction)
                  + MIN_REQUIRED_FOR_DETOUR)) ;

    memcpy( reinterpret_cast<void*> (reinterpret_cast<unsigned long> (voidptr_AddressOfDetouredFunction)
             + OPCODE_LENGTH), &Relocation, ADDRESS_LENGTH) ;
    unprotect(FuncGetPage(reinterpret_cast <unsigned long> (voidptr_BackupForOriginalFunction)),uslngPageSize) ;

    return voidptr_BackupForOriginalFunction ;
}


// C++ is typesafe, they said...
// I say: Yes, but at which price ?
template <class DataType>
DataType TemplateFuncInterceptFunction( DataType dt_Original_Function, unsigned long uslng_FunctionAddress,
                                        unsigned long uslng_modified_FunctionName, unsigned long uslng_DetourLength)
{
    return reinterpret_cast<DataType>
            ( reinterpret_cast<unsigned long>
                ( InterceptFunction( reinterpret_cast<void*> (uslng_FunctionAddress),
                                     uslng_DetourLength,
                                     reinterpret_cast<void*> (uslng_modified_FunctionName)
                                   )
                )
            );
}


void SayHello()
{
    printf("Hello World\n");
}


void modified_SayHello()
{
    printf("**** World\n");
}

void (*original_SayHello)();
//#define SayHello_COPY 9
#define SayHello_COPY 6






void unpatchfunc(void* patched_function, unsigned char* original_function, unsigned long uslng_DetourLength)
{
    //DWORD dw_OldProtect;
    //VirtualProtect(patched_function, uslng_DetourLength, PAGE_EXECUTE_READWRITE, &dw_OldProtect);
    unprotect(FuncGetPage(reinterpret_cast<unsigned long>(patched_function) ), uslngPageSize) ;
    unsigned int intIndex;
    for( intIndex = 0; intIndex < uslng_DetourLength; ++intIndex)
        *( (unsigned char*) patched_function + intIndex) = *(original_function + intIndex) ;

    //VirtualProtect(patched_function, uslng_DetourLength, dw_OldProtect, &dw_OldProtect);
    unprotect(FuncGetPage(reinterpret_cast<unsigned long>(patched_function) ), uslngPageSize) ;
    if(original_function!=NULL)
        free( (void*) original_function) ;
}


int main()
{
    system( CLEAR_SCREEN ) ;
    uslngPageSize = GETPAGESIZE() ;
    uslngPageMask = ( ~(uslngPageSize - 1) ) ;
    printf("PageSize: %ld\n", uslngPageSize) ;
    printf("PageMask: 0x%08lX\n", uslngPageMask) ;
    SayHello() ;
    printf("Hotpatching now!!!\n") ;
    HOTPATCH(SayHello) ;
    printf("Hotpatched:\n") ;
    SayHello() ;
    printf("Backup:\n") ;
    original_SayHello() ;
    printf("Unpatching now\n") ;
    UNPATCH(SayHello);
    // expands to: unpatchfunc( (void*) SayHello, (unsigned char*) original_SayHello, (int) SayHello_COPY) ;
    printf("Unpatched:\n") ;
    SayHello() ;
    printf("EXIT_SUCCESS\n") ;
    return EXIT_SUCCESS ;
}

```

---

### Post by WitchCraft on 2009-03-01
New problem arose:
It will crash if you compile with -fPIC...

It crashes when you call original_SayHello

I don't know why, anybody can help ?
I'd suppose it is because EIP is in one of the registers, and that creates a problem with jmp rel32 - but then it wouldn't run modified_SayHello as well, or am I wrong?

---


---
title: "glibc detected *** free(): invalid next size (normal)"
date: 2006-10-31
forum: Programming Talk
---

### Post by mesh2005 on 2006-10-31
I have an old c program and it is working on Redhat 7.2 I tried to run it on my ubuntu machine but I got the following error
glibc detected *** free(): invalid next size (normal)
How I can fix it?
Thank you

---

### Post by toojays on 2006-10-31
Do you have the source for this program? I suggest you compile it with debugging turned on, then run it under valgrind to find out where the memory error is coming from.

A workaround is to run the program with MALLOC_CHECK_=1 set in your environment. See [https://www.redhat.com/archives/fedora-list/2005-January/msg01918.html](https://www.redhat.com/archives/fedora-list/2005-January/msg01918.html)

---

### Post by mesh2005 on 2006-10-31
Thank you for your reply. Could you please tell me how can I turn on the debugging using GCC?

---

### Post by MWAAAHAAA on 2006-10-31
Debugging is enabled by passing the -g option to gcc.

The error message about free() stems from the fact that you are trying to delete an invalid pointer.

---

### Post by mesh2005 on 2006-11-01
I removed the free () but still get the same error
I tried to use gdb:
Program received signal SIGABRT, Aborted.
0xffffe410 in __kernel_vsyscall ()


Can anyone help?

---

### Post by amo-ej1 on 2006-11-01
what does a *bt* in gdb give you ?

---

### Post by mesh2005 on 2006-11-02
bt gave me :
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7eb39b1 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eb52c9 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7ee76ea in __fsetlocking () from /lib/tls/i686/cmov/libc.so.6
#4  0xb7eedf54 in malloc_trim () from /lib/tls/i686/cmov/libc.so.6
#5  0xb7eee2ca in free () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7ede646 in fclose () from /lib/tls/i686/cmov/libc.so.6
#7  0x080487d8 in get_chars (file=0x804a008, page_offset=512) at decode.c:108
#8  0x0804856e in main (argc=2, argv=0xbfbdc884) at decode.c:38

---

### Post by amo-ej1 on 2006-11-02
```

#6 0xb7ede646 in fclose () from /lib/tls/i686/cmov/libc.so.6
#7 0x080487d8 in get_chars (file=0x804a008, page_offset=512) at decode.c:108

```

What do you do at line 108 in decode.c ? Isn't there something wrong with the filehandle you're trying to close ?

---

### Post by mesh2005 on 2006-11-07
the same program is working on Redhat 7.2 and Debian

---

### Post by Aelfric5578 on 2007-11-26
I can't speak about the original poster's problem specifically, not seeing his code, but I've noticed in general that I've been having memory allocation issues on my Ubuntu machine that disappear when I compile and run the same code on another platform.  In my case, the other platform is NetBSD.  

I am still a Linux amateur and I'm very much a beginner in C programming, mostly teaching myself for a class I'm currently taking.  I've found myself wasting precious homework time trying to fix bugs that disappear without me doing anything when I bring over the source code to the BSD machines.  Is there any reason that Ubunttu would be treating memory allocation differently than other distros?  Is there anyway that I can avoid these seemingly unimportant but cripling errors?  Or am I missing something due to my inexperience?

---

### Post by facingnoob on 2008-11-26
after having the same problem, and searching in the inet for answers i finally solved it for me.
if you allocate memory with calloc (in my case) 
and then move with the pointer arround 

for example with for(n=10;n>=0;n--) printf("%d",pointer[n]) 

last n will be -1 !! this makes pointer[-1] which is the memory of any other programm.
this sort of seems to be an problem with ubuntu only (i dont know why) 

thus solution is setting n=0 bevor free(pointer) ;
here my full example: (it reades n numbers from console, and gives them out again)
i hoped i helped you all out of misery :=)

#include <stdio.h>
#include <stdlib.h>
int main(void)
{
	int *pointer, a[1]={0},i=0,n=0;
	//pointer=a;
	scanf("%d",&n);
	pointer=(int*) calloc(n-=1,sizeof(int));
	if(NULL==pointer) {printf("out of memory");exit(1);}
	for (i=0;i<=n;i++)
	{
		scanf("%d",&pointer[i]);
	}
	for (;n>=0;n--)
	{
		printf("%d\t",pointer[n]);
	}
	n=0; //reset pointer to save position 
	free(pointer);
	return 0;
}

---

### Post by facingnoob on 2008-11-26
i just noticed how strange this is as n=0 shouldn't change the pointer without pointer[n] 
and strange for another reason as &pointer shouldn't be moved with pointer[n]

sorry thought it worked, but it was only random luck, don't have a clue now...

---

### Post by monkeyking on 2008-11-26
> **Aelfric5578 said:**
> I can't speak about the original poster's problem specifically, not seeing his code, but I've noticed in general that I've been having memory allocation issues on my Ubuntu machine that disappear when I compile and run the same code on another platform.  In my case, the other platform is NetBSD.  

I am still a Linux amateur and I'm very much a beginner in C programming, mostly teaching myself for a class I'm currently taking.  I've found myself wasting precious homework time trying to fix bugs that disappear without me doing anything when I bring over the source code to the BSD machines.  Is there any reason that Ubunttu would be treating memory allocation differently than other distros?  Is there anyway that I can avoid these seemingly unimportant but cripling errors?  Or am I missing something due to my inexperience?

Just because it doesn't crash on another box doesn't mean that it works on the other box.

I'd rather have a nasty crash, than a silent error.

The newer versions of glibc, should be better at announcing faulty programs than the older ones.

---

### Post by arunasr on 2009-06-08
You are allocating 1 less int than you need:

pointer=(int*) calloc(n-=1,sizeof(int));

n-=1 will first decrement the value of n, then pass the resulting value to calloc. 

Say, you want 10 elements, indexed 0 to 9. Your code will only have 9 allocated, 0 to 8. The last scanf will overflow the allocated buffer.

Some OS'es will align the allocated memory to 16 or 32 boundary for efficiency reasons, so buffer overflow does not actually occur. I guess the new gcc agressively pursues potential buffer overflows, killing the program when detected.

---

### Post by bretzel on 2010-04-15
WOW! 4 days hunting ( even with valgrind ) for this exact crash ( or leak 
detection from libc shield :: abort ). I was actually allocating the 
exact amount of bytes I needed and adding +1 for safety as I've always done 
since 1998 ... 

The duty is: Serialize header block data + strings as arguements into a char array buffer.
[LIST]
 set (12) bytes for the size of the header block { 3 uint's } +
[/LIST]
[LIST]
 iterate through std::vector<std::string> as arg - count_total of arg.length()'s
[/LIST] 
[LIST]
 Total = (12) + count_total 
[/LIST]
Then, 

```

const char* arCommand::Serialize()
{
    int nArgs  = _Arguments.size();
    int ln;
    // arCommand::_pStream is the char array buffer for the serialized command
    if(_pStream) delete [] _pStream;
    uint accLen= sizeof(arProcotolHeader);
    uint ArgLength = 0;
    _Header.num_args = nArgs;
    // pCChar const char pointer to get each argument string
    const char* pCChar;
    char* pWrite;
    // Compute total length from the arguements
    for( int X=0; X < nArgs; X++) ArgLength += _Arguments[X].length();
    // Add nArgs zeros to terminate each param...
    [COLOR="DarkGreen"]_Header.args_data_length = ArgLength + nArgs*3;[/COLOR] // Works
    accLen += _Header.args_data_length;
    _pStream = new char[_Header.args_data_length];
    std::cerr << _Header.args_data_length << " bytes allocated to internal buffer\n";
    // Char pointer to the header data
    pCChar = HeaderData();
    pWrite = _pStream;
    std::cerr << "Start serializing : the header:\n";
    //start serializing 1rst: the header
    for(int X = 0; X < sizeof(arProcotolHeader); X++) *pWrite++ = *pCChar++;
    std::cerr << "serializing the header: Done: " <<  pWrite-_pStream  << " bytes \n";
    // then iterate the arguments
    std::cerr << "serializing the arguments: " <<  _Header.num_args << " arguments, " << _Header.args_data_length << " bytes \n";
    for(int X = 0; X < nArgs; X++){
        pCChar = _Arguments[X].c_str();
        int L = strlen(pCChar);
        std::cerr << " Serializing Arg:" << X << "=[" << pCChar << "] length:" << strlen(pCChar) << " bytes\n";
        for(int x = 0; x < L; x++){
            *pWrite = *pCChar;
            //std::cerr<< "[" << *_position << "]::[" << *pCChar << "]   ";
            ++pWrite;
            ++pCChar;
        }
        // Add zero to terminate the argument string.
        *pWrite++ = 0;
        std::cerr << " pWrite is at:" << pWrite-_pStream << "\n";
    }
    
    _thisLength = pWrite - _pStream;
    _position  = _pStream;
    std::cerr << " TEsting dump serialised buffer:(_pStream)\n";
    for(int x = 0; x<_thisLength; x++){
        std::cerr << "[" << (int)*(_position) << "]";
        ++_position;
    }
    std::cerr << "\n\n\n\n\n";
    _position = 0;
    return _pStream;
}

```

Thus, Computing the size is normaly not hard to do, I was so confident that I was correctly allocating the right amount of bytes...Thanks to this forum and topic I 've fixed the problem. Hopefully this fixed computation of the size will be ok for other plateforms than Ubuntu ( or g++ versions ).

---


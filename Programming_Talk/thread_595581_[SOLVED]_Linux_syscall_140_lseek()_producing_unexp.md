---
title: "[SOLVED] Linux syscall 140 lseek() producing unexpected output"
date: 2007-10-28
forum: Programming Talk
---

### Post by Carl Hamlin on 2007-10-28
Here is the code:

```

section .data

	testd	db	'Generic Text'
	testsz	equ	$ - testd

section .text
global	_start

_start:

	pop	ebx		;	ebx - argc
	pop	ebx		;	ebx - argv
	pop	ebx		;	ebx - filename to write to
	
	mov	eax, 8		;	eax - syscall_creat
	mov	ecx, 00664Q	;	ecx - read/write
	int	80h		;	syscall_creat
	
	mov	eax, 140	;	eax - syscall_lseek
	sub	ecx, ecx	;	ecx - offset 0
	mov	edx, 2		;	edx - SEEK_END - seek to end of file and apply no offset
	int	80h		;	syscall_lseek
	
	mov	eax, 4		;	eax - syscall_write
	mov	ecx, testd	;	ecx - pointer to data to be written
	mov	edx, testsz	;	edx - number of bytes to be written
	int	80h		;	syscall_write
	
	mov	eax, 1		;	eax - syscall_exit
	sub	ebx, ebx	;	ebx - errorcode 0
	int	80h		;	syscall_exit

```

In the wake of my recent debugger issues, I have determined that at least one of the issues I was having with the code I was attempting to debug has to do with the lseek syscall.

The above code is *supposed* to write 'Generic Text' to a file specified on the command line, appending the text to the end of the file.

Except it doesn't. All it does is create the file.

When I remove the call to lseek, then it writes the text, but of course doesn't append it to the end of the file and ends up overwriting whatever was already there.

The bulk of my experience is in writing assembly language for embedded platforms. I'm trying to get a grip on the Linux syscall system.

What am I doing wrong here?

I've reviewed what precious little documentation there is on this topic and the only thing I can think of is that I'm using the calling convention for 'lseek()', and SHOULD be using 'llseek()'.

If that is the case, then can someone please tell me how to populate the esi and edi registers?

---

### Post by Carl Hamlin on 2007-10-28
OK, hold the phone - I'm looking at the code again and I can already see an elementary error that might explain a few things.

---

### Post by Carl Hamlin on 2007-10-28
Well, that'll teach me to post without the moron filter turned on. Never mind - I think I've got this one covered.

Sheesh.

As many of you have likely intuited, I wasn't juggling the file descriptor quite right.

---

### Post by Carl Hamlin on 2007-10-28
OK. Back to the original question:

From Randall Hyde's documentation on Linux syscalls:

```

3.53       llseek
        // llseek - 64-bit version of lseek.
        procedure linux.llseek
        (
                    fd:dword;
                    offset_high:dword;
                    offset_low:dword;
             var theResult:linux.loff_t;
                    whence:dword
        );
             @nodisplay;
        begin llseek;
             linux.pushregs;
             mov( linux.sys_llseek, eax );
             mov( fd, ebx );
             mov( offset_high, ecx );
             mov( offset_low, edx );
             mov( theResult, esi );
             mov( whence, edi );
             int( $80 );
             linux.popregs;
        end llseek;
        DESCRIPTION
             The linux.llseek function repositions the offset of the file descriptor fd to (offset_high<<32) | offset_low bytes
        relative to the beginning of the file, the current position in the file, or the end of the file, depending on whether
        whence is linux.seek_set, linux.seek_cur, or linux.seek_end, respectively.
                  It returns the resulting file position in the argument result.
Linux System Calls
        RETURN VALUE
                 Upon successful completion, linux.llseek returns 0. Otherwise, it returns a negative error code in
        EAX.
        ERRORS
        errno.ebadf               fd is not an open file descriptor.
        errno.einval              whence is invalid.
        CONFORMING TO
            This function is Linux-specific, and should not be used in programs intended to be portable.
        BUGS
            The ext2 filesystem does not support files with a size of 2GB or more.

```

Having confirmed that I need to conform the call to llseek() instead of lseek(), in addition to making the bonehead realization that the file descriptor lives in eax after the file is created/opened, I have modfied the code:

```

section .data

	fd1	dd	0
	testd	db	'Generic Text'
	testsz	equ	$ - testd

section .text
global	_start

_start:

	pop	ebx		;	ebx - argc
	pop	ebx		;	ebx - argv
	pop	ebx		;	ebx - filename to write to
	
	mov	eax, 5		;	eax - syscall_creat
	mov	ecx, 00664Q	;	ecx - read/write
	int	80h		;	syscall_creat
	mov	[fd1], eax
	
	mov	eax, 140	;	eax - syscall_lseek
	mov	ebx, [fd1]
	sub	ecx, ecx	;	ecx - offset 0
	sub	edx, edx	;	edx - offset 0
	sub	esi, esi	;	esi - 'theResult', whatever that means...
	mov	edi, 2		;	edi - SEEK_END
	int	80h		;	syscall_lseek
	
	mov	eax, 4		;	eax - syscall_write
	mov	ebx, [fd1]
	mov	ecx, testd	;	ecx - pointer to data to be written
	mov	edx, testsz	;	edx - number of bytes to be written
	int	80h		;	syscall_write
	
	mov	eax, 1		;	eax - syscall_exit
	sub	ebx, ebx	;	ebx - errorcode 0
	int	80h		;	syscall_exit

```

So now my question becomes this:

What goes in the esi register? 'theResult' doesn't give me anything concrete to go on. The documentation says 'linux.loff_t' is the populator for 'theResult', but I'm still in the dark. The above code overwrites the original file everytime - we're not seeking to the end.

I'll probably work this out myself, given time, but MAN I'm frustrated.

---

### Post by Carl Hamlin on 2007-10-28
For those of you who are following - it *looks* like 'linux.loff_t' is where the new offset for the file position gets stored. We'll see.

EDIT:

Maybe not.

---

### Post by slavik on 2007-10-29
umm, have you tried creating the file with append mode?

---

### Post by Carl Hamlin on 2007-10-29
Hey, thanks for the suggestion!

I didn't realize there was such an animal. Now to figure out how to specify 'append'.

Also, i discovered that all the syscall numbers are available in unstd.h, which is a *stellar* discovery for me because no I can dump llseek() and do lseek() like I originally planned.

If 'append mode' does the job, I'll still need to get lseek() nailed down, but that'll definitely be a huge help.

---

### Post by slavik on 2007-10-29
basically, opening a file for append is like creating the file if it isn't there and seeking to the end.

---

### Post by Carl Hamlin on 2007-10-29
That'd be absolutely what I need right now, if I could find documentation on how to specify 'append' in octal during the create/open call.

So far, the documentation is decidedly lacking. No surprising; there's very, very, very little documentation on writing assembly language under Linux. Everything seems to assume you're writing C/C++.

---

### Post by Carl Hamlin on 2007-10-29
Well, I manually entered 0-7 as the most significant digit for the mode specification, using create and open to see which one turned on append mode.

Seems that none of them do. I'll keep looking, but I'm thinking 'append mode' might operate on a higher level.

---

### Post by Carl Hamlin on 2007-10-30
So.. much... pain...

I looked up the lseek() command in unistd.h. Turns out 140 *is* llseek(), which is complex and likely not intended to be hand coded (although it can be). lseek() is 19, and works like I thought it did.

Also. creat() TRUNCATES the file if it already exists. That would have been good to know.

But finally, (and this is what had me tearing what little hair I have left out) opening files in mode 00644Q does not allow for writing unless the program is being run as root.

Fortunately, 00666Q does.

Problem resolved.

---

### Post by slavik on 2007-10-30
644 is read and write for owner, read for group, and read for all others.

---

### Post by NathanB on 2007-10-31
Carl, just for future reference, you will likely bump into more ASM folk at these hang-outs:

[http://tech.groups.yahoo.com/group/linux-nasm-users/](http://tech.groups.yahoo.com/group/linux-nasm-users/)
[http://board.flatassembler.net/](http://board.flatassembler.net/)
[http://groups.google.com/group/comp.lang.asm.x86/topics?hl=en&lnk=rgh](http://groups.google.com/group/comp.lang.asm.x86/topics?hl=en&lnk=rgh)
[http://members.save-net.com/jko@save-net.com/asm/](http://members.save-net.com/jko@save-net.com/asm/)
[http://groups.yahoo.com/group/aoaprogramming/](http://groups.yahoo.com/group/aoaprogramming/)

Nathan.
[http://del.icio.us/Evenbit/Linux](http://del.icio.us/Evenbit/Linux)

---

### Post by Carl Hamlin on 2007-10-31
Nathan:

If you're ever in Denver look me up and I'll buy you a beer. Thank you for these links - I'll mosey on over and check them out.

---


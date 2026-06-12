---
title: "segmentation fault in C on ubuntu"
date: 2008-02-06
forum: Programming Talk
---

### Post by chetanbhole on 2008-02-06
I have been facing the following problem. 
I have Ubuntu installed on my laptop with 1.5GM RAM (though i have set the  swap space to a low 256MB).

When i allocate an array of a really large size (around 15MB), my C program segment faults.
It does not when i try to run the same program on my desktop that has Linux Fedora 4 installed that has 1GM of RAM (but 2GB of swap space.)

Anyone have any idea on why this is happening? From the system monitor, i always see that my swap space on both the machines is totally unused always and so decided to have so low a swap space the next time i installed ubuntu. Even after allocating arrays of huge size my main RAM memory used is still very small too.

Thanks.

---

### Post by Wybiral on 2008-02-06
Can you post your code?

---

### Post by Lster on 2008-02-06
Hi

It might be best if you post your code. However, assuming you use malloc for allocation, if you look at the this:

[http://www.cplusplus.com/reference/clibrary/cstdlib/malloc.html](http://www.cplusplus.com/reference/clibrary/cstdlib/malloc.html)

> Return Value
On success, a pointer to the memory block allocated by the function.
The type of this pointer is always void*, which can be cast to the desired type of data pointer in order to be dereferenceable.
**If the function failed to allocate the requested block of memory, a null pointer is returned.**

Do you check what malloc returns?

---

### Post by chetanbhole on 2008-02-08
Hi,

The code is as simple as it can get. Absolutely no allocation from the heap.

#include<stdio.h>

int main() {

	int A[3][1000][1000] ={0};

	printf("\n hello \n");

	return 0;

}

Interstingly, this doesn't seem to be a problem with ubuntu.
My machine is a dual boot and so tried running the same code on windows using the gcc compiler to compile it. It throws an microsoft report bug error when i try to run it.

Thanks for the help.

---

### Post by chetanbhole on 2008-02-08
In my earlier mail where i say "this doesn't seem to be a problem with ubuntu"  i actually meant that the program fails on both ubuntu and windows.

Thanks

---

### Post by Zugzwang on 2008-02-08
The solution had been posted here:

[http://ubuntuforums.org/showthread.php?t=57158&highlight=stack+allocation+fault]("http://ubuntuforums.org/showthread.php?t=57158&highlight=stack+allocation+fault")

You are allocating more memory on the stack than its size.

---

### Post by Wybiral on 2008-02-08
Why are you trying to initialize "A[3][1000][1000]" as "{0}"?

---

### Post by chetanbhole on 2008-02-08
I just wanted the array to have non-junk values and so initialized the entire array to 0.

I understand that while allocating this array of 12MB, i am crossing the segmentation limits. But the question is - why is it crossing the segmentation limits on my laptop (intel processor 32bit) and not my desktop (dell machine with an intel processor 32bit)? 

Or is it because the desktop machine might be having segment registers larger in size than my laptop machine and so can have a larger segment limit? (inspite of both being 32bit machines)

Thanks for the help

---

### Post by mike_g on 2008-02-08
> #include<stdio.h>

int main() {

int A[3][1000][1000] ={0};

printf("\n hello \n");

return 0;

}
With that code you are almost definitely going to blow the stack (on windows at least its 1MB). You should be able o get it to work by using dynamic allocation. IE: malloc, or calloc (if you want the memory set to 0).

---

### Post by hod139 on 2008-02-08
> **Zugzwang said:**
> The solution had been posted here:

[http://ubuntuforums.org/showthread.php?t=57158&highlight=stack+allocation+fault](http://ubuntuforums.org/showthread.php?t=57158&highlight=stack+allocation+fault)
.

I miss LordHunter317 around here.  He had a way of keeping things interesting (e.g. [http://ubuntuforums.org/showthread.php?t=42375](http://ubuntuforums.org/showthread.php?t=42375))


As for helping the OP, see this thread that we just had 1 week ago: [http://ubuntuforums.org/showthread.php?t=680535](http://ubuntuforums.org/showthread.php?t=680535)

---

### Post by stroyan on 2008-02-08
You are being misled by the term 'segmentation fault'.
It isn't really about i386 segmentation registers.
It is a very old term dating back to unix on a pdp-11.
A program gets a segmentation fault when it accesses a virtual address that is not mapped.
Your program does that when you exceed the maximum stack size.
(That maximum can be changed by the ulimit shell builtin.)

A very similar 'bus error' signal can happen when accessing an address that has no permission for the type of access, or an alignment violation, or hardware that doesn't respond.

You can learn more about the history and meanings of these faults at wikipedia-
[http://en.wikipedia.org/wiki/Segmentation_fault](http://en.wikipedia.org/wiki/Segmentation_fault)
[http://en.wikipedia.org/wiki/Bus_error](http://en.wikipedia.org/wiki/Bus_error)

---

### Post by pmasiar on 2008-02-08
> **hod139 said:**
> I miss LordHunter317 around here.  He had a way of keeping things interesting (e.g. [http://ubuntuforums.org/showthread.php?t=42375](http://ubuntuforums.org/showthread.php?t=42375))


As for helping the OP, see this thread that we just had 1 week ago: [http://ubuntuforums.org/showthread.php?t=680535](http://ubuntuforums.org/showthread.php?t=680535)

hod139, maybe you want to add these links (and more from your bookmarks)  to C/C++ FAQ: [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635)

You may want to talk to aks44, IIUC that FAQ is being split to 'compile' and 'errors' parts.

---

### Post by chetanbhole on 2008-02-10
Stroyan,

the ulimit command does definitely make a difference in my case.
I increased the stack limit size to around 20MB  (ulimit -s 20000) and the program runs.
Thanks alot.

---


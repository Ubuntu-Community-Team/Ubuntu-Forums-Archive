---
title: "Make pointers work across processes ( through shared memory)"
date: 2011-01-19
forum: Programming Talk
---

### Post by kunalgrao on 2011-01-19
Hello

I have a pointer to an instance of a class. This instance is created and initialized in Process A (process A keeps running and the instance is always present). Now, I want process B to modify/update the values of the members of this object (process A is running and that object is present).  Process A and process B are completely independent. ( Process B is not called from process A using fork() ).

I am interested in only passing the pointer to this object through shared memory to process B and process B should be able to dereference that pointer to its correct location. 

I know that each process has its own address space and that just passing pointer of process A to process B will not make sense to process B. The memory mapping in process A will be different from that in process B.

Now, my question is, can we somehow identify that mapping and use that in process B such that process B is able to correctly dereference the process A pointer ?

I have been able to move the pointer from process A to process B through shared memory IPC. Now I should be able to dereference this pointer correctly in process B.

Any ideas/suggestions ?

Thanks & Regards,
Kunal

---

### Post by psusi on 2011-01-19
The pointer has to actually point to somewhere in a shared memory segment, and both processes have to map that segment.  Then the sending process has to subtract the base address of its mapping, and the receiving process has to add the base address of its mapping.

Also you need to make sure that both processes don't try to access the object at the same time, like with a mutex.

---

### Post by kunalgrao on 2011-01-19
psusi, Thanks for your quick reply.

I understood the first part of your reply, i.e. the pointer should point somewhere in the shared memory segment. So probably, I'll copy the object in the shared memory segment and have the pointer to it as well in the shared segment. I'll map this shared segment to both the processes ( shared segment can be created/attached using shmget, shmat ?? or should I look into mmap ?? ). This way everything is visible to both the processes.

Can you please elaborate on the next part of your reply, i.e. " Then the sending process has to subtract the base address of its  mapping, and the receiving process has to add the base address of its  mapping."

It would be good if you can explain with some arbitrary address values.

Thanks & Regards,
Kunal

---

### Post by kunalgrao on 2011-01-19
aa

---

### Post by kunalgrao on 2011-01-19
aa

---

### Post by kunalgrao on 2011-01-19
aa

---

### Post by kunalgrao on 2011-01-19
aa

---

### Post by kunalgrao on 2011-01-19
I have copied the object and the pointer to the object, both in the shared memory segment. 

Both the processes are attaching to the shared memory segment. Process A is writing in the shared memory segment and process B wants to read it. Now, Process B is able to pick up the pointer to the object, but when it is dereferencing it, it is not getting proper value. 

I guess, here comes the part which you were saying, "Then the sending process has to subtract the base address of its   mapping, and the receiving process has to add the base address of its   mapping."

Can you please elaborate on how do I do that ?  which base address are we talking about ? 

Thanks & Regards,
Kunal

P.S: Please ignore the previous 4-5 messages with "aa" ..somehow my prev. message got posted multiple times..and i am not finding how to delete them ..anyway..ignore those and please continue the thread forward ..Thanks !!

---

### Post by psusi on 2011-01-19
> **kunalgrao said:**
> 
Can you please elaborate on how do I do that ?  which base address are we talking about ? 


The address of the mapping.  If the mapping starts at 0x1000 and your pointer is 0x1040, then you need to subtract to get the difference of 0x40.  The other process might have mapped it at 0x7000 so it needs to add to get to 0x7040.

---

### Post by kunalgrao on 2011-01-22
[IMG]http://dl.dropbox.com/u/4645378/pointers_across_different_processes_through_shared_memory.png[/IMG]

Please have a look at the attached image. If I have understood correctly,Suppose the data is in shared memory at 0x9000. Process A maps it to 0x6000 and process B maps it to 0x4000. Now process B writes the location in the shared pointer as 0x4000. Process A reads it as 0x4000, but it has no clue that the actual location is 0x9000 which it has mapped to 0x6000. So what Process A has to do is add 0x2000 ( Difference in mapping between Process A and process B) to 0x4000 and look at that location. Is this understanding correct ? If not, please help me understand it clearly.

Thanks & Regards,
Kunal

---

### Post by psusi on 2011-01-22
Not quite.  There is no "actual location".  To talk about its location requires process context.  The only way to talk about it as any sort of "actual location" outside any process is with a list of physical addresses, and only the kernel ever knows or cares about those.

Since one process thinks the memory is at 0x4000 and the other thinks it is at 0x6000, the only way they can communicate is by using relative addresses.  While process A knows the mapping as 0x4000, and an object inside that mapping as 0x41C0, that is meaningless to process B.  So, to communicate with process B, you need to just send the address of the object relative to the start of the mapping ( wherever that may be ), which in this case is 0x1C0.  Since process B knows it has mapped the segment to 0x6000, it can then compute the absolute address of 0x61C0.

---

### Post by kunalgrao on 2011-01-23
I guess you are assuming that a single big chunk of memory is created as shared memory. And using only relative addressing, we can move through the shared memory to access data from that through different processes (as if the shared memory is a contiguous block with different starting address for each process). 

In my case, I am not having a single chunk of shared memory. The pointer and the data are in 2 different shared segments (which both processes are attaching to). How do I make the pointer work in this case ? I hope the question is clear.

In the previous diagram the outer box of shared memory was mis-leading I guess ..That was just to separate it out from the 2 processes. The actual shared segments are the 2 small boxes inside..So the pointer to data and the actual data are in 2 different shared segments. Now, I want to make sure that pointer dereferencing, resolves to proper data location when other process reads it ..let me know if something isn't clear ..

Thanks for your help ..

Kunal

---

### Post by worksofcraft on 2011-01-23
Did you check how to use [Posix shared memory objects]("http://linux.die.net/man/3/shm_open")?
However, I don't think you can transfer pointers between processes in a portable way because for different processes memory management is likely to map addresses to different blocks of memory.

---

### Post by kunalgrao on 2011-01-23
worksofcraft, yes I did check that. Using that I was able to share data between 2 processes. That is working fine for me. But, somehow I am trying to figure out a way to share pointers between 2 processes (even if that means copying the data and pointer in some shared region, and a pointer provided by one process must make sense to the other process and should resolve to the correct data location).

---

### Post by slavik on 2011-01-23
why not serialize/unserialize objects and move those in/out shmem? you can even do this over a network.

if you put an object in shmem, then creating a pointer for it is useless.

---

### Post by kunalgrao on 2011-01-23
Slavik, I can directly read the object inside the shared memory from the other process. My real concern is that the object itself contains some member variables which are pointers. I am looking for a way to handle these pointers. For that, I want to find a way to make pointers work across proceses.

I understand what you siad that putting the object in shared memory and then creating a pointer for it is useless..but my concern is that the object itself has some member variables which are pointers ..so if I can find a way to make pointers work across processes, then I can apply that for the object member variables (which are pointers) ..I hope you got the point ..

---

### Post by psusi on 2011-01-23
> **kunalgrao said:**
> 
In my case, I am not having a single chunk of shared memory. The pointer and the data are in 2 different shared segments (which both processes are attaching to). How do I make the pointer work in this case ? I hope the question is clear.

Why do you have two different segments?  I would just stick with a single segment, but if you want to use two, then the same logic applies, just to each one individually.  In other words, when adding and subtracting the segment base address, you need to use the appropriate one for the segment in question.

> **worksofcraft said:**
> Did you check how to use [Posix shared memory objects]("http://linux.die.net/man/3/shm_open")?
However, I don't think you can transfer pointers between processes in a portable way because for different processes memory management is likely to map addresses to different blocks of memory.

It is usually a good idea to read the thread before posting.  The OP said he is using posix shared memory, and I have been describing how to transfer pointers, so it is possible.

> **kunalgrao said:**
> but my concern is that the object itself has some member variables which are pointers

Then those pointers must also point to objects allocated inside the shared memory segment, and be stored in relative form, then be converted back to absolute addresses within each process only when dereferencing them.

---

### Post by worksofcraft on 2011-01-23
> **psusi said:**
> 
It is usually a good idea to read the thread before posting.  The OP said he is using posix shared memory, and I have been describing how to transfer pointers, so it is possible.

I was just checking if either of you were aware of the documentation. Like is there any reason you prefer to hunt through your data adjusting pointers rather than use flags like:

MAP_FIXED
or
MAP_SHARED
?

Anyway you have to be very careful of what you put in there cuz things like std::string or even a simple constant text string and objects of classes that have virtual methods and also function pointers, are probably going to cause a few problems.

My understanding is to treat it the same as a file. Storing pointers in files is a recipe for disaster.

---

### Post by psusi on 2011-01-23
Yea, try to map it to the same address in both processes, but might not be able to.

---

### Post by slavik on 2011-01-24
> **kunalgrao said:**
> Slavik, I can directly read the object inside the shared memory from the other process. My real concern is that the object itself contains some member variables which are pointers. I am looking for a way to handle these pointers. For that, I want to find a way to make pointers work across proceses.

I understand what you siad that putting the object in shared memory and then creating a pointer for it is useless..but my concern is that the object itself has some member variables which are pointers ..so if I can find a way to make pointers work across processes, then I can apply that for the object member variables (which are pointers) ..I hope you got the point ..
read about serialization/flattening. :)

if you leave pointers as is, you will either get a segfault (good) or undefined behavior (very bad).

---

### Post by kunalgrao on 2011-01-24
I was able to implement as per the diagram I had attached previously and it worked fine..I was able to get the pointer dereferenced properly in other process to the correct data value.

Now, this works fine for integer pointer, but when I am trying with function pointer, I am not able to do that. Probably because, to get the location to dereference, I am using pointer addition and subraction, which is defined for fixed length data types. When I am doing with function pointer I get this message:

 error: ISO C++ forbids using pointer to a function in subtraction

Any thoughts on how to proceed further for function pointers .. ?

Thanks & Regards,
Kunal

---

### Post by psusi on 2011-01-24
You can't.  The function is not in the shared memory segment.

---

### Post by kunalgrao on 2011-01-24
is it possible if the function as well is in the shared memory segment ? the function pointer will be dereferenced correctly ?

---

### Post by psusi on 2011-01-24
> **kunalgrao said:**
> is it possible if the function as well is in the shared memory segment ? the function pointer will be dereferenced correctly ?

Not really.  You would have to copy the function into the shared memory, and then patch the vtable in both programs to point there, which I don't think you can do.

I suggest taking a step back and describing the big picture of what you are doing and why.  I can't imagine a problem to which this would be a sensible solution.

For instance, why do you want to separate programs to share memory, instead of just forking one program?

---


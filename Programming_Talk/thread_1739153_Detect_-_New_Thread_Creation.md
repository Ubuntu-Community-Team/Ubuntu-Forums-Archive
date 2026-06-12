---
title: "Detect - New Thread Creation"
date: 2011-04-25
forum: Programming Talk
---

### Post by Gihan Lakmal on 2011-04-25
In my project, I want to detect new thread creation of particular process and I want to get instructions of newly created thread at execution time to migrate process to another place. Who knows process migration please help me to do this.

---

### Post by Tony Flury on 2011-04-26
The only way I can think of for process B to detect that process A has started a new thread is for the new thread to write something in a shared place - i.e. a file or shared memory.

Unless of course the code is shared - i don't know of a way that Process B can take over the thread being run by Process A - the threading model does not work like.

---

### Post by Gihan Lakmal on 2011-04-26
> **Tony Flury said:**
> The only way I can think of for process B to detect that process A has started a new thread is for the new thread to write something in a shared place - i.e. a file or shared memory.

Unless of course the code is shared - i don't know of a way that Process B can take over the thread being run by Process A - the threading model does not work like.

Thanks for your reply...

I think if I can monitor clone call of relevant process, system can be able to identify the new thread creation. Are there any mechanism or scripts to do that.

---

### Post by BkkBonanza on 2011-04-27
What do you actually mean by "migrate process to another place"?

Threads share common memory within a process. Usually when you create a thread you store the thread id as a reference, maybe in an array or list. So you can detect how many threads exist by looking at their referring id values being present. But I don't know what you intend with the above phrase - you want to detach threads and attach them to a different process? I'm not aware of any way to do that. Processes do not share common memory and are much more separated than threads.

---

### Post by Gihan Lakmal on 2011-04-27
> **BkkBonanza said:**
> What do you actually mean by "migrate process to another place"?

Threads share common memory within a process. Usually when you create a thread you store the thread id as a reference, maybe in an array or list. So you can detect how many threads exist by looking at their referring id values being present. But I don't know what you intend with the above phrase - you want to detach threads and attach them to a different process? I'm not aware of any way to do that. Processes do not share common memory and are much more separated than threads.

Thanks guy for your kindly reply.

yep,
I'll explain what I want to do. In my project I try to reduce the workload of CPU and move some processes to the GPU. In implementation I try to recognize new threads of relevant process and move those threads in to the GPU (specially data parallel programs) then execute those threads in GPU and get result back. I use C to implement this project and use Ubuntu as a operating system. Before moving threads, its required to identify new thread creation of target program/process (via clone system call - are there any simple methods ??), get instructions, memory locations and current value of those locations. Then I can execute those threads in GPU. After execution it pump-backs  results in to main memory. Thats the proposed project. I required help to detect new thread creation and get thread instructions and memory locations required to thread execution with current values. I'm still unable to do that but several times I tried to do that finally all efforts end-up with system crashes :( . If anyone knowes about detection part or any other part please kind enough to help me.

---

### Post by BkkBonanza on 2011-04-27
I don't know of any way to do that but I haven't researched it. What comes to mind initially is that you would have to write a replacement version of pthread_create, and perhaps some other pthreads functions. It would be able to make a decision about what core to create the thread on, but also since the gpu uses completely different machine code it would have to translate code as well.

Maybe it could analyze the thread's code before deciding but that would be quite difficult and likely slow. More simply, a programmer would make choice to link against your pthreads library and provide special attributes (in the same way they can set stack size for example) that would indicate that optionally this thread would benefit from the gpu. I'd assume it can't share memory if running on the gpu and so you would have to analyze whether the code is dependent on sharing memory.

Also it may be feasible to make a program that analyzes a binary and then patches it to use the enhanced pthread_create for thread code that would benefit. This would be easier and give satisfactory results.

---

### Post by Gihan Lakmal on 2011-04-27
> **BkkBonanza said:**
> I don't know of any way to do that but I haven't researched it. What comes to mind initially is that you would have to write a replacement version of pthread_create, and perhaps some other pthreads functions. It would be able to make a decision about what core to create the thread on, but also since the gpu uses completely different machine code it would have to translate code as well.

Maybe it could analyze the thread's code before deciding but that would be quite difficult and likely slow. More simply, a programmer would make choice to link against your pthreads library and provide special attributes (in the same way they can set stack size for example) that would indicate that optionally this thread would benefit from the gpu. I'd assume it can't share memory if running on the gpu and so you would have to analyze whether the code is dependent on sharing memory.

Also it may be feasible to make a program that analyzes a binary and then patches it to use the enhanced pthread_create for thread code that would benefit. This would be easier and give satisfactory results.

hmm.... 

In this project not use specific programs or any other specifically written programs instead of it uses generic multi-core multi-threaded application without any changes. most of points you highlighted are correct. In my project there are external memory management unit which capable to handle all conflicts in between CPU and GPU also there are module called Event Handler which capable to handle all instructions and mapped generic CPU instructions with GPU instructions. also I looking for get out thread instructions and mapped those machine instructions in to the GPU instructions then run the specific thread in GPU. thats the reason I highly depend on the system calls of Operating System because otherwise I must use compiler instructions and mapped those instructions in compile time but it is not a most generic version of my project. anyway Thank You Very Much for your Kind Reply and give some idea to me Thanks Again.

---

### Post by slavik on 2011-04-27
don't think you can do that.

GPGPU programming is not as simple as it sounds. You can't simply schedule things to be run on the GPU.

---

### Post by Gihan Lakmal on 2011-04-28
> **slavik said:**
> don't think you can do that.

GPGPU programming is not as simple as it sounds. You can't simply schedule things to be run on the GPU.

"GPGPU programming is not as simple as it sounds." 1000000% correct GPGPU programming not simple that is the one of major reason why GPU based solutions not popular. In my project try to reduce the programming complexity of GPU computing that's the major goal I try to achieve. I think that procedure is ok with my scope, are there any weak points please notify those weak points then I can revise my path and redirect to the correct path. Its very helpful me to success that project and introduce quality software.

---


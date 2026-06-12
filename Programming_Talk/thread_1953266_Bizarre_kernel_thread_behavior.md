---
title: "Bizarre kernel thread behavior"
date: 2012-04-05
forum: Programming Talk
---

### Post by gardnan on 2012-04-05
So, I have been experimenting a bit with kernel modules recently, and have tried to write my own kernel thread.

At first what I had was this for my kernel thread function:

```

static int __sched mythreadfunc(void *data)
{
    while (!kthread_should_stop())
    {
         shedule();
     }
     return 0;
}
```Which would be started from the module init function and killed by the module exit function. However, I noticed that with this method, the thread took up 99.9% of CPU time.

I looked then at how kswapd was implemented in the kernel and changed it to this:
```

static int __sched mythreadfunc(void *data)
{
    wait_queue_head_t mywait;
    DEFINE_WAIT(wait);
    prepare_to_wait(&myway, &wait, TASK_INTERRUPTIBLE);
    while (!kthread_should_stop())
    {
         shedule();
         finish_wait(&mywait, &wait);
     }
     return 0;
}
```This worked perfectly fine for a while. But suddenly, after having removed it several times before, removing it completely hung the system. It just hung. On a different kernel, it started spewing out "<IRQ>" kernel messages.

If anyone had any insights on how to properly create and manage a kernel thread, I would be much obliged.

---

### Post by CynicRus on 2012-04-06
```

#include <linux/module.h> 
	#include <linux/sched.h> 
	#include <linux/delay.h> 
	
	static int param = 3; 
	module_param( param, int, 0 ); 
	
	static int thread( void * data ) {
	   printk( KERN_INFO "thread: child process [%d] is running\n", current->pid ); 
	   ssleep( param );                                  /* pause 3 s */ 
	   printk( KERN_INFO "thread: child process [%d] is completed\n", current->pid ); 
	   return 0; 
	} 
	
	int test_thread( void ) { 
	   pid_t pid; 
	   printk( KERN_INFO "thread: main process [%d] is running\n", current->pid ); 
	   pid = kernel_thread( thread, NULL, CLONE_FS );     /* create new thread */ 
	   ssleep( 5 );                                      /* pause 5 &#1089;. */ 
	   printk( KERN_INFO "thread: main process [%d] is completed\n", current->pid ); 
	   return -1; 
	} 
	
	module_init( test_thread ); 


```

---

### Post by gardnan on 2012-04-06
So I fixed my problem, and developed a little bit of theory as to why I was wrong. The first code bit just continously schedules, but I forgot to place the kthread into a TASK_INTERRUPTIBLE state. That meant that it could not be interrupted for any reason, which contributed heavily to using up CPU. 

The second approach worked at first because placing a thread or process on a wait queue has the side effect of making it INTERRUPTIBLE.

 However, as I have learned, the wait queue system is fairly complex, and I think that my customized kernel build may have effected it somehow, which had the effect that when a thread was suddenly ended, such as through a module unloading, it caused an error in the wait queue system. Anyway, I guess I solved my own problem for now.

---

### Post by gardnan on 2012-04-06
Well, right when I thought I had it down, it turns out that there are multiple ways of doing it.

This especially contradicts my earlier theory that it was the interruptability of the thread that caused the CPU increase, as ssleep is a wrapper around schedule_timeout_uninterruptible. It seems like setting the interruptability of the task at all causes the cpu time to decrease significantly.

Overall it is quite strange, however, it does feel good to be bombarded by too many different solutions after having none!

PS. I would like to hear more about what you know about kernel scheduling, CynicRus.

---


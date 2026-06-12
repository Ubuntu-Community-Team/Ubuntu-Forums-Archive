---
title: "replacing keyboard handler"
date: 2005-05-31
forum: Programming Talk
---

### Post by Ronbin on 2005-05-31
hi 
I'm trying to replace my keyboard interrupt handler using [this](http://www.faqs.org/docs/kernel/x1206.html) tuto. I've changed the code a bit, and now it looks like this:
```
 
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/sched.h>
#include <linux/tqueue.h>
#include <linux/interrupt.h>
#include <asm/io.h>

/* Bottom Half */
static void got_char(void *scancode)
{
   printk(KERN_ALERT"Scan Code %x %s.\n",
          (int) *((char *) scancode) & 0x7F,
          *((char *) scancode) & 0x80 ? "Released" : "Pressed");
}

/* This function services keyboard interrupts. It reads the relevant
 * information from the keyboard and then scheduales the bottom half
 * to run when the kernel considers it safe.
 */
void irq_handler(int irq, void *dev_id, struct pt_regs *regs)
{
   /* This variables are static because they need to be 
    * accessible (through pointers) to the bottom half routine.
    */
  static unsigned char scancode;
  unsigned char status;  
  DECLARE_TASKLET(task, got_char, &scancode); 

   /* Read keyboard status */
   status = inb(0x64);
   scancode = inb(0x60);
  
   /* Scheduale bottom half to run */
    tasklet_schedule(&task);}

/* Initialize the module - register the IRQ handler */
int init_module()
{
   
        free_irq(1, NULL);
	printk(KERN_ALERT"free\n");
	int result = request_irq(1,irq_handler,SA_INTERRUPT,"test_keyboard_irq_handler",NULL);
	        if ( result != 0 )
        	{
                	printk ( KERN_ALERT"error, result=%d\n",result );
                	return -1;
        	}
        	else
        	{
                	printk ( KERN_ALERT"succes!\n" );
                	return 0;
        	}

}


/* Cleanup */
void cleanup_module()
{
  free_irq(1, NULL);
}

``` 
after compiling the module, I try to load it with insmod, but it shows this
> trying to free free IRQ1
free
error, result=-16
insmod: error inserting 'intrpt.ko': -1 Operation not permitted

aby idea????

---

### Post by LordHunter317 on 2005-05-31
[QUOTE=Ronbin]hi 
I'm trying to replace my keyboard interrupt handler using [this](http://www.faqs.org/docs/kernel/x1206.html) tuto. I've changed the code a bit, and now it looks like this:
```
 
#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/sched.h>
#include <linux/tqueue.h>
#include <linux/interrupt.h>
#include <asm/io.h>

/* Bottom Half */
static void got_char(void *scancode)
{
   printk(KERN_ALERT"Scan Code %x %s.\n",
          (int) *((char *) scancode) & 0x7F,
          *((char *) scancode) & 0x80 ? "Released" : "Pressed");
}

/* This function services keyboard interrupts. It reads the relevant
 * information from the keyboard and then scheduales the bottom half
 * to run when the kernel considers it safe.
 */
void irq_handler(int irq, void *dev_id, struct pt_regs *regs)
{
   /* This variables are static because they need to be 
    * accessible (through pointers) to the bottom half routine.
    */
  static unsigned char scancode;
  unsigned char status;  
  DECLARE_TASKLET(task, got_char, &scancode); 

   /* Read keyboard status */
   status = inb(0x64);
   scancode = inb(0x60);
  
   /* Scheduale bottom half to run */
    tasklet_schedule(&task);}

/* Initialize the module - register the IRQ handler */
int init_module()
{
   
        free_irq(1, NULL);
	printk(KERN_ALERT"free\n");
	int result = request_irq(1,irq_handler,SA_INTERRUPT,"test_keyboard_irq_handler",NULL);
	        if ( result != 0 )
        	{
                	printk ( KERN_ALERT"error, result=%d\n",result );
                	return -1;
        	}
        	else
        	{
                	printk ( KERN_ALERT"succes!\n" );
                	return 0;
        	}

}


/* Cleanup */
void cleanup_module()
{
  free_irq(1, NULL);
}

``` 
after compiling the module, I try to load it with insmod, but it shows this


aby idea????[/QUOTE]
 It means just what it says.  You tried to free an IRQ that wasn't in use, which is a serious bug.  You do it as the first call in init_module()

Not to be mean, but if you can't decipher such a simple message, you probably really shouldn't be doing kernel programming.

---

### Post by Ronbin on 2005-05-31
[QUOTE=LordHunter317]It means just what it says.  You tried to free an IRQ that wasn't in use, which is a serious bug.  You do it as the first call in init_module()

Not to be mean, but if you can't decipher such a simple message, you probably really shouldn't be doing kernel programming.[/QUOTE]
Yes, I'm a totally newbe to kernel programming, but....

the call which causes the error is "request_irq()" and not "free_irq()"
i tried to free the IRQ number 1, which is the one for the keyboard, so it is in use.

the original code worked in a OS with kernel 2.4, but did not in my 2.6 kernel, so I changed the tq_struct to a tasklet. That's the only change.

---

### Post by Ronbin on 2005-06-01
ok, I've found the new version of the tutorial [here](http://www.tldp.org/LDP/lkmpg/2.6/html/index.html) 
the code gets like this
```

/*
 *  intrpt.c - An interrupt handler.
 *
 *  Copyright (C) 2001 by Peter Jay Salzman
 */

/* 
 * The necessary header files 
 */

/* 
 * Standard in kernel modules 
 */
#include <linux/kernel.h>	/* We're doing kernel work */
#include <linux/module.h>	/* Specifically, a module */
#include <linux/sched.h>
#include <linux/workqueue.h>
#include <linux/interrupt.h>	/* We want an interrupt */
#include <asm/io.h>

#define MY_WORK_QUEUE_NAME "WQsched.c"

static struct workqueue_struct *my_workqueue;

/* 
 * This will get called by the kernel as soon as it's safe
 * to do everything normally allowed by kernel modules.
 */
static void got_char(void *scancode)
{
	printk(KERN_INFO "Scan Code %x %s.\n",
	       (int)*((char *)scancode) & 0x7F,
	       *((char *)scancode) & 0x80 ? "Released" : "Pressed");
}

/* 
 * This function services keyboard interrupts. It reads the relevant
 * information from the keyboard and then puts the non time critical
 * part into the work queue. This will be run when the kernel considers it safe.
 */
irqreturn_t irq_handler(int irq, void *dev_id, struct pt_regs *regs)
{
	/* 
	 * This variables are static because they need to be
	 * accessible (through pointers) to the bottom half routine.
	 */
	static int initialised = 0;
	static unsigned char scancode;
	static struct work_struct task;
	unsigned char status;

	/* 
	 * Read keyboard status
	 */
	status = inb(0x64);
	scancode = inb(0x60);

	if (initialised == 0) {
		INIT_WORK(&task, got_char, &scancode);
		initialised = 1;
	} else {
		PREPARE_WORK(&task, got_char, &scancode);
	}

	queue_work(my_workqueue, &task);

	return IRQ_HANDLED;
}

/* 
 * Initialize the module - register the IRQ handler 
 */
int init_module()
{
	my_workqueue = create_workqueue(MY_WORK_QUEUE_NAME);

	/* 
	 * Since the keyboard handler won't co-exist with another handler,
	 * such as us, we have to disable it (free its IRQ) before we do
	 * anything.  Since we don't know where it is, there's no way to
	 * reinstate it later - so the computer will have to be rebooted
	 * when we're done.
	 */
	free_irq(1, NULL);

	/* 
	 * Request IRQ 1, the keyboard IRQ, to go to our irq_handler.
	 * SA_SHIRQ means we're willing to have othe handlers on this IRQ.
	 * SA_INTERRUPT can be used to make the handler into a fast interrupt.
	 */
	return request_irq(1,	/* The number of the keyboard IRQ on PCs */
			   irq_handler,	/* our handler */
			   SA_SHIRQ, "test_keyboard_irq_handler",
			   (void *)(irq_handler));
}

/* 
 * Cleanup 
 */
void cleanup_module()
{
	/* 
	 * This is only here for completeness. It's totally irrelevant, since
	 * we don't have a way to restore the normal keyboard interrupt so the
	 * computer is completely useless and has to be rebooted.
	 */
	free_irq(1, NULL);
}

/* 
 * some work_queue related functions are just available to GPL licensed Modules
 */
MODULE_LICENSE("GPL");

``` 

Edit: OK, it was all my system's fault. Yesterday, I formated , and installed hoary. My new problem:

I've loaded the module, but, in order to replace the handler with mine, the system lets both handlers running.  Perhaps, I must indicate what's the system's handler's "dev_id" when I call free_irq, but I don't know it. Any idea???

---

### Post by prashantpat on 2008-03-11
Hi all,
As Ronbin mentioned original code works on linux kernel 2.4 and changed code works well on kernel 2.6, I tried both the code on kernel 2.4.20-8 and kernel 2.6.9-5 respectively. But I couldnt compile the program even. I have linux kernel 2.4.20-8 on my machine. Following errors I am getting when I compile the program..

In file included from /usr/src/linux-2.4.20-8/include/linux/sched.h:16,
                from interrupt.c:18:
/usr/src/linux-2.4.20-8/include/linux/timex.h:173: field `time' has
incomplete type
In file included from /usr/src/linux-2.4.20-8/include/linux/sched.h:23,
                from interrupt.c:18:
/usr/src/linux-2.4.20-8/include/asm/mmu.h:12: field `sem' has incomplete type
In file included from /usr/src/linux-2.4.20-8/include/linux/sched.h:31,
                from interrupt.c:18:
/usr/src/linux-2.4.20-8/include/linux/pid.h:18: field `task_list' has
incomplete type
/usr/src/linux-2.4.20-8/include/linux/pid.h:19: field `hash_chain' has
incomplete type
/usr/src/linux-2.4.20-8/include/linux/pid.h:24: field `pid_chain' has
incomplete type
/usr/src/linux-2.4.20-8/include/linux/pid.h:36: parse error before '(' token
/usr/src/linux-2.4.20-8/include/linux/pid.h:38: parse error before '(' token
/usr/src/linux-2.4.20-8/include/linux/pid.h:43: parse error before '(' token
/usr/src/linux-2.4.20-8/include/linux/pid.h:49: parse error before '(' token
/usr/src/linux-2.4.20-8/include/linux/pid.h:52: parse error before '(' token
In file included from interrupt.c:19:
/usr/src/linux-2.4.20-8/include/linux/tqueue.h:39: field `list' has
incomplete type
/usr/src/linux-2.4.20-8/include/linux/tqueue.h: In function `run_task_queue':
/usr/src/linux-2.4.20-8/include/linux/tqueue.h:121: dereferencing
pointer to incomplete type
In file included from /usr/src/linux-2.4.20-8/include/linux/irq.h:69,
                from /usr/src/linux-2.4.20-8/include/asm/hardirq.h:6,
                from /usr/src/linux-2.4.20-8/include/linux/interrupt.h:46,
                from interrupt.c:22:
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h: At top level:
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:81: parse error before '(' token
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h: In function `x86_do_profile':
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:206: `prof_buffer'
undeclared (first use in this function)
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:206: (Each undeclared
identifier is reported only once
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:206: for each function it
appears in.)
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:219: `prof_shift'
undeclared (first use in this function)
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:225: `prof_len'
undeclared (first use in this function)
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h: In function
`register_profile_notifier_R83804553':
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:241: `ENOSYS' undeclared
(first use in this function)
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h: In function
`unregister_profile_notifier_Rf8b8e6e2':
/usr/src/linux-2.4.20-8/include/asm/hw_irq.h:246: `ENOSYS' undeclared
(first use in this function)
In file included from interrupt.c:22:
/usr/src/linux-2.4.20-8/include/linux/interrupt.h: At top level:
/usr/src/linux-2.4.20-8/include/linux/interrupt.h:79: parse error
before '(' token
/usr/src/linux-2.4.20-8/include/linux/interrupt.h:80: parse error
before '(' token
/usr/src/linux-2.4.20-8/include/linux/interrupt.h:156: parse error
before '(' token
/usr/src/linux-2.4.20-8/include/linux/interrupt.h:164: parse error
before '(' token
interrupt.c:53: confused by earlier errors, bailing out


Can someone please help me out.
Thanks in advance.

---


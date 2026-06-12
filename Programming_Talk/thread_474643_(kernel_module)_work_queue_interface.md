---
title: "(kernel module) work queue interface"
date: 2007-06-15
forum: Programming Talk
---

### Post by kometonja on 2007-06-15
hi.
recent versions of linux module's work queue inteface has changed and i can't find any appropriate documentation for it. can *please* someone help me to make the basic skeletion of work queue module. here's what i have done by now.

thanks for your time

```

#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/workqueue.h>
#include <linux/sched.h>
#include <linux/init.h>
#include <linux/interrupt.h>

#define MY_WORK_QUEUE_NAME "THsched"

//static void intrpt_routine(void *);
void my_workqueue_handler(void *arg);

static struct workqueue_struct *my_workqueue;
static struct delayed_work *dwork;
//static struct work_struct Task;

static int die = 0; /* 1 for shutdown */
static int TimerIntrpt = 0;

//static DECLARE_WORK(Task, my_workqueue_handler);

void * my_workqueue_handler(void *arg)
{
	TimerIntrpt++;

	if (die == 0)
		queue_delayed_work(my_workqueue, dwork, 100);
}

int __init init_module() {

	my_workqueue = create_workqueue(MY_WORK_QUEUE_NAME);
	queue_delayed_work(my_workqueue, dwork, 100);
	
	
	printk(KERN_INFO "Module %s loaded.\n", MY_WORK_QUEUE_NAME);
	
	return 0;
}

void __exit cleanup_module() {
	die = 1;

	flush_workqueue(my_workqueue);

	cancel_delayed_work(dwork);	
	destroy_workqueue(my_workqueue);

	printk(KERN_INFO "Module %s unloaded.\n", MY_WORK_QUEUE_NAME);

	return;
}

```

---

### Post by leibowitz on 2007-06-15
I don't know about kernel programming, but I can say if you get no response from here in the following couple of days maybe you can post your request to the kernel mailing-list or somewhere else. 

You will probably get more help there.

You can also try to look in google groups:
[http://groups.google.com/groups/search?q=kernel+module+programming&qt_s=Search+Groups](http://groups.google.com/groups/search?q=kernel+module+programming&qt_s=Search+Groups)

---

### Post by kometonja on 2007-06-19
here it is.. maybe someone'll find it useful..

```

#include <linux/kernel.h>
#include <linux/module.h>
#include <linux/workqueue.h>
#include <linux/sched.h>
#include <linux/init.h>
#include <linux/interrupt.h>

#define Q_NAME "THsched"

MODULE_LICENSE("GPL");

static void work_func(struct work_struct *work);


static int die = 0; /* 1 for shutdown */
static int TimerIntrpt = 0;


//tasks to be run
//static struct work_struct *w_s;
static DECLARE_DELAYED_WORK(w_s, work_func);
//static INIT_DELAYED_WORK(w_s, work_func);
static struct workqueue_struct *my_workqueue;


static void work_func(struct work_struct *work)
{
	TimerIntrpt++;

	if (die == 0) {
		queue_delayed_work(my_workqueue, &w_s, 100);
	}		
}

int __init init_module() {
	//crete wq
	my_workqueue = create_singlethread_workqueue(Q_NAME);
	if(!my_workqueue) {
		return -1;
	}	
	queue_delayed_work(my_workqueue, &w_s, 100);
	
	
	printk(KERN_INFO "Module %s loaded.\n", Q_NAME);
	
	return 0;
}

void __exit cleanup_module() {
	die = 1;

	flush_workqueue(my_workqueue);

	cancel_delayed_work(&w_s);	
	destroy_workqueue(my_workqueue);

	printk(KERN_INFO "Module %s unloaded (%i).\n", Q_NAME, TimerIntrpt);

	return;
}

```

---


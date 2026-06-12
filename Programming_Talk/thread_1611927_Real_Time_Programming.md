---
title: "Real Time Programming"
date: 2010-11-02
forum: Programming Talk
---

### Post by GaryH on 2010-11-02
Hi Everybody,
I've been experimenting with the response time of 10.04 and I have a question about the relationship among latency and nice and programatically setting thread attributes.

My main program program follows and please observer how the playout and capture threads are created and the measures taken to let the kernel know the threads are real time. Hey experts, if this is messed up please let me know.
> int main(int argc, char *argv[]) {
    int i;
    double angle;
    pthread_t playout_tid, capture_tid;
    pthread_attr_t attr_playout, attr_capture;

    for(i=0;i<NUM_FRAMES; i++) {
        angle= (16*M_PI*i)/NUM_FRAMES;
	sine_wave.frame[i].right = 32767.*sin(angle);
	sine_wave.frame[i].left = 32767.*cos(angle);
    }

    if(jtt_init(SAMPLE_RATE*4*sizeof(frame_t))<0){
        printf("Out of memory!\n");
	exit(0);
    }

    mlockall(MCL_CURRENT | MCL_FUTURE);
    thread_create(&playout_tid, &attr_playout, 99, playout, NULL);
    thread_create(&capture_tid, &attr_capture, 99, capture, NULL);

    while(1){
        sleep(10);
    }
}

The code for thread_create follows and please observer how and which and to what value the thread attributes are set. Is this messed up?
> /* posix thread initializer */
int thread_create(pthread_t* tid, pthread_attr_t* attr, int prio, void * fct, void * arg){
	int err=0;
	struct sched_param sch;

	if(pthread_attr_init(attr)<0)
		err=1;
	if(pthread_attr_setscope(attr,PTHREAD_SCOPE_PROCESS)<0)
		err+=2;
	if(pthread_attr_setschedpolicy(attr, SCHED_FIFO)<0)
		err+=4;
	sch.sched_priority = prio;
	if(pthread_attr_setschedparam(attr,&sch)<0)
		err+=8;
	if(pthread_create(tid, attr, fct, arg)<0)
		err+=16;
	if(err)	{
		printf("thread create error %d\n",err);
		return -1;
	}
	return 0;
}


A couple of functions that I wrote which came in handy to measure response time:
> /* hi res timers */
typedef unsigned long long nano_time_t;
nano_time_t tickGet(void){
	struct timespec ts;
	clock_gettime(CLOCK_MONOTONIC, &ts);
	return (nano_time_t)ts.tv_nsec + BILLION * (nano_time_t)ts.tv_sec;
}
void nano_sleep(nano_time_t arg){
	struct timespec ts;
	ts.tv_sec  = arg/BILLION;
	ts.tv_nsec = arg%BILLION;
	nanosleep(&ts,NULL);
}


Based on the following I assume i should have a response time on the order of 5mSec.
> kernel.sched_child_runs_first = 0
kernel.sched_min_granularity_ns = 1000000
kernel.sched_latency_ns = 5000000
kernel.sched_wakeup_granularity_ns = 1000000
kernel.sched_shares_ratelimit = 250000
kernel.sched_shares_thresh = 4
kernel.sched_features = 15834235
kernel.sched_migration_cost = 500000
kernel.sched_nr_migrate = 32
kernel.sched_time_avg = 1000
kernel.sched_rt_period_us = 1000000
kernel.sched_rt_runtime_us = 950000
kernel.sched_compat_yield = 0

Whew! Anybody still awake? Okay now for the question. Try as I might I couldn't get anywhere near a 5mSec consistent response time by tuning the thread attributes; however, as soon as I started my process with nice --1, low and behold, 99% of the time I hit 5-6 mSec.

What's going on?:confused:

Peace everybody,
Gary H

---


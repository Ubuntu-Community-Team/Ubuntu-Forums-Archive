---
title: "C++ multi thread, slow???? boost::thread"
date: 2009-02-05
forum: Programming Talk
---

### Post by TamisLaan on 2009-02-05
Hello people,

I am experimenting with multi-threading and i am hitting a performance barrier. 

I am executing the following bit of code:
```

#include <boost/thread/thread.hpp>
#include <iostream>
using namespace std;
using namespace boost;


struct kernel
{
	float *dat;
	int from;
	int to;
	void operator()()
	{
		for(int j=0;j<100;j++)
		{
			for(int i = from; i<to;i++)
			{
				dat[i]=(clock()%657735296874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				dat[i]=(clock()%657735296874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				dat[i]=(clock()%65752796874%324294534085%6532409824%3463257234%6897346346362%7834924)/(457839457%28397897983/6%923409854);
				dat[i]=(clock()%6532547796874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397893467983/6%346923409854);
				dat[i]=(clock()%657796874%32435435329085%65324036434639824%346364353257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				dat[i]=(clock()%657793466874%32346429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				dat[i]=(clock()%657734696874%34362429085%653632409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				dat[i]=(clock()%657346796874%32429085%6532436409824%3463257234%6897362%7834924)/(457839457%2839789798363/6%934623409854);
				dat[i]=(clock()%65725234796874%32429085%6532409824346%3463257234%6893467362%7834924)/(457839457%28397897983/6%923409854);
			}
		}
	}
};

int main()
{
	float data[99999];
	kernel thrd01_kernel;
	kernel thrd02_kernel;

	thrd01_kernel.from = 0;
	thrd01_kernel.to = 99999;
	thrd01_kernel.dat = data;

	thrd02_kernel.from = 50000;
	thrd02_kernel.to = 99999;
	thrd02_kernel.dat = data;

    clock_t start, finish;
    start = clock();
    thrd01_kernel.operator ()();
    finish = clock();
    cout << "single thread (seconds): "<< ((double)(finish - start))/CLOCKS_PER_SEC << endl;

    thrd01_kernel.from = 0;
    thrd01_kernel.to = 50000;

    start = clock();

    thread thrd01_run(thrd01_kernel);
    thread thrd02_run(thrd02_kernel);
    thrd02_run.join();
    thrd01_run.join();

    finish = clock();
    cout << "2 threads (seconds): "<< ((double)(finish - start))/CLOCKS_PER_SEC << endl;
}

```

I am running this simply as a experiment but the problem is is that when using 2 threads instead of one, the computation time of 2 threads is always slower.

At first i was using stdlib rand() function but this made the processing time of 2 threads 15x greater!.

Am i missing something here? I am compiling with -lboost_thread.

---

### Post by TamisLaan on 2009-02-05
Ugh, this is another test i just made using pthread. 

```

#include <pthread.h>
#include <iostream>
using namespace std;


void *scram(void *dat)
{
	for(int k=0;k<2;k++)
	{
		for(int j=0;j<99999;j++)
		{
			for(int i = 0; i<99999;i++)
			{
				((float*)dat)[i]=(657735296874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657735296874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(65752796874%324294534085%6532409824%3463257234%6897346346362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(6532547796874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397893467983/6%346923409854);
				((float*)dat)[i]=(657796874%32435435329085%65324036434639824%346364353257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657793466874%32346429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657734696874%34362429085%653632409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657346796874%32429085%6532436409824%3463257234%6897362%7834924)/(457839457%2839789798363/6%934623409854);
				((float*)dat)[i]=(65725234796874%32429085%6532409824346%3463257234%6893467362%7834924)/(457839457%28397897983/6%923409854);
			}
		}
	}
	return NULL;
};

void *scram2(void *dat)
{
	for(int k=0;k<1;k++)
	{
		for(int j=0;j<99999;j++)
		{
			for(int i = 0; i<99999;i++)
			{
				((float*)dat)[i]=(657735296874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657735296874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(65752796874%324294534085%6532409824%3463257234%6897346346362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(6532547796874%32429085%6532409824%3463257234%6897362%7834924)/(457839457%28397893467983/6%346923409854);
				((float*)dat)[i]=(657796874%32435435329085%65324036434639824%346364353257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657793466874%32346429085%6532409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657734696874%34362429085%653632409824%3463257234%6897362%7834924)/(457839457%28397897983/6%923409854);
				((float*)dat)[i]=(657346796874%32429085%6532436409824%3463257234%6897362%7834924)/(457839457%2839789798363/6%934623409854);
				((float*)dat)[i]=(65725234796874%32429085%6532409824346%3463257234%6893467362%7834924)/(457839457%28397897983/6%923409854);
			}
		}
	}
	return NULL;
};

int main()
{


    //cout << "CPU cores in system: "<< thread::hardware_concurrency() << endl;
    cout << "initiating test" << endl;
	float data[99999];
	float data1[99999];
	float data2[99999];

    pthread_t thread1, thread2;

    clock_t start2, finish2;
    start2 = clock();
    pthread_create( &thread1, NULL, scram2, (void*) data1);
    pthread_create( &thread2, NULL, scram2, (void*) data2);
    pthread_join( thread1, NULL);
    pthread_join( thread2, NULL);
    finish2 = clock();
    cout << "2 threads (seconds): "<< ((double)(finish2 - start2))/CLOCKS_PER_SEC << endl;

	clock_t start, finish;
    start = clock();
    scram(data);
    finish = clock();
    cout << "single thread (seconds): "<< ((double)(finish - start))/CLOCKS_PER_SEC << endl;

}

``` 

Same thing as with using boost threads, 1 thread is faster then 2.

Any one willing to confirm this??

---

### Post by dribeas on 2009-02-05
> **TamisLaan said:**
> I am running this simply as a experiment but the problem is is that when using 2 threads instead of one, the computation time of 2 threads is always slower.

At first i was using stdlib rand() function but this made the processing time of 2 threads 15x greater!.

Am i missing something here? I am compiling with -lboost_thread.

I would review the experiment, specially how the time is meassured. I have compiled your own code in to executables, the first one only runs the 1 thread test, while the second runs the 2 thread test:

```

dribeas@golden:~/code/test/boost_thread$ time ./cmp 
single thread (seconds): 28.31

real	0m28.346s
user	0m15.665s
sys	0m12.653s
dribeas@golden:~/code/test/boost_thread$ time ./cmp 
2 threads (seconds): 30.55

real	0m15.501s
user	0m15.549s
sys	0m15.017s

```

clock() will give you an estimate of the processing time spent by your application. As you can see in the experiment above, the multithreaded version takes considerably less real time, while it does take more computation time. Adding more threads will add computations to your program, but if you have enough processors the paralelization will reduce the time it takes to perform all operations. 

Also note that while the user time spent in both experiments is roughly the same (15.5 / 15.6 seconds) while the system overhead in the second experiment is greater than the first (15 / 12.6 seconds), that amounts for most of the difference identified by clock().

---

### Post by kavon89 on 2009-02-06
Are you sure you are splitting the work in half and allowing both threads to work in parallel on their respective halves of the computation? If you've got a processor that is good with multiple threads (dual core, hyper-threading) it should end up being much quicker.

---


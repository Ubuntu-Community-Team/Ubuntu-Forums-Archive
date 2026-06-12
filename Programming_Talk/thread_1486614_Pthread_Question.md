---
title: "Pthread Question"
date: 2010-05-18
forum: Programming Talk
---

### Post by loderunner88 on 2010-05-18
Hi Everyone,
I am working on a project for my senior design which utilizes the pthread library. I am trying to get a setup where threads use different priority values and use the CPU at different rates.
I have setup a trial system to test this but have been unable to achieve the desired results. 
Here is the output of the code:
It can be observed that the priority of 50 is never set to the program itself. The attr value takes the priorty, but after a pthread_create the value is once again set to zero. I thought this might be related to having a realtime linux kernel, but even after installing linux-rt using aptitude i still achieve the same results. Any thoughts would be helpful. I cant seem to set PTHREAD_SCOPE_PROCESS either. Is this the reason that the priorities aren't sticking? 

Also, pthread_setschedparam and pthread_getschedparam result in segfaults after upgrading to ubuntu 10.04 .This is a separate issue, but if someone has ideas on this I would be very helpful as well.

```
Creating Cntrl thread.
Control: Initial thread settings.
  priority = 0
 scope error = 95
 new priority = 50
 get attr policy = 2
 get attr param  = 50
 get attr scope  = 0
 post: attr paramtr = 50
 post: new priority = 50
 post: attr policy = 2
 post: attr scope  = 0
Control: check settings.
  final priority = 0
  final policy   = 0
Cntrl thread created sucessfully

```

```
void Cntrl::Create(pthread_t &thrd)
{

    cerr << "Creating Cntrl thread." << endl;
    int policy = SCHED_RR, error, ans_policy,ans_scope;
    struct sched_param param,ans_param;
    memset(&param, 0, sizeof(param));

    pthread_attr_t attr;

   error = pthread_attr_init( &attr);              // init attriutes to default values
       //pthread_getschedparam(thrd, &policy, &param);
    cerr << "Control: Initial thread settings." << endl;
    cerr << "  priority = " << param.sched_priority << endl;
    //cerr << "  curpriority = " << param.sched_curpriority << endl;

    if (error)
    {
        cerr << " Control: pthread attribute error = "<< error << endl;
    }
    else
    {
        param.sched_priority = CNTRL_PRIORITY;
        /* set the scheduling algorithm to PROCESS or SYSTEM */
        //pthread_setschedparam(thrd, policy, &param);    // sets param to use policy
        error = pthread_attr_setscope(&attr, PTHREAD_SCOPE_PROCESS);
        if(error){
            cerr << " scope error = " << error<< endl;
        }
        pthread_attr_setschedpolicy(&attr, SCHED_RR);
        pthread_attr_setschedparam(&attr, &param);      // set atribte to us param
        pthread_attr_getschedparam(&attr, &ans_param);      //
        pthread_attr_getschedpolicy(&attr, &ans_policy);      //
         pthread_attr_getscope(&attr, &ans_scope);      //
        cerr << " new priority = " << param.sched_priority << endl;
        cerr << " get attr policy = " << ans_policy << endl;
        cerr << " get attr param  = " << ans_param.sched_priority << endl;
        cerr << " get attr scope  = " << ans_scope << endl;
        //  pthread_create
        //  1)  thrd -- an opaque return value
        //  2)  NULL -- opaque attribute value
        //  3)  start_routine --
        //  4)  arg -- arg for start routine
        /* Set up the threads priority */
        pthread_create(&thrd, &attr, thrd_cntrl_comm, this);
        pthread_attr_getschedparam(&attr, &ans_param);      //
        cerr << " post: attr paramtr = "  << ans_param.sched_priority << endl;
        cerr << " post: new priority = " << ans_param.sched_priority << endl;
        pthread_attr_getschedpolicy(&attr, &ans_policy);      //
        cerr << " post: attr policy = " << ans_policy << endl;
        pthread_attr_getscope(&attr, &ans_scope);      //
        cerr << " post: attr scope  = " << ans_scope << endl;
        pthread_getschedparam(thrd, &ans_policy, &ans_param);
        cerr << "Control: check settings." << endl;
        cerr << "  final priority = " << ans_param.sched_priority << endl;
        cerr << "  final policy   = " << ans_policy << endl;


        cerr << "Cntrl thread created sucessfully" << endl;
    }
}
```

---

### Post by dwhitney67 on 2010-05-18
I guess you decided that it wasn't worth checking for errors with these two statements?
```

pthread_attr_setschedpolicy(&attr, SCHED_RR);
pthread_attr_setschedparam(&attr, &param);

```
My information may be dated because Linux is always changing their man-pages, but IIRC, one needs to run their code as a privileged (ie root) user when attempting to use a scheduling policy other than SCHED_OTHER; otherwise the scheduling policy defaults to SCHED_OTHER.

---

### Post by loderunner88 on 2010-05-18
Hi there,
Thanks for the response.
I tried the following:
```
        errpolicy=pthread_attr_setschedpolicy(&attr, SCHED_RR);
        errparam=pthread_attr_setschedparam(&attr, &param);      // set atribte to us param
	cerr<<"error policy= "<<errpolicy<<endl;
	cerr<<"error param= "<<errparam<<endl;
```

and they both outputted a 0 which I believe means execution was successful.
```
error policy= 0
error param= 0

```

I also tried running the program as sudo and I still got final priority=0
Any ideas?

---

### Post by loderunner88 on 2010-05-19
So I found out why 
```
pthread_getschedparam(thrd, &policy, &param);

``` 
was causing problems. thrd needed to be created via pthread_create() first.

I am still however unable to set priorities. Anyone?

---


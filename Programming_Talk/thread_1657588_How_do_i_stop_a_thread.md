---
title: "How do i stop a thread?"
date: 2011-01-01
forum: Programming Talk
---

### Post by cftmon on 2011-01-01
I want my thread to stop as soon as the main thread finishes. My thread contains code that changes the channel of a wireless adapter through ioctl calls.It contains a infinite loop. 


Problem is that the thread still keeps running even after i call pthread_exit. Is something missing here?I tried pthread_kill and it exits the entire program instead.

```
void* changeChannel(void* args)
{
   
    while(true)
   {
          //change channel here..
   }

}
//main thread
   pthread_t chgchannel;
   int t = pthread_create(&chgchannel,NULL,&changeChannel, (void *)devName.c_str() );
   
   if(t)
   {
      std::cout << "fail" << std::endl;
   }
   
   pcap_loop(handler,100,procPacket,NULL); // packet capturing
   std::cout << "got:"+client << std::endl;
   std::cout << "finished" << std::endl;
   pthread_exit(&chgchannel);
```

---

### Post by MadCow108 on 2011-01-01
see pthread_cancel
[http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_cancel.3.html](http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_cancel.3.html)

you could also use a global/threadlocal variable for the while loop which gets changed by the mainthread or on signal from main thread (from pthread_kill)
```

void thread() {
  while(keep_running){
  ...
  }
}

```

---

### Post by cftmon on 2011-01-01
somehow using pthread_cancel and/or global variables give me  segmentation fault :confused:
```
void thread() {
  while(sig!=-1){
  ...
  }
}
```

---

### Post by MadCow108 on 2011-01-01
do you still have this in the code?
pthread_exit(&chgchannel);
this is wrong, pthread_exit takes a pointer the return value, not the a pointer to the thread handle

also (void *)devName.c_str() in pthread_create is unsafe.
if devName goes out of scope before the thread has copied it you have a problem.

else please post more code.

---

### Post by cftmon on 2011-01-02
> **MadCow108 said:**
> do you still have this in the code?
pthread_exit(&chgchannel);
this is wrong, pthread_exit takes a pointer the return value, not the a pointer to the thread handle

also (void *)devName.c_str() in pthread_create is unsafe.
if devName goes out of scope before the thread has copied it you have a problem.

else please post more code.

thanks for the info, yea i removed pthread_exit, i need to use (void *)devName.c_str() as the thread requires a device name to call the driver.Or the compiler would complain

As for the segmentation faults, it was not the threading problem but rather my codes went haywire in a thread.I confirmed this with a simple cout in the thread.
Strange thing is that it worked okay when i fork() it. 
I post the code for everyone to see(scrutinize):lolflag: Anyone good with ioctl calls? I am still new to it.

```

#include <linux/wireless.h>
//changing of channels
void* changeChannel(void* args)
{

       char* devName = (char*) args;
       int channel = 0;
       int fd = sock_open();
       struct iw_freq  freq;
       freq.e=0;
       while(true)
       {
           
           struct iwreq* reqDev;
            sleep(2);

            freq.m =channel++;
            freq.flags=IW_FREQ_FIXED;
            reqDev->u.freq = freq;//segfault seeems to come from here?
            strncpy(reqDev->ifr_name, devName, IFNAMSIZ);
            ioctl(fd, SIOCSIWFREQ , reqDev);          
            if(channel==14)
            {
                channel=0;
            }            
       }
}
``````

//here create a thread to changing channels, and start capturing packets. devName is a std::string that contains a device name 
   pthread_t chgchannel;
   int t = pthread_create(&chgchannel,NULL,&changeChannel, (void *)devName.c_str() );  
   if(t)
   {
      std::cout << "fail" << std::endl;
   } 
   pcap_loop(handler,200,procPacket,NULL);
   std::cout << "got:"+client << std::endl;
   std::cout << "finished" << std::endl;
pthread_cancel(chgchannel);
```

---


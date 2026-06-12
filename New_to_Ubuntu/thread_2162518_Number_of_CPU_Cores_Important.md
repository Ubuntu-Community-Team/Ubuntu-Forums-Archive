---
title: "Number of CPU Cores Important?"
date: 2013-07-14
forum: New to Ubuntu
---

### Post by incurablegeek on 2013-07-14
I do know that Ubuntu can run on minimal resources, one of the reasons I'm moving away from Microsoft operating systems.

Does it make any difference the number of cores in an AMD CPU? Is there a performance boost with more cores due to Ubuntu's ability to multi-thread programs?

Thanks - and my apologies if this is yet another doltish question. I just need to purchase another CPU for my Ubuntu board, and really would like to know how best to spend/save my money.

---

### Post by silv3rm00n on 2013-07-14
more cpu cores mean more processing power, so performance boost.

---

### Post by incurablegeek on 2013-07-14
Thank you so much, silv3rm00n.

I've done some reading since my post and it appears that Ubuntu can take advantage of multi-core processors. I'm curious if it's possible to tell _which programs to use which cores_ or does Ubuntu desktop do that for you.

Also, since I'm locked into AMD ++ need to save money if possible, do you think the[SIZE=2] AMD FX-6300[/SIZE] is a _wise choice_?    [http://www.newegg.com/Product/Product.aspx?Item=N82E16819113286](http://www.newegg.com/Product/Product.aspx?Item=N82E16819113286)

Thanks again for the advice.

---

### Post by 3rdalbum on 2013-07-15
The operating system handles the multiprocessing for you. You can't specify "This program should use Core #2", it will be moved between cores and use multiple cores whenever necessary. Programs must be written to use multiple threads before they will use multiple cores simultaneously, but of course you can run multiple intensive programs at the same time and they will be allocated to different cores automatically.

In short, it is all taken care of for you.

---

### Post by slickymaster on 2013-07-15
The improvement in performance gained by the use of a multi-core processor depends very much on the software algorithms used and their implementation. In particular, possible gains are limited by the fraction of the software that can be run in parallel simultaneously on multiple cores.
The Ubuntu kernel is configured to support 8 processors / cores in 32-bit, and 64 processors / cores in 64-bit.

---

### Post by Cheesemill on 2013-07-15
> **3rdalbum said:**
> The operating system handles the multiprocessing for you. You can't specify "This program should use Core #2"

Actually you can set the affinity of a process to use a specific core using the taskset command. However this is usually always a bad idea as the Linux kernel is ***much*** better than a human will ever be at assigning threads to the best core.

---

### Post by incurablegeek on 2013-07-15
> the use of a multi-core processor depends very much on the software  algorithms used and their implementation. In particular, possible gains  are limited by the fraction of the software that can be run in parallel  simultaneously on multiple cores.

Yes, I do know that of course. I think as a result I phrased my question very poorly.

I should have asked:

1) Is there a list of open source programs that actually do support multi-threading?

2) Can Ubuntu Desktop act as a traffic cop and direct programs _**not written**_ for multi-threading to use different cores - or - _**does Ubuntu push all programs through a single core**_, leaving the other cores unused. I have noticed with Windows 7, for example, that, if I am running several programs at a time, all 6 cores are being used. I'm guessing that an AV program, for example, gets shoved into 1 core and so on down the line - or - that Windows actually _**parses single-threaded programs**_ up and runs them as efficiently as possible through all cores (although I don't think that is possible).

Sorry to be so persistent, but it's really not an easy problem to answer I would think. But then I am very new to Ubuntu.

---

### Post by Cheesemill on 2013-07-15
The Linux kernel will run processes on the same core if that is the most efficient way of handling the current system load.  If it's more efficient to run them on different cores instead then it will do that.

Basically you never have to worry about this sort of thing yourself. The gurus who write the Linux kernel put a lot of effort into the scheduler to make sure that it makes the correct decisions as to which process to run on which core.

---

### Post by incurablegeek on 2013-07-15
Cheesemill, THAT was the answer I was hoping for. Thank you so much.

Btw, I don't know if I posted this before but here is an eye-opening article about the bloated Windows kernel: [http://blog.zorinaq.com/?e=74](http://blog.zorinaq.com/?e=74)

I really, truly spent weeks reading up on MS "New Direction" with Windows 8, 8.1 and Server 2012. And as you can tell already from my posts, I'm the kind of person who want to know everything - in great detail. Well, from that reading I came away with the knowledge that Microsoft is like a ship without a rudder. I am a Linux convert. Long overdue, I know.

Thank you so much for tolerating my persistence.

Q.E.D. :KS

---

### Post by Paqman on 2013-07-15
You'll find that the kernel is extremely efficient at handling this. It's not just a case of a single program being assigned to a single core. The kernel has to handle dozens of processes simultaneously. A single application could spawn several processes, or it might be just one. The OS also has numerous processes for it's own use. The kernel is continuously managing the demands of all these processes, which includes swapping them between cores on the fly to manage the load in the most effective manner. A single process could be swapped from one core to another rapidly if the demand required it.

Linux is very good at things like this and memory management. Significantly better than Windows, apparently. It's one of the reasons why Linux has such a good reputation as a reliable workhorse for really demanding computing tasks.

---


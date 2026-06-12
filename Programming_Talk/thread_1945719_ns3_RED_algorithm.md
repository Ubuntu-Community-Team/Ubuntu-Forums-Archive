---
title: "ns3 RED algorithm"
date: 2012-03-23
forum: Programming Talk
---

### Post by cshekhar on 2012-03-23
[https://github.com/talau/ns-3-tcp-red/blob/master/scratch/red-test-1and3.cc](https://github.com/talau/ns-3-tcp-red/blob/master/scratch/red-test-1and3.cc)
i want to run this code . & analyse the output . But some there is some error,so not able to build . 
i am getting following error :

chander@chander-laptop:~/ns-allinone-3.13/ns-3.13$ ./waf
[B]Waf: Entering directory `/home/chander/ns-allinone-3.13/ns-3.13/build'
[1600/1662] cxxprogram: build/scratch/red-queue.cc.2.o -> build/scratch/red-queue
scratch/red-queue.cc.2.o: In function `CheckQueueSize(ns3::Ptr<ns3::Queue>)':
/home/chander/ns-allinone-3.13/ns-3.13/build/../scratch_/red-queue.cc:63: undefined reference to `ns3::RedQueue::GetQueueSize()'_
collect2: ld returned 1 exit status
Waf: Leaving directory `/home/chander/ns-allinone-3.13/ns-3.13/build'
Build failed
[/B]
i have underlined the error.
also this is the 63 line .in which there is error
 uint32_t qSize = StaticCast<RedQueue> (queue)->GetQueueSize ();

Guys just help me out on this !!
thanks

---

### Post by nothingspecial on 2012-03-24
*Thread moved to **Programming Talk**.*

---

### Post by Zugzwang on 2012-03-26
@OP: The error that you are getting is an error that is an error in the linking stage of building a program. There are three main causes of this error:

[LIST]
[*]The function under concern has been forgotten to be implemented.
[*]You are missing an object file to link against
[*]There is something wrong with [name mangling]("http://en.wikipedia.org/wiki/Name_mangling").
[/LIST]

The last problem typically occurs when compiling against a C library from a C++ program and probably not of significance here. The first two possible causes, along with causes I cannot think of right now, remain.

For the first one, check where the function GetQueueSize() of the RedQueue class is actually implemented. It is not the line "uint32_t qSize = StaticCast<RedQueue> (queue)->GetQueueSize ();" that causes the problem! As the "GetQueueSize" function has been declared, it should be implemented somewhere.

For the second possible cause, note that we (people reading in this forum) have no clue what "waf" is. So we don't know how your building process works and can't help you with that. If you think that the problem is here, please explain what "./waf" is, what it does, etc.

---


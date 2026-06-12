---
title: "Help with Boost.thread"
date: 2010-01-07
forum: Programming Talk
---

### Post by pholding on 2010-01-07
I'm new to boost.thread and I'm trying to write a quick c++ program where both the main thread and the worker thread are executing at the same time. The code is just two for loops counting from 0 to 4. Looking at the console output it seems the program is being executed sequentially rather than both the main function and worker function running in parallel.
 
Could someone please point out where I'm going wrong.
 
The code I've got is as follows:
 
```
#include <iostream>
#include <boost/thread.hpp>
void workerFunc()
{
    std::cout << "Worker: running " << std::endl;
    for (int i = 0; i < 5; i++){
      std::cout << "Worker " << i << std::endl;
    }
    std::cout << "Worker: finished" << std::endl;
}
int main(int argc, char* argv[])
{
    std::cout << "main: startup" << std::endl;
    boost::thread workerThread(workerFunc);
    std::cout << "main: waiting for thread" << std::endl;
    for (int j = 0; j < 5 ; j++){
      std::cout << "main: " << j << std::endl;
    }
    workerThread.join();
    std::cout << "main: done" << std::endl;
    return 0;
}
```
 
The result of the program is as follows
> main: startup
Worker: running
Worker 0
Worker 1
Worker 2
Worker 3
Worker 4
Worker: finished
main: waiting for thread
main: 0
main: 1
main: 2
main: 3
main: 4
main: done


---

### Post by johnl on 2010-01-07
This may be because the time it takes for your thread to run to completion is smaller than the the time slice allocated for that thread to run.  Try adding some sleeps in the loop:

```

#include <iostream>
#include <boost/thread.hpp>
#include <unistd.h>

void workerFunc()
{
    std::cout << "Worker: running " << std::endl;
    for (int i = 0; i < 5; i++){
      std::cout << "Worker " << i << std::endl;
      sleep(1);
    }
    std::cout << "Worker: finished" << std::endl;
}
int main(int argc, char* argv[])
{
    std::cout << "main: startup" << std::endl;
    boost::thread workerThread(workerFunc);
    std::cout << "main: waiting for thread" << std::endl;
    for (int j = 0; j < 5 ; j++){
      std::cout << "main: " << j << std::endl;
      sleep(1);
    }
    workerThread.join();
    std::cout << "main: done" << std::endl;
    return 0;
}

```

In other words, your code is fine -- it's just that as an example the time spent in each thread is too small to see the threading happen :)

---

### Post by pholding on 2010-01-07
johnl - Just complied your modification to the code and its now giving the results I expected.
 
Really appreciate the quick response and your help - Thankyou :D

---


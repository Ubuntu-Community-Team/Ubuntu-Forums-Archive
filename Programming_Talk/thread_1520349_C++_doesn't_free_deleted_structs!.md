---
title: "C++ doesn't free deleted structs!"
date: 2010-06-29
forum: Programming Talk
---

### Post by margemoosh on 2010-06-29
hi me and my friend are writing a program but now i found out that delete doesn't work properly in ubuntu for my program but works correctly in windows.
here is a sample code it take 600mb ram and in windows return it to OS but in ubuntu it just reduce from 600mb to 530mb!
i use gcc  4.4.3

```


struct node {
    vector<int> boardPieces;
    vector<node*> childs;
    // int turn;
    // int cappd;
    int black_no;
    int white_no;
    bool opened;
    string move;
    int eval;
}
int main(){
 int i;
    node *a;
    node *nodd = new node;
    for(i=0;i<10000;i++)for(int j=0;j<1000;j++){a=new node;nodd->childs.push_back(a);}
     cout << "done";
     cin >>i;

   for(i=0;i<10000000;i++){delete nodd->childs[i];}
  
    cout << "done";
    cin >> i;
return 0;
}




```

---

### Post by Zugzwang on 2010-06-29
This is no bug. It's just that Linux works differently here as there's normally also per-process memory management and there's no necessity for the process to return unused memory to the kernel immediately. Perhaps someone else know more on this.

---

### Post by margemoosh on 2010-06-29
> **Zugzwang said:**
> This is no bug. It's just that Linux works differently here as there's normally also per-process memory management and there's no necessity for the process to return unused memory to the kernel immediately. Perhaps someone else know more on this.

it's good to know that but i want to know if my program has any memory leaks or something because this structure will create a huge tree and deleting it may cause memory leaks.
so is there anyway that i can make my process return memory as i call delete?

---

### Post by soltanis on 2010-06-29
Well I'm not very familiar with C++ vectors but if you are using them correctly, then there should be no problem with freeing memory that you allocate.

Zugzwang is correct; the Linux kernel has an aggressive tendency to do what is called "caching memory". Linux, unlike Windows, recognizes a very important fact about RAM: there's no point in having it if you aren't using it. Take for example, this server (which has been running for 28 days):

```

$ free -m
             total       used       free     shared    buffers     cached
Mem:          1883       1826         57          0        172       1438
-/+ buffers/cache:        215       1668
Swap:         3775          0       3775
# free memory, in Megabytes (-m)

```

Almost all of this server's memory has been set aside, but as you can see, almost all of that is cached memory (with a small amount of free memory kept by the kernel in case a program requests it quickly). In other words, the kernel is in no hurry to reclaim memory pages back from a process, especially since it sounds like your program will probably just ask for them to be allocated again.

Whenever your system is low on memory and needs to set aside more pages, the kernel will automatically drop (or flush) the cached pages that haven't been used for the longest amount of time (incurring a small overhead while it combs through your memory doing so) and then allocates the memory for you.

In really low memory situations, you'll start swapping pages onto the disk.

[http://egloo.wordpress.com/2008/10/29/linux-cached-memory/](http://egloo.wordpress.com/2008/10/29/linux-cached-memory/)

P.S. If you want to know if you have real memory leaks, then I suggest compiling with the debugging flag on (-g) and running your program with Valgrind, an exceptional tool for detecting leaks.

---

### Post by dwhitney67 on 2010-06-29
You're worried about something that is really a non-issue.  If you take care of managing your applications allocated memory in a proper manner, you will have nothing to worry about.  Whether you allocate 10 items or 10 million, you still manage the memory in the same fashion, do you not?

Consider using boost's smart-pointers (or even C++'s tr1 smart-pointers), if you want to avoid having to rely on 'delete'.

---

### Post by margemoosh on 2010-06-29
thanks for the answers i think i dont have memory leaks:p
i just add some line to my code to reallocate that memory again and i after that my uses memory for this program was still 500mb.
it's good to know linux has thins like that!
i think my program will run faster in linux than windows:lolflag:

---

### Post by MadCow108 on 2010-06-29
use [valgrind](http://valgrind.org/) on your program, it will tell you if you have a (non-logical) memory leak or not (as long as it is encountered in the execution path).

---

### Post by Sockerdrickan on 2010-06-30
node *a;

    for(i=0;i<10000;i++)for(int j=0;j<1000;j++){a=new node;nodd->childs.push_back(a);}

i and j loops make no sense, you are losing 9999*1000 nodes because you are assigning childs all over without deleting first
i<1 would do it I guess

---

### Post by schauerlich on 2010-06-30
> **Sockerdrickan said:**
> i and j loops make no sense, you are losing 9999*1000 nodes because you are assigning childs all over without deleting first
i<1 would do it I guess

He's pushing them onto the vector, not overwriting them. A weird way of doing it, but I guess it works.

---

### Post by Sockerdrickan on 2010-07-01
> **schauerlich said:**
> He's pushing them onto the vector, not overwriting them. A weird way of doing it, but I guess it works.
This code makes my insides twist

---

### Post by dwhitney67 on 2010-07-01
I'm not sure why the OP felt compelled to create tens million child nodes; perhaps it was a stress test?

Here's a way to do it, but mitigating the need to call delete to free memory.
```

#include <boost/shared_ptr.hpp>
#include <vector>


class Node;
typedef boost::shared_ptr<Node> NodePtr;

struct Node
{
   std::vector<NodePtr> childs;
   //...
};


int main()
{
   const int N = 1000;  // I want the program to end in my lifetime; I could not wait for 10 million allocations.

   NodePtr nodd(new Node);

   for (int i = 0; i < N; ++i)
   {
      nodd->childs.push_back(NodePtr(new Node));
   }

   // all memory will be auto de-allocated when program exits
}

```

---


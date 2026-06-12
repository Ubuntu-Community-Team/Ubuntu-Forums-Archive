---
title: "fwrite probleam in ubuntu server 9.04"
date: 2009-07-28
forum: Programming Talk
---

### Post by ThomasHu on 2009-07-28
I save much video and audio data in ubuntu server 9.04. I found used memory increased in a crazy speed. I checked my program with valgrind and I didn't find any memory leak.
So I write a simple program ,like this:

#include <stdio.h>
#include <string>

int main()
{
    FILE * f = NULL;
    f = fopen("a.txt", "a+t");
    if (f == NULL)
        return 1;
    std::string msg = "This is a test!\n";
    do {
        fwrite(msg.c_str(), 1, msg.size(), f);
        fflush(f);
       usleep(1000);
    } while (true);
    fclose(f);
    return 0;
}

Then I still find the used memory still increase(use command "**top**").

the problem is:
1.Used memory increased at 124k;
2.Mem buffers increase at 4k;
3.swap memory isn't used;
4.after used memory nearly reach total memory, it don't increase. Sometimes used memory decreased.

Who can help me?

---

### Post by dwhitney67 on 2009-07-28
I rewrote your program in C++, as opposed to using your abomination of C++ and C.

My system did not have the memory problem you indicated.  The memory usage remained steady at 0.2% of my system's memory.  CPU utilization varied, but was never higher than 2%.

I have an old notebook, with a 1.4 GHz CPU, and 512 MB of memory.  It is running Ubuntu 9.04.

Here's the rewritten code:
```

#include <string>
#include <fstream>
#include <unistd.h>

int main()
{
   std::fstream file("a.txt", std::ios::out | std::ios::app);

   if (!file) {
      return 1;
   }

   const std::string msg = "This is a test!";

   do {
      file << msg << std::endl;
      usleep(1000);
   } while (true);
}

```

---

### Post by ThomasHu on 2009-07-28
At first I must thank you very much.
I try your code. But I find that used memory still increased at 124K.
I compile it with g++4.3.3.
I don't know whether it has problem because of g++4.3.3.

> **dwhitney67 said:**
> I rewrote your program in C++, as opposed to using your abomination of C++ and C.

My system did not have the memory problem you indicated.  The memory usage remained steady at 0.2% of my system's memory.  CPU utilization varied, but was never higher than 2%.

I have an old notebook, with a 1.4 GHz CPU, and 512 MB of memory.  It is running Ubuntu 9.04.

Here's the rewritten code:
```

#include <string>
#include <fstream>
#include <unistd.h>

int main()
{
   std::fstream file("a.txt", std::ios::out | std::ios::app);

   if (!file) {
      return 1;
   }

   const std::string msg = "This is a test!";

   do {
      file << msg << std::endl;
      usleep(1000);
   } while (true);
}

```

---

### Post by lisati on 2009-07-28
I re-wrote the program as follows and compiled it with gcc:
[php]
#include <stdio.h>
#define true 1

int main(void)
	{
	FILE * f = NULL;
	char msg[]="This is a test!\n";
	if ((f = fopen("a.txt", "a+t")) == NULL)
		return 1;
	do
		{
		fwrite(msg, 1, sizeof(msg), f);
		fflush(f);
		usleep(1000);
		} while (true);
	fclose(f);
	return 0;
	}
[/php]

I didn't notice any significant increase in memory use above what my system was using when idling.

Minor niggle: when's it meant to stop?

(I use the 64-bit version of 9.04)

---

### Post by ThomasHu on 2009-07-28
I removed g++4.3.3 and install g++3.4.
But the problem still exists.
I don't know why.

> **ThomasHu said:**
> At first I must thank you very much.
I try your code. But I find that used memory still increased at 124K.
I compile it with g++4.3.3.
I don't know whether it has problem because of g++4.3.3.

---

### Post by lisati on 2009-07-28
> **ThomasHu said:**
> At first I must thank you very much.
I try your code. But I find that used memory still increased at 124K.
I compile it with g++4.3.3.
I don't know whether it has problem because of g++4.3.3.

By "memory still increased at 124K" are you referring to the file size or the amount of memory currently in use by your program?

---

### Post by ThomasHu on 2009-07-28
[COLOR=Red]With top command, can you watch the fourth line, the third column " xxxxk used"[/COLOR]

as:
-----------------------------------------------------------------------------------------

Mem:    509308 total,    [COLOR=Red]251604k used[/COLOR],    257704k free,    12900k buffers

-----------------------------------------------------------------------------------------
[B]
In my computer [/B]**%MEM of process is also right. It's 0.2% in my computer.**

> **dwhitney67 said:**
> I rewrote your program in C++, as opposed to using your abomination of C++ and C.

My system did not have the memory problem you indicated.  The memory usage remained steady at [COLOR=Red]**0.2%**[/COLOR] of my system's memory.  CPU utilization varied, but was never higher than 2%.

I have an old notebook, with a 1.4 GHz CPU, and 512 MB of memory.  It is running Ubuntu 9.04.

Here's the rewritten code:
```

#include <string>
#include <fstream>
#include <unistd.h>

int main()
{
   std::fstream file("a.txt", std::ios::out | std::ios::app);

   if (!file) {
      return 1;
   }

   const std::string msg = "This is a test!";

   do {
      file << msg << std::endl;
      usleep(1000);
   } while (true);
}

```

---

### Post by Zugzwang on 2009-07-28
> **ThomasHu said:**
> [COLOR=Red]With top command, can you watch the fourth line, the third column " xxxxk used"[/COLOR]


This isn't the memory used by your program but rather the total amount of memory currently used by all processes on your computer. Increases here are not of your concern - Only watch the line below corresponding to your program. Basically, it is likely that other processes do not "feel" the need to save memory as long as there's still some available, so this might be the reason why you get this effect here.

Note that watching the actual memory consumption of your program using "top" is simpler if you (for example) call the executable of your program "zzz" and press ">" until it is at the top in the list.

---

### Post by ThomasHu on 2009-07-28
I think it's a problem about ubuntu kernel cache.
My program writes [COLOR=Red]1.75MByte [/COLOR]to disk [COLOR=Red]every second[/COLOR] with fwrite function.
So used memory increases in a crazy memory. Used memory rate will reach [COLOR=Red]100%[/COLOR] [COLOR=Red]after 20 minutes[/COLOR].  So it's a serious problem.
If my program don't run, the used memory don't increase.

> **Zugzwang said:**
> This isn't the memory used by your program but rather the total amount of memory currently used by all processes on your computer. Increases here are not of your concern - Only watch the line below corresponding to your program. Basically, it is likely that other processes do not "feel" the need to save memory as long as there's still some available, so this might be the reason why you get this effect here.

Note that watching the actual memory consumption of your program using "top" is simpler if you (for example) call the executable of your program "zzz" and press ">" until it is at the top in the list.

---

### Post by monraaf on 2009-07-28
It's not a problem or a bug it's a feature. Linux makes optimum use of free memory and uses it to cache data. This will improve system performance if you access that data later and it's still in the cache. Don't worry about it, Linux will free up some memory when it's needed.

---

### Post by ThomasHu on 2009-07-28
Thank you all.
Maybe I shouldn't worry about it.

quote=monraaf;7695517]It's not a problem or a bug it's a feature. Linux makes optimum use of free memory and uses it to cache data. This will improve system performance if you access that data later and it's still in the cache. Don't worry about it, Linux will free up some memory when it's needed.[/quote]

---


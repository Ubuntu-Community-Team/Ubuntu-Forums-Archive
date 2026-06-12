---
title: "Check How Much Free RAM in C?"
date: 2007-12-13
forum: Programming Talk
---

### Post by kripkenstein on 2007-12-13
Is there any standard way to find out how much free RAM the computer currently has, in C/C++?

I guess I can do popen and run **free**, then parse the output, but this seems kind of 'hackish' (and won't work on BSD/OpenSolaris/etc., necessarily).

The reason I need this is I'm trying to make it so an app doesn't use too much memory. The simple idea is to check how much free memory the computer currently has, and use some part of that. This is for caching stuff. It is similar to the disk cache, that is, I want to use free and unused memory to speed up my app, but I don't want to use so much memory that swapping occurs.

---

### Post by LaRoza on 2007-12-13
You could try mallocing (if that is a word) a set number of memory, then use that.

If it fails (returns NULL), you try a smaller chunk, etc.

---

### Post by TreeFinger on 2007-12-13
I really have no idea how it would be done. You have made me curious though.

My quick thought was that of checking every memory location and seeing if it is currently claimed by a variable.. and then display the amount of free space. I think that is a pretty terrible idea though.

---

### Post by LaRoza on 2007-12-13
> **TreeFinger said:**
> I really have no idea how it would be done. You have made me curious though.

My quick thought was that of checking every memory location and seeing if it is currently claimed by a variable.. and then display the amount of free space. I think that is a pretty terrible idea though.

Not really. It has the problem of eventual going into swap, so don't try to find the limit that way.

It is basically the same thing I stated, but more precise.

If your app needs a certain amount of space, use the malloc method, if your apps depends on the amount of space available, use the method you stated.

The memory doesn't only hold variables, it holds all code, including functions.

In C, to get a pointer to a function:

[php]
#include <stdio.h>

void function(char*name)
{
    puts(name);
}

int main(int args,char ** argv)
{
    void (*pointerToFunction)(char*);
    pointerToFunction = function;

    pointerToFunction("LaRoza");    

    return 0;
}
[/php]

It outputs "LaRoza". You can assign the pointer to a function to any function, as long as the return type, and parameters are the same.

---

### Post by kripkenstein on 2007-12-13
> **LaRoza said:**
> You could try mallocing (if that is a word) a set number of memory, then use that.

If it fails (returns NULL), you try a smaller chunk, etc.

Hmm, but I can malloc enough memory to start swapping, can't I? If I understand malloc, I wouldn't know if the memory allocated to me is in RAM or in swap.

---

### Post by LaRoza on 2007-12-13
> **kripkenstein said:**
> Hmm, but I can malloc enough memory to start swapping, can't I? If I understand malloc, I wouldn't know if the memory allocated to me is in RAM or in swap.

Yes, that is a problem with it.

How much memory are you going to be using or what do you except the specs will be on the computer?

---

### Post by kripkenstein on 2007-12-13
> **LaRoza said:**
> Yes, that is a problem with it.

How much memory are you going to be using or what do you except the specs will be on the computer?

Well it is an app people might use on lots of computers with different specs. The app can use anywhere from 50-500MB of RAM, the more, the faster things will be. So I want to 'adapt' to the specs automatically, just like the disk caching mechanism does. That is the idea, at least :)

---

### Post by wolfbone on 2007-12-13
$ man sysconf

_SC_PAGE_SIZE
_SC_PHYS_PAGES
_SC_AVPHYS_PAGES

---

### Post by kripkenstein on 2007-12-13
> **wolfbone said:**
> $ man sysconf

_SC_PAGE_SIZE
_SC_PHYS_PAGES
_SC_AVPHYS_PAGES
Thanks! This looks like what I need :)

---

### Post by kripkenstein on 2007-12-13
> **wolfbone said:**
> $ man sysconf

_SC_PAGE_SIZE
_SC_PHYS_PAGES
_SC_AVPHYS_PAGES

Whoops, spoke too soon before. This is close to what I need, but not quite. It gives the actual physical pages free, but I need to ignore pages taken up by the cache. That is, I want my app to use at least some of the memory used by cache. Otherwise, I will always get almost no free memory (since disk caching uses all available memory, as it should).

Sadly sysconf appears not to be able to give any information besides available physical pages - nothing on swap pages used, cache/buffers, etc. So I am back to considering parsing the output of 'free'...

---

### Post by wolfbone on 2007-12-13
You could also try reading /proc/meminfo.

---

### Post by kripkenstein on 2007-12-13
> **wolfbone said:**
> You could also try reading /proc/meminfo.
Thanks, that seems better than parsing 'free', which I see now reads /proc/meminfo.

This isn't perfect in that it is Linux-specific (so it might not work on BSD/Solaris), but I guess it's the best there is.

---

### Post by wolfbone on 2007-12-13
Doh!

---

### Post by Tuna-Fish on 2007-12-13
> **LaRoza said:**
> You could try mallocing (if that is a word) a set number of memory, then use that.

If it fails (returns NULL), you try a smaller chunk, etc.

Only, this never works. Malloc doesn't return null when you are out of mem, it only returns null if you are out of virtual memory for the process. (on 32 bit systems, somewhere between 2 and 3 gb, on 64 bit systems it wont happen...)

Malloc doesn't even reserve the memory actually, there's absolutely nothing stopping you form mallocing a ridiculous amount of memory. To prove a point, I malloced 20gb on a single process once on my machine. I didn't even have that much disk space. All mallocs returned a pointer.

---


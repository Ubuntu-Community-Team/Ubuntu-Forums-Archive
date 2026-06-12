---
title: "Cmake question"
date: 2010-10-19
forum: Programming Talk
---

### Post by zarzor_2010 on 2010-10-19
Hi All,
I have a problem with cache variables in cmake.

I want to check the combiler for a certain flag -C99 flag. So, I used the following statement
CHECK_C_COMPILER_FLAG("-C99" FLAG_OK)

The problem is that we I ran cmake for the first time it said that c99 is not found and set the FLAG_OK variable in CMakeCache.txt to 0.

Now, I fixed the problem =in the compiler to make it support -C99. But cmake doesnot check the flag any more and just keep saying not found. This is becuase the FLAG_OK is already equals to 0 in cache file.

Is there any way to delete the cahce variable. or force cmake to check for the flag every time I run it?

Thanks for your help
Mina

---

### Post by MadCow108 on 2010-10-20
either just delete the cachefile CMakeCache.txt or use the gui/interactive mode to edit the cache:
ccmake or cmake -i

---

### Post by zarzor_2010 on 2010-10-20
Thank you so much for your reply.
 
I tried deleteing the cmake.cache file and it worked fine. But if another user who is not experienced with cmake and tried to compile the code it wount work.
 
even if he fixed the problem, cmake will tell him to fix the -C99 flag.
 
So, is there any way to make it automated for normal users.?
 
Thanks
Mina

---

### Post by zarzor_2010 on 2010-10-21
Any help about this issue please?

Thanks

---

### Post by MadCow108 on 2010-10-22
you do not provide the cache to the user.
So the user would have to change compiler to make this check go wrong after it was cached once.
For things that can change often (like findfile) there is usually a way to reset the cache documented

---

### Post by zarzor_2010 on 2010-10-22
Thank you for your reply.
But I didnot fully understand.

I think that once the user run cmake to compile my code , it will create cmake.cache. Then if he fixed the errors and run cmake again, it wont check for the same flags again becuase it is already cached. And the user maynot know it is because of cmake.cahe and he thinks that he didnot fix the problem yet.


Tank you all for your help
Mina

---

### Post by zarzor_2010 on 2010-10-24
Any help will be appretiated.
 
Thank you

---

### Post by zarzor_2010 on 2010-10-25
Can any one at least recommend a website or a forum where I can ask about cmake.

Thanks

---

### Post by MadCow108 on 2010-10-26
just don't ship the broken cmake script then so the wrong value never gets cached ;)
And provide a readme on how to use cmake

the cmake mailing list would probably be a good place for questions.
[http://www.cmake.org/pipermail/cmake/](http://www.cmake.org/pipermail/cmake/)
But this has been asked before.
The answer is pretty much the same as mine.
CMake is not really designed to not use the cache.

---

### Post by zarzor_2010 on 2010-10-26
Thank you so much for your reply
I have posted an email to cmake list. 
I got the answer, and i thought about sharing it. it may help someone.
 
You can check if the library is not found using if. Then use 
 
>  
unset(variable CACHE) 

 
to remove it from the cache if it is not found. this way cmake can check this variable again.
 
Thank you again

---


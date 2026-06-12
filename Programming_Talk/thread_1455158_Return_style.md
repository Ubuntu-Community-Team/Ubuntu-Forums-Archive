---
title: "Return style"
date: 2010-04-15
forum: Programming Talk
---

### Post by weezerBo on 2010-04-15
When writing / executing a function, I generally have it so if it reaches the last return statement, it basically means it did its job correctly and returns the proper variable. If it's incapable of doing it's job, I exit early with false, NULL, etc. 

Lately I've come across code that does the exact opposite, it exits early on success and if it reaches the end it's assumed to have failed. 

```

if incapable
     return FAIL 
doCode
return WIN

if capable
     do CODE
     return WIN
return FAIL

```


I'm wondering, which do you generally use, and why? Also, are there proper names for exiting on success/failure, or is it just considered a quirk not worthy of documentation?

---

### Post by nvteighen on 2010-04-15
This has been discussed several times here; indeed, I myself remember to have caused one of them because of some code of mine :p

I usually tend to use the "return as soon as possible" idea because it helps to avoid flag variables and writing flow-controlling code designed just to bring the execution to return at the end of the procedure... which kinda defeats the idea of flow control: why use control structures just to have your procedure end anyway?

But, of course, there are times in which "grouping" returns is nicer and maybe even easier to write because, e.g. the cases involved are abstractable in a trivial way that doesn't imply to make your code a huge mess of loops whose only function is to prepare for a return statement.

So, briefly: my general rule is to return immediately, but accept to use other approaches if they fit in nicely :)

EDIT: Heck, I replied totally off-topic! Well, I think people tend to use the "if capable", but I'm not sure.

---

### Post by MindSz on 2010-04-15
I try to go for the "return as soon as you can" approach, just because it saves some lines of code in case of performance-critical stuff (like DSP on embedded systems).

---

### Post by doas777 on 2010-04-15
one of the reasons i do it the other way, is exception handling on funtions. the compiler says the function must return on all possible code paths (including the catch or below the catch block) so I return at the bottom of the try block, and then below the catch/throw return null. 98% of the time though my catch code branches (and thats what throws do), so it can never actually reach the 'return null;' line, but it makes the compiler happy. if it's in a loop, you may even be able to skipp some unneeded iterations by shortcircuiting.

```

try{
   foreach(String s in GetStringListFromDB()){
       if(s == iStringVal)
            return s;
   }
}
catch(Exception e){
     LogErrAndBail(e);
 }
return null;

```

I guess the correct answer is to ask yourself what question will get you the answer first: checking for error, or checking for success.

---

### Post by Reiger on 2010-04-15
Depends on whether or not your code is explicitly fail-fast. E.g. if you have a program capable of opening 5 different file types I'd write code like this:
(a) The file exists -> fail if not
(b) The file is readable -> fail if not
(c) The file type is usable -> fail if not
(d) Attempt to open the file in earnest.

---

### Post by CptPicard on 2010-04-15
I have always had a preference for returning as soon as I can; I feel it makes the algorithm more readable as it shows what the actual value of the function *is* right at the point where it is resolved... otherwise there needs to be more logic that you actually have to follow and calculate in your head to figure out what the final return value actually *is set to*, when it is returned.

---

### Post by slavik on 2010-04-16
> **weezerBo said:**
> When writing / executing a function, I generally have it so if it reaches the last return statement, it basically means it did its job correctly and returns the proper variable. If it's incapable of doing it's job, I exit early with false, NULL, etc. 

Lately I've come across code that does the exact opposite, it exits early on success and if it reaches the end it's assumed to have failed. 

```

if incapable
     return FAIL 
doCode
return WIN

if capable
     do CODE
     return WIN
return FAIL

```


I'm wondering, which do you generally use, and why? Also, are there proper names for exiting on success/failure, or is it just considered a quirk not worthy of documentation?
at face value, there is little difference in the two pieces of code.

either way, it is a comparison and a possible jump

---


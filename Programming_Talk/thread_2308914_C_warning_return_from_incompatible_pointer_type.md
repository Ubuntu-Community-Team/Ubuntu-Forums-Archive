---
title: "C: warning: return from incompatible pointer type"
date: 2016-01-06
forum: Programming Talk
---

### Post by zogboy809 on 2016-01-06
The function below works but the compiler issues a warning and I would like to understand why. Is there a better way to do this?
The function should just return a formatted string that I want to print to stdout and also write to a file in my main program.

> 
format.h: In function &#8216;printDate&#8217;:
format.h:30:2: warning: return from incompatible pointer type [enabled by default]
  return &buffer;
  ^
format.h:30:2: warning: function returns address of local variable [-Wreturn-local-addr]


```

char* printDate() {

    time_t tm;
    struct tm *ltime;

    time( &tm );
    ltime = localtime( &tm );
    ltime->tm_mon++;
    ltime->tm_year += 1900;

    char buffer [50];
    sprintf( buffer, "%02i:%02i:%02i ---- %02i-%02i-%04i",
            ltime->tm_hour, ltime->tm_min, ltime->tm_sec,
                ltime->tm_mday, ltime->tm_mon,  ltime->tm_year  );
    return &buffer;
}

```

---

### Post by Rocket2DMn on 2016-01-06
There are a couple of problems here.  To answer your first question, you would simply ```
return buffer;
``` since buffer is a pointer and is only derefenced when you try to access a char in it, like buffer[0] which is a char.
However, what you're doing is very unsafe, since buffer is stack allocated, that space will be made available to other functions once printDate returns.  You should either malloc the buffer and return the pointer (don't forget to free it!) or pass the buffer pointer as a parameter to printDate.  The latter is my preferred approach since it puts the responsibility of memory management on the code that calls the function.  You should probably also pass in a max length of the buffer and use snprintf instead.

---

### Post by zogboy809 on 2016-01-07
I managed to do it the latter way and now it compiles and runs without errors. I'm not new to programming but I'm new to C from Java so it's taking me a while to get my head around pointers and memory management. Your reply was very helpful, thanks.

---


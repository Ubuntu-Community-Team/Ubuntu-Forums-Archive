---
title: "[C/C++] A Function that Finds the Basename"
date: 2012-06-03
forum: Programming Talk
---

### Post by dodle on 2012-06-03
I am trying to write a function (in C) that finds the basename of a directory in the form of a string. I am having two issues:

1) I get the following error when it is compiled:
```
test.c: In function &#8216;GetBasename&#8217;:
test.c:30: warning: function returns address of local variable
```
I'm not sure how it is that I am passing the address. Aren't I returning the data contained in the string (char*)?

2) The returned value is always an empty string unless I put a print function before the return statement. How is the print function validating the string?

[php]#include <stdio.h>
#include <string.h>

char* GetBasename(char* arg0)
{
  int cmdlen = strlen(arg0);
  int lastdir, hassubdir = 0;
  
  int x;
  for (x = 0; x < cmdlen; x++)
  {
    if (arg0[x] == '/')
    {
      hassubdir = 1;
      lastdir = x;
    }
  }
  
  if (!hassubdir) return arg0;
  
  int start = (lastdir + 1);
  int basenamelen = (cmdlen - start);
  char basename[basenamelen];
  for (x = 0; x < strlen(basename); x++)
  {
    basename[x] = arg0[start];
    start++;
  }
  printf("Hello World!\n"); // String is returned empty if I don't use a print function here
  return basename;
}

int main()
{
  char* test = GetBasename("/foo/bar");
  printf("%s\n", test);
  
  return 0;
}[/php]

Perhaps these two problems are related?

---

### Post by hyper2hottie on 2012-06-03
Your problem is that you are creating the character array basename locally on the stack.  
As a result, when the function return, all of the local variables are destroyed.  So you return the pointer value but the data at that pointer location is not guaranteed to be what you put in it.

I expect that the print function prevents the data at basename from being destroyed because it is being passed into the function, so it stays on the stack.

Try this:
```
[COLOR=#000000][COLOR=#FF8000]
#include <stdio.h>
#include <string.h>

[/COLOR][COLOR=#0000BB]char[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000BB]GetBasename[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]char[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000BB]arg0[/COLOR][COLOR=#007700])
{
  [/COLOR][COLOR=#0000BB]int cmdlen [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]strlen[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]arg0[/COLOR][COLOR=#007700]);
  [/COLOR][COLOR=#0000BB]int lastdir[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]hassubdir [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700];
  
  [/COLOR][COLOR=#0000BB]int x[/COLOR][COLOR=#007700];
  for ([/COLOR][COLOR=#0000BB]x [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000BB]x [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000BB]cmdlen[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000BB]x[/COLOR][COLOR=#007700]++)
  {
    if ([/COLOR][COLOR=#0000BB]arg0[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]x[/COLOR][COLOR=#007700]] == [/COLOR][COLOR=#DD0000]'/'[/COLOR][COLOR=#007700])
    {
      [/COLOR][COLOR=#0000BB]hassubdir [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700];
      [/COLOR][COLOR=#0000BB]lastdir [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]x[/COLOR][COLOR=#007700];
    }
  }
  
  if (![/COLOR][COLOR=#0000BB]hassubdir[/COLOR][COLOR=#007700]) return [/COLOR][COLOR=#0000BB]arg0[/COLOR][COLOR=#007700];
  
  [/COLOR][COLOR=#0000BB]int start [/COLOR][COLOR=#007700]= ([/COLOR][COLOR=#0000BB]lastdir [/COLOR][COLOR=#007700]+ [/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700]);
  [/COLOR][COLOR=#0000BB]int basenamelen [/COLOR][COLOR=#007700]= ([/COLOR][COLOR=#0000BB]cmdlen [/COLOR][COLOR=#007700]- [/COLOR][COLOR=#0000BB]start[/COLOR][COLOR=#007700]);
  [/COLOR][COLOR=#0000BB]char* basename[/COLOR][COLOR=#007700] = (char*)malloc(basenamelen*sizeof(char)); //Changed to malloc to prevent being destroyed on return
  for ([/COLOR][COLOR=#0000BB]x [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700]; [/COLOR][COLOR=#0000BB]x [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000BB]strlen[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]basename[/COLOR][COLOR=#007700]); [/COLOR][COLOR=#0000BB]x[/COLOR][COLOR=#007700]++)
  {
    [/COLOR][COLOR=#0000BB]basename[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]x[/COLOR][COLOR=#007700]] = [/COLOR][COLOR=#0000BB]arg0[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]start[/COLOR][COLOR=#007700]];
    [/COLOR][COLOR=#0000BB]start[/COLOR][COLOR=#007700]++;
  }
  [/COLOR][COLOR=#0000BB]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#DD0000]"Hello World!\n"[/COLOR][COLOR=#007700]); [/COLOR][COLOR=#FF8000]// String is returned empty if I don't use a print function here
  [/COLOR][COLOR=#007700]return [/COLOR][COLOR=#0000BB]basename[/COLOR][COLOR=#007700];
}

[/COLOR][COLOR=#0000BB]int main[/COLOR][COLOR=#007700]()
{
  [/COLOR][COLOR=#0000BB]char[/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000BB]test [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]GetBasename[/COLOR][COLOR=#007700]([/COLOR][COLOR=#DD0000]"/foo/bar"[/COLOR][COLOR=#007700]);
  [/COLOR][COLOR=#0000BB]printf[/COLOR][COLOR=#007700]([/COLOR][COLOR=#DD0000]"%s\n"[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]test[/COLOR][COLOR=#007700]);

  free((void*)test); //Prevent memory leak

  return [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700];
}  
[/COLOR][/COLOR]
```

The casts may or may not be necessary depending on how you compile(C vs C++).

By using malloc you will allocate memory on the heap and it will not be destroyed until you call free.

---

### Post by dodle on 2012-06-04
> **hyper2hottie said:**
> Your problem is that you are creating the character array basename locally on the stack.  
As a result, when the function return, all of the local variables are destroyed.  So you return the pointer value but the data at that pointer location is not guaranteed to be what you put in it.

That sounds very familiar. I think I may have had this same problem before...

Unfortunately it is still not working.

---

### Post by Bachstelze on 2012-06-04
strlen() does not do what you think it does. You can't do strlen(basename) when there's nothing in basename yet.

---

### Post by Bachstelze on 2012-06-04
Your program in general is very confusing. There are a lot of string functions in the standard library. Use them. ;)

```
firas@av104151 ~ % cat test.c 
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char *GetBasename(char *arg0)
{
    int cmdlen = strlen(arg0);
    /* Strip trailing slashes if any */
    while (arg0[cmdlen-1] == '/') {
        arg0[cmdlen-1] = '\0';
        cmdlen--;
    }

    /* Locate the last slash */
    char *start = strrchr(arg0, '/');
    if (start == NULL) {
        return arg0;
    }
    start++;

    int basenamelen = strlen(start);
    char *basename = malloc(basenamelen*sizeof(char)+1);
    strncpy(basename, start, basenamelen+1);
    return basename;
}

int main()
{
    char* test = GetBasename("/foo/bar");
    printf("%s\n", test);
    free(test);
    return 0;
}  
firas@av104151 ~ % gcc -std=c99 -pedantic -Wall -Wextra -o test test.c
firas@av104151 ~ % ./test                                             
bar

```

---

### Post by the_unforgiven on 2012-06-04
Why not simply use [strrchr()]("http://linux.die.net/man/3/strrchr")?

Here is something I cooked up in 5 mins.
```

#include <stdio.h>
#include <string.h>

const char* get_basename(const char* arg)
{
    char* slash = strrchr(arg, '/');
    if (slash == NULL) 
        return arg;
    else if (slash == arg)
        return (arg + 1);
    else
        return (slash + 1);
}

int main(int argc, char** argv)
{
    if (argc < 2) {
        fprintf(stderr, "ERR: No argument passed\n");
        return -1;
    }

    const char *tmp = get_basename(argv[1]);
    printf("Got basename: %s\n", tmp); 
    return 0;
}

```

Does this help?

---

### Post by dodle on 2012-06-04
> **the_unforgiven said:**
> ```

#include <stdio.h>
#include <string.h>

const char* get_basename(const char* arg)
{
    char* slash = strrchr(arg, '/');
    if (slash == NULL) 
        return arg;
    else if (slash == arg)
        return (arg + 1);
    else
        return (slash + 1);
}

int main(int argc, char** argv)
{
    if (argc < 2) {
        fprintf(stderr, "ERR: No argument passed\n");
        return -1;
    }

    const char *tmp = get_basename(argv[1]);
    printf("Got basename: %s\n", tmp); 
    return 0;
}

```

Wow, that is brilliant.

[php]int main()
{
  char* hello = "hello my name is FREEDOM!!!";
  char* base = strrchr(hello, 'l');
  printf(base + 1);
  
  return 0;
}[/php]

output:
```
o my name is FREEDOM!!!
```

I really should take some more time to study the C/C++ documentation. But I still don't understand why my code didn't work. Arent' I returning the same type of data as you (char*)?

My code:
[php]char basename[basenamelen]; // = char*
...
return basename;[/php]

the_unforgiven's code:
[php]char* slash = strrchr(arg, '/'); // = char*
...
return (slash + 1);[/php]


**----- EDIT -----**

> **Bachstelze said:**
> ```
    int cmdlen = strlen(arg0);
    /* Strip trailing slashes if any */
    while (arg0[cmdlen-1] == '/') {
        arg0[cmdlen-1] = '\0';
        cmdlen--;
    }
```

Thanks, very useful.

---

### Post by Bachstelze on 2012-06-04
Read my post #4.

---

### Post by dodle on 2012-06-04
> **Bachstelze said:**
> Read my post #4.

Okay, I changed the following line:
[php]for (x = 0; x < strlen(basename); x++)[/php]

to:
[php]for (x = 0; x < basenamelen; x++)[/php]

But, I still get an empty string. Maybe I didn't understand you?

---

### Post by Bachstelze on 2012-06-04
Not sure what you did exactly; this works here:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char* GetBasename(char* arg0)
{
    int cmdlen = strlen(arg0);
    int lastdir, hassubdir = 0;

    int x;
    for (x = 0; x < cmdlen; x++) {
        if (arg0[x] == '/') {
            hassubdir = 1;
            lastdir = x;
        }
    }

    if (!hassubdir) {
        return arg0;
    }

    int start = (lastdir + 1);
    int basenamelen = (cmdlen - start);
    char* basename = malloc((basenamelen+1)*sizeof(char));
    for (x = 0; x < basenamelen; x++) {
        basename[x] = arg0[start];
        start++;
    }
    basename[x] = '\0';
    return basename;
}

int main()
{
    char* test = GetBasename("/foo/bar");
    printf("%s\n", test);
    free((void*)test);
    return 0;
}
```

---

### Post by dodle on 2012-06-04
Thanks for the help everyone. Here is what I am going with for now:

[php]char* GetBasename(char* arg0)
{
  int cmdlen = strlen(arg0);
  int hassubdir = 0;
  
  int x;
  for (x = 0; x < cmdlen; x++)
  {
    if (arg0[x] == '/') hassubdir = 1;
  }
  
  if (!hassubdir) return arg0;
  
  char* basename = strrchr(arg0, '/');
  basename++;
  
  return basename;
}[/php]

---

### Post by the_unforgiven on 2012-06-04
> **dodle said:**
> Thanks for the help everyone. Here is what I am going with for now:

[php]char* GetBasename(char* arg0)
{
  int cmdlen = strlen(arg0);
  int hassubdir = 0;
  
  int x;
  for (x = 0; x < cmdlen; x++)
  {
    if (arg0[x] == '/') hassubdir = 1;
  }
  
  if (!hassubdir) return arg0;
  
  char* basename = strrchr(arg0, '/');
  basename++;
  
  return basename;
}[/php]

Yes, this code will work - however, as an optimization you don't need the loop to check for hassubdir...
strrchr() is already doing that work for you :)

strrchr() returns NULL if the second argument is not found in the first; returns the **position** of the second argument within the first if it is found.

Let me explain with my code:
1. Let the reverse-search begin :)
```
    char* slash = strrchr(arg, '/'); 
```

2. If '/' is not found in the argument, then the argument itself is the basename:
```
    
if (slash == NULL) 
        return arg;

```

3. 'slash == arg' checks to see if the pointers coincide - in other words, if (slash == &arg[0]) (another way to say the same thing is if ('/' == arg[0])) - in which case, we just need to strip the slash and return the arg as is (i.e. return the string starting from arg[1]):
```

    else if (slash == arg)
        return (arg + 1);

```

4. else, since we found a slash somewhere in between the start and end, return the string starting from slash[1] within the original string:
```

    else
        return (slash + 1);

```

So, in these 4 simple steps, you can avoid buffer issues as well as have a simple yet optimized code ;)

Remember, at all times, the string returned from get_basename() is actually part of the original string passed as argument - you never need to copy out of it and hence, don't need a separate buffer.

Also, the string buffer passed as argument is always alive within the context of the caller - so, it's safe to return part of it without worrying about it getting freed because of stack frame.

Hope this helps ;)

---

### Post by dwhitney67 on 2012-06-04
> **the_unforgiven said:**
> 
```

const char* get_basename(const char* arg)
{
    char* slash = strrchr(arg, '/');
    if (slash == NULL) 
        return arg;
    else if (slash == arg)
        return (arg + 1);
    else
        return (slash + 1);
}


I took your code to augment it to handle additional cases; here's the modified code:
[code]
char* get_basename(char* arg)
{
    char* slash = strrchr(arg, '/');

    if (slash == NULL)
        return arg;

    else if (slash == arg)
        return strlen(arg) == 1 ? arg : arg + 1;

    else if (slash == arg + 1)
    {
        *slash = '\0';
        return arg;
    }

    return (slash + 1);
}

```

Additional cases could be:
[LIST]
[*]/
[*]<blah>/
[/LIST]

The Linux 'basename' command will return / (slash) for the first item above, and will return <blah> for the second item.

---

### Post by the_unforgiven on 2012-06-04
> **dwhitney67 said:**
> I took your code to augment it to handle additional cases; here's the modified code:
```

char* get_basename(char* arg)
{
    char* slash = strrchr(arg, '/');

    if (slash == NULL)
        return arg;

    else if (slash == arg)
        return strlen(arg) == 1 ? arg : arg + 1;

    else if (slash == arg + 1)
    {
        *slash = '\0';
        return arg;
    }

    return (slash + 1);
}

```

Additional cases could be:
[LIST]
[*]/
[*]<blah>/
[/LIST]

The Linux 'basename' command will return / (slash) for the first item above, and will return <blah> for the second item.
Cool. Thanks for the additional fixes... ;)

Here is my version with the same fixes:
```

const char* get_basename(char* arg)
{
    size_t l = strlen(arg);
    char* slash = strrchr(arg, '/');
    if (slash == NULL) {
        return arg;
    } else if (slash == arg) {
        // As per dwhitney67's fix - for case 1.
        return (l == 1 ? arg : (arg + 1));
    } else if (slash == (arg + l - 1)) {
        /*
         * slightly modified version of dwhitney67's fix - for case 2..
         * - using recursive call to get_basename() *after* stripping the last '/' - as in <blah>/
         */
        arg[l - 1] = 0;
        return get_basename(arg);
    } else {
        return (slash + 1);
    }
}

```

---

### Post by Bachstelze on 2012-06-04
How about [font=monospace]blah///////[/font]? ;)

---

### Post by dodle on 2012-06-04
Thanks, I appreciate the help. This will work great!

---

### Post by the_unforgiven on 2012-06-04
> **Bachstelze said:**
> How about [font=monospace]blah///////[/font]? ;)
With my latest code, it will still return 'blah' ;)

---

### Post by Bachstelze on 2012-06-04
Oh, yeah. I didn't read it in detail. I still vastly prefer mine. :D

---


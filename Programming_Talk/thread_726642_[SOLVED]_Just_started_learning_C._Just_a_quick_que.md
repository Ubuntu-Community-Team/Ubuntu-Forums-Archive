---
title: "[SOLVED] Just started learning C. Just a quick question..."
date: 2008-03-16
forum: Programming Talk
---

### Post by Nerdriot on 2008-03-16
Hi,

So, I just started learning C a couple of days ago, from this tutorial I found ([http://aelinik.free.fr/c/index.html]("http://aelinik.free.fr/c/index.html")), and I'm a little confused about one thing...

In the tutorial, and example like this was given:

```
int whatever ( int we1, int we2 )
{
     int yep;
     yep = we1 * we2;
     return yup;
}
```

And then later, in "main()", you'd have to do this:

```
main()
{
...
     int finally;
     finally = yup ( we1, we2 );
}

```

And THEN, when you wanted to call it, you'd just do something like this:

```
printf ( "Numbers multipled equal: %d", yup );
```

Well, it seems like to me, it'd be simpler to, when you're defining "whatever", just use a simple "return we1 * we2*;", and then later in the code, use it as "whatever ( we1, we2 )".

Is there something wrong with doing it that way? I'm a noob at this, obviously, but I've tested both ways, and it seems like the former requires more "effort", while the way I was doing it, just simply gets it done. Am I wrong?

Thanks!

---

### Post by LaRoza on 2008-03-16
You are write, there are many variables that do not need to be.

[php]
#include <stdio.h>

int whatever(int we1, int we2 )
{
     return we1 * we2;
}

int main(void)
{
    printf("Numbers multipled equal: %d", whatever(we1, we2));
    return 0;
}
[/php]

---

### Post by Nerdriot on 2008-03-16
Thank you :)

It just didn't seem like it made much sense to basically repeat the same thing over and over, just to give it a different name.

The tutorial is helpful, so I guess I can't complain... ;)

Anyway, thanks again! I'll mark the thread solved.

---


---
title: "[C++] Printing &quot;01&quot; in Place of &quot;1&quot;"
date: 2010-05-11
forum: Programming Talk
---

### Post by dodle on 2010-05-11
I just read how to do this two days ago, but can't remember where I saw it.  What I am trying to do is take in integer value ```
int x = 1;
``` and have it print out to the console as ```
01
```

---

### Post by dwhitney67 on 2010-05-11
This should work:
```

#include <iostream>
#include <iomanip>

int main()
{
   int i = 1;

   std::cout << std::setw(2) << std::setfill('0') << i << std::endl;
}

```

setw    == set width
setfill == set unused spaces to the given character

Read more here:  [http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

---

### Post by Tony Flury on 2010-05-11
I would do it like this : 

```

fprint(stdout, "%c%d", (i>0 &&i<=9)?'0':'', i);

or in pure c++

cout << (i>0 && i<=9)?'0':'' << i;

```

The conditional operator outputs a '0' character if i is between 0 and 9.

---

### Post by dodle on 2010-05-11
> **dwhitney67 said:**
> ```

#include <iostream>
#include <iomanip>

int main()
{
   int i = 1;

   std::cout << std::setw(2) << std::setfill('0') << i << std::endl;
}

```

Thanks, that does the trick.

@Tony Flury:  I couldn't get your code to work.  The compiler complained about an empty character constant.
> **Tony Flury said:**
> ```

cout << (i>0 && i<=9)?'0':'' << i;

```

But your code did lead me to do this (which I should have been able to figure out on my own >.<):```
if (i>0 && i<10)
    cout << 0;
  cout << i;
```

---

### Post by Tony Flury on 2010-05-11
> **dodle said:**
> Thanks, that does the trick.

@Tony Flury:  I couldn't get your code to work.  The compiler complained about an empty character constant.


I do say in my disclaimer that code is not tested ;-)

try
```

cout << (i>=0 && a<=9)?"0":"" << i;

```
I forgot you can't do an empty character - but of course you can do empty strings - dwhitney's solution is "smarter" though.

> 
But your code did lead me to do this (which I should have been able to figure out on my own >.<):```
if (i>0 && i<10)
    cout << 0;
  cout << i;
```

That works but is two lines which could be inadvertantly seperated etc. I would instinctively go with a one line solution to keep it all together.

---

### Post by raf_kig on 2010-05-11
```
printf("%02d", i);
```

---


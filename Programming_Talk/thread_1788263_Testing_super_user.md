---
title: "Testing super user"
date: 2011-06-22
forum: Programming Talk
---

### Post by zobayer1 on 2011-06-22
I want to test if current user is a super user. I think the root is a super user. But is it true that, only root is the super user?

Here is a simple algorithm:
```

#include <iostream>
#include <string>
#include <cstdlib>
using namespace std;

int main()
{
        string name = getenv("USER");
        if(name == "root") cout << "super user\n";
        else cout << "not a super user\n";
        return 0;
}

```

I am pretty much sure this is not the way. Can anyone tell me how can I say current user is super user or not.

Thanks in advance. ;)

---

### Post by dwhitney67 on 2011-06-22
Ha!  Don't use USER for comparisons; that environment variable can be spoofed.

Use geteuid() or getuid() instead.  I tend to see most applications use the former.

---

### Post by zobayer1 on 2011-06-22
> **dwhitney67 said:**
> Ha!  Don't use USER for comparisons; that environment variable can be spoofed.

Use geteuid() or getuid() instead.  I tend to see most applications use the former.

I also think so, using getenv() is not a good way.
But can you tell how to check is a userid is superuser ?

---

### Post by dwhitney67 on 2011-06-22
> **zobayer1 said:**
> I also think so, using getenv() is not a good way.
But can you tell how to check is a userid is superuser ?

I indicated which functions you can use in my previous post.

Here's a simple example:
```

#include <unistd.h>
#include <iostream>

int main()
{
   uid_t uid = geteuid();

   if (uid != 0)
   {
      std::cout << "You are not root!" << std::endl;
      return -1;
   }

   // ...
}

```

---

### Post by zobayer1 on 2011-06-22
Ok, so the root and super user is same always? I know that, root is set to id 0. So, is it something like, when a user is supposed to be super user, its effective id is 0 ?

Also, thanks for your help.

---

### Post by dwhitney67 on 2011-06-22
> **zobayer1 said:**
> Ok, so the root and super user is same always? I know that, root is set to id 0. So, is it something like, when a user is supposed to be super user, its effective id is 0 ?

Also, thanks for your help.

On certain Linux systems, such as Ubuntu, there is a root account, however its password is not set/enabled.  Thus one cannot login as root.  However, the admin-user on the system can use 'sudo' to effectively become the root user.  When the user is operating as root, their effective user-id is indeed 0.

Thus the program I presented earlier would deny a user who has not invoked 'sudo' or is not logged in as root.

---

### Post by zobayer1 on 2011-06-22
Now it is clear to me, thanks for your time :)

---

### Post by johnl on 2011-06-22
Can you tell us why you want to check if the user is root?  You might be able to accomplish what you want to do in an alternate manner, like checking if the current user has the capability (libcap-dev, sys/capability.h) required to perform some task.

---

### Post by zobayer1 on 2011-06-22
> **johnl said:**
> Can you tell us why you want to check if the user is root?  You might be able to accomplish what you want to do in an alternate manner, like checking if the current user has the capability (libcap-dev, sys/capability.h) required to perform some task.

I try linux system programming just to learn, and have fun, I am not doing anything professional level job. I was exploring **ls** program, and trying to write something similar myself, then I've found, that, -A option is set by default to super user, thats why I asked, how can I say if the program was invoked by a super user.

Thats all :) But thanks for your reply as well, I will take a look on those...

---


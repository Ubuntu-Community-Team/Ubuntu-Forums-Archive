---
title: "Determine user privileges?"
date: 2008-09-18
forum: Programming Talk
---

### Post by ensis2k on 2008-09-18
Is there a way to tell from within C if the user who executed the app is a super user? Or to be more specific: Does my application has access to system functions like "mlockall".

I do not want to realize in the middle of my app that necessary functions do not work properly because of that. So at startup I want to specifically check if the app is allowed to do so and return a proper error message if not.

Thanks in advance.

---

### Post by dwhitney67 on 2008-09-18
Try getuid().  If the value returned is 0, then you have superuser privileges; otherwise you do not.

[PHP]#include <unistd.h>
#include <stdio.h>

int main()
{
  printf( "uid = %d\n", getuid() );
  return 0;
}[/PHP]

---

### Post by ensis2k on 2008-09-19
Thank you. It works now. 
:guitar:

---


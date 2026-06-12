---
title: "The simple function from OpenGL crashes on Ubuntu 8.10"
date: 2009-01-28
forum: Programming Talk
---

### Post by Evgeny_chernov on 2009-01-28
I executed the following program on Ubuntu 8.10 on my virtual machine and on the same system on my notebook:
```

#include <GL/gl.h>

int main()
{
   GLfloat color[4];
   glGetFloatv(GL_CURRENT_COLOR, color);
   return 0;
}

```
And everywhere this program crashed on the line with glGetFloatv.

On the other distributions (like Fedora 10, OpenSUSE 11.1, RHEL 4) it didn't crash.

Does it crash only on my Ubuntu or on all ones?
And what is reason of this crash?

I'll be very pleased for any help.

---

### Post by Rocket2DMn on 2009-01-28
Moved to Programming Talk, you will probably get better help here.

---

### Post by Zugzwang on 2009-01-28
> **Evgeny_chernov said:**
> 
And everywhere this program crashed on the line with glGetFloatv.


Are you sure that you do not have to initialise the OpenGL library before using? If that is necessary and you do not do so, the result is undefined, i.e. might be different everywhere.

---


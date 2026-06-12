---
title: "Screen Issue"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Aeph on 2008-08-05
I recently helped a friend install Ubuntu on his computer, and he decided to hook it up to his TV. When he does this, the sides of the screen as well as the top and bottom are cut off. I do not know how to fix this. Is there anyone here who does?

---

### Post by overdrank on 2008-08-05
> **Aeph said:**
> I recently helped a friend install Ubuntu on his computer, and he decided to hook it up to his TV. When he does this, the sides of the screen as well as the top and bottom are cut off. I do not know how to fix this. Is there anyone here who does?

Hi and what is the model of the graphics card>
You can try the command ```
gksu displayconfig-gtk
```and set up there.

---

### Post by Aeph on 2008-08-05
> **overdrank said:**
> Hi and what is the model of the graphics card>


It's an NVIDIA 9600GT.

---

### Post by overdrank on 2008-08-05
> **Aeph said:**
> It's an NVIDIA 9600GT.

Ok then if nvidia, install the nvidia drivers and settings then use the  command ```
gksu nvidia-settings 
``` and setup the extra monitor there.

---


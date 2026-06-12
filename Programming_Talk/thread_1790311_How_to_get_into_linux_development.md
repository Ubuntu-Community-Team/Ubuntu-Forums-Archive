---
title: "How to get into linux development"
date: 2011-06-24
forum: Programming Talk
---

### Post by alegomaster on 2011-06-24
What steps do I need to take to get into a Linux OS development team . Right now I have basic knowledge of C, and computer science. I know it will take a while but can someone point out good books or webpages that can help me learn more about Linux OS development.

---

### Post by trent.josephsen on 2011-06-24
The most helpful webpages you'll find probably end in .edu, and I'm not talking about instructional materials.

There's an analogy involving the correct order of a cart and a horse that I believe would be appropriate here.  While I admire your decisiveness, kernel development (or, really, any specific technical field) isn't something you can get into overnight.  By the time you acquire the knowledge to tell you whether it's really something you want to do or not, you won't need us to tell you how to get started.

However, there are things you can do that are part of or closely related to OS development, just to test the waters.  I imagine writing your own shell, driver or bootloader would qualify here.  I defer to the superior expertise of the OS devs among us.

$0.02

---

### Post by kagov on 2011-06-25
> **trent.josephsen said:**
> The most helpful webpages you'll find  probably end in .edu, and I'm not talking about instructional materials.

There's an analogy involving the correct order of a cart and a horse  that I believe would be appropriate here.  While I admire your  decisiveness, kernel development (or, really, any specific technical  field) isn't something you can get into overnight.  By the time you  acquire the knowledge to tell you whether it's really something you want  to do or not, you won't need us to tell you how to get started.

However, there are things you can do that are part of or closely related  to OS development, just to test the waters.  I imagine writing your own  shell, driver or bootloader would qualify here.  I defer to the  superior expertise of the OS devs among us.

$0.02

This ^

and if you can read and understand code, why don't you take a look at the source of a pre-created Linux OS?

---

### Post by martinr on 2011-06-25
Unix Software Development, Unix Press, 1992, ISBN 0130176907

---

### Post by JupiterV2 on 2011-06-25
It also depends by what you mean by Linux development. Do you want to improve the whole linux platform by developing applications, tool or libraries generic to all distributions? Are you interested in kernel development or core software (like coreutils). Are you interested in improving GCC, and by extension, any program compiled with said compiler. Do you want to only help a specific distribution like Ubuntu, Debian or Fedora? There are umpteen hundreds of ways to help and contribute.

---

### Post by alegomaster on 2011-06-25
I want to get  into kernel development, or something related to that. It seems like that the best way to get into that is to first work on Drivers and items like that. Is there any good books regarding kernel development or driver development.

---

### Post by d3v1150m471c on 2011-06-25
Like kagov said, downloading some drivers or kernels and inspecting the source code is a good start. As for books, google is our friend.
```

#search google with the following:
linux driver development tutorial filetype:pdf

```

---

### Post by alegomaster on 2011-06-25
> **d3v1150m471c said:**
> Like kagov said, downloading some drivers or kernels and inspecting the source code is a good start.

Do you know of any drivers or kernels that are easy to understand. Like I said before I am not an expert with C so a driver or kernel with a simpler source code would be a better choice for me.

---

### Post by d3v1150m471c on 2011-06-25
[http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0")

---

### Post by alegomaster on 2011-06-25
> **d3v1150m471c said:**
> [http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0]("http://www.freesoftwaremagazine.com/articles/drivers_linux?page=0%2C0")

Thanks, guess like a have a bit of reading to do.

---

### Post by boast on 2011-06-25
I would think the best way to get started is to help with fixing reported bugs. Start with small bugs, and work your way up until you start getting good experience and can begin major projects on your own.

Or you can just try to dive straight into it. Guess it depends on you.

---

### Post by alegomaster on 2011-06-28
> **boast said:**
> I would think the best way to get started is to help with fixing reported bugs. Start with small bugs, and work your way up until you start getting good experience and can begin major projects on your own.

Or you can just try to dive straight into it. Guess it depends on you.

How should I do that

---


---
title: "How to open a file when shell scripting?"
date: 2012-11-29
forum: Programming Talk
---

### Post by Smythotech on 2012-11-29
Hey everyone,

I just got back into shell scripting and am just making a program for fun.  I'm using the terminal in Ubuntu 12.10 and am making a shell script.  

Now what I want to do is open a file that is the Documents directory.  It's a video file that I want to pop up at the end of the script.  

So how would i declare that in the script?

I was thinking something as simple as:

sudo open Sample.Avi /documents

But that didn't work.   Any ideas, or is this even possible?

---

### Post by newbie-user on 2012-11-29
You'd have to specify what program to use to open the video. Here's a quick script that will do what you want. It uses Totem to open the sample.avi file in the location /home/[user]/Documents/. Just copy the second line into whatever script you're writing.

```
#!/bin/bash

totem /home/[user]/Documents/sample.avi
```

---

### Post by Vaphell on 2012-11-29
you can try using **xdg-open**
it should call appropriate program based on the file type.

```
xdg-open some.file
```

---

### Post by Smythotech on 2012-11-29
> **newbie-user said:**
> You'd have to specify what program to use to open the video. Here's a quick script that will do what you want. It uses Totem to open the sample.avi file in the location /home/[user]/Documents/. Just copy the second line into whatever script you're writing.

```
#!/bin/bash

totem /home/[user]/Documents/sample.avi
```

Thank you very much, kind sir!

Worked like a charm!

---


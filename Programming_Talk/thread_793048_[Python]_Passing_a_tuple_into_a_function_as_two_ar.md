---
title: "[Python] Passing a tuple into a function as two arguments"
date: 2008-05-13
forum: Programming Talk
---

### Post by xelapond on 2008-05-13
I am writing a simple game in PyGlet just to get familiar with it, and had a question about tuples.  I have a tuple that holds the coordinates to an object.  To set this object to the tuple coordinates, I use the following line:
[php]ball_img.blit(BallPosition[0], BallPosition[1])[/php]Is there any way I can just pass the tuple as a whole so I do not have to address each coordinate individually?  It would be something like:
[php]ball_img.blit(BallPosition)[/php]Thanks, 

Alex

---

### Post by Wybiral on 2008-05-13
```

ball_img.blit(*BallPosition)

```

Likewise, you can expand kwargs with **dict

---

### Post by xelapond on 2008-05-13
Thanks, 

Just wondering, where do you learn all this stuff?  It seems you have an endless stack of Python wisdom:)

---

### Post by LaRoza on 2008-05-13
> **xelapond said:**
> Thanks, 

Just wondering, where do you learn all this stuff?  It seems you have an endless stack of Python wisdom:)

The Python docs?

---

### Post by Wybiral on 2008-05-13
> **LaRoza said:**
> The Python docs?

That, and Python is incredibly uniform about these things: "def f(*args, **kwargs)" called with "f(*sequence, **dict)"

---

### Post by pmasiar on 2008-05-13
many languages (starting with C) use *name as reference to name. Python does what you expect :-)

---


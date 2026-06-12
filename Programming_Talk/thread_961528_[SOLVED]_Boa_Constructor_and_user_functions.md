---
title: "[SOLVED] Boa Constructor and user functions"
date: 2008-10-28
forum: Programming Talk
---

### Post by MaxVK on 2008-10-28
Hi,

I am experimenting with Python and Boa Constructor and I am hitting a rather annoying problem.

I have a frame with a bunch of controls in it, and I am working through their functionality quite well, but the time has come where I need to write a function of my own.

However, having defined the function I found that I am getting an error about the wrong number of arguments, although I am passing the correct number.

The function is as follows:

```
def myfunc(arg1,arg2):
    ....
    ....
    Return theresult
```

To call it I am doing this:
```
x = myfunc(a,b)
```

However, the program halts at the point where I call the function, and gives me an error saying that the function requires 2 arguments and I gave it 3, which clearly I didn't.

I am assuming that I have created the function correctly, but of course that might not be the case - Just to clarify, the first time that this function is typed in the source is exactly as I have written it above, in other words Iv not 'defined' or otherwise set it up anywhere else.

Can anyone help me here please - Iv been searching for about 3 hours for this error, but I cant find anything that seems relevant to what I'm trying to do.

Regards

Max

---

### Post by Reiger on 2008-10-28
Python, eh? I heard something about Python implicitly passing the self object?

---

### Post by MaxVK on 2008-10-28
Hmm. Answered it myself.

It was a typo of sorts: The definition of the function was indented one time too many, which put it as a part of a frame by mistake. I have no idea where the wrong number of arguments error came from, but as soon as I out-dented the function it worked fine.

Never mind - live and learn

Regards

Max

---


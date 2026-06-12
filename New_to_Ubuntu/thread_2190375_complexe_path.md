---
title: "complexe path"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by raphael-cardinaux on 2013-11-27
Hello everybody,

I am using matlab everyday and the path is pretty complicated :
```
cd ../../usr/local/MATLAB/R2013a/bin

```
and only after that I can run it with ```
./matlab
```

Is there a way I could like save the path somewhere and with a simple command run my program?

---

### Post by jdeca57 on 2013-11-27
A simple bash script? 
Make a file matlab.sh with the #!/bin/bash and the commands you want in it. 
$chmod +x matlab.sh
./matlab.sh

---

### Post by Topsiho on 2013-11-27
In Octave, which is almost a 1:1 clone of Matlab (just as Linux is of Unix), you can use savepath().
Try to find out how to use this in Matlab, if it indeed is possible there.
Do not use Octave often, so can't help you here.

Topsiho

---

### Post by raphael-cardinaux on 2013-11-27
Thanks for the quick answers!

---

### Post by thatredbird on 2013-11-28
Seems like you could set up an alias too

alias name='command'

---


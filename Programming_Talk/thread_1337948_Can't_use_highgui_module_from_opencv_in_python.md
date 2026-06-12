---
title: "Can't use highgui module from opencv in python"
date: 2009-11-25
forum: Programming Talk
---

### Post by sephirot_5 on 2009-11-25
Well, I have a very important school project in wich I must implement some pattern recognition on maps. I chose opencv + python to do it.

I wanted to start testing algorithms for this purpouse, so I installed all opencv bin and dev packages i found in the repos (including the python ones).

I was testing if modules were loading correctly, and by running this simple python script

```

import sys
from opencv import *


if __name__=='__main__':
    img = highgui.cvLoadImage(argv[1])

```

I got this error:

```

NameError: name 'highgui' is not defined
File "/home/fabrizio/Projects/pyopencv/prueba.py", line 9, in <module>
  img = highgui.cvLoadImage(argv[1])

```

As you can see, opencv module is loading ok, but i have no luck with thehighgui one.

This project is very important, and I REALLY don't want to code on Windows just because this little error. Please help me oh Benevolent Ubuntu wizards... (:

---

### Post by ravindra.rajaram on 2009-11-26
I'm new to python, but I think this shud solve ur problem:

```
from opencv import highgui
```

---

### Post by sephirot_5 on 2009-11-26
> **ravindra.rajaram said:**
> I'm new to python, but I think this shud solve ur problem:

```
from opencv import highgui
```

I already tried that, no luck. I get the very same error :(

help.. pleaseee.....

---

### Post by nelfin on 2009-11-26
Chances are if Python's throwing a NameError, it's exactly what it means, that there's no highgui.

Try:
```
import opencv
print opencv.__all__
# print(opencv.__all__) if you're running 3.x
```

and see if 'highgui' is in there somewhere

---

### Post by sephirot_5 on 2009-11-26
> **nelfin said:**
> Chances are if Python's throwing a NameError, it's exactly what it means, that there's no highgui.

Try:
```
import opencv
print opencv.__all__
# print(opencv.__all__) if you're running 3.x
```

and see if 'highgui' is in there somewhere

It shows ther's no highgui module, indeed. Problem is, it _is_ supoused to be. Look at this -> [http://www.numenta.com/for-developers/software/pydoc/opencv.highgui.html](http://www.numenta.com/for-developers/software/pydoc/opencv.highgui.html)

I looked a little deeper in this problem. I found where python-opencv is installed (/var/lib/python-support/python2.6/opencv): there I can find several importable modules from opencv, including the so mentioned highgui one. No need to say the highgui one is the only i cannot import...

---

### Post by sephirot_5 on 2009-11-26
Ok guys, thank you. After rebooting my pc (it had been on for weeks), i was finally able to load that little dirty module. I'm not sure what happened (maybe my enviroment was not properly set until rebooting?), but all is up and running. Thanks again, I'm counting on you next time i have an linux-related programming question. Right? (:

---


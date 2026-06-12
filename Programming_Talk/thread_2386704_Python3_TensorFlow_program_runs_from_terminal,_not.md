---
title: "Python3 TensorFlow program runs from terminal, not from my IDE"
date: 2018-03-09
forum: Programming Talk
---

### Post by john_ladasky on 2018-03-09
Hi there,

I'm not yet sure whether this problem I'm having is specific to TensorFlow.  Any of you who are using it probably know that TensorFlow is not (and may never be?) in the Canonical repositories.  You have to turn all kinds of cartwheels to get it installed.

Three months ago I did have TensorFlow with GPU capability installed on my Ubuntu 17.10 system.  I use the system Python 3.6.  I could write and execute programs fine.  I also use an IDE called Geany.  You have to tell it you want to use the Python3 interpreter, because it comes out of the box calling Py2 by default.  Anyway, I know how to do that.

I had to do a full system reinstall.  I can still run my TensorFlow Py3 scripts from the terminal, but no longer from the Geany IDE.  This is bizarre.

Here is a very short diagnostic program:

```
import sys
print("\nPython version:")
print(sys.version)
import tensorflow as tf
print("\nTensorFlow version:")
print(tf.__version__)

```

Here is the output from a terminal session (yes, I know about the RuntimeWarning, I had the same warning when everything was working the last time):

```
Python version:
3.6.3 (default, Oct  3 2017, 21:45:48) 
[GCC 7.2.0]
/usr/lib/python3.6/importlib/_bootstrap.py:219: RuntimeWarning: compiletime version 3.5 of module 'tensorflow.python.framework.fast_tensor_util' does not match runtime version 3.6
  return f(*args, **kwds)

TensorFlow version:
1.4.0

```

But when I click the Execute button from Geany, here is my output:

```
Python version:
3.6.3 (default, Oct  3 2017, 21:45:48) 
[GCC 7.2.0]


Traceback (most recent call last):
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/pywrap_tensorflow.py", line 58, in <module>
    from tensorflow.python.pywrap_tensorflow_internal import *
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 28, in <module>
    _pywrap_tensorflow_internal = swig_import_helper()
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 24, in swig_import_helper
    _mod = imp.load_module('_pywrap_tensorflow_internal', fp, pathname, description)
  File "/usr/lib/python3.6/imp.py", line 243, in load_module
    return load_dynamic(name, filename, file)
  File "/usr/lib/python3.6/imp.py", line 343, in load_dynamic
    return _load(spec)
ImportError: libcudnn.so.6: cannot open shared object file: No such file or directory

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "tensorflow geany test.py", line 7, in <module>
    import tensorflow as tf
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/__init__.py", line 24, in <module>
    from tensorflow.python import *
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/__init__.py", line 49, in <module>
    from tensorflow.python import pywrap_tensorflow
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/pywrap_tensorflow.py", line 72, in <module>
    raise ImportError(msg)
ImportError: Traceback (most recent call last):
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/pywrap_tensorflow.py", line 58, in <module>
    from tensorflow.python.pywrap_tensorflow_internal import *
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 28, in <module>
    _pywrap_tensorflow_internal = swig_import_helper()
  File "/usr/local/lib/python3.6/dist-packages/tensorflow/python/pywrap_tensorflow_internal.py", line 24, in swig_import_helper
    _mod = imp.load_module('_pywrap_tensorflow_internal', fp, pathname, description)
  File "/usr/lib/python3.6/imp.py", line 243, in load_module
    return load_dynamic(name, filename, file)
  File "/usr/lib/python3.6/imp.py", line 343, in load_dynamic
    return _load(spec)
ImportError: libcudnn.so.6: cannot open shared object file: No such file or directory

Failed to load the native TensorFlow runtime.

```

The libcudnn.so.6 program is found when I execute from the terminal, but not from the Geany IDE.  It would appear that (as I intended) I am using the Ubuntu 17.10 system Python version 3.6.3 in both cases.  How is it possible for my program to behave differently?

I will also be asking questions of the TensorFlow folks... thanks for your insight!

---

### Post by monkeybrain20122 on 2018-03-09
Maybe because you put your LD_LIBRARY_PATH and cuda's PATH in .bashrc instead of .profile. GUI programs don't use environmental variables in .bashrc,  you have to put them in .profile (where both cli and gui programs will use them)

---

### Post by john_ladasky on 2018-03-12
Thank you monkeybrain20122, that was the reminder that I needed.  Only I ended up doing something a little more fundamental. 

 I needed TensorFlow applications to work from both the CLI and the GUI, and also from multiple user accounts.  That, I learned all over again, is achieved by modifying the base /etc/profile.  NVidia and TensorFlow's own installation guides do not cover this.

Adding this line to /etc/profile corrected the CUDA_PATH problems:

```
export CUDA_PATH=/usr/local/cuda/targets/x86_64-linux/lib
```

Check your installation details, the exact path you need to specify may vary.

However, trying to extend and/or modify LD_LIBRARY_PATH the same way did not work.  Eventually I rediscovered that you do that the way that is shown here:

[https://serverfault.com/questions/201709/how-to-set-ld-library-path-in-ubuntu](https://serverfault.com/questions/201709/how-to-set-ld-library-path-in-ubuntu)

I created a file called cuda.conf in /etc/ld.so.conf.d which reads:

```
# CUDA configuration, specifically for TensorFlow
/usr/local/cuda/lib64
/usr/local/cuda/extras/CUPTI/lib64
```

Then execute [B]sudo ldconfig.

[/B]Finally, there's one more problem: something in the execution chain expects to find a _symbolic link_ to [COLOR=#000000][FONT=&amp]libcudnn.so.6[/FONT][/COLOR] rather than the file itself!  When you try to invoke TensorFlow (even after a reboot) you will receive this error:

```
 /sbin/ldconfig: /usr/local/cuda/lib64/libcudnn.so.6 is not a symbolic link
```

To solve this last problem, proceed as shown here:   

[https://stackoverflow.com/questions/11542255/ldconfig-error-is-not-a-symbolic-link](https://stackoverflow.com/questions/11542255/ldconfig-error-is-not-a-symbolic-link)

Rename [COLOR=#000000][FONT=&amp]libcudnn.so.6[/FONT][/COLOR]  to something else, create a symbolic link to the file using **ln -s**, and name the _link_ [COLOR=#000000][FONT=&amp]libcudnn.so.6[/FONT][/COLOR].

This all feels like a terrible hack, but I can get it to work. I hope these instructions help someone else.  No doubt I'll need them again myself when I upgrade Ubuntu to 18.04 in a few months.

---

### Post by monkeybrain20122 on 2018-03-12
My set up is simpler (I am the only user)

I put these in my .profile
```
export PATH="/usr/local/cuda/bin:$PATH"
export LD_LIBRARY_PATH="/usr/local/cuda/lib64:$LD_LIBRARY_PATH"
```

/usr/local/cuda is a symlink I made to link to where Nvidia installed cuda, which is /usr/local/cuda-9.1 (I installed cuda from the .deb rather than the ./run file)

I don't use Geany, but importing tf works in spyder IDE as well as the terminal.

From spyder

```
Python 3.5.2 (default, Nov 23 2017, 16:37:01)
Type "copyright", "credits" or "license" for more information.

IPython 6.2.1 -- An enhanced Interactive Python.

import tensorflow as tf

tf.__version__
Out[2]: '1.5.0'
```

So it looks like you just need to put those two environmental variables in /etc/profile for system wide.

---

